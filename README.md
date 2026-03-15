from flask import Flask, render_template, request, redirect, url_for
from flask_sqlalchemy import SQLAlchemy
from flask_login import LoginManager, login_user, login_required, logout_user, UserMixin, current_user
from werkzeug.security import generate_password_hash, check_password_hash
import pandas as pd
import random
import os

app = Flask(__name__)

app.config["SECRET_KEY"] = "secret"
app.config["SQLALCHEMY_DATABASE_URI"] = "sqlite:///users.db"
app.config["UPLOAD_FOLDER"] = "uploads"

db = SQLAlchemy(app)

login_manager = LoginManager()
login_manager.init_app(app)


# -----------------------------
# DATABASE MODEL
# -----------------------------

class User(UserMixin, db.Model):

    id = db.Column(db.Integer, primary_key=True)

    username = db.Column(db.String(50), unique=True)
    password = db.Column(db.String(200))

    first_name = db.Column(db.String(50))
    last_name = db.Column(db.String(50))

    role = db.Column(db.String(10))


@login_manager.user_loader
def load_user(user_id):
    return User.query.get(int(user_id))


# -----------------------------
# INIT DATABASE
# -----------------------------

with app.app_context():

    db.create_all()

    if not os.path.exists("uploads"):
        os.mkdir("uploads")

    if not User.query.filter_by(username="admin").first():

        admin = User(
            username="admin",
            password=generate_password_hash("admin"),
            first_name="Admin",
            last_name="Admin",
            role="admin"
        )

        db.session.add(admin)
        db.session.commit()


# -----------------------------
# LOGIN
# -----------------------------

@app.route("/", methods=["GET","POST"])
def login():

    if request.method == "POST":

        username = request.form["username"]
        password = request.form["password"]

        user = User.query.filter_by(username=username).first()

        if user and check_password_hash(user.password, password):

            login_user(user)

            if user.role == "admin":
                return redirect("/admin")

            return redirect("/dashboard")

    return render_template("login.html")


# -----------------------------
# ADMIN PAGE
# -----------------------------

@app.route("/admin", methods=["GET","POST"])
@login_required
def admin():

    if current_user.role != "admin":
        return "Access denied"

    if request.method == "POST":

        new_user = User(

            username=request.form["username"],
            password=generate_password_hash(request.form["password"]),

            first_name=request.form["first_name"],
            last_name=request.form["last_name"],

            role=request.form["role"]
        )

        db.session.add(new_user)
        db.session.commit()

    users = User.query.all()

    return render_template(
        "admin.html",
        users=users
    )


# -----------------------------
# USER DASHBOARD
# -----------------------------

@app.route("/dashboard")
@login_required
def dashboard():

    return render_template(
        "dashboard.html",
        user=current_user
    )


# -----------------------------
# DATASET UPLOAD
# -----------------------------

@app.route("/upload", methods=["POST"])
@login_required
def upload():

    file = request.files["file"]

    path = os.path.join(app.config["UPLOAD_FOLDER"], file.filename)

    file.save(path)

    df = pd.read_csv(path)

    # тестовые значения метрик модели
    accuracy = round(random.uniform(0.7,0.95),3)
    loss = round(random.uniform(0.1,0.4),3)

    return render_template(
        "analytics.html",
        accuracy=accuracy,
        loss=loss
    )


# -----------------------------
# LOGOUT
# -----------------------------

@app.route("/logout")
@login_required
def logout():

    logout_user()

    return redirect("/")


# -----------------------------

if __name__ == "__main__":
    app.run(debug=True)

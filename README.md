from flask import Flask, render_template, request, redirect
from flask_sqlalchemy import SQLAlchemy
from flask_login import LoginManager, login_user, login_required, logout_user, UserMixin, current_user
from werkzeug.security import generate_password_hash, check_password_hash

import pandas as pd
import numpy as np
import os

from sklearn.model_selection import train_test_split
from sklearn.preprocessing import LabelEncoder, StandardScaler

import tensorflow as tf
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Dense

app = Flask(__name__)

app.config["SECRET_KEY"] = "secret"
app.config["SQLALCHEMY_DATABASE_URI"] = "sqlite:///users.db"
app.config["UPLOAD_FOLDER"] = "uploads"

db = SQLAlchemy(app)

login_manager = LoginManager()
login_manager.init_app(app)

# -----------------------
# DATABASE MODEL
# -----------------------

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


# -----------------------
# INIT DATABASE
# -----------------------

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


# -----------------------
# LOGIN
# -----------------------

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


# -----------------------
# ADMIN
# -----------------------

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

    return render_template("admin.html", users=users)


# -----------------------
# USER DASHBOARD
# -----------------------

@app.route("/dashboard")
@login_required
def dashboard():

    return render_template(
        "dashboard.html",
        user=current_user
    )


# -----------------------
# TRAIN MODEL
# -----------------------

@app.route("/upload", methods=["POST"])
@login_required
def upload():

    file = request.files["file"]

    path = os.path.join(app.config["UPLOAD_FOLDER"], file.filename)

    file.save(path)

    df = pd.read_csv(path)

    # -------------------
    # DATA PREPARATION
    # -------------------

    X = df.iloc[:, :-1].values
    y = df.iloc[:, -1].values

    encoder = LabelEncoder()
    y = encoder.fit_transform(y)

    scaler = StandardScaler()
    X = scaler.fit_transform(X)

    X_train, X_test, y_train, y_test = train_test_split(
        X, y, test_size=0.2
    )

    # -------------------
    # TENSORFLOW MODEL
    # -------------------

    model = Sequential()

    model.add(Dense(64, activation="relu", input_shape=(X.shape[1],)))
    model.add(Dense(32, activation="relu"))
    model.add(Dense(len(np.unique(y)), activation="softmax"))

    model.compile(
        optimizer="adam",
        loss="sparse_categorical_crossentropy",
        metrics=["accuracy"]
    )

    history = model.fit(
        X_train,
        y_train,
        epochs=10,
        validation_split=0.2,
        verbose=0
    )

    loss, accuracy = model.evaluate(X_test, y_test, verbose=0)

    accuracy = round(float(accuracy),3)
    loss = round(float(loss),3)

    epochs = list(range(1,11))
    val_accuracy = history.history["val_accuracy"]

    return render_template(
        "analytics.html",
        accuracy=accuracy,
        loss=loss,
        epochs=epochs,
        val_accuracy=val_accuracy
    )


# -----------------------
# LOGOUT
# -----------------------

@app.route("/logout")
@login_required
def logout():

    logout_user()

    return redirect("/")


# -----------------------

if __name__ == "__main__":
    app.run(debug=True)

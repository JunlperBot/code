import numpy as np
import librosa
import tensorflow as tf

from flask import Flask, request, jsonify, render_template
from flask_sqlalchemy import SQLAlchemy

from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Dense, Conv1D, MaxPooling1D, Flatten

from sklearn.preprocessing import LabelEncoder
from collections import Counter


####################################
# FLASK CONFIG
####################################

app = Flask(__name__)

app.config["SQLALCHEMY_DATABASE_URI"] = "sqlite:///users.db"

db = SQLAlchemy(app)


####################################
# DATABASE
####################################

class User(db.Model):

    id = db.Column(
        db.Integer,
        primary_key=True
    )

    login = db.Column(
        db.String(50),
        unique=True
    )

    password = db.Column(
        db.String(50)
    )

    name = db.Column(
        db.String(50)
    )

    surname = db.Column(
        db.String(50)
    )

    role = db.Column(
        db.String(10)
    )


####################################
# AUTH FUNCTIONS
####################################

def authenticate(login, password):

    user = User.query.filter_by(
        login=login,
        password=password
    ).first()

    return user


def create_user(login, password, name, surname, role):

    user = User(
        login=login,
        password=password,
        name=name,
        surname=surname,
        role=role
    )

    db.session.add(user)
    db.session.commit()


####################################
# AUDIO FEATURE EXTRACTION
####################################

def extract_features(wav):

    y, sr = librosa.load(wav, sr=16000)

    mfcc = librosa.feature.mfcc(
        y=y,
        sr=sr,
        n_mfcc=40
    )

    return np.mean(mfcc.T, axis=0)


####################################
# DATASET LOADER
####################################

def load_dataset(path):

    data = np.load(path, allow_pickle=True)

    train_x = data["train_x"]
    train_y = data["train_y"]

    valid_x = data["valid_x"]
    valid_y = data["valid_y"]

    encoder = LabelEncoder()

    train_y = encoder.fit_transform(train_y)
    valid_y = encoder.transform(valid_y)

    X_train = []
    X_valid = []

    for wav in train_x:
        X_train.append(extract_features(wav))

    for wav in valid_x:
        X_valid.append(extract_features(wav))

    X_train = np.array(X_train)
    X_valid = np.array(X_valid)

    return X_train, train_y, X_valid, valid_y


####################################
# MODEL
####################################

def create_model(num_classes):

    model = Sequential()

    model.add(
        Conv1D(
            64,
            3,
            activation="relu",
            input_shape=(40,1)
        )
    )

    model.add(MaxPooling1D(2))

    model.add(
        Conv1D(
            128,
            3,
            activation="relu"
        )
    )

    model.add(MaxPooling1D(2))

    model.add(Flatten())

    model.add(
        Dense(
            128,
            activation="relu"
        )
    )

    model.add(
        Dense(
            num_classes,
            activation="softmax"
        )
    )

    model.compile(
        optimizer="adam",
        loss="sparse_categorical_crossentropy",
        metrics=["accuracy"]
    )

    return model


####################################
# TRAIN MODEL
####################################

def train_model(dataset_path):

    X_train, y_train, X_valid, y_valid = load_dataset(dataset_path)

    X_train = X_train.reshape(-1,40,1)
    X_valid = X_valid.reshape(-1,40,1)

    num_classes = len(set(y_train))

    model = create_model(num_classes)

    history = model.fit(
        X_train,
        y_train,
        validation_data=(X_valid,y_valid),
        epochs=30,
        batch_size=32
    )

    model.save("alien_model.h5")

    return history


####################################
# ANALYTICS
####################################

def class_distribution(labels):

    return dict(Counter(labels))


def top5_classes(labels):

    counts = Counter(labels)

    return counts.most_common(5)


####################################
# LOAD MODEL
####################################

try:
    model = tf.keras.models.load_model("alien_model.h5")
except:
    model = None


####################################
# ROUTES
####################################

@app.route("/")
def login_page():

    return render_template("login.html")


@app.route("/login", methods=["POST"])
def login():

    login = request.form["login"]
    password = request.form["password"]

    user = authenticate(login, password)

    if user:

        return render_template(
            "dashboard.html",
            user=user
        )

    return "Invalid login"


@app.route("/create_user", methods=["POST"])
def create():

    create_user(
        request.form["login"],
        request.form["password"],
        request.form["name"],
        request.form["surname"],
        "user"
    )

    return "User created"


####################################
# PREDICT SINGLE FILE
####################################

@app.route("/predict", methods=["POST"])
def predict():

    file = request.files["file"]

    features = extract_features(file)

    features = np.array(features).reshape(1,40,1)

    pred = model.predict(features)

    return jsonify(
        {"class": int(pred.argmax())}
    )


####################################
# TEST DATASET
####################################

@app.route("/test_dataset", methods=["POST"])
def test_dataset():

    file = request.files["file"]

    data = np.load(file, allow_pickle=True)

    X = data["test_x"]
    y = data["test_y"]

    preds = []

    for i in range(len(X)):

        f = extract_features(X[i])

        f = np.array(f).reshape(1,40,1)

        p = model.predict(f)

        preds.append(p.argmax())

    accuracy = np.mean(
        np.array(preds) == y
    )

    return jsonify(
        {"accuracy": float(accuracy)}
    )


####################################
# RUN SERVER
####################################

if __name__ == "__main__":

    db.create_all()

    app.run(
        debug=True
    )

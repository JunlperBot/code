<!DOCTYPE html>
<html>
<head>

<title>Авторизация</title>

<link rel="stylesheet"
href="{{ url_for('static', filename='css/style.css') }}">

</head>

<body>

<h2>Авторизация</h2>

<form method="post">

<label>Логин</label>
<input type="text" name="username">

<label>Пароль</label>
<input type="password" name="password">

<button type="submit">Войти</button>

</form>

</body>
</html>

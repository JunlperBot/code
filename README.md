<!DOCTYPE html>
<html>

<head>

<title>Администратор</title>

<link rel="stylesheet"
href="{{ url_for('static', filename='css/style.css') }}">

</head>

<body>

<h2>Панель администратора</h2>

<h3>Создать пользователя</h3>

<form method="post">

<input name="username" placeholder="Логин">

<input name="first_name" placeholder="Имя">

<input name="last_name" placeholder="Фамилия">

<input type="password" name="password" placeholder="Пароль">

<select name="role">

<option value="user">User</option>
<option value="admin">Admin</option>

</select>

<button type="submit">Создать</button>

</form>

<hr>

<h3>Список пользователей</h3>

{% for u in users %}

<p>
{{u.username}}
|
{{u.first_name}} {{u.last_name}}
|
{{u.role}}
</p>

{% endfor %}

<br>

<a href="/logout">Выйти</a>

</body>
</html>

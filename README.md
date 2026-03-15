
<!DOCTYPE html>
<html>

<head>

<title>Пользователь</title>

<link rel="stylesheet"
href="{{ url_for('static', filename='css/style.css') }}">

</head>

<body>

<h2>Профиль пользователя</h2>

<p>
{{user.first_name}} {{user.last_name}}
</p>

<h3>Загрузить тестовый набор данных</h3>

<form action="/upload" method="post" enctype="multipart/form-data">

<input type="file" name="file">

<button type="submit">Загрузить</button>

</form>

<br>

<a href="/logout">Выйти</a>

</body>
</html>

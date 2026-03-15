<!DOCTYPE html>
<html>

<head>

<title>Аналитика</title>

<link rel="stylesheet"
href="{{ url_for('static', filename='css/style.css') }}">

<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>

<script src="{{ url_for('static', filename='js/charts.js') }}"></script>

</head>

<body>

<h2>Аналитика модели</h2>

<p>Accuracy: {{accuracy}}</p>
<p>Loss: {{loss}}</p>

<h3>Accuracy vs Epochs</h3>
<canvas id="accuracyChart"></canvas>

<h3>Количество записей по цивилизациям</h3>
<canvas id="classChart"></canvas>

<h3>Accuracy тестовых записей</h3>
<canvas id="testChart"></canvas>

<h3>Top 5 классов</h3>
<canvas id="topChart"></canvas>

<br>

<a href="/dashboard">Назад</a>

</body>
</html>

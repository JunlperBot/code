<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>

<h2>Аналитика модели</h2>

<p>Accuracy: {{accuracy}}</p>
<p>Loss: {{loss}}</p>

<canvas id="accuracyChart"></canvas>

<script>

const epochs = {{epochs|tojson}}
const accuracy = {{val_accuracy|tojson}}

new Chart(document.getElementById("accuracyChart"), {

type:"line",

data:{

labels:epochs,

datasets:[{

label:"Validation Accuracy",

data:accuracy

}]

}

})

</script>

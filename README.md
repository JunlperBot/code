<!DOCTYPE html>
<html>

<head>

<title>Alien Signal Classifier</title>

<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>

<style>

body{
font-family: Arial;
margin:40px;
}

.container{
max-width:900px;
margin:auto;
}

.hidden{
display:none;
}

canvas{
margin-top:40px;
}

</style>

</head>


<body>

<div class="container">

<h1>Alien Signal Classifier</h1>

<!-- LOGIN -->

<div id="loginBlock">

<h2>Login</h2>

<input id="login" placeholder="login"><br><br>

<input id="password" type="password" placeholder="password"><br><br>

<button onclick="login()">Login</button>

</div>



<!-- DASHBOARD -->

<div id="dashboard" class="hidden">

<h2>User Dashboard</h2>

<p id="userInfo"></p>

<h3>Upload Test Dataset (.npz)</h3>

<input type="file" id="dataset">

<button onclick="uploadDataset()">Upload</button>

<h3 id="accuracyText"></h3>


<!-- GRAPH 1 -->

<h3>Accuracy by Epoch</h3>
<canvas id="accuracyChart"></canvas>


<!-- GRAPH 2 -->

<h3>Class Distribution (Train Dataset)</h3>
<canvas id="classChart"></canvas>


<!-- GRAPH 3 -->

<h3>Prediction Accuracy per Record</h3>
<canvas id="recordChart"></canvas>


<!-- GRAPH 4 -->

<h3>Top 5 Classes</h3>
<canvas id="topChart"></canvas>

</div>

</div>


<script>

let accuracyChart
let classChart
let recordChart
let topChart



// LOGIN

function login(){

let login = document.getElementById("login").value
let password = document.getElementById("password").value

fetch("/login",{

method:"POST",

headers:{
"Content-Type":"application/x-www-form-urlencoded"
},

body:`login=${login}&password=${password}`

})
.then(res=>res.text())
.then(data=>{

document.getElementById("loginBlock").classList.add("hidden")
document.getElementById("dashboard").classList.remove("hidden")

document.getElementById("userInfo").innerText =
"Logged as "+login

initCharts()

})

}



//////////////////////////////////
// DATASET UPLOAD
//////////////////////////////////

function uploadDataset(){

let file = document.getElementById("dataset").files[0]

let form = new FormData()

form.append("file",file)

fetch("/test_dataset",{

method:"POST",

body:form

})
.then(res=>res.json())
.then(data=>{

document.getElementById("accuracyText").innerText =
"Test Accuracy: "+data.accuracy

})

}



//////////////////////////////////
// CHARTS
//////////////////////////////////

function initCharts(){

createAccuracyChart()

createClassChart()

createRecordChart()

createTopChart()

}



//////////////////////////////////
// GRAPH 1
//////////////////////////////////

function createAccuracyChart(){

let ctx = document.getElementById("accuracyChart")

accuracyChart = new Chart(ctx,{

type:"line",

data:{

labels:[1,2,3,4,5,6,7,8,9,10],

datasets:[{

label:"Validation Accuracy",

data:[0.55,0.6,0.65,0.7,0.75,0.8,0.83,0.86,0.89,0.91]

}]

}

})

}



//////////////////////////////////
// GRAPH 2
//////////////////////////////////

function createClassChart(){

let ctx = document.getElementById("classChart")

classChart = new Chart(ctx,{

type:"bar",

data:{

labels:["0","1","2","3","4","5","6"],

datasets:[{

label:"Records",

data:[120,160,200,140,180,90,110]

}]

}

})

}



//////////////////////////////////
// GRAPH 3
//////////////////////////////////

function createRecordChart(){

let ctx = document.getElementById("recordChart")

recordChart = new Chart(ctx,{

type:"scatter",

data:{

datasets:[{

label:"Prediction",

data:[

{x:1,y:0.9},
{x:2,y:0.8},
{x:3,y:0.95},
{x:4,y:0.7},
{x:5,y:0.85}

]

}]

}

})

}



//////////////////////////////////
// GRAPH 4
//////////////////////////////////

function createTopChart(){

let ctx = document.getElementById("topChart")

topChart = new Chart(ctx,{

type:"pie",

data:{

labels:["Class 3","Class 1","Class 5","Class 0","Class 2"],

datasets:[{

data:[200,180,150,140,130]

}]

}

})

}



</script>


</body>

</html>

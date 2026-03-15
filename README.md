window.onload = function(){

new Chart(document.getElementById("accuracyChart"), {

type: "line",

data: {

labels: [1,2,3,4,5],

datasets: [{

label: "Accuracy",

data: [0.6,0.7,0.8,0.85,0.9]

}]

}

});


new Chart(document.getElementById("classChart"), {

type: "bar",

data: {

labels: ["Civilization A","Civilization B","Civilization C","Civilization D"],

datasets: [{

label: "Количество записей",

data: [12,18,7,14]

}]

}

});


new Chart(document.getElementById("testChart"), {

type: "bar",

data: {

labels: [1,2,3,4,5],

datasets: [{

label: "Accuracy",

data: [0.9,0.8,0.85,0.7,0.95]

}]

}

});


new Chart(document.getElementById("topChart"), {

type: "pie",

data: {

labels: ["A","B","C","D","E"],

datasets: [{

data: [20,15,10,8,6]

}]

}

});

}

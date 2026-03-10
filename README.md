# Ex03 To-Do List using JavaScript
## Date:

## AIM
To create a To-do Application with all features using JavaScript.

## ALGORITHM
### STEP 1
Build the HTML structure (index.html).

### STEP 2
Style the App (style.css).

### STEP 3
Plan the features the To-Do App should have.

### STEP 4
Create a To-do application using Javascript.

### STEP 5
Add functionalities.

### STEP 6
Test the App.

### STEP 7
Open the HTML file in a browser to check layout and functionality.

### STEP 8
Fix styling issues and refine content placement.

### STEP 9
Deploy the website.

### STEP 10
Upload to GitHub Pages for free hosting.

## PROGRAM
```
<!DOCTYPE html>
<html>
<head>
<title>Todo Application</title>

<style>

body{
font-family: Arial;
background:#f4f4f4;
text-align:center;
}

.container{
width:400px;
margin:auto;
background:white;
padding:20px;
border-radius:10px;
box-shadow:0 0 10px rgba(0,0,0,0.2);
}

input{
width:70%;
padding:8px;
}

button{
padding:8px;
margin:3px;
cursor:pointer;
}

li{
list-style:none;
padding:10px;
margin:5px;
background:#eee;
display:flex;
justify-content:space-between;
align-items:center;
}

.completed{
text-decoration:line-through;
color:gray;
}

</style>

</head>

<body>

<h1>Todo Application 📝</h1>

<div class="container">

<input type="text" id="taskInput" placeholder="Enter a task">
<button onclick="addTask()">Add</button>

<br><br>

<button onclick="filterTasks('all')">All</button>
<button onclick="filterTasks('completed')">Completed</button>
<button onclick="filterTasks('pending')">Pending</button>

<ul id="taskList"></ul>

</div>

<script>

let tasks = JSON.parse(localStorage.getItem("tasks")) || [];
let currentFilter = "all";

function saveTasks(){
localStorage.setItem("tasks",JSON.stringify(tasks));
}

function renderTasks(){

const list = document.getElementById("taskList");
list.innerHTML="";

tasks.forEach((task,index)=>{

if(currentFilter==="completed" && !task.completed) return;
if(currentFilter==="pending" && task.completed) return;

let li = document.createElement("li");

li.innerHTML = `
<span onclick="toggleTask(${index})" class="${task.completed ? 'completed' : ''}">
${task.text}
</span>

<div>
<button onclick="editTask(${index})">Edit</button>
<button onclick="deleteTask(${index})">Delete</button>
</div>
`;

list.appendChild(li);

});

}

function addTask(){

let input=document.getElementById("taskInput");
let text=input.value.trim();

if(text===""){
alert("Enter a task");
return;
}

tasks.push({text:text,completed:false});

input.value="";

saveTasks();
renderTasks();

}

function deleteTask(index){

tasks.splice(index,1);

saveTasks();
renderTasks();

}

function toggleTask(index){

tasks[index].completed=!tasks[index].completed;

saveTasks();
renderTasks();

}

function editTask(index){

let newText=prompt("Edit task",tasks[index].text);

if(newText!==null && newText.trim()!==""){
tasks[index].text=newText;
saveTasks();
renderTasks();
}

}

function filterTasks(type){

currentFilter=type;
renderTasks();

}

renderTasks();

</script>

</body>
</html>
```

## OUTPUT
<img width="1918" height="1077" alt="Screenshot 2026-03-10 132530" src="https://github.com/user-attachments/assets/e53f20f2-7154-4c41-b36b-0bdfb603dc19" />


## RESULT
The program for creating To-do list using JavaScript is executed successfully.

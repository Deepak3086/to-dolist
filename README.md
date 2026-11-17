# Ex03 To-Do List using JavaScript

**Date:**

## AIM
To create a To-do Application with all features using JavaScript.

## ALGORITHM

**STEP 1**
Build the HTML structure (index.html).

**STEP 2**
Style the App (style.css).

**STEP 3**
Plan the features the To-Do App should have.

**STEP 4**
Create a To-do application using JavaScript.

**STEP 5**
Add functionalities.

**STEP 6**
Test the App.

**STEP 7**
Open the HTML file in a browser to check layout and functionality.

**STEP 8**
Fix styling issues and refine content placement.

**STEP 9**
Deploy the website.

**STEP 10**
Upload to GitHub Pages for free hosting.

## PROGRAM

### index.html

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>To-Do List</title>
  <link rel="stylesheet" href="style.css" />
</head>
<body>
  <div class="container">
    <h1>To-Do List</h1>

    <div class="input-box">
      <input type="text" id="taskInput" placeholder="Enter a task..." />
      <button onclick="addTask()">Add</button>
    </div>

    <ul id="taskList"></ul>
  </div>

  <script src="script.js"></script>
</body>
</html>
```

### style.css

```css
body {
  font-family: Arial, sans-serif;
  background: #eef1f7;
  display: flex;
  justify-content: center;
  padding-top: 60px;
}

.container {
  background: #fff;
  width: 380px;
  padding: 24px;
  border-radius: 12px;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.15);
}

h1 {
  text-align: center;
  margin-top: 0;
}

.input-box {
  display: flex;
  gap: 8px;
  margin-bottom: 16px;
}

.input-box input {
  flex: 1;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 6px;
}

button {
  background: #4f6df5;
  color: #fff;
  border: none;
  padding: 10px 14px;
  border-radius: 6px;
  cursor: pointer;
}

button:hover {
  background: #3b55d9;
}

ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

li {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 10px;
  border-bottom: 1px solid #eee;
  cursor: pointer;
}

li.done span {
  text-decoration: line-through;
  color: gray;
}

li button {
  background: #e5484d;
  padding: 5px 10px;
}
```

### script.js

```javascript
const taskInput = document.getElementById("taskInput");
const taskList = document.getElementById("taskList");

let tasks = JSON.parse(localStorage.getItem("tasks")) || [];

function saveTasks() {
  localStorage.setItem("tasks", JSON.stringify(tasks));
}

function renderTasks() {
  taskList.innerHTML = "";

  tasks.forEach((task, index) => {
    const li = document.createElement("li");
    if (task.done) li.classList.add("done");

    const span = document.createElement("span");
    span.textContent = task.text;
    span.onclick = () => toggleTask(index);

    const delBtn = document.createElement("button");
    delBtn.textContent = "Delete";
    delBtn.onclick = () => deleteTask(index);

    li.append(span, delBtn);
    taskList.appendChild(li);
  });
}

function addTask() {
  const text = taskInput.value.trim();
  if (text === "") {
    alert("Please enter a task!");
    return;
  }
  tasks.push({ text: text, done: false });
  taskInput.value = "";
  saveTasks();
  renderTasks();
}

function toggleTask(index) {
  tasks[index].done = !tasks[index].done;
  saveTasks();
  renderTasks();
}

function deleteTask(index) {
  tasks.splice(index, 1);
  saveTasks();
  renderTasks();
}

taskInput.addEventListener("keypress", (e) => {
  if (e.key === "Enter") addTask();
});

renderTasks();
```

## OUTPUT


<img width="1337" height="837" alt="image" src="https://github.com/user-attachments/assets/57bf3d68-e174-489a-81b3-2a644a9f6bf8" />


## RESULT
The program for creating To-do list using JavaScript is executed successfully.

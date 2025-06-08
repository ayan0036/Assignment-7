 <!DOCTYPE html>
<html>
<head>
  <title>DOM and Events</title>
</head>
<body>
  <h1 id="main-heading">Original Heading</h1>
  <p class="main-paragraph">This is a paragraph.</p>
  <button id="changeTextBtn">Click Me</button>

  <br><br>

  <input type="text" id="nameInput" placeholder="Enter your name">
  <button id="submitBtn">Submit</button>
  <p id="welcomeMessage"></p>

  <br><br>

  <button id="bgChangeBtn">Change Background</button>

  <br><br>

  <input type="text" id="taskInput" placeholder="Enter a task">
  <button id="addTaskBtn">Add</button>
  <ul id="taskList"></ul>

  <script src="script.js"></script>
</body>
</html>

 document.getElementById("changeTextBtn").addEventListener("click", function() {
  document.getElementById("main-heading").textContent = "Heading Changed";
  document.querySelector(".main-paragraph").textContent = "Paragraph Changed";
});

document.getElementById("submitBtn").addEventListener("click", function() {
  var name = document.getElementById("nameInput").value;
  document.getElementById("welcomeMessage").textContent = "Welcome, " + name + "!";
});

document.getElementById("bgChangeBtn").addEventListener("click", function() {
  var color = "#" + Math.floor(Math.random() * 16777215).toString(16);
  document.body.style.backgroundColor = color;
});

document.getElementById("addTaskBtn").addEventListener("click", function() {
  var taskText = document.getElementById("taskInput").value;
  if (taskText.trim() !== "") {
    var li = document.createElement("li");
    li.textContent = taskText;
    var delBtn = document.createElement("button");
    delBtn.textContent = "Delete";
    delBtn.addEventListener("click", function() {
      li.remove();
    });
    li.appendChild(delBtn);
    document.getElementById("taskList").appendChild(li);
    document.getElementById("taskInput").value = "";
  }
});

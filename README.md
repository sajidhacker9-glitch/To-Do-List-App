<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Shopping List</title>
  <style>
    body {
      font-family: "Segoe UI", sans-serif;
      background: linear-gradient(135deg, #6a11cb, #2575fc);
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      margin: 0;
    }

    .todo-container {
      background: #fff;
      padding: 25px;
      border-radius: 15px;
      box-shadow: 0 8px 20px rgba(0,0,0,0.2);
      width: 350px;
      display: flex;
      flex-direction: column;
    }

    h2 {
      text-align: center;
      color: #333;
      margin-bottom: 10px;
    }

    /* fixed-height scrollable list */
    #taskList {
      list-style: none;
      padding: 0;
      margin: 0 0 20px;
      max-height: 200px;
      overflow-y: auto;
    }

    li {
      padding: 10px;
      background: #f8f9fa;
      margin-bottom: 10px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      border-radius: 8px;
      transition: 0.3s;
    }

    li:hover {
      background: #e9ecef;
    }

    li.completed span {
      text-decoration: line-through;
      color: gray;
    }

    .task-buttons {
      display: flex;
      gap: 8px;
    }

    .cross-btn {
      background: #007bff;
      color: white;
      border: none;
      padding: 5px 8px;
      border-radius: 6px;
      cursor: pointer;
    }

    .cross-btn:hover {
      background: #0056b3;
    }

    .delete-btn {
      background: #dc3545;
      color: white;
      border: none;
      padding: 5px 8px;
      border-radius: 6px;
      cursor: pointer;
    }

    .delete-btn:hover {
      background: #a71d2a;
    }

    .input-section {
      display: flex;
      justify-content: space-between;
    }

    .input-section input {
      flex: 1;
      padding: 10px;
      border: 2px solid #ddd;
      border-radius: 8px;
      font-size: 14px;
    }

    .add-btn {
      margin-left: 10px;
      padding: 10px 15px;
      background: #28a745;
      color: #fff;
      border: none;
      border-radius: 8px;
      cursor: pointer;
      transition: 0.2s;
    }

    .add-btn:hover {
      background: #218838;
    }
  </style>
</head>
<body>
  <div class="todo-container">
    <h2>📝 Shopping List</h2>
    <ul id="taskList">
      <li>
        <span>Potato 200</span>
        <div class="task-buttons">
          <button class="cross-btn" onclick="crossTask(this)">✔️</button>
          <button class="delete-btn" onclick="deleteTask(this)">❌</button>
        </div>
      </li>
    </ul>
    <div class="input-section">
      <input
        type="text"
        id="taskInput"
        placeholder="e.g. Potato 200"
      />
      <button class="add-btn" onclick="addTask()">Add</button>
    </div>
  </div>

  <script>
    function addTask() {
      const input = document.getElementById("taskInput");
      const text = input.value.trim();
      if (!text) return;

      const li = document.createElement("li");
      li.innerHTML = `
        <span>${text}</span>
        <div class="task-buttons">
          <button class="cross-btn" onclick="crossTask(this)">✔️</button>
          <button class="delete-btn" onclick="deleteTask(this)">❌</button>
        </div>
      `;
      document.getElementById("taskList").appendChild(li);

      input.value = "";
      input.focus();
    }

    function crossTask(button) {
      button.closest("li").classList.toggle("completed");
    }

    function deleteTask(button) {
      button.closest("li").remove();
    }
  </script>
</body>
</html>
```

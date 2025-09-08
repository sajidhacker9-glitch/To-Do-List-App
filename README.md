shopping-list-app/
├─ index.html         # Main HTML markup
├─ styles.css         # Styling for layout, colors, and scroll behavior
└─ script.js          # Logic for adding, crossing, and deleting tasks

<link rel="stylesheet" href="styles.css" />

…

<script src="script.js"></script>

function addTask() {
  const input = document.getElementById("taskInput");
  const text  = input.value.trim();
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


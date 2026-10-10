<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>Personal To-Do List</title>

    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
</head>

<body class="bg-gray-100 min-h-screen">

    <div class="max-w-lg mx-auto p-6">

        <!-- Heading -->
        <h1 class="text-3xl font-bold text-center text-blue-600 mb-6">
            Personal To-Do List
        </h1>

        <!-- Input Area -->
        <div class="bg-white p-5 rounded-lg shadow-md">

            <div class="flex gap-2">

                <input
                    type="text"
                    id="taskInput"
                    placeholder="Enter a task"
                    class="flex-1 border border-gray-300 rounded-lg px-4 py-2
                           focus:outline-none focus:ring-2 focus:ring-blue-500"
                >

                <button
                    id="addTask"
                    class="bg-blue-600 text-white px-5 py-2 rounded-lg
                           hover:bg-blue-700"
                >
                    Add
                </button>

            </div>

            <!-- Task List -->
            <ul id="taskList" class="mt-5 space-y-3"></ul>

        </div>

    </div>


    <script>

        // Get elements
        const taskInput = document.getElementById("taskInput");
        const addTaskButton = document.getElementById("addTask");
        const taskList = document.getElementById("taskList");


        // Function to add task
        function addTask() {

            const task = taskInput.value.trim();

            // Check empty input
            if (task === "") {
                alert("Please enter a task!");
                return;
            }

            // Create list item
            const li = document.createElement("li");

            li.className =
                "flex items-center justify-between bg-gray-50 " +
                "border border-gray-200 rounded-lg p-3";


            // Create task text
            const taskText = document.createElement("span");

            taskText.textContent = task;

            taskText.className =
                "flex-1 cursor-pointer text-gray-700";


            // Mark task as completed
            taskText.addEventListener("click", function () {

                taskText.classList.toggle("line-through");

                taskText.classList.toggle("text-gray-400");

            });


            // Create delete button
            const deleteButton = document.createElement("button");

            deleteButton.textContent = "Delete";

            deleteButton.className =
                "bg-red-500 text-white px-3 py-1 rounded-lg " +
                "hover:bg-red-600 ml-3";


            // Delete task
            deleteButton.addEventListener("click", function () {

                li.remove();

            });


            // Add text and button to list item
            li.appendChild(taskText);
            li.appendChild(deleteButton);

            // Add list item to task list
            taskList.appendChild(li);

            // Clear input
            taskInput.value = "";

            taskInput.focus();
        }


        // Add button click event
        addTaskButton.addEventListener("click", addTask);


        // Add task using Enter key
        taskInput.addEventListener("keydown", function(event) {

            if (event.key === "Enter") {
                addTask();
            }

        });

    </script>

</body>
</html>

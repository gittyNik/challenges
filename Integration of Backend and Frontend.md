Integration of Backend and Frontend Challenge
=============================================

In this challenge, you will be integrating a backend API with a frontend web application. You will use JavaScript to make HTTP requests to the backend API and render the response on the frontend.

Example
-------

Here's an example of the API endpoint that you will be working with:

`GET /api/todos`

This endpoint returns a list of todos in JSON format:

```json

[
  {
    "id": 1,
    "title": "Complete the challenge",
    "completed": false
  },
  {
    "id": 2,
    "title": "Submit the challenge",
    "completed": false
  }
]

```
On the frontend, you will create an HTML page with a table to display the list of todos. You will use JavaScript to make a GET request to the API endpoint and render the todos on the HTML page.

Releases
--------

### Release 1

Create an HTML page with a table to display the list of todos. The table should have three columns: `ID`, `Title`, and `Completed`.

### Release 2

Write JavaScript code to make a GET request to the `/api/todos` endpoint and retrieve the list of todos.

### Release 3

Write JavaScript code to render the list of todos on the HTML page. Each todo should be displayed as a row in the table with the `ID`, `Title`, and `Completed` columns populated with the corresponding values from the API response.

### Release 4

Add a form to the HTML page to allow the user to add a new todo. The form should have an input field for the `Title` and a checkbox for `Completed`. When the user submits the form, a POST request should be made to the `/api/todos` endpoint to add the new todo.

### Release 5

Add functionality to the table to allow the user to mark a todo as completed. When the user clicks the checkbox in the `Completed` column, a PATCH request should be made to the `/api/todos/:id` endpoint to update the todo with the given `ID`. The table should be updated to reflect the change in the todo's `completed` status.


### Solution

#### Release 1

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <title>Todos</title>
  </head>
  <body>
    <h1>Todos</h1>
    <table>
      <thead>
        <tr>
          <th>ID</th>
          <th>Title</th>
          <th>Completed</th>
        </tr>
      </thead>
      <tbody id="todos-table">
      </tbody>
    </table>
  </body>
</html>
```

#### Release 2

```javascript
async function fetchTodos() {
  const response = await fetch('/api/todos');
  const todos = await response.json();
  return todos;
}

```

#### Release 3

```javascript
async function renderTodos() {
  const todos = await fetchTodos();
  const table = document.getElementById('todos-table');
  table.innerHTML = '';
  todos.forEach(todo => {
    const row = document.createElement('tr');
    const idCell = document.createElement('td');
    const titleCell = document.createElement('td');
    const completedCell = document.createElement('td');
    idCell.textContent = todo.id;
    titleCell.textContent = todo.title;
    completedCell.textContent = todo.completed ? 'Yes' : 'No';
    row.appendChild(idCell);
    row.appendChild(titleCell);
    row.appendChild(completedCell);
    table.appendChild(row);
  });
}
renderTodos();
```

#### Release 4

```html
<form id="add-todo-form">
  <label for="title">Title:</label>
  <input type="text" id="title" name="title" required>
  <label for="completed">Completed:</label>
  <input type="checkbox" id="completed" name="completed">
  <button type="submit">Add Todo</button>
</form>
```
    
```javascript
    async function addTodo() {
  const form = document.getElementById('add-todo-form');
  const title = form.elements.title.value;
  const completed = form.elements.completed.checked;
  const response = await fetch('/api/todos', {
    method: 'POST',
    headers: {
      'Content-Type': 'application/json'
    },
    body: JSON.stringify({ title, completed })
  });
  const newTodo = await response.json();
  const table = document.getElementById('todos-table');
  const row = document.createElement('tr');
  const idCell = document.createElement('td');
  const titleCell = document.createElement('td');
  const completedCell = document.createElement('td');
  idCell.textContent = newTodo.id;
  titleCell.textContent = newTodo.title;
  completedCell.textContent = newTodo.completed ? 'Yes' : 'No';
  row.appendChild(idCell);
  row.appendChild(titleCell);
  row.appendChild(completedCell);
  table.appendChild(row);
  form.reset();
}
const form = document.getElementById('add-todo-form');
form.addEventListener('submit', event => {
  event.preventDefault();
  addTodo();
});
```

#### Release 5

```javascript
To implement the functionality to mark a todo as completed, we can add an event listener to the checkboxes in the "Completed" column of the table. When a checkbox is clicked, we can make a PATCH request to the server to update the corresponding todo item.

Here's an example solution:

javascript
Copy code
// get all the checkboxes in the table
const checkboxes = document.querySelectorAll('input[type="checkbox"]');

// add event listener to each checkbox
checkboxes.forEach((checkbox) => {
  checkbox.addEventListener('click', async (event) => {
    const id = event.target.dataset.id;
    const completed = event.target.checked;

    try {
      // make PATCH request to server to update todo item
      const response = await fetch(`/api/todos/${id}`, {
        method: 'PATCH',
        headers: {
          'Content-Type': 'application/json'
        },
        body: JSON.stringify({ completed })
      });

      if (!response.ok) {
        throw new Error('Failed to update todo item');
      }

      // update the todo item in the table
      const row = event.target.parentNode.parentNode;
      row.classList.toggle('completed', completed);
    } catch (error) {
      console.error(error);
    }
  });
});
```
In this solution, we first select all the checkboxes in the table using document.querySelectorAll(). We then add an event listener to each checkbox using .forEach(). When a checkbox is clicked, we extract the todo item ID and the completed status from the checkbox's dataset attribute.

We then make a PATCH request to the server using fetch(). We pass in the todo item ID and completed status as the request body. If the response is not ok, we throw an error.

Finally, we update the todo item in the table by toggling the completed class on its row using classList.toggle(). The completed class applies a strikethrough style to the todo item's title to indicate that it has been completed.











Challenge: Building a Task Manager App
--------------------------------------

### Example

We are going to build a task manager app using React and Node.js. The app will allow users to add, edit, and delete tasks. The tasks will be stored in a MongoDB database using Mongoose.

### Releases

#### Release 1:

-   Set up a Node.js project with Express and Mongoose.
-   Create a task schema in Mongoose with fields for title, description, and completed status.
-   Create a REST API with endpoints for getting all tasks, getting a single task, adding a new task, updating an existing task, and deleting a task.

#### Release 2:

-   Create a React app with a list of tasks.
-   Use the Fetch API to retrieve the list of tasks from the backend API.
-   Display the list of tasks in a table.

#### Release 3:

-   Add a form to the React app for adding a new task.
-   Use the Fetch API to add the new task to the backend API.
-   Update the list of tasks in the table to include the new task.

#### Release 4:

-   Add functionality to the table to allow the user to edit a task.
-   When the user clicks the Edit button for a task, display a form with the task details pre-filled.
-   Use the Fetch API to update the task in the backend API.
-   Update the list of tasks in the table to reflect the updated task.

#### Release 5:

-   Add functionality to the table to allow the user to delete a task.
-   When the user clicks the Delete button for a task, display a confirmation dialog.
-   Use the Fetch API to delete the task from the backend API.
-   Update the list of tasks in the table to remove the deleted task.


###  Solution

#### Release 1

```javascript
// server.js
const express = require('express');
const mongoose = require('mongoose');
const taskSchema = new mongoose.Schema({
  title: { type: String, required: true },
  description: { type: String },
  completed: { type: Boolean, default: false },
});
const Task = mongoose.model('Task', taskSchema);
mongoose.connect('mongodb://localhost/tasks', { useNewUrlParser: true });
const app = express();
app.use(express.json());
app.get('/api/tasks', async (req, res) => {
  const tasks = await Task.find();
  res.json(tasks);
});
app.get('/api/tasks/:id', async (req, res) => {
  const task = await Task.findById(req.params.id);
  if (!task) {
    return res.status(404).json({ error: 'Task not found' });
  }
  res.json(task);
});
app.post('/api/tasks', async (req, res) => {
  const task = new Task({
    title: req.body.title,
    description: req.body.description,
  });
  await task.save();
  res.status(201).json(task);
});
app.patch('/api/tasks/:id', async (req, res) => {
  const task = await Task.findByIdAndUpdate(req.params.id, req.body, { new: true });
  if (!task) {
    return res.status(404).json({ error: 'Task not found' });
  }
  res.json(task);
});
app.delete('/api/tasks/:id', async (req, res) => {
  const task = await Task.findByIdAndDelete(req.params.id);
  if (!task) {
    return res.status(404).json({ error: 'Task not found' });
  }
  res.json({ message: 'Task deleted' });
});
const PORT = process.env.PORT || 5000;
app.listen(PORT, () => console.log(`Server started on port ${PORT}`));
```


#### Release 2

Step 1: Create a React App Create a new React app using `npx create-react-app task-list-app`. Change directory into the newly created app using `cd task-list-app`.

Step 2: Install Dependencies To fetch data from the backend API, we will use the `fetch` function. Install it using `npm install --save node-fetch`.

Step 3: Create the TaskList component Create a new component called `TaskList` in `src/components/TaskList.js`. In the `TaskList` component, use the `useState` hook to store the list of tasks retrieved from the backend API. Use the `useEffect` hook to fetch the list of tasks when the component is mounted. In the `render` method, display the list of tasks in a table.

Here is the code for the `TaskList` component:

```javascript
import React, { useState, useEffect } from 'react';
import fetch from 'node-fetch';

function TaskList() {
  const [tasks, setTasks] = useState([]);

  useEffect(() => {
    async function fetchTasks() {
      const response = await fetch('/api/tasks');
      const tasks = await response.json();
      setTasks(tasks);
    }
    fetchTasks();
  }, []);

  return (
    <table>
      <thead>
        <tr>
          <th>Title</th>
          <th>Description</th>
          <th>Completed</th>
        </tr>
      </thead>
      <tbody>
        {tasks.map((task) => (
          <tr key={task._id}>
            <td>{task.title}</td>
            <td>{task.description}</td>
            <td>{task.completed ? 'Yes' : 'No'}</td>
          </tr>
        ))}
      </tbody>
    </table>
  );
}

export default TaskList;
```

Step 4: Create the App component Create a new component called `App` in `src/App.js`. In the `App` component, import the `TaskList` component and render it.

Here is the code for the `App` component:


```javascript
import React from 'react';
import TaskList from './components/TaskList';

function App() {
  return (
    <div>
      <TaskList />
    </div>
  );
}

export default App;
```

Step 5: Start the app Start the app using `npm start`. Open your browser and go to `http://localhost:3000` to view the app.

You should now see a table displaying the list of tasks retrieved from the backend API.

#### Release 3

To add a new task in the React app and update the list of tasks in the table, you can follow these steps:

1.  Create a form component in the React app for adding a new task. The form should include input fields for the title and description of the task and a submit button.

Here's an example of what the form component could look like:

```javascript
import React, { useState } from 'react';
import './App.css';

function AddTaskForm(props) {
  const [title, setTitle] = useState('');
  const [description, setDescription] = useState('');

  const handleTitleChange = (event) => {
    setTitle(event.target.value);
  }

  const handleDescriptionChange = (event) => {
    setDescription(event.target.value);
  }

  const handleSubmit = (event) => {
    event.preventDefault();
    const newTask = { title, description };
    props.addTask(newTask);
    setTitle('');
    setDescription('');
  }

  return (
    <form onSubmit={handleSubmit}>
      <label htmlFor="title">Title</label>
      <input id="title" type="text" value={title} onChange={handleTitleChange} />
      <label htmlFor="description">Description</label>
      <input id="description" type="text" value={description} onChange={handleDescriptionChange} />
      <button type="submit">Add Task</button>
    </form>
  );
}

export default AddTaskForm;
```

1.  Add a method to the React app that uses the Fetch API to send a POST request to the backend API with the new task data.

Here's an example of what the method could look like:

```javascript
const addTask = (task) => {
  fetch('/api/tasks', {
    method: 'POST',
    headers: {
      'Content-Type': 'application/json',
    },
    body: JSON.stringify(task),
  })
    .then(response => response.json())
    .then(data => {
      setTasks([...tasks, data]);
    })
    .catch(error => console.error(error));
}```

This method sends a POST request to the `/api/tasks` endpoint with the new task data in JSON format. It then updates the list of tasks in the React app by adding the new task to the existing tasks array.

1.  Pass the `addTask` method as a prop to the `AddTaskForm` component so that it can be called when the form is submitted.

Here's an example of how to use the `AddTaskForm` component in the React app:

```javascript
import React, { useState, useEffect } from 'react';
import './App.css';
import TaskTable from './TaskTable';
import AddTaskForm from './AddTaskForm';

function App() {
  const [tasks, setTasks] = useState([]);

  useEffect(() => {
    fetch('/api/tasks')
      .then(response => response.json())
      .then(data => setTasks(data))
      .catch(error => console.error(error));
  }, []);

  const addTask = (task) => {
    fetch('/api/tasks', {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json',
      },
      body: JSON.stringify(task),
    })
      .then(response => response.json())
      .then(data => {
        setTasks([...tasks, data]);
      })
      .catch(error => console.error(error));
  }

  return (
    <div className="App">
      <h1>Task List</h1>
      <TaskTable tasks={tasks} setTasks={setTasks} />
      <AddTaskForm addTask={addTask} />
    </div>
  );
}

export default App;
```

In this example, the `addTask` method is passed as a prop
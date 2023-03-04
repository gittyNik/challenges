# Challenge: Building Scalable Express Apps

## Introduction

In this challenge, you will learn how to build scalable Express apps. You will review an example code and understand how it achieves scalability. Then, you will solve each release by writing code that achieves the desired functionality.

## Example

The example code demonstrates how to build a scalable Express app by using the following techniques:

- Separating concerns with the Model-View-Controller (MVC) architecture.
- Using middleware functions to handle common tasks such as error handling, logging, and authentication.
- Implementing the Singleton design pattern to create a database connection.
- Using the Router middleware to organize routes into separate files.
- Using environment variables to configure the app for different environments.

```javascript
// app.js
const express = require('express');
const app = express();

// Middleware
const logger = (req, res, next) => {
  console.log(`${req.method} ${req.url}`);
  next();
};

app.use(logger);
app.use(express.json());

// Routes
const usersRouter = require('./routes/users');

app.use('/users', usersRouter);

// Error Handling
app.use((err, req, res, next) => {
  console.error(err.stack);
  res.status(500).send('Internal Server Error');
});

// Start Server
const PORT = process.env.PORT || 3000;
app.listen(PORT, () => {
  console.log(`Server listening on port ${PORT}`);
});

```

```javascript
// routes/users.js
const express = require('express');
const router = express.Router();
const usersController = require('../controllers/users');

router.get('/', usersController.listUsers);
router.get('/:id', usersController.getUserById);
router.post('/', usersController.createUser);
router.put('/:id', usersController.updateUser);
router.delete('/:id', usersController.deleteUser);

module.exports = router;

```

```javascript
// models/users.js
const users = [
  { id: 1, name: 'Alice', email: 'alice@example.com' },
  { id: 2, name: 'Bob', email: 'bob@example.com' },
  { id: 3, name: 'Charlie', email: 'charlie@example.com' }
];

module.exports = users;
```

## Releases

### Release 1: List of Users

Create an endpoint that returns a list of users. The list should be retrieved from a database.

### Release 2: Get User by ID

Create an endpoint that retrieves a user by ID from the database.

### Release 3: Add User

Create an endpoint that adds a user to the database.

### Release 4: Update User

Create an endpoint that updates a user in the database.

### Release 5: Delete User

Create an endpoint that deletes a user from the database.

## Instructions

1. Review the example code and understand how it achieves scalability.
2. Solve each release by writing code that achieves the desired functionality.
3. Submit your code without any answers to releases provided.














# Challenge: Building a REST API with Express

## Example Code

Please review the following code and understand how it uses Express to create a REST API. The code is a simple API that allows users to manage a list of tasks.

```javascript
const express = require('express');
const bodyParser = require('body-parser');

const app = express();
app.use(bodyParser.json());

let tasks = [  { id: 1, name: 'Task 1', description: 'This is task 1' },  { id: 2, name: 'Task 2', description: 'This is task 2' },  { id: 3, name: 'Task 3', description: 'This is task 3' }];

app.get('/tasks', (req, res) => {
  res.send(tasks);
});

app.get('/tasks/:id', (req, res) => {
  const task = tasks.find(t => t.id === parseInt(req.params.id));
  if (!task) return res.status(404).send('The task with the given ID was not found.');
  res.send(task);
});

app.post('/tasks', (req, res) => {
  const task = {
    id: tasks.length + 1,
    name: req.body.name,
    description: req.body.description
  };
  tasks.push(task);
  res.send(task);
});

app.put('/tasks/:id', (req, res) => {
  const task = tasks.find(t => t.id === parseInt(req.params.id));
  if (!task) return res.status(404).send('The task with the given ID was not found.');

  task.name = req.body.name;
  task.description = req.body.description;
  res.send(task);
});

app.delete('/tasks/:id', (req, res) => {
  const task = tasks.find(t => t.id === parseInt(req.params.id));
  if (!task) return res.status(404).send('The task with the given ID was not found.');

  const index = tasks.indexOf(task);
  tasks.splice(index, 1);
  res.send(task);
});

const port = process.env.PORT || 3000;
app.listen(port, () => console.log(`Listening on port ${port}...`));
```

Releases
--------

### Release 0: Add validation

Add validation to the API to ensure that the name and description fields are not empty when creating or updating a task.

### Release 1: Add pagination

Add support for pagination to the API. Modify the `/tasks` endpoint to return only a subset of the tasks based on a `page` query parameter and a `page_size` query parameter.

### Release 2: Add search

Add support for searching tasks by name or description. Modify the `/tasks` endpoint to accept a `q` query parameter, and return only tasks that match the search term.

### Release 3: Add authentication

Add authentication to the API. Modify the API to require an API key to be included in the request headers for all endpoints except the `/login` endpoint.

### Release 4: Add permissions

Add support for permissions to the API. Modify the API to allow users with the `admin` role to create, update, and delete tasks, and allow users with the `user` role to only view tasks.

Instructions
------------

Review the example code and understand how it achieves scalability.
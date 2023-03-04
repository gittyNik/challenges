Challenge: Express and Mongoose in JavaScript
---------------------------------------------

### Example

In this challenge, we will be creating a web application using Express.js and Mongoose.js. Our application will allow users to create and view blog posts.

We will be creating a simple database schema for our blog posts using Mongoose.js, and using Express.js to create routes for our web application.

### Releases

#### Release 0: Set up the project

Create a new directory for the project and run `npm init` to set up a new Node.js project. Install `express`, `mongoose`, and `body-parser` using npm.

Create an `app.js` file and require `express`, `mongoose`, and `body-parser`. Create a new instance of `express` and set up a basic route to test your server.

#### Release 1: Create the BlogPost schema

Using Mongoose.js, create a new schema for our blog posts. The schema should include the following fields:

-   `title`: the title of the blog post
-   `body`: the body of the blog post
-   `date`: the date the blog post was created

#### Release 2: Create the routes

Create routes for our application that allow users to:

-   View a list of all blog posts
-   Create a new blog post

#### Release 3: Create the views

Create the views for our application using a templating engine like EJS or Pug. Create a view that displays all blog posts, and a view for creating a new blog post.

#### Release 4: Add validation

Add validation to the form for creating a new blog post. The title and body fields should be required, and the title field should be limited to 100 characters.

### Bonus Release

Add the ability for users to edit and delete blog posts.

Resources
---------

-   [Express.js](https://expressjs.com/)
-   [Mongoose.js](https://mongoosejs.com/)

Good luck!







Express and Mongoose Challenge
------------------------------

In this challenge, you will be working with Express and Mongoose to build a REST API that allows users to manage a list of tasks. You will need to use Mongoose to define a schema for the tasks and to interact with a MongoDB database. You will also use Express to create the routes and handle the HTTP requests and responses.

### Example

To help you get started, here's an example of what the API should do:

-   GET /tasks - Returns a list of all tasks.
-   POST /tasks - Adds a new task to the database.
-   GET /tasks/:id - Returns a specific task by ID.
-   PUT /tasks/:id - Updates a specific task by ID.
-   DELETE /tasks/:id - Deletes a specific task by ID.

### Releases

#### Release 0: Set up the project

Create a new Express project and initialize a Git repository. Set up a basic server that listens on port 3000 and responds to HTTP requests with a "Hello, World!" message.

#### Release 1: Define the Mongoose schema

Use Mongoose to define a schema for the tasks. The schema should include a title, a description, a due date, and a completed flag. The title and description should be required fields.

#### Release 2: Connect to the MongoDB database

Use Mongoose to connect to a MongoDB database. You can use a local database or a cloud-based service like MongoDB Atlas.

#### Release 3: Create the GET /tasks route

Create a new route that returns a list of all tasks in the database. The response should be a JSON array of task objects.

#### Release 4: Create the POST /tasks route

Create a new route that adds a new task to the database. The request body should include the title, description, and due date of the new task. The completed flag should default to false.

#### Release 5: Create the GET /tasks/:id route

Create a new route that returns a specific task by ID. The response should be a JSON object representing the task.

Good luck!
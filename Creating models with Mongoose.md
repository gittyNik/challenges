Challenge: Creating Models with Mongoose
----------------------------------------

In this challenge, you will create a simple application using Mongoose to define and work with models for a database.

### Example

Before we begin, let's take a look at an example of how to create a model using Mongoose:

```javascript
const mongoose = require('mongoose');

// Create a schema for our data
const userSchema = new mongoose.Schema({
  firstName: String,
  lastName: String,
  email: String,
  age: Number,
});

// Create a model for our schema
const User = mongoose.model('User', userSchema);`
```

In the above example, we first import the `mongoose` library. Then, we create a schema using the `mongoose.Schema` method, which defines the structure of our data. In this case, we are creating a schema for a user that includes a first name, last name, email, and age.

Next, we use the `mongoose.model` method to create a model for our schema. The first argument is the name of the model (which should be singular), and the second argument is the schema that the model should use. In this case, we are creating a `User` model that uses the `userSchema` schema.

### Releases

#### Release 1: Define a schema for a book

Define a Mongoose schema for a book that includes the following fields:

-   `title`: a string representing the title of the book
-   `author`: a string representing the author of the book
-   `year`: a number representing the year the book was published
-   `genre`: a string representing the genre of the book

#### Release 2: Create a model for the book schema

Using the schema you defined in Release 1, create a Mongoose model for the book that is named "Book".

#### Release 3: Save a new book to the database

Write a function that creates a new book object and saves it to the database. The book object should have the following properties:

-   `title`: "The Great Gatsby"
-   `author`: "F. Scott Fitzgerald"
-   `year`: 1925
-   `genre`: "Literary fiction"

#### Release 4: Find all books in the database

Write a function that finds all books in the database and logs them to the console.

#### Release 5: Find a book by title

Write a function that finds a book in the database by its title and logs it to the console.

### Constraints

-   Use Mongoose to interact with the database.
-   Use the `mongoose.connect()` method to connect to a MongoDB database.
-   Use `console.log()` to display the results of each release.


## Solution

#### Release 1: Define a schema for a book

```javascript
const mongoose = require('mongoose');

const bookSchema = new mongoose.Schema({
  title: {
    type: String,
    required: true
  },
  author: {
    type: String,
    required: true
  },
  year: {
    type: Number,
    required: true
  },
  genre: {
    type: String,
    required: true
  }
});
module.exports = Book;
```



#### Release 2: Create a model for the book schema

```javascript

const Book = mongoose.model('Book', bookSchema);
```

#### Release 3: Save a new book to the database

```javascript
async function createBook() {
  const book = new Book({
    title: 'The Great Gatsby',
    author: 'F. Scott Fitzgerald',
    year: 1925,
    genre: 'Literary fiction'
  });

  try {
    await book.save();
    console.log('Book saved:', book);
  } catch (error) {
    console.error('Error saving book:', error);
  } 
}

createBook();
In this solution, we define a createBook() function that creates a new Book object with the specified properties and saves it to the database using the save() method. We use async/await syntax to handle the asynchronous nature of the database operations. If the book is saved successfully, we log a message to the console with the saved book object. If there is an error, we log an error message to the console. Finally, we disconnect from the database using mongoose.disconnect().

This code assumes that you have already defined a Book model and connected to a MongoDB database using Mongoose. You may need to modify the connection string to match your own database configuration.

```

#### Release 4: Find all books in the database

```javascript
function findAllBooks() {
  Book.find({}, function(err, books) {
    if (err) {
      console.log(err);
    } else {
      console.log(books);
    }
  });
}
```
Explanation:

The Book.find() method is used to find all the documents in the books collection in the database.
The first argument {} specifies the search criteria as an empty object, which returns all documents in the collection.
The callback function takes two parameters, an error object and the result array books.
If there is an error, it is logged to the console.
If there is no error, the result array books is logged to the console.
Note: Make sure to require the Book model in your code and establish a connection to your MongoDB database before calling the findAllBooks() function.

#### Release 5: Find a book by title

```javascript
function findBookByTitle(title) {
  Book.findOne({ title }, (err, book) => {
    if (err) {
      console.log(err);
      return;
    }

    console.log(book);
  });
}
```
This function takes in a title parameter and uses the findOne() method to find a book in the database with that title. If an error occurs, it logs the error to the console. If no error occurs, it logs the book object to the console.










# Creating Models with Mongoose

In this challenge, you will be creating a Mongoose model for a blog post and writing functions to interact with the database.

Example
-------

```javascript
const mongoose = require('mongoose');

// Define a schema for a blog post
const postSchema = new mongoose.Schema({
  title: {
    type: String,
    required: true
  },
  body: {
    type: String,
    required: true
  },
  author: {
    type: String,
    required: true
  },
  date: {
    type: Date,
    default: Date.now
  },
  tags: {
    type: [String],
    required: true
  },
  comments: {
    type: [{
      name: String,
      body: String,
      date: {
        type: Date,
        default: Date.now
      }
    }],
    default: []
  }
});

// Create a Mongoose model for the blog post schema
const Post = mongoose.model('Post', postSchema);`
```

Releases
--------

#### Release 1: Create a new blog post and save it to the database. The blog post should have the following properties:

-   `title`: "First Post"
-   `body`: "This is my first blog post."
-   `author`: "John Doe"
-   `tags`: ["first post", "beginner"]

#### Release 2: Write a function to find all blog posts in the database and log them to the console.

#### Release 3: Write a function to find a blog post by its author and log it to the console.

#### Release 4: Write a function to add a comment to a blog post. The function should take the following parameters:

-   `postId`: the ID of the blog post to add the comment to
-   `name`: the name of the commenter
-   `body`: the text of the comment

#### Release 5: Write a function to delete a comment from a blog post. The function should take the following parameters:

-   `postId`: the ID of the blog post to delete the comment from
-   `commentId`: the ID of the comment to delete.


## Solution

#### Release 1: Create a new blog post and save it to the database

```javascript
// Create a new blog post and save it to the database
const post = new Post({
  title: "First Post",
  body: "This is my first blog post.",
  author: "John Doe",
  tags: ["first post", "beginner"]
});

post.save((err) => {
  if (err) {
    console.log(err);
  } else {
    console.log("Blog post saved successfully!");
  }
});
```
This code creates a new Post object with the specified properties and saves it to the database using the save() method. If an error occurs during the save operation, it is logged to the console. Otherwise, a success message is logged.

#### Release 2: Find all blog posts in the database
To find all blog posts in the database, we can use the find() method on the Post model:

```javascript
Post.find({}, (err, posts) => {
  if (err) {
    console.error(err);
  } else {
    console.log(posts);
  }
});
```
This will return all posts in the database and log them to the console. The first argument to find() is an empty object, which means it will return all documents in the collection.

#### Release 3: Find a blog post by its author
To find a blog post by its author, we can use the find method on the Post model with a query object that matches the desired author. 
```javascript

Post.find({ author: 'John Doe' }, (err, posts) => {
  if (err) {
    console.error(err);
  } else {
    console.log(posts);
  }
});
```
This code will find all blog posts where the author is "John Doe" and log them to the console.

#### Release 4: Add a comment to a blog post

```javascript
async function addComment(postId, name, body) {
  try {
    const post = await Post.findById(postId);
    if (!post) {
      console.log(`Post with ID ${postId} not found`);
      return;
    }

    const comment = {
      name,
      body
    };

    post.comments.push(comment);
    await post.save();

    console.log(`Comment added to post with ID ${postId}`);
  } catch (err) {
    console.error(err);
  }
}
```
This function uses async/await to handle asynchronous operations in a more readable manner. It first tries to find the post with the given ID using Post.findById(). If the post is not found, it logs a message and returns. If the post is found, it creates a new comment object using the name and body parameters, and adds it to the comments array of the post using post.comments.push(). Finally, it saves the updated post using post.save(). If any errors occur during this process, they are caught and logged to the console.

#### Release 5: Delete a comment from a blog post

```javascript
async function deleteComment(postId, commentId) {
  try {
    const post = await Post.findById(postId);
    if (!post) {
      throw new Error(`Post with ID ${postId} not found`);
    }
    const commentIndex = post.comments.findIndex(c => c._id.equals(commentId));
    if (commentIndex === -1) {
      throw new Error(`Comment with ID ${commentId} not found in post with ID ${postId}`);
    }
    post.comments.splice(commentIndex, 1);
    await post.save();
    console.log(`Comment with ID ${commentId} deleted from post with ID ${postId}`);
  } catch (err) {
    console.error(err.message);
  }
}

```
This function first finds the post with the given postId using findById. If the post is not found, it throws an error.

Next, it finds the index of the comment to delete in the comments array of the post. If the comment is not found, it throws an error.

Then it uses the splice method to remove the comment from the comments array, and saves the updated post using the save method.

Finally, it logs a message to the console indicating that the comment was deleted. If any error occurs, it logs the error message to the console.
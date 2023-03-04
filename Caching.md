Challenge: Caching in JavaScript
================================

Introduction
------------

Caching is an important technique used in computer science to improve the performance of applications. In web development, caching is used to store frequently accessed data so that it can be quickly retrieved the next time it is needed, instead of fetching it from the server every time. This can significantly reduce the amount of time it takes for web pages to load, which can have a big impact on the user experience.

In this challenge, you will learn about caching in JavaScript and implement a caching mechanism for a web application.

Example
-------

Before we get started with the releases, let's take a look at an example to understand how caching works in JavaScript.

```javascript

// Define a function to compute the factorial of a number
function factorial(n) {
  if (n === 0 || n === 1) {
    return 1;
  }
  return n * factorial(n - 1);
}

// Compute the factorial of 5
console.log(factorial(5)); // Output: 120

// Compute the factorial of 5 again
console.log(factorial(5)); // Output: 120`
```

In this example, we define a function called `factorial` that computes the factorial of a number. We then call this function twice with the same argument (`5`). The first time we call it, the function executes and returns the correct result (`120`). The second time we call it, the function executes again and returns the same result (`120`).

Now let's modify the example to use caching:

```javascript

// Define a caching function to compute the factorial of a number
function cachedFactorial() {
  let cache = {};
  return function(n) {
    if (n in cache) {
      console.log('Fetching from cache:', n);
      return cache[n];
    } else {
      console.log('Calculating result for:', n);
      let result = factorial(n);
      cache[n] = result;
      return result;
    }
  }
}
```

// Create a cached version of the factorial function
let factorial = cachedFactorial();

// Compute the factorial of 5
console.log(factorial(5)); // Output: Calculating result for: 5, 120

// Compute the factorial of 5 again
console.log(factorial(5)); // Output: Fetching from cache: 5, 120`

In this modified example, we define a new function called `cachedFactorial` that returns a new function that caches the results of the `factorial` function. We then create a new variable called `factorial` that is assigned the result of calling `cachedFactorial`. When we call `factorial` with the argument `5` for the first time, the `cachedFactorial` function computes the result and stores it in the `cache` object. The result is then returned and printed to the console. When we call `factorial` with the argument `5` again, the `cachedFactorial` function checks if the result is already in the cache, and if it is, it returns the cached result instead of recomputing it.


## Releases:

### Release 0: Understand how caching works in JavaScript

Review the provided example code and understand how it implements caching.

### Release 1: Create a caching function

Create a function that can be used to cache any data in memory. The function should take two parameters, a key and a value, and store the value in a cache object using the key as the identifier.

### Release 2: Create a function to retrieve cached data

Create a function that can be used to retrieve cached data from memory. The function should take one parameter, the key of the cached data, and return the cached data if it exists.

### Release 3: Implement caching in API endpoints

Modify your API endpoints to use caching for frequently requested data. Use the caching functions you created in Release 1 and Release 2 to store and retrieve data from cache.

### Release 4: Add cache expiration

Add a feature to your caching function that automatically expires cached data after a certain period of time. This will prevent stale data from being returned to clients.

## Instructions
- Review the example code and understand how it implements caching.
- Solve each release by writing code that achieves the desired functionality.
- For releases 1 to 4, use a caching library of your choice.
- For release 5, implement your own caching mechanism.












Challenge: Caching in JavaScript
--------------------------------

In this challenge, you will learn how to use caching to speed up web applications. You will implement a simple caching mechanism that will cache responses from an API for a short period of time to avoid making unnecessary API requests.

### Example

Here's an example of how caching can improve the performance of a web application:

```javascript

// Without caching
const response = await fetch('https://api.example.com/data');
const data = await response.json();
// ...use the data...

// With caching
let data;
const cachedResponse = sessionStorage.getItem('cachedResponse');
if (cachedResponse) {
  data = JSON.parse(cachedResponse);
} else {
  const response = await fetch('https://api.example.com/data');
  data = await response.json();
  sessionStorage.setItem('cachedResponse', JSON.stringify(data));
}
// ...use the data...`
```
### Releases

#### Release 0: Basic caching

Implement a simple caching mechanism that stores responses from an API in memory for a short period of time. The cache should have a configurable expiration time, and it should automatically expire entries that have exceeded their expiration time. When a new request comes in for a URL that is already in the cache, the cached response should be returned immediately.

#### Release 1: Middleware

Create a middleware that adds caching support to your Express application. The middleware should be configurable with a cache duration, and it should cache responses from all routes that have not been explicitly excluded from caching.

#### Release 2: Cache invalidation

Implement a mechanism for cache invalidation. When a resource is updated or deleted, the corresponding cache entry should be removed. You should be able to invalidate the cache for individual routes or for the entire cache.

#### Release 3: Cache eviction

Implement a cache eviction mechanism that automatically removes the least recently used cache entries when the cache reaches a certain size limit. The cache size limit should be configurable.

#### Release 4: Advanced caching

Implement advanced caching techniques such as conditional GET requests, etags, and partial caching. These techniques can significantly improve the performance of your web application by reducing the amount of data that needs to be transferred between the server and the client.

### Instructions

1.  Review the example code and understand how caching works.
2.  Solve each release by writing code that achieves the desired functionality.
# Node.js Express Hello World (1-hello-world)

Welcome to your first Node.js and Express project! This tutorial will walk you through creating a simple web server that responds with "Hello, World!".

## What are Node.js, npm, and Express?

- **Node.js** is a runtime environment that allows you to run JavaScript code outside of a web browser. This means you can use JavaScript to build server-side applications.

- **npm (Node Package Manager)** is a tool that comes with Node.js. It helps you install and manage additional code (called packages or dependencies) that other developers have written. It's kind of like an app store for developers.

- **Express** is one of these packages. It's a web framework that makes it easier to create web applications with Node.js. It handles a lot of the complex stuff so you can focus on writing your application code.

## Getting Started

### Install Node.js

First, you need to install Node.js on your computer:
1. Go to [nodejs.org](https://nodejs.org)
2. Download and install the LTS (Long Term Support) version
3. Verify installation by opening your terminal/command prompt and typing:
   ```bash
   node --version
   npm --version
   ```
   Both commands should display version numbers.

### Create Your Project

1. Create a new folder for your project and navigate to it in the terminal:
   ```bash
   cd hello-world-express
   ```
   Make sure you're in the correct directory! You don't want to be in the wrong directory when you're running commands like `npm install` or `node app.js`, this is a common source of errors. 
   
   You can check your current directory with the `pwd` command. The output should be something like `C:\Users\YourUsername\hello-world-express`.

2. Initialize a new Node.js project:
   ```bash
   npm init -y
   ```
   This creates a `package.json` file that will track your project dependencies.

3. Modify your package.json to support ES modules by adding the line:
   ```json
   "type": "module",
   ```

4. Install Express:
   ```bash
   npm install express
   ```

5. Create a new file called `app.js` and copy the code from this repository into it.

### Understanding Generated Files

When you run `npm install`, several new items will appear in your project:

- **node_modules/** folder: Contains all the code for your dependencies (such as Express and its dependencies). This folder can be quite large and should not be committed to git.

- **package-lock.json**: Automatically generated file that keeps track of the exact versions of all dependencies. This helps ensure consistent installations across different machines.

## Understanding the Code

Let's break down what each part of `app.js` does:

1. `import express from 'express';` - This imports the Express framework using modern ES modules syntax.
2. `const app = express();` - This creates a new Express application object and assigns it to the `app` variable. This is the main object that we use to configure our routes and start the server.
3. `app.get('/', ...)` - This creates a route on the `app` object that handles GET requests to the home page ('/')
4. `res.send('Hello, World!');` - This sends the response "Hello, World!" back to the client.
5. `app.listen(PORT, ...)` - This starts the server on port 3000. Computers can use many ports for different applications, so we need to tell the server which port to listen on. 3000 is a common port for web servers.

## Running Your Application

1. In your terminal, make sure you're in your project directory.
2. Run the server:
   ```bash
   node app.js
   ```
3. Open your web browser and visit: `http://localhost:3000`
4. You should see "Hello, World!" displayed in your browser!
5. You can stop the server by pressing `Ctrl + C` in the terminal.

## What's Next?

Congratulations! You've created your first Node.js web server using Express. In future lessons, you'll learn how to:
- Add more routes
- Learn about HTTP methods (GET, POST, etc.)
- Work with templates to create HTML pages
- Connect to a database
- And more!

## Troubleshooting Common Errors

If you see an error like "port already in use":
- Another program might be using port 3000. In this case, you can try changing the PORT number in app.js to 3001 or another number.
- You might have another instance of the server running. This often happens accidentally if you have multiple instances of your editor open. One of them might be still be running a node server in the terminal.

If you see "module not found" errors:
- Make sure you ran `npm install express`.
- Check that you're runnig the project from the correct directory.
- Try deleting the `node_modules` folder and running `npm install` again.

<br/>

*Note: This tutorial was created with the help of AI tools.*
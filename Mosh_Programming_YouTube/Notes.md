## Introduction

- React was developed by FaceBook in 2011.
- _Challenge_: The browser takes the HTML code and create a tree like structure called `Document Object Model`, in short, DOM. Once a DOM has been created, you can easily use Vanilla JavaScript (JavaScript without third party tools) to interact with elements. As the application grows, it becomes challenging. <br>
  How does React address this challenge? <br>
- It treats everything in the webpage as a component and take care of creating and updating DOM elements without us having to worry about.
- Components help us write reusable, modular, and better organized code.
- React creates a tree of components with App component enclosing everything.

# Creating a React App

- There are two ways of creating a React App:
  (a) _CRA_ (create react app) - official one provided by React. <br>
  (b) _vite_: faster and small bundle sizes.
- To create a React project, navigate to the directory you want to create it then enter the following code and follow the instructions in it.

```javascript
npm create vite@latest
```

# Project Structure

- React uses `virtual dom` to update the elements. It takes the components and build a DOM for updating the nodes(elements).
- React is a JavaScript Library for creating user interfaces.

# React Ecosystem

- React is a library in additon to other frameworks: `Angular` and `Vue`.
- What is the difference between a library and a framework?
- **Library** is a tool providing specific functionality while **framework** is a set of tools and guidelines for building apps.
- React is good for User Interfaces (UI). But we need additional functionality for aspects like:
  (a) Routing. <br/>
  (b) HTTP. <br />
  (c) Managing app state. <br/>
  (d) Internationalisaion. <br/>
  (e) Form validation. <br />
  (f) Animations. <br />
- React doesn't provide an opinion for the tools to use to achieve other functionality and we're free to select the tools we can use for added functionality.

# Creating a ListGroup Component
- 

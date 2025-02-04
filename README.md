# React Documentation
## Creating and Nesting Components
- React apps are made up of *components.*
- Component is a piece of UI (user interface) that has its own logic and appearance.
- Component can be a section of a page or even the entire page itself.
- React components are javascript functions returning markup language.
```bash jsx
function MyButton(){
    return (
        <button>I'm a button</button>
        );
}
```
- Function name representing a react component must start with a capital letter to avoid confusion with the normal html tags, which are lowercase. 
- Now that I have declared `MyButton` element, I can **nest** it in another component.
```bash javascript
export default function MyApp(){
    return(
        <div>
        <h1>This is heading 1</h1>
        < MyButton/>
        </div>
    )
}
```
- `export default` keywords indicate the main function in a file.
## Writing MarkUp as JSX
- All the markup we have written above is called *jsx*. It is optional, but most React projects use it for convenience. 
- JSX is stricter than HTML. Why is this the case?
1. You must close all tags like <br />. <br>
2. A component can't return multiple JSX tags. The solution to this:
- To return multiple jsx tags, wrap the parent under `<div>...<div/>` or `<>...</>` wrapper. 
```bash jsx
function AboutPage(){
    return(
        <>
        <h1>About Page</h1>
        <p> Hello there. <br /> How do you do?<p/>
        </>
    );
}
```
- If I have a lot of HTML to port to JSX, I can use the [online converter](https://transform.tools/html-to-jsx). <br>

## Adding Styles
- In React, a CSS class name is written as `className` and it works the same way as class in HTML `class` attribute.

```bash jsx
<img className = "avatar"/>
```
- Then you write CSS rules separately and link it to HTML file.
- React doesn't provide specific way to add CSS. In case I am using an external framework, the only way to manouvre is to thoroughly read the documentation of the specific framework.
## Displaying Data
- JSX let's me put markup on Javascript.
- Use of `curly braces` enables me to 'escape back` to JavaScript and embed variables from my code and display it to the user.
- For example, the following code will display `user.name`:
```jsx
return(
    <h1>
    {user.name}
    <h1/>
);
```
- Also, I can "escape into JavaScript" from JSX attributes. How? I have to use curly braces instead of quotes.
- In the code example below `className = "avatar"` passes `avatar` as a string to CSS class, but `src = {image.userURL}` reads the JavaScript `image.URL` variable value and then passes the value as the `source` attribute.
```jsx
return(
    <img
    className = "avatar";
    src = {image.URL};
    />
)
```
- I can also put complex expressions inside JSX curly braces (string concatenation): Example code is shown below:
```jsx
const user = {
    name: "Harry Porter";
    imageUrl: "https://i.imgur.com/yXOvdOSs.jpg";
    imageSize: 90;
}

export default function Profile(){
   
    return(
         <>
         <h1> {user.name}<h1/>
         <img
         className = "avatar";
         src = {user.imageUrl};
         alt = {'Photo of ' + user.name};
         style = {
            {
                width: user.imageSize;
                height: user.imageSize;
            }
         }
         />
         </>
    );
    
}

```

## Conditional Rendering
- In React, we use the same syntax for writing JavaScript conditions. No special syntax.
- Example:
```jsx
let content;
if(isLoggedIn){
    content = <AdminPanel/>;
} else{
    content = <LoginForm/>
}
return(
    <>
    {content}
    </>
)
```
- For a more compact code, I can use `conditional ? operator` that works inside the JSX code as:
```jsx
<>
{
    isLoggedIn? (
        <AdminPanel/>
    ) : (
        <LoginForm/>
    )

}
</>
```
## Rendering Lists
- Rely on Javascript features like `for loop` and `array map()` to render lists components.
- consider an array of products:
```javascript
const products = [
    {title: 'Cabbage', id = 1},
    {title: 'Garlic', id = 2},
    {title: 'Apple', id = 3}
];
```
- Inside my component, I have to use `map()` function to transform an array of products into `<li>` items.
```jsx
const listItems = products.map(product=>
    <li key = {product.id}>
    {product.title}
    </li>
)
return(
    <ul>{listItems}</ul>
)
```
- Notice how `<li>` has got a `key` that uniquely identifies an item among its siblings. You have to pass in a string of a number for this unique idenfitication.
- Key usually comes from data, particularly database ID. 
- Why use keys? It assists React to know what happens to an item if I insert, deleter, or rearrange items.
## Responding to Events
- Response events are handled by defining `event handlers` functions inside my components.
```javascript
function MyButton(){
    function handleClick(){
        alert("You clicked me!");
    }
}
return{
    <button onClick = {handleClick}>
    Click Me
    </button>
}
```
- Notice how `onClick = {handleClick}` doesn't have parantheses. I only need to *pass it down* as React will call the event handler function when the user clicks the function.
## Updating the Screen
- Often, I want my components to `remember` information and display it.
- For instance, I want a button to give the number of times it has been clicked.
- To do this, I need to add `state` to my component. 
- first, I need to import `useState` from React.
```javascript
import { useState } from 'react';
```
- Now, I can declare `state variable` inside my component:
```javascript
function MyButton(){
    const [count, setCount] = useState(0);
    //
}
```
- From `useState`, I will get two things: the current state (`count`) and the function (`setCount`) that let's me update the count.
- I can give them any names, but the convention is `[something, setSomething]`.
- For the first time the button is displayed, the `count` value will be zero because 0 is set to the function `setCount`.
- If I want to change the state, I call the function `setCount` and pass a new value to it.
- Clicking this button will increment the counter.
```javascript
function MyButton(){
    const [count, setCount] = useState(0);
    function handleClick(){
        setCount(count+1);
    }
}
return (
    <button onclick = {handleClick}>
    Click {count} times
    </button>
)
```
- If I render my component several times, each component will have its own state independent of others.
```javascript
import { useState } from 'react';

export default function MyApp() {
  return (
    <div>
      <h1>Counters that update separately</h1>
      <MyButton />
      <MyButton />
    </div>
  );
}

function MyButton() {
  const [count, setCount] = useState(0);

  function handleClick() {
    setCount(count + 1);
  }

  return (
    <button onClick={handleClick}>
      Clicked {count} times
    </button>
  );
}

```
- Each button `remembers` its own `count` without affecting the ones for others.

## Using Hooks
- Any function starting with keyword `use` is calle a hook. 
- `useState` is a React in-built hook. There are also others.
- I can build my own hooks by combining the existing ones.
- They are restrictive than other functions. 
- I can only call hooks at `the top of components or other hooks`.
- If I want to use `useState` in a condition or a loop, extract a new component and put it there.

## Sharing Data Between Components
- As earlier seen, every button had its own state of `count`. What about if we want all similar buttons to update at the same time when one button is clicked (share data and update together)?
- To make this possible, I need to move state to the nearest component `upwards` containing both buttons. 
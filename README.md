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

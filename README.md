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
- 
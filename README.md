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

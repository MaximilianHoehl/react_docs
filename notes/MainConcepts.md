## Basics
<div id="root"> contains the main app component

## Render React Dom
```javascript
const element = <h1>Hello, world</h1>;
ReactDOM.render(element, document.getElementById('root'));
```
```javascript
function tick(){        //creates component
    const element = (   //creates element
        <div>
            <h1>Hey there!</h1>
            <h2>Today: {new Date().toLocalTimeString()}</h2>
        </div>
    );
    ReactDOM.render(element, document.getElementById('root'));
}
```
## Create React Component
Older way was over ES6 classes
```javascript
class myComponent extends React.Component{
    render(){ //React component 'constructor'
        return <h1>I'm {this.props.name}</h1> //element
    }
}
```
Create component over function (faster)
```javascript
function MyComponent(props){ //component
    return <h1>I'm {props.name}</h1> //element
}
```
Call a component
```javascript
<MyComponent name='LabComp' /> 
```
Represent component as element
```javascript
const myElement = <MyComponent name='LabComp' />; //React passes object 'props' with property 'name' to component 'MyComponent'
```
Another Example
```javascript
function Welcome(props){
    return <h1>Hello, {props.name}!</h1>
}
const element = <Welcome name='Sarah' />;
ReactDOM.render(
    element,
    document.getElementById('root')
);
```


stateless components will be written as functional components 
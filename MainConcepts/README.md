# Main Concepts

### General
- <div id="root"> in index.html contains the main app component

### Render React Dom
```javascript
const element = <h1>Hello, world</h1>;
ReactDOM.render(element, document.getElementById('root'));
```

### Create React Component
For stateful components
```javascript
class myComponent extends React.Component{
    render(){
        return <h1>I'm {this.props.name}</h1> //element
    }
}
```
Create stateless components over function (faster)
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
- You define components properties by setting them in <MyComp prop1='X', prop2='Y' />
- The react created props object lets you unpack those props
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

### Composing Components
Components can be nested and reused
```javascript
function Welcome(props){
    return <h1>Hey, {pros.name}!</h1>
}
function App(){
    return (
        <div>
            <Welcome name='Twix' />
            <Welcome name='Nami' />
            <Welcome name='Bounty' />
        </div>
    );
}
ReactDOM.render(
    <App />,
    document.getElementById('root')
);
```
```
Name props fom owns point of view, not from parent/context ones.
(If you create a an avatar-component containing profilepic and username, 
dont call the name props.author just because you created it during the creation of a commentsection)
```
Another example of component compositions:
```javascript
function Avatar(props){
    return (
        <img className='Avatar' 
         src={props.user.Avatar}
         alt={props.user.name} 
        />
    );
}
function UserInfo(props){
    return (
        <div className='UserInfo'>
            <Avatar Avatar={props.profilePic} />
            <p className='UserName'>{props.name}</p>
            <p className='Karma'>{props.karmaPoints}</p>
        </div>
    );
}
function Comment(props){
    return (
        <div className='Comment'>
            <UserInfo profilePic={props.userProfilePic} name={props.author} karmaPoints={props.userKarma} />
            <div className='Comment-text'>
                {props.content}
            </div>
            <div className='Date'>
                {props.commentDate}
            </div>
        </div>
    );
}
```
### Important
```
Props are Read-Only!
We never change their properties inside of a function/class created component
```
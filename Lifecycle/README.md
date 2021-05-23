# Lifecycle
```
Its important to free up resources. 
Therefore we only create self rendering components when they are needed - **Mounting**.
And we clear those components up as soon as we do not need them anymore - **Unmounting**.
```
### Lifecycle Methods
*Special methods that get called on specifig lifecycle events*

### Stateful components
- Needs to be written as ES6 class
- Needs a constructor that calls super(props)
- Constructor inits this.state
- Render Method returns the element
- Updatemethod contains the code to execute per update
- Lifecyclemethods define timers that call Updatemethod or destroy them
```javascript
//state is an object that changes over time (here: when edited by timer callback)
class Clock extends React.Component{
    constructor(props){
        super(props);
        this.state = {date: new Date()};
    }
    componentDidMount(){ //lifecyclemethod - gets called when mounted
        this.timer = setInterval(
            () => this.update(),
            1000
        );
    }
    componentWillUnmount(){ //lifecyclemethod - gets called when unmounted
        clearInterval(this.timer);
    }
    update(){
        this.setState = { //sets this.state property
            date: new Date()
        };
    }
    render(){
        return(
            <div className='Clock'>
                Current time: {this.state.date.toLocalTimeString()}
            </div>
        );
    }
}
ReactDOM.render(
    <Clock />,
    document.getElementById('root')
);
```

### Important stuff about State
- Do only modify over setState(). Do not modify directly.
- setState() may be async! So do not pass stuff that relys on the next state
    ```javascript
    // Wrong
    this.setState({
        counter: this.state.counter + this.props.increment,
    });
    ```
- instead use a form of setState() that accepts a callback
    ```javascript
    //Correct
    this.setState((state, props) => ({
        counter: state.counter + props.increment
    }));
    ```
- setState() merges the passed object into the stateobj. So you dont use the other properties
    ```javascript
    constructor(props) {
        super(props);
        this.state = {
            posts: [],
            comments: []
        };
    }
    componentDidMount() {
        fetchPosts().then(response => {
            this.setState({
                posts: response.posts //leaves 'state.comments' alone but replaces 'state.posts'
            });
        });

        fetchComments().then(response => {
            this.setState({
                comments: response.comments //leaves 'state.posts' alone but replaces 'state.comments'
            });
        });
    }
    ```


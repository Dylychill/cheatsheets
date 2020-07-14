# React

### Making Component

```js
function Person(props) {
    return <div style={{fontSize: props.age}}>
        {props.name}
    </div>
}
```
- The curly braces indicate a shift between JS and HTML, usually they are blue.

- Props are the only parameter and can be accessed with dot notation or bracket notation (props.name or props['name'])

### Use the component
- Capitalize the component tag (note the color changes to indicate it being built in component or not).

- Can be self closing tag or not

- Props (like arguments) can be passed into the component by writing them as attributes to the tag.

```js
<Person name="alice" age={30}/>
```

### Looping over components using .map()

- map is built in JavaScript

- Map always expects something to be returned

- It takes 2 arguments in this order: item (the value/thing itself) and index (unique variable through the loop)

- Requires a unique key using the index, so each loop has a unique key which cannot be accessed in the props - specific to React.

```js
function App()
    const people=['Alice', 'Bob', 'Casey']
    return <div>
        {people.map((item, index)=>{
            return <Person key={index} name={item}/>
        })}
    </div>
```

### useState
- saved as 2 variable array, the first is the value and the second is a function you make that will update the first value.

- Used to handle changes on the site


```js
function Counter(){
    const [count, setCount] = useState(0)
    return <button onClick={()=> setCount(count+1)}>
        You clicked me {count} times!
    </button>
}
```

### Conditionaly rendering components

```js
function App(){
    return <div>
        {1+1===2 && <WillRender />}
        {1+1===3 && <WontRender />}
        {1+1===2 ? <WillRender /> : <WontRender />}
    </div>
}
```

### useEffect
- useEffect is for code to run at specific times indicated by the array argument. Empty arrays mean run once at startup, while elements in the array will prompt running whenever they change.

```js
function App(){
  useEffect(()=>{
  }, [])
  return <div>hello world</div>
}
```

**or use useEffect more dynamically**

```js
function Person(props){
  useEffect(()=>{
    // this code will run EVERY time
    // that the persons "age" changes
  }, [props.age])
  return <div>{props.age}</div>
}
```
# React

## Creating a React App
There are plenty of ways to incoporate React. One form is using toolchains which basically do a bunch of set up for you. 

`npx create-react-app [name]`: creates a new react project with given name in the current directory. Can do this in a blank folder
- npx is a [package runner tool](https://medium.com/@maybekatz/introducing-npx-an-npm-package-runner-55f7d4bd282b)
- create-react-app toolchain is great for single page and beginner React projects.
- creates a public folder with front-facing content, node_modules containing dependencies for react, src folder for our react files, and package.json files.
- These are template and base files. App.js in the src folder is the main React file which is linked to the index.html file in public folder. When React is compiled into JS and given to the browser it pops in here.

`npm start`: inside a react project, opens in browser

`npm run build`: to build your app. When you’re ready to deploy to production, running this will create an optimized build of your app in the build folder.

`npm test`: Starts the test runner.

`npm run eject`: Removes this tool and copies build dependencies, configuration files and scripts into the app directory. If you do this, you can’t go back!

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

## useRef
React uses a virtual DOM - it is converted to JS and that is what makes the DOM
- Can't make assumptions about the DOM because the state is always changing, that is why you can't mess with it directly
- useRef() hook is how to interact with it
- Assigned refs are accessed by "ref.current" which is the actual element

```js
// auto focus an input!
function App(){
  const divRef = useRef()
  useEffect(()=>{
    divRef.current.focus()
  }, [])
  return <input ref={divRef}
    placeholder="hello world"
  />
}
```

## Create-react-app directory 


## Example app
```js
import React, {useState, useEffect} from 'react';
import './App.css';

const counterz=[{
  label:'Add One', n:1, initial:5
},{
  label:'Minus Two', n:-2
},{
  label:'Add 100', n:100
}]

function App() {
  return (
    <div className="App">
      {counterz.map((c,i)=>{
        return <Counter key={i} // React needs a "key"
          label={c.label} n={c.n} initial={c.initial}
        />
      })}
    </div>
  )
}

function Counter(props){
  const {label, n, initial} = props
  const [count, setCount] = useState(initial||0)
  return <div style={{marginTop:25}}>
    <button onClick={()=> setCount(count+n)}>
      {label}
    </button>
    <div>
      {count}
    </div>
  </div>
}

export default App;

```

## Animations with React
```js
function TextInput({show}){
  const [width] = useState(Math.random()*300)
  const inputRef = useRef()
  useEffect(()=>{
    if(show) {
      setTimeout(()=> inputRef.current.focus(), 250)
    }
    else inputRef.current.blur()
  }, [show])
  return <input ref={inputRef} 
    placeholder="hello world"
    style={{
      width: width,
      transition: 'all 0.2s',
      transform: show ? 
        'translate(0,0) rotate(0)' : 
        'translate(400px,0) rotate(180deg)',
      opacity: show ? 1 : 0,
    }}
  />
}
```

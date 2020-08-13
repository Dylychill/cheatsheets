# Javascript

### variables

```js
// 3 ways to make variables
var hi = 'hello'
let hi = 'hello' // let is better
const hi = 'hello' // consts cant change
```
**variable types**
```js
// simple types
let hi = 'hello' // string
let num = 10 // number
let bool = true // boolean

// compound types (you can mix-and-match types)
let arr = [1,2,3,'hi'] // array
arr[3] // equals 'hi'

let obj = { // object
    hi: 'hello',
    n: 1001,
    b: false,
    funky: function(){
        // you can even put functions inside
    }
}
obj.funky() // will run the funky function
obj.n // equals 1001
obj['n'] // ALSO equals 1001

// functions are also variables!
var funky = function(){
    console.log('a funky function')
}
```

### functions
```js
// function definition. It returns the answer (but not all functions need to return something)
// this function has 2 arguments, "a" and "b"
function add(a,b){
    // the body of the function
    return a+b
}
// calling a function (and passing in 2 values)
// now c = 3
var c = add(1,2)

// fat arrow syntax (mean "return")
// this is identical to the other one
// you dont have to type the word "function"!
var add2 = (a,b) => a+b
```

### loops
```js
for(let i=0; i<100; i++) {
    console.log(i) // will print every number between 0 and 100
}

// .map !!! we use it in React all the time
[1,2,3].map((n,i)=> console.log(n,i))
```

### if statements
```js
if(3===2) {
    console.log('nope')
} else {
    console.log('yup')
}
if(3=='3') { // == only compares value
    console.log('YES!!')
}
if(3==='3') { // === compares value AND type
    console.log('nope')
}
if(3!=='3') { // === compares value AND type, ! means not and replaces a = symbol
    console.log('yess')
}
if (true&&false) { // AND
    console.log('nope')
}
if (true || false) { // OR
    console.log('YES!!')
}


// "ternary expression" one-line if statement
// evaluates the expression ? if true pick first variable : if false pick the second
var n = 2==='2' ? 10 : 'hello' // prints "hello"
```
```jsx
// ternary expressions are very useful in React code, to make dynamic props
<div style={{
    color: darkMode ? 'white' : 'black'
}} />

// or for dynamically rendering components
function Header(){
    const [settings, setSettings] = useState(false)
    return <div>
        { settingsToggled ?
            <SettingsMenu /> :
            <ToggleButton />
        }
    </div>
}

// conditions - && is common
// below, MyComponent will only render if condition is true
const [condition, setCondition] = useState(true);
return <div>
    {condition && <MyComponent />}
    {!condition && <TheOtherComponent />}
</div>
```
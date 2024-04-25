### Vid 2
- Challenge:
    - Build the Header component
```jsx
// Header.js
import React from "react"

export default function Header() {
    return (
        <header className="header">
            <img 
                src="./images/troll-face.png" 
                className="header--image"
            />
            <h2 className="header--title">Meme Generator</h2>
            <h4 className="header--project">React Course - Project 3</h4>
        </header>
    )
}
```
### Vid 3
-  Challenge: 
   - Create a Meme component.
   - Inside the Meme component, render a styled form with our 2 inputs and the button.
   - Don't worry about adding any functionality yet
```jsx
  //Meme.js
  import React from "react"

  export default function Meme() {
    return (
        <main>
            <form className="form">
                <input 
                    type="text"
                    placeholder="Top text"
                    className="form--input"
                />
                <input 
                    type="text"
                    placeholder="Bottom text"
                    className="form--input"
                />
                <button 
                    className="form--button"
                >
                    Get a new meme image 🖼
                </button>
            </form>
        </main>
    )
  }
```
### Vid 6
- Instruction: 
  - Add our new function to the button
```jsx
  import React from "react"

  export default function App() {
    function handleClick() {
        console.log("I was clicked!")
    }

    return (
        <div className="container">
            <img src="https://picsum.photos/640/360" />
            <button onClick={handleClick()}>Click me</button>// handleClick function added here
    )
  }
```
- Challenge: 
  - Log something to the console when the mouse hovers over the image
```jsx
  import React from "react"

  export default function App() {
    function handleClick() {
        console.log("I was clicked!")
    }
    
    function handleOnMouseOver() {
        console.log("MouseOver")
    }

    return (
        <div className="container">
            <img 
                src="https://picsum.photos/640/360" 
                onMouseOver={handleOnMouseOver} 
            />
            <button onClick={handleClick}>Click me</button>
        </div>
    )
  }

```
### Vid 7
-  Challenge: 
    - Get a random image from the `memesData` array when the "new meme image" button is clicked.
    - Log the URL of the image to the console. (Don't worry about displaying the image ye)
```jsx
import React from "react"
import memesData from "../memesData.js"

export default function Meme() {

    let url
    
    function getMemeImage() {
        const memesArray = memesData.data.memes
        const randomNumber = Math.floor(Math.random() * memesArray.length)
        url = memesArray[randomNumber].url
        console.log(url)
    }
    
    return (
        <main>
            <div className="form">
                <p>{url}</p>
                <input 
                    type="text"
                    placeholder="Top text"
                    className="form--input"
                />
                <input 
                    type="text"
                    placeholder="Bottom text"
                    className="form--input"
                />
                <button 
                    className="form--button"
                    onClick={getMemeImage}
                >
                    Get a new meme image 🖼
                </button>
            </div>
        </main>
    )
}
```
### Vid 8
- Challenge: Map over the thingsArray to generate a <p> element for each item and render them on the page below the button
```jsx
import React from 'react';
import ReactDOM from 'react-dom';

function App() {
    const thingsArray = ["Thing 1", "Thing 2"]

    const thingsElements = thingsArray.map(thing => <p key={thing}>{thing}</p>)
    
    return (
        <div>
            <button>Add Item</button>
            {thingsElements}
        </div>
    )
}

ReactDOM.render(<App />, document.getElementById('root'));
```
-  Challenge: Add an event listener to the button so when it is clicked, it adds another thing to our array
    - Hint: use the array length + 1 to determine the number of the "Thing" being added. Also, have you event listener console.log(thingsArray) after adding the new item to the array
    - Spoiler: the page won't update when new things get added to the array!
```jsx
import React from 'react';
import ReactDOM from 'react-dom';

function App() {
    const [things, setThings] = React.useState(["Thing 1", "Thing 2"])
    
    function addItem() {
        const newThingText = `Thing ${things.length + 1}`
        setThings(prevState => [...prevState, newThingText])
    }
    
    const thingsElements = things.map(thing => <p key={thing}>{thing}</p>)
    
    return (
        <div>
            <button onClick={addItem}>Add Item</button>
            {thingsElements}
        </div>
    )
}

ReactDOM.render(<App />, document.getElementById('root'));
```
### Vid 10
- Challenge: complete the function below
    - Given a name, return "Good <timeOfDay>, <name>!" depending on the current time of day.
```jsx

function greeting(name) {
    const date = new Date()
    const hours = date.getHours()
    
    let timeOfDay
    if(hours >= 4 && hours < 12) {
        timeOfDay = "morning"
    } else if(hours >= 12 && hours < 17) {
        timeOfDay = "afternoon"
    } else if(hours >= 17 && hours < 20) {
        timeOfDay = "evening"
    } else {
        timeOfDay = "night"
    }
    
    return `Good ${timeOfDay}, ${name}!`
}

console.log(greeting("Bob"))
```
### Vid 11
-  Quiz
    1. How would you describe the concept of "state"?
        - Internal data of a React component that represents its current condition.

    2. When would you want to use props instead of state?
        - When passing data from a parent component to a child component.

    3. When would you want to use state instead of props?
        - When managing data within a component that can change over time.

    4. What does "immutable" mean? Are props immutable? Is state immutable?
        - "Immutable" means unchangeable. Props are immutable. State is mutable.

### Vid 12
-   Challenge: Replace our hard-coded "Yes" on the page with ome state initiated with `React.useState()`
```jsx
import React from "react"

export default function App() {

    const result = React.useState("Yes")
    console.log(result)
    return (
        <div className="state">
            <h1 className="state--title">Is state important to know?</h1>
            <div className="state--value">
                <h1>{result[0]}</h1>
            </div>
        </div>
    )
}
```
### Vid 14
-  Challenge: 
     1. Create a function called `handleClick` that runssetIsImportant("No")
     2. add a click event listener to the div.state--value that runs `handleClick` when the div is clicked.
```jsx
import React from "react"

export default function App() {
    const [isImportant, setIsImportant] = React.useState("Yes")

    function handleClick() {
        setIsImportant("No")
    }
    
    return (
        <div className="state">
            <h1 className="state--title">Is state important to know?</h1>
            <div className="state--value" onClick={handleClick}>
                <h1>{isImportant}</h1>
            </div>
        </div>
    )
}
```
### Vid 15
- Challenge: 
    1. Set up state to track our count (initial value is 0)
    2. Create a function called `add` that runs when the + button is clicked. (Can just console.log("add") for now)
    3. See if you can think of a way to add 1 to the count every time the + button is clicked
    4. Add functionality to the minus button.
```jsx
// 1
import React from "react"

export default function App() {

    const [count, setCount] = React.useState(0) // Here
    
    return (
        <div className="counter">
            <button className="counter--minus">–</button>
            <div className="counter--count">
                <h1>{count}</h1>
            </div>
            <button className="counter--plus">+</button>
        </div>
    )
}

// 2
import React from "react"

export default function App() {

    const [count, setCount] = React.useState(0)
    
    function add() { // Here
        setCount(1)
    }
    
    return (
        <div className="counter">
            <button className="counter--minus">–</button>
            <div className="counter--count">
                <h1>{count}</h1>
            </div>
            <button className="counter--plus" onClick={add}>+</button>
        </div>
    )
}

// 3
import React from "react"

export default function App() {

    const [count, setCount] = React.useState(0)
    
    function add() {
        setCount(count + 1) // Here
    }
    
    return (
        <div className="counter">
            <button className="counter--minus">–</button>
            <div className="counter--count">
                <h1>{count}</h1>
            </div>
            <button className="counter--plus" onClick={add}>+</button>
        </div>
    )
}

// 4
import React from "react"

export default function App() {

    const [count, setCount] = React.useState(0)
    
    function add() {
        setCount(count + 1)
    }
    
    function subtract() { // Here
        setCount(count - 1)
    }
    
    return (
        <div className="counter">
            <button className="counter--minus" onClick={subtract}>–</button>
            <div className="counter--count">
                <h1>{count}</h1>
            </div>
            <button className="counter--plus" onClick={add}>+</button>
        </div>
    )
}
```

### Vid 17
- Quiz
    1. You have 2 options for what you can pass in to a state setter function (e.g. `setCount`). What are they?
        - The new value/state or a function that receives the previous state and returns the new state.

    2. When would you want to pass the first option (from answer above) to the state setter function?
        - When the new state does not depend on the previous state and can be directly provided as a value.

    3. When would you want to pass the second option (from answer above) to the state setter function?
        - When the new state depends on the previous state, and you need to compute the new state based on the previous state's value or perform some logic before updating the state.

### Vid 18
- Challenge: 
    - Save the random meme URL in state
    - Create new state called `memeImage` with an empty string as default
    - When the getMemeImage function is called, update the `memeImage` state to be the random chosen image URL
    - Below the div.form, add an <img /> and set the src to the new `memeImage` state you created
```jsx
//Meme.js
import React from "react"
import memesData from "../memesData.js"

export default function Meme() {
    const [memeImage, setMemeImage] = React.useState("") // Here
    
    function getMemeImage() {
        const memesArray = memesData.data.memes
        const randomNumber = Math.floor(Math.random() * memesArray.length)
        setMemeImage(memesArray[randomNumber].url) // Here
        
    }
    
    return (
        <main>
            <div className="form">
                <input 
                    type="text"
                    placeholder="Top text"
                    className="form--input"
                />
                <input 
                    type="text"
                    placeholder="Bottom text"
                    className="form--input"
                />
                <button 
                    className="form--button"
                    onClick={getMemeImage}
                >
                    Get a new meme image 🖼
                </button>
            </div>
            <img src={memeImage} /> // Here
        </main>
    )
}
```

### Vid 19
- Challenge: Replace the if/else below with a ternary to determine the text that should display on the page
```jsx
// Not quite there yet
import React from "react"

export default function App() {

    const isGoingOut = true
    let answer = isGoingOut ? "Yes" : "No"
    
    return (
        <div className="state">
            <h1 className="state--title">Do I feel like going out tonight?</h1>
            <div className="state--value">
                <h1>{answer}</h1>
            </div>
        </div>
    )
}

// There ya go, you got it!
import React from "react"

export default function App() {

    const isGoingOut = true
    
    return (
        <div className="state">
            <h1 className="state--title">Do I feel like going out tonight?</h1>
            <div className="state--value">
                <h1>{isGoingOut ? "Yes" : "No"}</h1>
            </div>
        </div>
    )
}
```

### Vid 20
- Challenge: 
     - Initialize state for `isGoingOut` as a boolean
     - Make it so clicking the div.state--value flips that boolean value (true -> false, false -> true)
     - Display "Yes" if `isGoingOut` is `true`, "No" otherwise
```jsx
import React from "react"

export default function App() {
    const [isGoingOut, setIsGoingOut] = React.useState(true)

    function changeMind() {
        setIsGoingOut(prevState => !prevState)
    }
    
    return (
        <div className="state">
            <h1 className="state--title">Do I feel like going out tonight?</h1>
            <div onClick={changeMind} className="state--value">
                <h1>{isGoingOut ? "Yes" : "No"}</h1>
            </div>
        </div>
    )
}
```
### Vid 22
- Challenge: 
    - Convert the code below to use an array held in state instead of a local variable. 
    - Initialize the state array with the same 2 items below
```jsx
import React from 'react';
import ReactDOM from 'react-dom';

function App() {
    const [thingsArray, setThingsArray] = React.useState(["Thing 1", "Thing 2"])
    
    function addItem() {
        setThingsArray(prevState => {
            return [...prevState, `Thing ${prevState.length + 1}`]
        })
    }
    
    const thingsElements = thingsArray.map(thing => <p key={thing}>{thing}</p>)
    
    return (
        <div>
            <button onClick={addItem}>Add Item</button>
            {thingsElements}
        </div>
    )
}

ReactDOM.render(<App />, document.getElementById('root'));
// Note: I was not able to repeat this over again from  wrote memory, mostly because of there being tight time constraints for my studying and I've currently no Dexmethylphenidate handy ("Yeah, suuure...", they all said.) lol. But that's the answer anyhow!
```

### Vid 23
-  Challenge: Fill in the values in the markup using the properties of our state object above (Ignore `isFavorite` for now)
```jsx
import React from "react"

export default function App() {
    const [contact, setContact] = React.useState({
        firstName: "John",
        lastName: "Doe",
        phone: "+1 (719) 555-1212",
        email: "itsmyrealname@example.com",
        isFavorite: false
    })

    function toggleFavorite() {
        console.log("Toggle Favorite")
    }
    
    return (
        <main>
            <article className="card">
                <img src="./images/user.png" className="card--image" />
                <div className="card--info">
                    <img 
                        src={`../images/star-empty.png`} 
                        className="card--favorite"
                        onClick={toggleFavorite}
                    />
                    <h2 className="card--name">
                        {contact.firstName} {contact.lastName} // Here
                    </h2>
                    <p className="card--contact">{contact.phone}</p> // Here
                    <p className="card--contact">{contact.email}</p> // Here
                </div>
                
            </article>
        </main>
    )
}
```
- Challenge: Use a ternary to determine which star image filename should be used based on the `contact.isFavorite` property
```jsx
import React from "react"

export default function App() {
    const [contact, setContact] = React.useState({
        firstName: "John",
        lastName: "Doe",
        phone: "+1 (719) 555-1212",
        email: "itsmyrealname@example.com",
        isFavorite: false
    })

    let starIcon = contact.isFavorite ? "star-filled.png" : "star-empty.png" // Here
    
    function toggleFavorite() {
        console.log("Toggle Favorite")
    }
    
    return (
        <main>
            <article className="card">
                <img src="./images/user.png" className="card--image" />
                <div className="card--info">
                    <img 
                        src={`../images/${starIcon}`} // Here
                        className="card--favorite"
                        onClick={toggleFavorite}
                    />
                    <h2 className="card--name">
                        {contact.firstName} {contact.lastName}
                    </h2>
                    <p className="card--contact">{contact.phone}</p>
                    <p className="card--contact">{contact.email}</p>
                </div>
                
            </article>
        </main>
    )
}

```

### Vid 25
- Challenge:
    - Update our state to save the meme-related data as an object called `meme`. It should have the following 3 properties:
      - topText
      - bottomText
      - randomImage.
    - The 2 text states can default to empty strings for now, and randomImage should default to "http://i.imgflip.com/1bij.jpg"
    - Next, create a new state variable called `allMemeImages`which will default to `memesData`, which we imported above
    - Lastly, update the `getMemeImage` function and the markup to reflect our newly reformed state object and array in the correct way.
```jsx
import React from "react"
import memesData from "../memesData.js"

export default function Meme() {

    const [meme, setMeme] = React.useState({ // Here
        topText: "",
        bottomText: "",
        randomImage: "http://i.imgflip.com/1bij.jpg" 
    })
    const [allMemeImages, setAllMemeImages] = React.useState(memesData) // Here
    
    
    function getMemeImage() {
        const memesArray = allMemeImages.data.memes
        const randomNumber = Math.floor(Math.random() * memesArray.length)
        const url = memesArray[randomNumber].url // Here
        setMeme(prevMeme => ({
            ...prevMeme,
            randomImage: url
        }))
        
    }
    
    return (
        <main>
            <div className="form">
                <input 
                    type="text"
                    placeholder="Top text"
                    className="form--input"
                />
                <input 
                    type="text"
                    placeholder="Bottom text"
                    className="form--input"
                />
                <button 
                    className="form--button"
                    onClick={getMemeImage}
                >
                    Get a new meme image 🖼
                </button>
            </div>
            <img src={meme.randomImage} className="meme--image" />
        </main>
    )
}
```
### Vid 26
- Challenge:
    - Create a new component named Count
        - It should receive a prop called `number`, whose value is the current value of our count
        - Have the component render the whole div.counter--count and display the incoming prop `number`
    - Replace the div.counter--count below with an instance of the new Count component
```jsx
// Count.js
import React from "react"

export default function Count(props) {
    return (
        <div className="counter--count">
            <h1>{props.number}</h1>
        </div>
    )
}
// App.js
import React from "react"
import Count from "./Count"

export default function App() {
    const [count, setCount] = React.useState(0)
    
    function add() {
        setCount(prevCount => prevCount + 1)
    }
    
    function subtract() {
        setCount(prevCount => prevCount - 1)
    }
    
    console.log("App component rendered")
    
    return (
        <div className="counter">
            <button className="counter--minus" onClick={subtract}>–</button>
            <Count number={count} />
            <button className="counter--plus" onClick={add}>+</button>
        </div>
    )
}
```

### Vid 27
- Challenge: Move the star image into its own component
     - It should receive a prop called `isFilled` that it uses to determine which icon it will display
     - Import and render that component, passing the value of `isFavorite` to the new `isFilled` prop.
     - Don't worry about the ability to flip this value quite yet. Instead, you can test if it's working by manually changing `isFavorite` in state above.
```jsx
// Star.js
import React from "react"

export default function Star(props) {
    const starIcon = props.isFilled ? "star-filled.png" : "star-empty.png"
    return (
        <img 
            src={`../images/${starIcon}`} 
            className="card--favorite"
            onClick={props.handleClick}
        />
    )
}
// App.js
import React from "react"
import Star from "./Star"

export default function App() {
    const [contact, setContact] = React.useState({
        firstName: "John",
        lastName: "Doe",
        phone: "+1 (719) 555-1212",
        email: "itsmyrealname@example.com",
        isFavorite: false // Manually toggle between true or false
    })

    let starIcon = contact.isFavorite ? "star-filled.png" : "star-empty.png"
    
    function toggleFavorite() {
        setContact(prevContact => ({
            ...prevContact,
            isFavorite: !prevContact.isFavorite
        }))
    }
    
    return (
        <main>
            <article className="card">
                <img src="./images/user.png" className="card--image" />
                <div className="card--info">
                    <Star isFilled={contact.isFavorite} />
                    <h2 className="card--name">
                        {contact.firstName} {contact.lastName}
                    </h2>
                    <p className="card--contact">{contact.phone}</p>
                    <p className="card--contact">{contact.email}</p>
                </div>
                
            </article>
        </main>
    )
}

```

### Vid 28
- Challenge:
    - If the star is filled, add an aria-label of "Unmark as favorite".
    - Otherwise, use the aria-label of "Mark as favorite".
```jsx
import React from "react"

export default function Star(props) {
    const starIcon = props.isFilled ? "star-filled.png" : "star-empty.png"
    const buttonLabel = props.isFilled ? "Unmark as favorite" : "Mark as favorite"
    return (
        <button
            onClick={props.handleClick}
            aria-label={buttonLabel}
        >
            <img
                src={`../images/${starIcon}`}
                className="card--favorite"
            />
        </button>
    )
}
```

### Vid 29
-  Challenge:
    - Raise state up a level and pass it down to both the Header and Body components through props.
```jsx
// Before
// App.js
import React from "react"
import Header from "./Header"
import Body from "./Body"

export default function App() {
    return (
        <main>
            <Header />
            <Body />
        </main>
    )
}

// Body.js
import React from "react"

export default function Body() {
    return (
        <section>
            <h1>Welcome back, ___!</h1>
        </section>
    )
}

// Header.js
import React from "react"

export default function Header() {
    const [user, setUser] = React.useState("Joe")
    
    return (
        <header>
            <p>Current user: {user}</p>
        </header>
    )
}

// After
// App.js
import React from "react"
import Header from "./Header"
import Body from "./Body"

export default function App() {
    const [user, setUser] = React.useState("Bob")
    
    return (
        <main>
            <Header user={user} />
            <Body user={user} />
        </main>
    )
}

// Header.js
import React from "react"

export default function Header(props) {
    return (
        <header>
            <p>Current user: {props.user}</p>
        </header>
    )
}

// Body.js
import React from "react"

export default function Body(props) {
    return (
        <section>
            <h1>Welcome back, {props.user}!</h1>
        </section>
    )
}

```
### Vid 30
- Challenge part 1:
     1. Initialize state with the default value of the array pulled in from boxes.js
     2. Map over that state array and display each one as an empty square (black border, transparent bg color)(Don't worry about using the "on" property yet)
```jsx
import React from "react"
import boxes from "./boxes"

export default function App() {
    const [squares, setSquares] = React.useState(boxes) // Here
    const squareElements = squares.map(square => ( // Here
        <div className="box" key={square.id}></div>
    ))

    return (
        <main>
            {squareElements}
        </main>
    )
}
```
### Vid 31
- Challenge 1: use a ternary to determine the backgroundColor.
    - If darkMode is true, set it to "#222222"
    - If darkMode is false, set it to "#cccccc"
```jsx
  const styles = {
        backgroundColor: props.darkMode ? "#222222" : "#cccccc"
    }
```
### Vid 32
-  Challenge part 2:
     1. Create a separate component called "Box" and replace the `div` above with our <Box /> components
     2. Pass the Box component a prop called `on` with the value of the same name from the `boxes` objects
     3. In the Box component, apply dynamic styles to determine the backgroundColor of the box. If it's `on`, set the backgroundColor to "#222222". If off, set it to "none"
```jsx
// App.js
import React from "react"
import boxes from "./boxes"
import Box from "./Box"

export default function App() {
    const [squares, setSquares] = React.useState(boxes)
    
    const squareElements = squares.map(square => (
        <Box key={square.id} on={square.on} />
    ))

    return (
        <main>
            {squareElements}
        </main>
    )
}

// Box.js
import React from "react"

export default function Box(props) {
    const styles = {
        backgroundColor: props.on ? "#222222" : "none"
    }
    
    return (
        <div style={styles} className="box"></div>
    )
}
```
    
### Vid 33
- Challenge: 
    - Create state controlling whether this box is "on" or "off". Use the incoming `props.on` to determine the initial state.
    - Create an event listener so when the box is clicked, it toggles from "on" to "off".
    - Goal: clicking each box should toggle it on and off.
```jsx
import React from "react"

export default function Box(props) {
    const [on, setOn] = React.useState(props.on)
    
    const styles = {
        backgroundColor: on ? "#222222" : "transparent"
    }
    
    function toggle() {
        setOn(prevOn => !prevOn)
    }
    
    return (
        <div style={styles} className="box" onClick={toggle}></div> // Added this later after re-watching the video
    )
}
```

### Vid 34
- Challenge: 
    - Create a toggle() function that logs "clicked!" to the console
    - Pass that function down to each of the Box components and set it up so when they get clicked it runs the function
```jsx
// This challenge was too difficult for me to reproduce very well. 
```
### Vid 35
- Challenge: 
    - Use setSquares to update the correct square in the array. 
    - Make sure not to directly modify state!
    - Hint: look back at the lesson on updating arrays in state if you need a reminder on how to do this
```jsx
    function toggle(id) {
        setSquares(prevSquares => { // Here
            const newSquares = []
            for(let i = 0; i < prevSquares.length; i++) {
                const currentSquare = prevSquares[i]
                if(currentSquare.id === id) {
                    const updatedSquare = {
                        ...currentSquare,
                        on: !currentSquare.on
                    }
                    newSquares.push(updatedSquare)
                } else {
                    newSquares.push(currentSquare)
                }
            }
            return newSquares
        })
    }
// This challenge was a difficult for me.
```

### Vid 38
-  Challenge:
     - Create state `isShown` (boolean, default to `false`)
     - Add a button that toggles the value back and forth
```jsx
import React from "react"

export default function Joke(props) {
    const [isShown, setIsShown] = React.useState(false) // Here

    function toggleShown(){
        console.log(isShown) // Outputs: false 
        setIsShown(prevShown => !prevShown)
    }
    return (
        <div>
            {props.setup && <h3>{props.setup}</h3>}
            <p>{props.punchline}</p>
            <button onClick={toggleShown}>Show Punchline</button> // Here
            <hr />
        </div>
    )
}

```
- Challenge:
    - Only display the punchline paragraph if `isShown` is true
```jsx
// I need to improve my JS writing to properly get the right answers in this challenge.  
```
### Vid 39
- Challenge
    - Only display the `<h1>` below if there are unread messages
```jsx
import React from "react"

export default function App() {
    const [messages, setMessages] = React.useState(["a", "b"])

    return (
        <div>
            {messages.length > 0 && <h1>You have {messages.length} unread messages!</h1>} // Can be placed on separate lines to improve readability.
        </div>
    )
}
```

### Vid 41
- Challenge:
     - If there are no unread messages, display "You're all caught up!"
     - If there are > 0 unread messages, display "You have <n> unread message(s)"
        - If there's exactly 1 unread message, it should read "message" (singular)
```jsx
import React from "react"

export default function App() {
    const [messages, setMessages] = React.useState(["a"]) // Unread messages

    return (
        <div>
            {
                messages.length === 0 ?
                <h1>You're all caught up!</h1> :
                <h1>You have {messages.length} unread message{messages.length > 1 && "s"}</h1> // If greater than one message it goes from singular to plural
            }
        </div>
    )
}

```
### Vid 42
- Quiz
    1. What is "conditional rendering"?
        - Dynamically displaying content based on conditions.

    2. When would you use &&?
        - For simple "truthy" checks in conditional rendering. 

    3. When would you use a ternary?
        - Choosing between two options based on a condition.

    4. What if you need to decide between > 2 options on
    what to display?
        - Use nested ternary operators or switch-case or mapping over data 

### Vid 44
- Challenge: 
    - Update the firstName state on every keystroke
```jsx
import React from "react"

export default function Form() {
    const [firstName, setFirstName] = React.useState("")
    
    console.log(firstName)
    
    function handleChange(event) {
        setFirstName(event.target.value) // Here
    }
    
    return (
        <form>
            <input
                type="text"
                placeholder="First Name"
                onChange={handleChange}
            />
        </form>
    )
}
```
### Vid 45
- Challenge: 
    - Track the applicant's last name as well
```jsx
import React from "react"

export default function Form() {
    const [firstName, setFirstName] = React.useState("")
    const [lastName, setLastName] = React.useState("")

    console.log(firstName, lastName) // Output: prints the text from the two inputs to let me know that I followed the procedure correctly, life is good!
    
    function handleFirstNameChange(event) { 
        setFirstName(event.target.value)
    }
    
    function handleLastNameChange(event) {  
        setLastName(event.target.value)
    }
    
    return (
        <form>
            <input
                type="text"
                placeholder="First Name"
                onChange={handleFirstNameChange}
            />
            <input
                type="text"
                placeholder="Last Name"
                onChange={handleLastNameChange}
            />
        </form>
    )
}
```

### Vid 47
- Challenge:
    - Add an email field/state to the form
```jsx
import React from "react"

export default function Form() {
    const [formData, setFormData] = React.useState(
        {firstName: "", lastName: "", email: ""} // Added in email
    )

    
    console.log(formData) // Output: confirmed proper output
    
    function handleChange(event) {
        setFormData(prevFormData => {
            return {
                ...prevFormData,
                [event.target.name]: event.target.value
            }
        })
    }
    
    return (
        <form>
            <input
                type="text"
                placeholder="First Name"
                onChange={handleChange}
                name="firstName"
            />
            <input
                type="text"
                placeholder="Last Name"
                onChange={handleChange}
                name="lastName"
            />
            <input // Duplicated the above broiler plate code and changed the content to update the email info.
                type="email"
                placeholder="Email"
                onChange={handleChange}
                name="email"
            />
        </form>
    )
}

```

### Vid 49
- Challenge: 
    - Add a textarea for "comments" to the form
    - Make sure to update state when it changes.
```jsx
import React from "react"

export default function Form() {
    const [formData, setFormData] = React.useState(
        {firstName: "", lastName: "", email: "", comments: ""} // Add comments object
    )
    
    console.log(formData.comments) // Output: whatever is typed into the new textarea field inside my practice form.
    
    function handleChange(event) {
        setFormData(prevFormData => {
            return {
                ...prevFormData,
                [event.target.name]: event.target.value
            }
        })
    }
    
    
    return (
        <form>
            <input
                type="text"
                placeholder="First Name"
                onChange={handleChange}
                name="firstName"
                value={formData.firstName}
            />
            <input
                type="text"
                placeholder="Last Name"
                onChange={handleChange}
                name="lastName"
                value={formData.lastName}
            />
            <input
                type="email"
                placeholder="Email"
                onChange={handleChange}
                name="email"
                value={formData.email}
            />
            <textarea  // Add textarea element
                value={formData.comments} // Necessary for it to be a controlled component
                placeholder="Comments"
                onChange={handleChange}
                name="comments"
            />
        </form>
    )
}
```
### These tutorials on <mark>forms are extremely valuable for my final project</mark>. 

### Vid 55
- Quiz
  1. In a vanilla JS app, at what point in the form submission process do you gather all the data from the filled-out form?
      - Gather all the data from the filled-out form upon submitting the form, usually in an event handler for the form's submit event.


  2.  In a React app, when do you gather all the data from the filled-out form?
      - You would typically gather all the data from the filled-out form when handling the form's submit event, similar to a vanilla JS app.


  3. Which attribute in the form elements (value, name, onChange, etc.) should match the property name being held in state for that input?
      - 'Name' attribute of the form element should match the property name being held in state for that input element. This allows the data to be correctly associated with the corresponding state property.


  4. What's different about a saving the data from a checkbox element vs. other form elements?
      - Checkboxes allow multiple selections, resulting in an array of selected values.

  5. How do you watch for a form submit? How can you trigger a form submit?
      - Watch for form submit by attaching an event handler to the form's onSubmit attribute. Trigger form submit by clicking a submit button or calling the form's submit() method.

### Vid 56
- Challenge: Connect the form to local state
     1. Create a state object to store the 4 values we need to save.
     2. Create a single handleChange function that can manage the state of all the inputs and set it up correctly
     3. When the user clicks "Sign up", check if the password & confirmation match each other. If so, log "Successfully signed up" to the console. If not, log "passwords to not match" to the console.
     4. Also when submitting the form, if the person checked the "newsletter" checkbox, log "Thanks for signing up for our newsletter!" to the console.
```jsx
// State object
    const [formData, setFormData] = React.useState({
        email: "",
        password: "",
        passwordConfirm: "",
        joinedNewsletter: true
    })
// handleChange function
    function handleChange(event) {
        const {name, value, type, checked} = event.target
        setFormData(prevFormData => ({
            ...prevFormData,
            [name]: type === "checkbox" ? checked : value
        }))
    }
    console.log(formData)
// While I had difficulty recreating the JS logic for recreating proper functioning of the 'Sign up' button, the progression of wiring up the form was pretty straight forward. 

```
### Vid 57
- Challenge: 
     1. Set up the text inputs to save to the `topText` and `bottomText` state variables.
     2. Replace the hard-coded text on the image with the text being saved to state.
```jsx
import React from "react"
import memesData from "../memesData.js"

export default function Meme() {

    
    const [meme, setMeme] = React.useState({
        topText: "",
        bottomText: "",
        randomImage: "http://i.imgflip.com/1bij.jpg" 
    })
    const [allMemeImages, setAllMemeImages] = React.useState(memesData)
    
    
    function getMemeImage() {
        const memesArray = allMemeImages.data.memes
        const randomNumber = Math.floor(Math.random() * memesArray.length)
        const url = memesArray[randomNumber].url
        setMeme(prevMeme => ({
            ...prevMeme,
            randomImage: url
        }))
        
    }
    
    function handleChange(event) { // Event handler function for pulling in the event to set the meme and change the top/bottom text depending on what name gets pulled in
        const {name, value} = event.target
        setMeme(prevMeme => ({
            ...prevMeme,
            [name]: value
        }))
    }
    
    return (
        <main>
            <div className="form">
                <input 
                    type="text"
                    placeholder="Top text"
                    className="form--input"
                    name="topText" // Here
                    value={meme.topText}
                    onChange={handleChange}
                />
                <input 
                    type="text"
                    placeholder="Bottom text"
                    className="form--input"
                    name="bottomText" // Here
                    value={meme.bottomText}
                    onChange={handleChange}
                />
                <button 
                    className="form--button"
                    onClick={getMemeImage}
                >
                    Get a new meme image 🖼
                </button>
            </div>
            <div className="meme">
                <img src={meme.randomImage} className="meme--image" />
                <h2 className="meme--text top">{meme.topText}</h2> // Here
                <h2 className="meme--text bottom">{meme.bottomText}</h2> // Here
            </div>
        </main>
    )
}
```

### Vid 62

- Quiz
    1. What is a "side effect" in React? What are some examples?
        - Side effects are extra things a component can do besides rendering. Examples: making API calls, changing the webpage content, handling user interactions.

    2. What is NOT a "side effect" in React? Examples?
        - Regular stuff a component does without any extra actions. Examples: calculating values, checking conditions, displaying data.

    3. When does React run your useEffect function? When does it NOT run
   the effect function?
        - React runs useEffect after the component renders. It skips running if the dependencies haven't changed.

    4. How would you explain what the "dependecies array" is?
        - The "dependencies array" is like a list of things React watches. When anything in the list changes, the effect function runs again. If the list is empty, the effect runs only once, when the component first shows up. It's a way to control when the effect should happen based on specific changes.

### Vid 63
- Quiz:
     1. What will happen if I put back our Star Wars API call into the effect function?
        - If I put the Star Wars API call back into the effect function, the effect will be triggered whenever theres a change in the count state. It means that every time the "Add" button is clicked and the count is updated, the API call will be made and the fetched data will be logged to the console.

     2. How will the useEffect be different if I use setStarWarsData() instead of console.log()
        - If I use setStarWarsData(data) instead of console.log(data) in the useEffect, the fetched Star Wars data will be stored in the starWarsData state variable. Each time the effect runs (when the count state changes), the API call will be made, and the fetched data will be set as the new value of starWarsData, updating the displayed JSON object and re-rendering the component stuff.

     3. What SHOULD be in our dependencies array in this case?
        - I think the count state variable should be included in the dependencies array to ensure that the effect is re-run whenever the count value changes. By including count in the dependencies array, React knows that the effect is dependent on the count value and will re-execute it whenever count changes, ensuring the correct behavior of the component.

### Vid 64
- Challenge: 
    - Combine `count` with the request URL so pressing the "Get Next Character" button will get a new character from the Star Wars API.
    - Remember: don't forget to consider the dependencies array!
```jsx
import React from "react"

export default function App() {
    const [starWarsData, setStarWarsData] = React.useState({})
    const [count, setCount] = React.useState(1)

    
    React.useEffect(function() {
        console.log("Effect ran")
        fetch("https://swapi.dev/api/people/" + count) // Here
            .then(res => res.json())
            .then(data => setStarWarsData(data))
    }, [count]) // Here
    
    return (
        <div>
            <h2>The count is {count}</h2>
            <button onClick={() => setCount(prevCount => prevCount + 1)}>Get Next Character</button>
            <pre>{JSON.stringify(starWarsData, null, 2)}</pre>
        </div>
    )
}
// My version of the code works fine
```
### Vid 65
- Challenge: 
    - As soon as the Meme component loads the first time, make an API call to "https://api.imgflip.com/get_memes".
    - When the data comes in, save just the memes array part of that data to the `allMemes` state
    - Think about if there are any dependencies that, if they changed, you'd want to cause to re-run this function.
    - Hint: for now, don't try to use an async/await function.
    - Instead, use `.then()` blocks to resolve the promises from using `fetch`. We'll learn why after this challenge.
```jsx
import React from "react"

export default function Meme() {
    
    const [meme, setMeme] = React.useState({
        topText: "",
        bottomText: "",
        randomImage: "http://i.imgflip.com/1bij.jpg" 
    })
    const [allMemes, setAllMemes] = React.useState([])
    
    React.useEffect(() => {
        fetch("https://api.imgflip.com/get_memes")
            .then(res => res.json())
            .then(data => setAllMemes(data.data.memes))
    }, [])

// Other code not included
}
    
```
- Challenge: 
    - Try to figure out why our code is broken! 😞
```jsx
    function getMemeImage() {
        const randomNumber = Math.floor(Math.random() * allMemes.length) // Here
        const url = allMemes[randomNumber].url
        setMeme(prevMeme => ({
            ...prevMeme,
            randomImage: url
        }))
        
    }
```

### Vid 66
-  Challenge:
    - 1. Create state called `show`, default to `true`
    - 2. When the button is clicked, toggle `show`
    - 3. Only display `<WindowTracker>` if `show` is `true`
```jsx
import React from "react"
import WindowTracker from "./WindowTracker"

export default function App() {

    const [show, setShow] = React.useState(true)
    
    function toggle() {
        setShow(prevShow => !prevShow)
    }
    
    return (
        <div className="container">
            <button onClick={toggle}>
                Toggle WindowTracker
            </button>
            {show && <WindowTracker />}
        </div>
    )
}
```
- Challenge:
     1. Create state called `windowWidth`, default to `window.innerWidth`
     2. When the window width changes, update the state
     3. Display the window width in the h1 so it updates every time it changes
```jsx
import React from "react"

export default function WindowTracker() {

    const [windowWidth, setWindowWidth] = React.useState(window.innerWidth) // Here
    
    React.useEffect(() => {
        window.addEventListener("resize", function() {
            setWindowWidth(window.innerWidth) // Here
        })
    }, [])
    
    return (
        <h1>Window width: {windowWidth}</h1>
    )
}

```


# React for Beginners — Class Notes

---

# React

React is a javascript library used for building user interface (UI) , especially for web applications.
It is used to create fast , interactive , and reusable UI.

The components React introduced are :
  Virtual DOM
  Component-based Architecture
  Efficiency Rendering

---

---

## Advantages

---

  Component based architecture
  High Performance
  Reusable Code
  One-way data flow
  SEO Friendly - can support server side rendering
  Large Ecosystem
  Easy Testing - Components can be tested individually

---

# Single Page Application (SPA)

---

A SPA is a web application that loads only one HTML page and dynamically updates content without reloading the entire page.

Traditional Websites --> Every click loads a new page from the server
SPA --> Only content changes , not the full page

## "React only updates chnaged components using virtual DOM."



# Virtual DOM

---

---



## The virtual DOM is a lightweight copy of the Real DOM. React creates a virtual representation of the UI in memory.

when changes occur:

1. React creates a new virtual DOM
2. Compares it with previous virtual DOM
3. Find differences
4. Updates only changed parts in real DOM
This process is called Diffing / Reconcilation

---



# DOM

---

---



## DOM stands for Document Object Model. It is basically a tree like structure created by the browser when a webpage loads.

The browser takes your HTML code and converts it into objects that javascript can understand and change.

---



# Topic 1: React Project Structure

---



## What Is a React Project?

When you create a React project, it gives you a whole folder full of files and folders. You do not need to understand every single file right away. You only need to understand a few important ones to get started.

Think of it like moving into a new apartment. The apartment has many rooms. You don't use all of them at once. You start with the most important ones.

---



## The Folder Structure

```
my-react-app/
│
├── public/                  ← Folder visible to the browser directly
│   └── index.html           ← The ONE HTML file React uses
│
├── src/                     ← Folder where you write your React code
│   ├── App.tsx              ← Your main component (the heart of your app)
│   └── main.tsx             ← Where React starts running
│
├── package.json             ← List of all tools/libraries your project uses
└── ... (other config files — ignore for now)
```

---



## Each File and Folder Explained



### The `public/` Folder

This folder contains files that go directly to the browser without React touching them. The most important file here is `index.html`.

Think of `public/` as the display window of a shop. Whatever is kept there is visible directly to anyone passing by — no special processing needed.

---



### `public/index.html` — The Only HTML File

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>My React App</title>
  </head>
  <body>
    <div id="root"></div>
  </body>
</html>
```

This is a nearly empty HTML page. It has one critical line:

```html
<div id="root"></div>
```

This `<div>` is an empty box. React will find this box and put your entire application inside it.

Think of it like a construction site. The `index.html` is an empty plot of land with a plot number (`id="root"`). React is the construction crew that builds the entire building on that plot.

---



### The `src/` Folder

This is where you write your code. This is your workspace. Most of your time will be spent inside this folder.

---



### `src/main.tsx` — Where React Starts

```tsx
import React from 'react'
import ReactDOM from 'react-dom/client'
import App from './App'

ReactDOM.createRoot(document.getElementById('root')!).render(
  <App />
)
```

This file has one job: **start React and connect it to the HTML page.**


| Line                                      | What it does                                      |
| ----------------------------------------- | ------------------------------------------------- |
| `import React from 'react'`               | Loads the React library                           |
| `import ReactDOM from 'react-dom/client'` | Loads the part of React that talks to the browser |
| `import App from './App'`                 | Loads your App component (your UI)                |
| `document.getElementById('root')`         | Finds the `<div id="root">` in the HTML file      |
| `.render(<App />)`                        | Puts your App inside that div                     |


Think of `main.tsx` as the main electrical switch of a building. You flip it, and everything turns on. It connects the power (React) to the building (your HTML page).

---



### `src/App.tsx` — Your Main Component

```tsx
function App() {
  return (
    <div>
      <h1>Hello World!</h1>
    </div>
  )
}

export default App
```

This is where your actual UI starts. Think of this as the front door of your app. Everything the user sees begins here.

---



### `package.json` — The Ingredient List

```json
{
  "name": "my-react-app",
  "dependencies": {
    "react": "^18.0.0",
    "react-dom": "^18.0.0"
  }
}
```

This file is like a recipe card for your project. It lists the name of your project and all the libraries it needs to work. When someone downloads your project and runs `npm install`, this file tells npm exactly what to download.

---



## How React Connects to HTML — Flow Diagram

```
index.html
    │
    │  has a <div id="root">  (empty box)
    ▼
main.tsx
    │
    │  finds that div
    │  renders <App /> inside it
    ▼
App.tsx
    │
    │  contains your UI (components, text, buttons)
    ▼
Browser displays your React app
```

---



## Common Mistakes

- **Editing** `index.html` **frequently** — You almost never need to touch this file. React handles it.
- **Writing components outside** `src/` — Always write your components inside the `src/` folder.
- **Treating** `package.json` **as something to edit manually** — You don't edit it directly. Just understand what it represents.

---



## Common Questions

**Q: Why is there only one HTML file? Real websites have many pages.**

React creates what is called a Single Page Application (SPA). It looks like many pages, but it is actually one HTML file where React swaps out the content dynamically. We will learn this later.

**Q: What does** `.tsx` **mean? Why not** `.js`**?**

`.tsx` means it is a TypeScript file that can also contain JSX (the HTML-like syntax in React). For now, treat it like JavaScript with a few extra rules.

---



## Practice Task

Look at your project folder and answer:

1. Which file contains `<div id="root">`?
2. Which file connects React to that div?
3. Which file is the main component?

---

---



# Topic 2: JSX Basics

---



## What Is JSX?

**JSX = JavaScript + XML (HTML-like code)**

Normally, HTML and JavaScript are two separate languages. You write HTML in `.html` files and JavaScript in `.js` files.

JSX lets you write HTML-looking code directly inside your JavaScript or TypeScript. That is the whole idea.

---



## Why Does JSX Exist?

Before JSX, to create a button in React you had to write:

```javascript
// Without JSX — difficult to read
React.createElement('button', { className: 'btn' }, 'Click Me')
```

With JSX, you write:

```jsx
// With JSX — clean and readable
<button className="btn">Click Me</button>
```

JSX was created to make React code look like HTML so it is easier to read and write.

Behind the scenes, JSX gets converted back to that `createElement` code automatically. React handles that conversion — you never have to write it yourself.

---



## Analogy

JSX is like autocorrect for developers. When you type a shortcut on your phone, it expands to the full word. JSX is a shortcut — you write readable HTML-like code, and React converts it to complex JavaScript automatically.

---



## Code Example — JSX in a Component

```tsx
function Welcome() {
  return (
    <div> 
      <h1>Hello, Students!</h1>
      <p>Welcome to React class.</p>
    </div>
  )
}
```

---



## Line-by-Line Explanation

```tsx
function Welcome() {
```

- `function` — This is how you create a function (a block of reusable code) in JavaScript
- `Welcome` — The name of this component. Always starts with a capital letter (explained in Topic 4)
- `()` — The parentheses. Empty for now. This is where inputs (props) go later.
- `{` — Opens the function body. Everything inside `{ }` belongs to this function.

```tsx
  return (
```

- `return` — Every React component must return some UI. This is what the component will display.
- `(` — We open a bracket because the JSX spans multiple lines. This is just for readability.

```tsx
    <div>
      <h1>Hello, Students!</h1>
      <p>Welcome to React class.</p>
    </div>
```

- This looks exactly like HTML — and that is JSX.
- `<div>` — A container that holds other elements
- `<h1>` — A large heading
- `<p>` — A paragraph
- Everything is nested inside `<div>...</div>`

```tsx
  )
}
```

- `)` — Closes the bracket opened with `return (`
- `}` — Closes the function body

---



## Common Mistakes

- **Forgetting** `return` — If you don't return the JSX, nothing appears on screen.
- **Writing lowercase component names** — `<welcome />` will not work. It must be `<Welcome />`.
- **Not closing tags** — In HTML you can write `<br>` but in JSX you must write `<br />`.

---



## Common Questions

**Q: Is JSX a new language?**

No. JSX is a special syntax for React. It gets converted to regular JavaScript. You are still writing JavaScript — just with HTML-like shortcuts.

**Q: Can I write JavaScript inside JSX?**

Yes. We cover this in the next topic using curly braces `{ }`.

---



## Practice Task

Write a component called `MyCard` that returns:

- A `<div>` containing
- An `<h2>` with your name
- A `<p>` with your city

---

---



# Topic 3: JSX Rules

---



## JSX Has Rules

JSX looks like HTML but it is not exactly HTML. It has important rules you must follow. If you break these rules, React will give you an error.

Think of JSX rules like traffic rules. They exist so that React can work correctly.

---



## Rule 1: Always Return One Parent Element

**Wrong:**

```tsx
function App() {
  return (
    <h1>Hello</h1>
    <p>World</p>
  )
}
// Error: You cannot return two elements side by side.
```

**Correct:**

```tsx
function App() {
  return (
    <div>
      <h1>Hello</h1>
      <p>World</p>
    </div>
  )
}
```

**Why this rule exists:**

A function can only return one thing. If you try to return two elements without a container, JavaScript gets confused. By wrapping everything in a `<div>`, you are returning one thing that contains many things.

Think of it like carrying items. You can carry many things inside one bag. But you cannot carry two separate bags in one hand without dropping something. The `<div>` is your bag.

---



### Alternative: React Fragment

If you don't want an extra `<div>` in your HTML output, use a Fragment:

```tsx
function App() {
  return (
    <>
      <h1>Hello</h1>
      <p>World</p>
    </>
  )
}
```

The `<>...</>` is an invisible wrapper. It groups elements without adding an extra div to the page.

---



## Rule 2: Use `className` Instead of `class`

**Wrong:**

```tsx
<div class="container">Hello</div>
```

**Correct:**

```tsx
<div className="container">Hello</div>
```

**Why this rule exists:**

In JavaScript, `class` is a reserved keyword used for Object-Oriented Programming. To avoid a conflict, React uses `className` when referring to CSS classes.

---



## Rule 3: Use `{ }` Curly Braces for JavaScript Inside JSX

Inside JSX, you can jump into JavaScript by wrapping code in `{ }`. This is one of the most powerful features of JSX.

---



### Example 1 — Using a Variable

```tsx
function Greeting() {
  const name = "Arjun"

  return (
    <h1>Hello, {name}!</h1>
  )
}
```

**Output:** `Hello, Arjun!`

- `const name = "Arjun"` — Creates a variable called `name` with value `"Arjun"`
- `{name}` — Tells JSX: put whatever is stored in `name` right here
- Without `{ }`, it would literally show: `Hello, name!`

---



### Example 2 — Doing Math

```tsx
function MathExample() {
  return (
    <p>2 + 2 = {2 + 2}</p>
  )
}
```

**Output:** `2 + 2 = 4`

React calculates `2 + 2` and places the result on the page.

---



### Example 3 — Simple Condition (Ternary Operator)

```tsx
function AgeCheck() {
  const age = 20

  return (
    <p>{age >= 18 ? "Adult" : "Minor"}</p>
  )
}
```

**What is** `? :`**?**

This is called the ternary operator. It is a short way to write an if/else statement.

```
condition ? "value if true" : "value if false"
```

Since `age` is `20`, which is `>= 18`, this displays: `Adult`

---



## Common Mistakes

- **Using** `class` **instead of** `className` — Very common. React will warn you.
- **Forgetting** `{ }` **around variables** — Writing `Hello name` shows the text "name" literally.
- **Writing** `if/else` **directly inside JSX** — You cannot do this. Use the ternary `? :` operator instead.
- **Two parent elements with no wrapper** — Always wrap in one parent.

---



## Common Questions

**Q: Will the whole app crash if I break a rule?**

React gives you clear error messages in the browser. It will tell you exactly what is wrong. Read the error message — don't panic.

**Q: Can I put any JavaScript inside** `{ }`**?**

Almost anything that produces a value — variables, math, conditions, function calls. You cannot put `if` statements or `for` loops directly though.

---



## Practice Task

Create a component called `StudentInfo` that:

- Has a variable `studentName = "your name"`
- Has a variable `score = 85`
- Displays: `"Hello, [name]! Your score is [score] out of 100."`
- Uses `className="card"` on the div

---

---



# Topic 4: Components

---



## What Is a Component?

A component is a **reusable piece of UI** (User Interface).

Instead of writing the same code again and again for similar-looking things, you write it once as a component and reuse it wherever you need.

---



## Why Do Components Exist?

Imagine building a website with 50 student profile cards. Without components, you would copy and paste the same HTML 50 times. If you needed to change the design, you would have to change it 50 times.

With components, you write the card design once and reuse it 50 times. Change it once — it updates everywhere.

**Analogy:** Think of LEGO blocks. LEGO makes one standard block shape, and you use that same block thousands of times to build anything. Components are LEGO blocks for your UI.

---



## How Components Build a Page

```
App  (the main component)
  │
  ├── Header component
  │     └── Logo, NavBar
  │
  ├── MainContent component
  │     ├── StudentCard component   ← same component, different data
  │     ├── StudentCard component
  │     └── StudentCard component
  │
  └── Footer component
```

Every piece of the page is a component. Components can contain other components.

---



## Creating a Component — `Welcome.tsx`

**Step 1: Create a new file called** `Welcome.tsx` **inside** `src/`

```tsx
// src/Welcome.tsx

function Welcome() {
  return (
    <div>
      <h2>Welcome to React Class!</h2>
      <p>We are learning components today.</p>
    </div>
  )
}

export default Welcome
```

---



## Line-by-Line: `Welcome.tsx`

```tsx
function Welcome() {
```

Creates a function called `Welcome`. In React, a component is just a function that returns JSX.

```tsx
  return (
    <div>
      <h2>Welcome to React Class!</h2>
      <p>We are learning components today.</p>
    </div>
  )
```

Returns the JSX — what the component will show on screen. The `<div>` wraps everything (Rule 1).

```tsx
export default Welcome
```

- `export` — Makes this component available to other files
- `default` — This is the main thing this file exports
- `Welcome` — The name of what we are exporting

Think of `export default` as putting your product on a store shelf. Other files (like customers) can come and `import` it.

---



## Using the Component in `App.tsx`

```tsx
// src/App.tsx

import Welcome from './Welcome'

function App() {
  return (
    <div>
      <h1>My React App</h1>
      <Welcome />
      <Welcome />
      <Welcome />
    </div>
  )
}

export default App
```

---



## Line-by-Line: `App.tsx`

```tsx
import Welcome from './Welcome'
```

- `import` — Brings the component from another file into this one
- `Welcome` — The name we want to use here (should match what was exported)
- `from './Welcome'` — The path to the file (`./`  means "same folder")

```tsx
<Welcome />
```

- You use a component just like an HTML tag
- The capital letter tells React: this is a Component, not a regular HTML element
- `/>` — Self-closing tag (since Welcome doesn't wrap any children here)

---



## Why Must Component Names Start With Capital Letters?

React uses the capital letter to decide:

- `<div>` — lowercase — built-in HTML element
- `<Welcome>` — uppercase — your React component

If you name your component `welcome` (lowercase) and write `<welcome />`, React treats it as an unknown HTML tag and ignores it.

---



## Common Mistakes

- **Forgetting** `export default` — The component exists but cannot be used in other files.
- **Forgetting to** `import` **before using** — `<Welcome />` will throw an error if not imported.
- **Lowercase component names** — `<welcome />` will not work.
- **Wrong file path in import** — Double-check the path and spelling.

---



## Common Questions

**Q: Can a component use another component?**

Yes. This is exactly how React apps are built — components inside components, like building blocks stacked together.

**Q: How many components can I create?**

As many as you need. Large applications have hundreds of components.

---



## Practice Task

1. Create a file `Footer.tsx`
2. Write a component that shows: "Made with love by [your name]"
3. Export it and import it into `App.tsx`
4. Use it twice — what happens?

---

---



# Topic 5: Props

---



## What Are Props?

**Props = Properties = Data passed from a parent component to a child component.**

Right now, our `Welcome` component always shows the same text. What if we want it to show different names for different students? That is what props are for.

Props let you customize a component by passing it different data each time you use it.

---



## Why Do Props Exist?

Without props, reusable components would always look identical. With props, you can use the same component with different data.

**Analogy:** Think of a name badge template. The template (component) is the same design. But each person's name (prop) is different.

---



## Code Example — Passing Props



### `Welcome.tsx` — The Child (receives props)

```tsx
function Welcome(props) {
  return (
    <div>
      <h2>Hello, {props.name}!</h2>
      <p>You are studying: {props.course}</p>
    </div>
  )
}

export default Welcome
```



### `App.tsx` — The Parent (sends props)

```tsx
import Welcome from './Welcome'

function App() {
  return (
    <div>
      <Welcome name="Arjun" course="Computer Science" />
      <Welcome name="Priya" course="Mathematics" />
      <Welcome name="Rahul" course="Physics" />
    </div>
  )
}

export default App
```

---



## Line-by-Line Explanation



### In `App.tsx`:

```tsx
<Welcome name="Arjun" course="Computer Science" />
```

- `name="Arjun"` — Passing a prop called `name` with value `"Arjun"`
- `course="Computer Science"` — Passing a prop called `course`
- Think of it like calling a function with arguments: `Welcome({ name: "Arjun", course: "Computer Science" })`



### In `Welcome.tsx`:

```tsx
function Welcome(props) {
```

- `props` — A special parameter that receives all data sent from the parent
- `props` is an object. If we passed `name="Arjun"`, then `props.name` equals `"Arjun"`

```tsx
<h2>Hello, {props.name}!</h2>
```

- `{props.name}` — Gets the value of `name` from the props object
- First card: `Hello, Arjun!`
- Second card: `Hello, Priya!`

---



## What Gets Rendered?

```
┌──────────────────────────────────┐
│  Hello, Arjun!                   │
│  You are studying: Computer Sci  │
└──────────────────────────────────┘

┌──────────────────────────────────┐
│  Hello, Priya!                   │
│  You are studying: Mathematics   │
└──────────────────────────────────┘

┌──────────────────────────────────┐
│  Hello, Rahul!                   │
│  You are studying: Physics       │
└──────────────────────────────────┘
```

Same component → Different data → Different output.

---



## Cleaner Way: Destructuring Props

Instead of writing `props.name` every time, you can destructure:

```tsx
// Instead of this:
function Welcome(props) {
  return <h2>Hello, {props.name}!</h2>
}

// Write this:
function Welcome({ name, course }) {
  return (
    <div>
      <h2>Hello, {name}!</h2>
      <p>You are studying: {course}</p>
    </div>
  )
}
```

`{ name, course }` — Instead of receiving a whole bag (props) and then opening it, you directly take out only what you need.

---



## Common Mistakes

- **Spelling prop names differently** — Sending `name="Arjun"` but accessing `props.Name` (capital N) will not work.
- **Forgetting** `{ }` **in JSX** — Writing `props.name` without curly braces shows literal text.
- **Trying to change props** — Props are read-only. A child component cannot change its own props.
- **Sending numbers without** `{ }` — `age="20"` sends a string. `age={20}` sends a number. Use `{ }` for non-string values.

---



## Common Questions

**Q: What if I don't pass a required prop?**

The prop will be `undefined`. You can set default values for props (covered later).

**Q: Can I pass numbers or booleans as props?**

Yes. Use curly braces: `score={95}` or `isActive={true}`.

**Q: Can a child send data back to the parent?**

Not directly through props. That requires functions passed as props, which is a more advanced topic.

---



## Data Flow — Always One Direction

```
App (Parent)
    │
    │  sends props (data flows DOWN only)
    ▼
Welcome (Child)
```

Data in React always flows from parent to child. Never the other way through props.

---



## Practice Task

Create a component `StudentCard` that receives:

- `name` prop
- `rollNumber` prop
- `grade` prop

Use it in `App.tsx` for 3 different students.

---

---



# Topic 6: Basic Styling

---



## How to Style React Components

There are 3 main ways to add styles in React:

1. Importing a CSS file (most common)
2. Inline styles (styles written directly in JSX)
3. CSS Modules (advanced — not covered today)

---



## Method 1: Importing a CSS File

**Step 1: Create a CSS file**

```css
/* src/App.css */

.card {
  background-color: #f0f0f0;
  padding: 20px;
  border-radius: 8px;
  margin: 10px;
}

.heading {
  color: #333333;
  font-size: 24px;
}
```

**Step 2: Import the CSS file in your component**

```tsx
// src/App.tsx
import './App.css'

function App() {
  return (
    <div className="card">
      <h1 className="heading">Hello!</h1>
    </div>
  )
}
```

---



## Line-by-Line

```tsx
import './App.css'
```

Tells React to load the styles from this file. The `./` means "in the same folder". After importing, all classes in that CSS file are available to use.

```tsx
<div className="card">
```

- `className` — Not `class` in React
- `"card"` — Matches the `.card` rule in the CSS file
- React applies those styles to this `<div>`

---



## Method 2: Inline Styles

```tsx
function Box() {
  return (
    <div style={{ backgroundColor: 'blue', color: 'white', padding: '20px' }}>
      I am a blue box
    </div>
  )
}
```

---



## Why Two Curly Braces `{{ }}`?

This is a very common point of confusion. Let's break it down:

```tsx
style={{ backgroundColor: 'blue' }}
```

- The **outer** `{ }` — tells JSX "I am writing JavaScript here"
- The **inner** `{ }` — is a JavaScript object (key-value pairs)

So it reads as: `style={ /* a JavaScript object */ }`

You can also write it more clearly like this:

```tsx
function Box() {
  const myStyle = {
    backgroundColor: 'blue',
    color: 'white',
    padding: '20px'
  }

  return (
    <div style={myStyle}>
      I am a blue box
    </div>
  )
}
```

This is identical — just split into two steps.

---



## CSS vs Inline Style Property Names


| CSS Property       | Inline Style in React |
| ------------------ | --------------------- |
| `background-color` | `backgroundColor`     |
| `font-size`        | `fontSize`            |
| `border-radius`    | `borderRadius`        |
| `margin-top`       | `marginTop`           |


In React inline styles, property names use **camelCase** (no hyphens). This is because hyphens have meaning in JavaScript (subtraction). React uses camelCase to avoid confusion.

---



## Common Mistakes

- `**class` instead of `className`** — Will not work.
- **Missing the double curly braces** — `style={ color: 'red' }` is wrong. Must be `style={{ color: 'red' }}`.
- **Using hyphens in inline style** — `font-size` should be `fontSize`.
- **Missing quotes around string values** — `color: red` is wrong. Must be `color: 'red'`.

---



## Common Questions

**Q: Which method is better — CSS file or inline styles?**

CSS files are better for larger projects. Inline styles are quick for small, specific overrides. Most real projects use CSS files.

---



## Practice Task

Style your `StudentCard` component:

- Give it a background color
- Add padding and border-radius
- Make the name bold using CSS
- Try once with a CSS file and once with inline style

---

---



# Topic 7: Event Handling

---



## What Are Events?

An event is something that happens because of a user action.

Examples:

- User clicks a button — `onClick` event
- User types in a field — `onChange` event
- User hovers over something — `onMouseOver` event

React lets you listen for these events and respond to them with a function.

---



## Why Do We Need Events?

Without events, your website is static — like a picture. Events make it interactive.

**Analogy:** Think of a light switch. The switch is there, but it only does something when you click it. The click is the event. The lights turning on is the response.

---



## Basic Click Event

```tsx
function MyButton() {
  return (
    <button onClick={() => alert("Hello!")}>
      Click Me
    </button>
  )
}
```

---



## Line-by-Line

```tsx
<button onClick={() => alert("Hello!")}>
```

- `onClick` — An event handler: "when this is clicked, do something"
- `{` — Opening curly brace (writing JavaScript in JSX)
- `() => alert("Hello!")` — An arrow function
- `alert("Hello!")` — A browser function that shows a popup
- `}` — Closing curly brace

---



## What Is an Arrow Function?

An arrow function is a short way to write a function.

**Standard function:**

```javascript
function sayHello() {
  alert("Hello!")
}
```

**Arrow function (shorter):**

```javascript
() => alert("Hello!")
```

Both do the same thing. Arrow functions are commonly used in React event handlers.

Breaking down `() => alert("Hello!")`:

- `()` — No input parameters
- `=>` — "Then do this"
- `alert("Hello!")` — The action to perform

---



## Better Practice: Separate Named Function

```tsx
function MyButton() {

  function handleClick() {
    alert("Button was clicked!")
    console.log("User clicked!")
  }

  return (
    <button onClick={handleClick}>
      Click Me
    </button>
  )
}
```

---



## IMPORTANT: Function Reference vs Function Call

This is one of the most common beginner mistakes.

```tsx
// Correct — pass the function reference
<button onClick={handleClick}>Click Me</button>

// Wrong — this calls the function immediately, not on click
<button onClick={handleClick()}>Click Me</button>
```

**The difference:**

- `handleClick` — "Here is the function. Run it when the button is clicked."
- `handleClick()` — "Run this function right now immediately."

**Analogy:**

- `handleClick` — Giving someone your number to call you later
- `handleClick()` — Calling them immediately right now

---



## Event with Input Field

```tsx
function MyInput() {
  function handleChange(event) {
    console.log(event.target.value)
  }

  return (
    <input type="text" onChange={handleChange} />
  )
}
```

`event` is a special object React passes automatically when an event happens. `event.target.value` gives the current value of the input field.

---



## Common Mistakes

- `**onClick={handleClick()}**` — The `()` calls it immediately. Remove the parentheses.
- **Forgetting** `{ }` **around the function** — `onClick=handleClick` will not work.
- **Not naming handler functions consistently** — Convention is `handleClick`, `handleSubmit`, `handleChange`.

---



## Common Questions

**Q: What events can React handle?**

Many: `onClick`, `onChange`, `onSubmit`, `onKeyDown`, `onMouseOver` and more. All HTML events work in React using camelCase naming.

**Q: What is** `console.log`**?**

It prints a message in the browser's developer console. Press F12 and go to the Console tab to see it. Very useful for checking values while coding.

---



## Practice Task

Create a button component that:

- On click, shows an alert saying "You clicked the button!"
- Also logs "Button clicked!" to the console
- Uses a separate named function instead of an inline arrow function

---

---



# Topic 8: useState Hook

---



## What Is State?

State is data inside your component that can **change over time** — and when it changes, React **automatically updates the UI**.

The classic example: a counter.

- Starts at 0
- Click a button — becomes 1
- Click again — becomes 2

That number (0, 1, 2...) is state.

---



## Why Can't We Just Use Normal Variables?

Let's see what happens with a normal variable:

```tsx
function Counter() {
  let count = 0

  function handleClick() {
    count = count + 1
    console.log(count)   // count IS updating in memory...
  }

  return (
    <div>
      <p>Count: {count}</p>   // ...but the UI NEVER updates!
      <button onClick={handleClick}>+1</button>
    </div>
  )
}
```

**The problem:** Even though `count` changes in memory, React does not know it changed. React does not re-render the component. The UI stays stuck at 0.

**Analogy:** Imagine a scoreboard at a cricket match. The scorer changes the number in their notebook, but forgets to update the scoreboard. The audience (the UI) still sees the old score.

---



## The Solution: useState

`useState` is a Hook — a special React function that:

1. Stores a value (state)
2. Gives you a way to update it
3. Automatically tells React to re-render the component when the value changes

---



## Counter App Using useState

```tsx
import { useState } from 'react'

function Counter() {

  const [count, setCount] = useState(0)

  function handleClick() {
    setCount(count + 1)
  }


  return (
    <div>
      <h2>Count: {count}</h2>
      <button onClick={handleClick}>Click to Add</button>
    </div>
  )
}

export default Counter
```

---



## The Most Important Line — Explained Slowly

```tsx
const [count, setCount] = useState(0)
```

Let's break this down piece by piece.

### `useState(0)`

- `useState` — A React function (Hook) that creates state
- `(0)` — The initial value — count starts at `0`
- `useState` returns two things: the current value AND a function to update it



### `const [count, setCount] = ...`

This is array destructuring — a way to unpack two values at once.

`useState` gives back an array with two items:

```
[ currentValue,  functionToUpdateValue ]
```

We name them:

- `count` — The current value of the state (starts at 0)
- `setCount` — The function we call to update the state

**Think of it like this:**

```
count    = the scoreboard number (everyone can see it)
setCount = the remote control to change the number
```



### The Naming Convention

- The value is named the thing it represents: `count`, `name`, `isOpen`
- The updater function is named `set` + the value name: `setCount`, `setName`, `setIsOpen`

---



## What Happens When You Click — Step by Step

```
User clicks button
    │
    ▼
handleClick() runs
    │
    ▼
setCount(count + 1) is called
    │
    ▼
React sees that state has changed
    │
    ▼
React re-renders the Counter component
(runs the function again from top to bottom)
    │
    ▼
count now has the new value (1, 2, 3...)
    │
    ▼
UI updates to show the new count
```

This is called **re-rendering**. Every time state changes, React reruns the component function and updates only what changed on screen. This is React working efficiently in the background.

---



## Another Example — Toggle On/Off

```tsx
import { useState } from 'react'

function LightSwitch() {
  const [isOn, setIsOn] = useState(false)

  function handleToggle() {
    setIsOn(!isOn)
  }

  return (
    <div>
      <p>Light is: {isOn ? "ON" : "OFF"}</p>
      <button onClick={handleToggle}>Toggle Light</button>
    </div>
  )
}
```

- `false` — light is off initially
- `!isOn` — flips the value (false becomes true, true becomes false)
- Every click toggles: false → true → false → true...

---



## Common Mistakes

- **Using a normal variable instead of useState** — The UI will not update.
- **Updating state wrong** — `count = count + 1` will not work. Must use `setCount(count + 1)`.
- **Forgetting to import useState** — `import { useState } from 'react'` is required at the top.

---



## Common Questions

**Q: What is a Hook?**

A Hook is a special React function that lets you use React features inside a component. `useState` is the Hook for managing state. There are other Hooks too, but we cover those later.

**Q: Can I have more than one state in a component?**

Yes. Call `useState` as many times as you need:

```tsx
const [count, setCount] = useState(0)
const [name, setName]   = useState("Arjun")
const [isOpen, setIsOpen] = useState(false)
```

**Q: Why** `const` **if count can change?**

The `const` refers to the array binding itself not changing. But the state value changes — React gives you a new `count` value on every re-render.

---



## Practice Task

Build a Like Button:

- Start with `likes = 0`
- A button that says "Like"
- Every click adds 1 to likes
- Display: "5 Likes"
- Bonus: Can you make it toggle (like and unlike)?

---

---



# Topic 9: Practice Activity — Student Card

---



## The Task

Build a Student Card component that shows a student's details and has a button that says "View Profile".

**Target output:**

```
┌──────────────────────────────────┐
│  Arjun Sharma                    │
│  Course: Computer Science        │
│  College: IIT Delhi              │
│                                  │
│  [ View Profile ]                │
└──────────────────────────────────┘
```

Display 3 cards in `App.tsx` with different student data.

---



## How to Think Before Writing Code

Before writing any code, ask yourself:

**"What is this UI made of?"**

Break it down:

1. There is a card — a styled box
2. Inside: a name, course, college
3. A button

**"What data changes between cards?"**

The name, course, and college. Those should be props.

**"Does anything update when clicked?"**

The button could show an alert. If we wanted to track clicks, we would need state.

**React thinking = break UI into components + identify what is data (props vs state)**

---



## Step 1: Create `StudentCard.tsx`

```tsx
// src/StudentCard.tsx

import './StudentCard.css'

function StudentCard({ name, course, college }) {

  function handleViewProfile() {
    alert("Viewing profile of: " + name)
  }

  return (
    <div className="card">
      <h2 className="student-name">{name}</h2>
      <p>Course: {course}</p>
      <p>College: {college}</p>
      <button className="view-btn" onClick={handleViewProfile}>
        View Profile
      </button>
    </div>
  )
}

export default StudentCard
```

---



## Step 2: Create `StudentCard.css`

```css
/* src/StudentCard.css */

.card {
  background-color: #ffffff;
  border: 1px solid #e0e0e0;
  border-radius: 12px;
  padding: 24px;
  margin: 16px;
  width: 280px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
}

.student-name {
  color: #2c3e50;
  margin-bottom: 8px;
}

.view-btn {
  background-color: #3498db;
  color: white;
  border: none;
  padding: 10px 20px;
  border-radius: 6px;
  cursor: pointer;
  margin-top: 12px;
  font-size: 14px;
}

.view-btn:hover {
  background-color: #2980b9;
}
```

---



## Step 3: Use It in `App.tsx`

```tsx
// src/App.tsx

import StudentCard from './StudentCard'

function App() {
  return (
    <div style={{ display: 'flex', flexWrap: 'wrap', padding: '20px' }}>
      <h1 style={{ width: '100%', textAlign: 'center' }}>
        Student Directory
      </h1>

      <StudentCard
        name="Arjun Sharma"
        course="Computer Science"
        college="IIT Delhi"
      />

      <StudentCard
        name="Priya Patel"
        course="Data Science"
        college="NIT Surat"
      />

      <StudentCard
        name="Rahul Menon"
        course="Cybersecurity"
        college="BITS Pilani"
      />
    </div>
  )
}

export default App
```

---



## Concepts Used in This Activity


| Concept        | Where it appears                                     |
| -------------- | ---------------------------------------------------- |
| Component      | `StudentCard` is a reusable component                |
| Props          | `name`, `course`, `college` passed from App          |
| CSS file       | `StudentCard.css` imported and used with `className` |
| Event handling | `onClick={handleViewProfile}` on the button          |
| JSX Rules      | `className`, single parent, `{ }` for variables      |


---



## Bonus Challenge

Add a `useState` to count how many times "View Profile" was clicked on each card. Display: "Viewed 3 times".

---

---



# Topic 10: Mini Project — Counter App

---



## Project Overview

Build a counter with:

- Increment (+1) button
- Decrement (-1) button
- Reset button
- The count displayed in the center

---



## Complete Code

```tsx
// src/Counter.tsx

import { useState } from 'react'

function Counter() {
  const [count, setCount] = useState(0)

  function handleIncrement() {
    setCount(count + 1)
  }

  function handleDecrement() {
    setCount(count - 1)
  }

  function handleReset() {
    setCount(0)
  }

  return (
    <div style={{
      textAlign: 'center',
      padding: '40px',
      fontFamily: 'Arial, sans-serif'
    }}>
      <h1>Counter App</h1>

      <div style={{
        fontSize: '80px',
        fontWeight: 'bold',
        color: count > 0 ? 'green' : count < 0 ? 'red' : 'black',
        margin: '20px'
      }}>
        {count}
      </div>

      <div>
        <button
          onClick={handleDecrement}
          style={{ fontSize: '24px', margin: '10px', padding: '10px 24px' }}
        >
          -
        </button>

        <button
          onClick={handleReset}
          style={{ fontSize: '18px', margin: '10px', padding: '10px 24px' }}
        >
          Reset
        </button>

        <button
          onClick={handleIncrement}
          style={{ fontSize: '24px', margin: '10px', padding: '10px 24px' }}
        >
          +
        </button>
      </div>

      <p style={{ color: 'gray', marginTop: '20px' }}>
        {count === 0 ? "Start clicking!" : `You are at ${count}`}
      </p>
    </div>
  )
}

export default Counter
```

---



## Key Learning Points in This Project

**Three separate handler functions:**
`handleIncrement`, `handleDecrement`, `handleReset` — each with a single clear responsibility.

**Dynamic color based on state:**

```
count > 0  → green  (positive)
count < 0  → red    (negative)
count = 0  → black  (zero)
```

This shows that the UI reacts to the data automatically.

**Template literal:**
`You are at ${count}` — another way to place variables inside strings using backticks and `${ }`.

**All core concepts working together:**
State, Events, Rendering, Styling — combined into one real component.

---

---



# Summary — Concepts Covered


| Topic             | Key Idea                                      |
| ----------------- | --------------------------------------------- |
| Project Structure | `index.html` → `main.tsx` → `App.tsx`         |
| JSX               | HTML-like syntax inside JavaScript            |
| JSX Rules         | One parent, `className`, `{ }` for JavaScript |
| Components        | Reusable functions that return JSX            |
| Props             | Pass data from parent to child                |
| Styling           | CSS files + `className` + inline styles       |
| Events            | `onClick`, arrow functions, handler functions |
| useState          | State that automatically updates the UI       |
| Student Card      | Practice combining all concepts               |
| Counter App       | Mini project with increment, decrement, reset |


---



## The Big Picture

```
Components are reusable pieces of UI
          ↓
Props make each component customizable
          ↓
State makes components interactive
          ↓
Events trigger state changes
          ↓
React automatically updates the UI
```



## React's Core Idea

> Your UI is a function of your state.
>
> When state changes — React re-renders — UI updates.
> You do not manually update the page. React does it for you.


# HTML and CSS — Starter Notes
### For Students Beginning Their Web Development Journey Before React

---

# What You Are Learning and Why

Before writing a single line of React, you need to understand what React is actually building on top of. React generates HTML and applies CSS — the same HTML and CSS every website on the internet uses. Understanding these first makes React make complete sense instead of feeling like magic.

```
HTML  →  the structure  (what is on the page)
CSS   →  the appearance (how it looks)
React →  the behaviour  (how it responds to the user)
```

By the end of this module you will be able to build a complete static webpage from scratch, which is exactly the kind of output React produces dynamically.

---
---

# Part 1 — HTML

---

# Topic 1: What Is HTML?

---

## Concept

**HTML** stands for HyperText Markup Language. It is the language used to create the structure and content of every webpage.

HTML uses **tags** — special words wrapped in angle brackets — to describe what each piece of content is. A tag tells the browser: "this is a heading", "this is a paragraph", "this is an image", "this is a button."

The browser reads those tags and displays the content accordingly.

---

## Why HTML Exists

Without HTML, a browser would have no idea how to display text. Should it be large or small? Is it a heading or a paragraph? Is it a link or plain text? HTML provides those labels.

**Analogy:** Think of HTML like the steel frame of a building. It defines where the walls, floors, and rooms are. It has no paint, no furniture, no decoration — just the essential structure that everything else is built on.

---

## The Basic Structure of Every HTML File

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>My First Page</title>
  </head>
  <body>
    <h1>Hello, World!</h1>
    <p>This is my first webpage.</p>
  </body>
</html>
```

---

## Line-by-Line Explanation

```html
<!DOCTYPE html>
```
Tells the browser this is a modern HTML5 document. Always the very first line.

```html
<html lang="en">
```
The root element — every other element lives inside this. `lang="en"` tells the browser the content is in English, which helps screen readers and search engines.

```html
<head>
```
Contains information **about** the page — not visible content. Things like the title, CSS links, and metadata.

```html
<meta charset="UTF-8" />
```
Sets the character encoding. This ensures special characters (accents, symbols) display correctly.

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
```
Makes the page display correctly on mobile devices. Without this, mobile browsers zoom out and show a tiny desktop-sized page.

```html
<title>My First Page</title>
```
The text that appears in the browser tab. Not shown on the page itself.

```html
<body>
```
Everything inside `<body>` is visible on the page — headings, paragraphs, images, buttons, everything the user sees.

```html
<h1>Hello, World!</h1>
```
A level-1 heading. The largest heading. Every page should have exactly one `<h1>`.

```html
<p>This is my first webpage.</p>
```
A paragraph of text.

---

## Opening and Closing Tags

Most HTML elements have an opening tag and a closing tag:

```html
<p>This is a paragraph.</p>
 ↑                      ↑
opening tag         closing tag (has a /)
```

Some elements are **self-closing** — they have no content and no closing tag:

```html
<img src="photo.jpg" alt="A photo" />
<br />
<input type="text" />
<meta charset="UTF-8" />
```

---

## HTML Attributes

Attributes provide extra information about an element. They go inside the opening tag:

```html
<a href="https://google.com">Visit Google</a>
   ↑
   attribute: name="value"
```

Common attributes:

| Attribute | Used On | Purpose |
|-----------|---------|---------|
| `href` | `<a>` | The URL the link goes to |
| `src` | `<img>`, `<video>` | The file to display |
| `alt` | `<img>` | Text if image cannot load |
| `class` | Any element | For CSS styling |
| `id` | Any element | A unique identifier |
| `type` | `<input>`, `<button>` | What kind of input or button |
| `placeholder` | `<input>` | Grey hint text inside the field |

---
---

# Topic 2: HTML Elements You Must Know

---

## Headings — h1 to h6

```html
<h1>Largest Heading — Page Title</h1>
<h2>Section Heading</h2>
<h3>Sub-Section Heading</h3>
<h4>Smaller Still</h4>
<h5>Very Small</h5>
<h6>Smallest Heading</h6>
```

Use headings in order. `h1` is the main title. `h2` is for major sections. `h3` for sub-sections. Do not skip levels (no `h1` then `h3` directly).

---

## Text and Paragraphs

```html
<p>This is a paragraph. Browser adds space above and below automatically.</p>

<strong>This text is bold.</strong>
<em>This text is italic.</em>

<br />    <!-- line break — forces text to the next line -->
<hr />    <!-- horizontal rule — a dividing line across the page -->
```

---

## Links

```html
<!-- External link — opens another website -->
<a href="https://google.com">Go to Google</a>

<!-- Opens in a new tab -->
<a href="https://google.com" target="_blank">Open in New Tab</a>

<!-- Link to another page in your project -->
<a href="about.html">About Us</a>

<!-- Link that scrolls to a section on the same page -->
<a href="#contact">Jump to Contact</a>
```

---

## Images

```html
<img src="student.jpg" alt="A student studying" />

<!-- From the internet -->
<img src="https://example.com/photo.jpg" alt="Description of the image" />
```

- `src` — where the image file is (path or URL)
- `alt` — alternative text shown if the image fails to load; also read by screen readers. Always include it.

---

## Lists

```html
<!-- Unordered list — bullet points -->
<ul>
  <li>React</li>
  <li>Node.js</li>
  <li>PostgreSQL</li>
</ul>

<!-- Ordered list — numbered -->
<ol>
  <li>Learn HTML</li>
  <li>Learn CSS</li>
  <li>Learn React</li>
</ol>
```

---

## Buttons

```html
<button>Click Me</button>
<button type="submit">Submit Form</button>
<button type="button" onclick="alert('Hello!')">Say Hello</button>
```

---

## Inputs and Forms

```html
<form>
  <label for="name">Your Name:</label>
  <input type="text" id="name" placeholder="Enter your name" />

  <label for="email">Email:</label>
  <input type="email" id="email" placeholder="you@example.com" />

  <label for="password">Password:</label>
  <input type="password" id="password" />

  <label for="age">Age:</label>
  <input type="number" id="age" min="1" max="120" />

  <label for="course">Select Course:</label>
  <select id="course">
    <option value="cs">Computer Science</option>
    <option value="ds">Data Science</option>
    <option value="cyber">Cybersecurity</option>
  </select>

  <button type="submit">Submit</button>
</form>
```

The `for` attribute on `<label>` must match the `id` on the input — this connects them so clicking the label focuses the input.

---

## Containers — div and span

```html
<!-- div — block container. Takes up the full width. Used to group things. -->
<div>
  <h2>Section Title</h2>
  <p>Section content.</p>
</div>

<!-- span — inline container. Only as wide as its content. Used inside text. -->
<p>My favourite colour is <span style="color: red;">red</span>.</p>
```

`div` and `span` have no meaning on their own — they are blank containers used for grouping and styling.

---

## Semantic HTML — Meaningful Tags

HTML5 introduced tags that describe the role of their content:

```html
<header>       <!-- top of the page — logo, nav -->
<nav>          <!-- navigation links -->
<main>         <!-- the main content of the page -->
<section>      <!-- a distinct section of content -->
<article>      <!-- an independent piece of content, like a blog post -->
<aside>        <!-- sidebar content -->
<footer>       <!-- bottom of the page -->
```

```html
<!-- Example structure using semantic HTML -->
<body>
  <header>
    <h1>MyApp</h1>
    <nav>
      <a href="/">Home</a>
      <a href="/about">About</a>
    </nav>
  </header>

  <main>
    <section>
      <h2>Featured Students</h2>
      <article>
        <h3>Arjun Sharma</h3>
        <p>Computer Science student.</p>
      </article>
    </section>
  </main>

  <footer>
    <p>Made with care.</p>
  </footer>
</body>
```

Use semantic tags instead of `<div>` for every section. It makes the HTML easier to read and helps search engines understand the page structure.

---

## Common Mistakes

- **Not closing tags** — `<p>Forgot to close` causes the browser to guess where the paragraph ends, often incorrectly.
- **Wrong nesting** — `<p><div>text</div></p>` is invalid. Block elements like `div` cannot go inside inline elements like `p`.
- **Using `<br>` for spacing** — Use CSS margins and padding instead of multiple `<br>` tags.
- **Missing `alt` on images** — Always include it, even if it is an empty string `alt=""` for decorative images.
- **Multiple `<h1>` tags** — A page should have exactly one `<h1>`.

---

## Common Questions

**Q: Does the browser care about indentation and spacing?**

No. The browser ignores whitespace between tags. Indentation is for humans reading the code. Use consistent 2-space indentation.

**Q: What is the difference between `id` and `class`?**

`id` must be unique on the page — only one element can have a given id. `class` can be shared by many elements. Use `id` for unique elements (a login form, the main header). Use `class` for groups of elements that share styling (all cards, all buttons).

---

## Practice Task 1 — Build a Personal Profile Page

Create an HTML file called `profile.html` with:
- A `<header>` with your name as `<h1>` and a `<nav>` with three links
- A `<main>` section with:
  - A profile image using `<img>`
  - A short paragraph about yourself
  - An unordered list of your skills
  - An ordered list of your goals
- A `<footer>` with "Made by [your name]"
- No CSS yet — structure only

---
---

# Part 2 — CSS

---

# Topic 3: What Is CSS?

---

## Concept

**CSS** stands for Cascading Style Sheets. It controls how HTML elements look — colours, fonts, sizes, spacing, layouts, and animations.

HTML provides the structure. CSS provides the appearance.

---

## Why CSS Exists

Without CSS, every webpage would look like a plain text document — black text, blue links, white background, Times New Roman font. CSS is what makes the web visually rich.

**Analogy:** If HTML is the steel frame of a building, CSS is everything you see when the building is finished — the paint, the tiles, the lighting, the furniture. Same structure, completely different look depending on the CSS applied.

---

## How to Connect CSS to HTML

**Method 1: External stylesheet (always use this)**

```html
<!-- In the <head> of your HTML file -->
<link rel="stylesheet" href="styles.css" />
```

CSS lives in a separate `.css` file. Clean separation between structure and style.

**Method 2: Internal style block**

```html
<head>
  <style>
    h1 { color: blue; }
  </style>
</head>
```

Useful for quick testing. Not recommended for real projects.

**Method 3: Inline style**

```html
<p style="color: red; font-size: 18px;">Inline styled text</p>
```

Avoid this for general styling. Used for dynamic styles set by JavaScript or React.

---

## CSS Syntax

```css
selector {
  property: value;
  property: value;
}
```

- **Selector** — which HTML elements to target
- **Property** — what to change (colour, size, font, etc.)
- **Value** — what to set it to
- Each property-value pair ends with a semicolon `;`
- The whole block is wrapped in curly braces `{ }`

---

## Your First CSS File

```css
/* styles.css */

/* This is a CSS comment */

body {
  font-family: Arial, sans-serif;
  background-color: #f5f5f5;
  color: #333333;
  margin: 0;
  padding: 0;
}

h1 {
  color: #4361ee;
  font-size: 32px;
}

p {
  font-size: 16px;
  line-height: 1.6;
}
```

---
---

# Topic 4: CSS Selectors

---

## Concept

A selector targets which HTML elements a style rule applies to.

---

## The Main Selectors

```css
/* Element selector — targets all elements of this type */
p {
  color: #333;
}

/* Class selector — targets elements with this class */
.card {
  background: white;
  border-radius: 8px;
}

/* ID selector — targets the one element with this id */
#main-title {
  font-size: 36px;
}

/* Descendant selector — targets p inside .card */
.card p {
  font-size: 14px;
}

/* Multiple selectors — apply the same rule to several elements */
h1, h2, h3 {
  font-weight: bold;
}

/* Pseudo-class — targets element in a specific state */
button:hover {
  background-color: #2980b9;   /* when mouse hovers over button */
}

a:visited {
  color: purple;               /* after a link has been clicked */
}

input:focus {
  border-color: #4361ee;       /* when input is active/focused */
}
```

---

## Specificity — Which Style Wins?

When multiple rules target the same element, CSS uses specificity to decide which one applies.

```
ID selector       →  most specific  (wins over everything)
Class selector    →  medium
Element selector  →  least specific
```

```css
/* All target the same <p class="intro" id="first-p"> */

p            { color: black; }     /* specificity: low */
.intro       { color: blue;  }     /* specificity: medium — wins over p */
#first-p     { color: red;   }     /* specificity: high — wins over .intro */
```

Prefer class selectors for most styling. Use IDs sparingly.

---
---

# Topic 5: The Box Model

---

## Concept

Every HTML element is a rectangular box. The box has four layers:

```
┌─────────────────────────────────┐
│           MARGIN                │  ← space outside the border
│   ┌─────────────────────────┐   │
│   │         BORDER          │   │  ← the visible border line
│   │   ┌─────────────────┐   │   │
│   │   │     PADDING     │   │   │  ← space between border and content
│   │   │  ┌───────────┐  │   │   │
│   │   │  │  CONTENT  │  │   │   │  ← text, image, etc.
│   │   │  └───────────┘  │   │   │
│   │   └─────────────────┘   │   │
│   └─────────────────────────┘   │
└─────────────────────────────────┘
```

---

## Box Model Properties

```css
.box {
  width:   300px;
  height:  150px;

  padding:  20px;         /* space inside — all four sides */
  padding-top:    10px;   /* or target individual sides */
  padding-right:  20px;
  padding-bottom: 10px;
  padding-left:   20px;

  border:        2px solid #333;   /* thickness style colour */
  border-radius: 8px;              /* rounds the corners */

  margin:  16px;          /* space outside — all four sides */
  margin-top:    8px;     /* or individual sides */
  margin-bottom: 8px;
  margin-left:   auto;    /* auto centres a block element horizontally */
  margin-right:  auto;
}
```

---

## box-sizing: border-box

By default, `width` and `height` do not include padding and border. This causes confusion:

```css
/* Default behaviour — actual width = 300 + 20 + 20 + 2 + 2 = 344px */
.box {
  width:   300px;
  padding: 20px;
  border:  2px solid black;
}

/* Fix — makes width and height include padding and border */
* {
  box-sizing: border-box;
}

/* Now .box is exactly 300px wide */
```

Always add `* { box-sizing: border-box; }` at the top of your CSS. It makes sizing predictable.

---
---

# Topic 6: Common CSS Properties

---

## Typography

```css
.text-example {
  font-family:  'Segoe UI', Arial, sans-serif;  /* font stack */
  font-size:    18px;
  font-weight:  bold;    /* normal, bold, 100–900 */
  font-style:   italic;
  color:        #333333;
  text-align:   center;  /* left, center, right, justify */
  line-height:  1.6;     /* 1.6x the font size — good for readability */
  text-decoration: none;  /* removes underline from links */
  text-transform:  uppercase;
  letter-spacing:  1px;
}
```

---

## Colours

```css
.colour-examples {
  color:            #333333;     /* hex — 6 digits, # prefix */
  color:            #333;        /* short hex — 3 digits */
  color:            rgb(51, 51, 51);     /* red, green, blue — 0 to 255 */
  color:            rgba(51, 51, 51, 0.8); /* rgb + alpha (opacity) 0–1 */
  background-color: cornflowerblue;     /* named colours */
}
```

---

## Display

```css
/* Block — takes full width, starts on a new line */
div, p, h1, h2, section { display: block; }

/* Inline — only as wide as content, flows with text */
span, a, strong, em { display: inline; }

/* Inline-block — inline flow but can have width and height */
.badge { display: inline-block; width: 80px; }

/* None — hides the element completely (still in HTML, just invisible) */
.hidden { display: none; }
```

---

## Backgrounds

```css
.hero {
  background-color:  #1a1a2e;
  background-image:  url('hero.jpg');
  background-size:   cover;     /* fills the area, may crop */
  background-position: center;
  background-repeat: no-repeat;
}
```

---

## Sizing

```css
.element {
  width:     400px;      /* fixed width */
  width:     100%;       /* full width of its parent */
  max-width: 800px;      /* never wider than 800px */
  min-width: 200px;      /* never narrower than 200px */
  height:    200px;
  min-height: 100vh;     /* at least the full viewport height */
}
```

`vh` = viewport height. `100vh` is the full visible height of the browser window.
`vw` = viewport width. `100vw` is the full visible width.

---
---

# Topic 7: Flexbox — The Layout System

---

## Concept

**Flexbox** is a CSS layout model that makes it easy to arrange elements in a row or column, align them, and distribute space between them.

Before Flexbox, creating layouts in CSS required hacks and workarounds. Flexbox made layouts straightforward.

---

## Why Flexbox

Centering something on a page was notoriously difficult before Flexbox. Now it takes three lines:

```css
.container {
  display:         flex;
  justify-content: center;
  align-items:     center;
}
```

React UIs use Flexbox constantly. Almost every component layout you build will use it.

---

## How Flexbox Works

Apply `display: flex` to the **parent** (container). The children automatically become flex items and arrange themselves.

```
Parent (flex container)
  ├── Child 1 (flex item)
  ├── Child 2 (flex item)
  └── Child 3 (flex item)
```

---

## The Main Flexbox Properties

```css
.container {
  display:         flex;

  /* Direction of the main axis */
  flex-direction:  row;           /* default — left to right */
  flex-direction:  column;        /* top to bottom */
  flex-direction:  row-reverse;   /* right to left */

  /* Alignment along the main axis (horizontal in row) */
  justify-content: flex-start;    /* default — items at start */
  justify-content: flex-end;      /* items at end */
  justify-content: center;        /* items centred */
  justify-content: space-between; /* space between items, no space at edges */
  justify-content: space-around;  /* equal space around each item */
  justify-content: space-evenly;  /* exactly equal space everywhere */

  /* Alignment along the cross axis (vertical in row) */
  align-items:     stretch;       /* default — items stretch to fill */
  align-items:     flex-start;    /* items at the top */
  align-items:     flex-end;      /* items at the bottom */
  align-items:     center;        /* items centred vertically */

  /* Wrapping — allow items to move to the next line */
  flex-wrap:       nowrap;        /* default — everything on one line */
  flex-wrap:       wrap;          /* wraps to next line if needed */

  /* Spacing between items */
  gap:             20px;          /* space between all flex items */
  gap:             16px 24px;     /* row gap, column gap */
}
```

---

## Flex Item Properties

```css
.item {
  /* How much this item grows relative to others */
  flex-grow:   1;     /* take up remaining space */
  flex-grow:   0;     /* default — do not grow */

  /* Shorthand: grow shrink basis */
  flex:        1;           /* grow and shrink equally, basis 0 */
  flex:        0 0 200px;   /* fixed 200px, no grow, no shrink */
}
```

---

## Common Flexbox Patterns

```css
/* Centre anything vertically and horizontally */
.centre-content {
  display:         flex;
  justify-content: center;
  align-items:     center;
  min-height:      100vh;
}

/* Navbar — logo left, links right */
.navbar {
  display:         flex;
  justify-content: space-between;
  align-items:     center;
  padding:         16px 32px;
}

/* Card grid that wraps */
.card-grid {
  display:   flex;
  flex-wrap: wrap;
  gap:       20px;
}

.card {
  flex: 0 0 300px;    /* fixed 300px wide, no grow */
}

/* Sidebar + main layout */
.layout {
  display: flex;
}

.sidebar { flex: 0 0 250px; }
.main    { flex: 1; }        /* takes all remaining space */
```

---

## Common Mistakes

- **Applying flex properties to the wrong element** — `justify-content` goes on the parent container, not the children.
- **Confusing `justify-content` and `align-items` direction** — `justify-content` is along the main axis (horizontal in row). `align-items` is along the cross axis (vertical in row). When `flex-direction` is `column`, they swap.
- **Forgetting `flex-wrap: wrap`** — Without it, items shrink to fit on one line even if you set a fixed width.

---

## Practice Task 2 — Style the Profile Page

Take the profile page from Practice Task 1 and add a `styles.css` file:
- `* { box-sizing: border-box; margin: 0; padding: 0; }`
- A background colour on `body`
- Style the `<header>` with flexbox (logo left, nav links right)
- Centre the profile section
- Make the lists display as a flex row with gaps
- Style the `<footer>` with a dark background and centred white text
- Round the profile image using `border-radius: 50%`

---
---

# Topic 8: CSS Grid

---

## Concept

**CSS Grid** is a two-dimensional layout system. While Flexbox is excellent for one-dimensional layouts (a row or a column), Grid is designed for two-dimensional layouts (rows AND columns simultaneously).

---

## When to Use Grid vs Flexbox

| Flexbox | Grid |
|---------|------|
| One direction — a row or a column | Two directions — rows and columns |
| Content-driven (size based on content) | Layout-driven (you define the tracks) |
| Navigation bar, card row, button group | Page layout, image gallery, form layout |

In practice, you use both — Grid for the overall page structure, Flexbox for individual components within cells.

---

## Basic Grid

```css
.grid-container {
  display:               grid;
  grid-template-columns: 1fr 1fr 1fr;   /* three equal columns */
  gap:                   20px;
}
```

`1fr` = one fraction of the available space. Three columns of `1fr 1fr 1fr` means each gets one third.

---

## Grid Properties

```css
.container {
  display: grid;

  /* Define column sizes */
  grid-template-columns: 200px 1fr 1fr;       /* fixed first, two equal */
  grid-template-columns: repeat(3, 1fr);       /* same as 1fr 1fr 1fr */
  grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
  /* auto-fill: as many 250px+ columns as fit — responsive grid */

  /* Define row sizes */
  grid-template-rows: auto;     /* rows size to their content */
  grid-template-rows: 80px auto 60px;  /* header, content, footer */

  /* Space between cells */
  gap:        20px;             /* row and column gap */
  row-gap:    16px;
  column-gap: 24px;
}
```

---

## Responsive Card Grid

```css
.card-grid {
  display:               grid;
  grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
  gap:                   24px;
}
```

This one rule creates a grid that:
- Fits as many 280px-wide columns as possible
- Expands them to fill remaining space
- Wraps to the next row automatically
- Works on any screen size without media queries

---

## Spanning Cells

```css
/* A grid item that spans two columns */
.featured-card {
  grid-column: span 2;
}

/* A grid item that spans two rows */
.tall-item {
  grid-row: span 2;
}

/* An item that spans the full width */
.full-width {
  grid-column: 1 / -1;   /* from first to last column */
}
```

---
---

# Topic 9: Responsive Design and Media Queries

---

## Concept

**Responsive design** means a webpage that looks good on all screen sizes — phones, tablets, and desktops. Instead of building three separate sites, you write CSS that adapts.

---

## Media Queries

A media query applies CSS rules only when a condition is met — usually when the screen is a certain size.

```css
/* Default styles — for all screens (mobile first approach) */
.card-grid {
  display:               grid;
  grid-template-columns: 1fr;   /* one column on small screens */
  gap:                   16px;
}

/* When screen is at least 600px wide */
@media (min-width: 600px) {
  .card-grid {
    grid-template-columns: 1fr 1fr;   /* two columns on tablets */
  }
}

/* When screen is at least 900px wide */
@media (min-width: 900px) {
  .card-grid {
    grid-template-columns: repeat(3, 1fr);   /* three columns on desktops */
  }
}
```

---

## Common Breakpoints

| Name | Width | Target |
|------|-------|--------|
| Mobile | up to 480px | Small phones |
| Large mobile | 481px to 768px | Large phones |
| Tablet | 769px to 1024px | Tablets |
| Desktop | 1025px and above | Laptops and desktops |

---

## Mobile-First vs Desktop-First

**Mobile-first** (recommended) — Write styles for mobile by default. Use `min-width` media queries to add styles for larger screens.

**Desktop-first** — Write styles for desktop by default. Use `max-width` media queries to scale down for smaller screens.

Mobile-first is the industry standard because most users are on mobile, and it produces simpler, cleaner CSS.

---
---

# Topic 10: CSS Variables

---

## Concept

CSS variables (custom properties) let you store a value once and reuse it throughout your stylesheet. When you want to change a colour, font, or spacing value, you change it in one place and it updates everywhere.

---

## Defining and Using Variables

```css
/* Define variables on the :root element — available everywhere */
:root {
  --primary-color:    #4361ee;
  --secondary-color:  #3f37c9;
  --text-color:       #333333;
  --background-color: #f5f5f5;
  --border-radius:    8px;
  --font-size-base:   16px;
  --spacing-sm:       8px;
  --spacing-md:       16px;
  --spacing-lg:       24px;
}

/* Use variables with var() */
.button {
  background-color: var(--primary-color);
  border-radius:    var(--border-radius);
  padding:          var(--spacing-sm) var(--spacing-md);
  font-size:        var(--font-size-base);
}

.card {
  background-color: white;
  border:           1px solid var(--primary-color);
  border-radius:    var(--border-radius);
  padding:          var(--spacing-lg);
}
```

When you change `--primary-color` in one place, every button, card, and element using it updates automatically.

---

## Why This Matters for React

React uses CSS variables extensively in design systems. When you see code like `var(--primary)` in React projects, this is exactly what it means.

---
---

# Part 3 — Case Studies

---

# Case Study 1: Student Profile Card

---

## What We Are Building

A styled student profile card — the kind of UI component you will build many times in React.

```
┌─────────────────────────────────┐
│                                 │
│         [Avatar Circle]         │
│         Arjun Sharma            │
│      Computer Science, IIT      │
│                                 │
│   📧 arjun@example.com          │
│   📍 Mumbai, India              │
│                                 │
│  React  Node.js  PostgreSQL     │
│                                 │
│      [  View Profile  ]         │
│                                 │
└─────────────────────────────────┘
```

---

## HTML

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Student Profile Card</title>
  <link rel="stylesheet" href="card.css" />
</head>
<body>

  <div class="page-centre">
    <div class="card">

      <div class="card-header">
        <div class="avatar">AS</div>
        <h2 class="student-name">Arjun Sharma</h2>
        <p class="student-info">Computer Science &mdash; IIT Delhi</p>
      </div>

      <div class="card-body">
        <div class="detail-row">
          <span class="detail-label">Email:</span>
          <span class="detail-value">arjun@example.com</span>
        </div>
        <div class="detail-row">
          <span class="detail-label">Location:</span>
          <span class="detail-value">Mumbai, India</span>
        </div>
      </div>

      <div class="skills">
        <span class="skill-badge">React</span>
        <span class="skill-badge">Node.js</span>
        <span class="skill-badge">PostgreSQL</span>
      </div>

      <div class="card-footer">
        <button class="btn-primary">View Profile</button>
      </div>

    </div>
  </div>

</body>
</html>
```

---

## CSS

```css
/* card.css */

* {
  box-sizing: border-box;
  margin:     0;
  padding:    0;
}

:root {
  --primary:     #4361ee;
  --text-dark:   #1a1a2e;
  --text-muted:  #666666;
  --bg:          #f0f2f5;
  --radius:      12px;
}

body {
  font-family:     'Segoe UI', Arial, sans-serif;
  background-color: var(--bg);
}

/* Centre the card on the page */
.page-centre {
  display:          flex;
  justify-content:  center;
  align-items:      center;
  min-height:       100vh;
  padding:          20px;
}

/* The card */
.card {
  background:    white;
  border-radius: var(--radius);
  box-shadow:    0 4px 20px rgba(0, 0, 0, 0.1);
  width:         340px;
  overflow:      hidden;
}

/* Top section with blue background */
.card-header {
  background:  var(--primary);
  color:       white;
  text-align:  center;
  padding:     32px 24px 24px;
}

/* Circular avatar with initials */
.avatar {
  width:           72px;
  height:          72px;
  border-radius:   50%;
  background:      rgba(255, 255, 255, 0.25);
  font-size:       24px;
  font-weight:     bold;
  display:         flex;
  justify-content: center;
  align-items:     center;
  margin:          0 auto 16px;
}

.student-name {
  font-size:   22px;
  font-weight: 700;
  margin-bottom: 4px;
}

.student-info {
  font-size:  14px;
  opacity:    0.85;
}

/* Details section */
.card-body {
  padding: 20px 24px;
}

.detail-row {
  display:       flex;
  gap:           12px;
  margin-bottom: 10px;
  font-size:     14px;
}

.detail-label {
  color:       var(--text-muted);
  min-width:   70px;
  font-weight: 600;
}

.detail-value {
  color: var(--text-dark);
}

/* Skills */
.skills {
  display:     flex;
  flex-wrap:   wrap;
  gap:         8px;
  padding:     0 24px 20px;
}

.skill-badge {
  background:    #eef2ff;
  color:         var(--primary);
  border-radius: 20px;
  padding:       4px 14px;
  font-size:     13px;
  font-weight:   600;
}

/* Footer button */
.card-footer {
  padding:     16px 24px 24px;
  text-align:  center;
}

.btn-primary {
  background:    var(--primary);
  color:         white;
  border:        none;
  border-radius: 8px;
  padding:       12px 40px;
  font-size:     15px;
  font-weight:   600;
  cursor:        pointer;
  width:         100%;
  transition:    background 0.2s;
}

.btn-primary:hover {
  background: #3451d1;
}
```

---

## What This Teaches

| Concept | Where it appears |
|---------|-----------------|
| Semantic containers | `.card`, `.card-header`, `.card-body`, `.card-footer` |
| CSS variables | `--primary`, `--radius` used throughout |
| Flexbox centering | `.page-centre`, `.avatar`, `.skills` |
| Box model | `padding`, `margin`, `border-radius` |
| `border-radius: 50%` | Circular avatar |
| `:hover` pseudo-class | Button hover effect |
| `transition` | Smooth hover animation |
| `box-shadow` | Card depth |

---
---

# Case Study 2: Login Page

---

## What We Are Building

A centred login form — the same login UI you built in React, now built with pure HTML and CSS.

---

## HTML

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Login</title>
  <link rel="stylesheet" href="login.css" />
</head>
<body>

  <div class="page">
    <div class="login-card">

      <div class="login-header">
        <h1>Welcome Back</h1>
        <p>Sign in to your account</p>
      </div>

      <form class="login-form">
        <div class="form-group">
          <label for="email">Email Address</label>
          <input
            type="email"
            id="email"
            placeholder="you@example.com"
            class="form-input"
          />
        </div>

        <div class="form-group">
          <label for="password">Password</label>
          <input
            type="password"
            id="password"
            placeholder="Enter your password"
            class="form-input"
          />
        </div>

        <div class="form-options">
          <label class="checkbox-label">
            <input type="checkbox" /> Remember me
          </label>
          <a href="#" class="forgot-link">Forgot password?</a>
        </div>

        <button type="submit" class="btn-login">Sign In</button>
      </form>

      <p class="signup-text">
        Don't have an account? <a href="#">Sign up</a>
      </p>

    </div>
  </div>

</body>
</html>
```

---

## CSS

```css
/* login.css */

* {
  box-sizing: border-box;
  margin:     0;
  padding:    0;
}

:root {
  --primary: #4361ee;
  --error:   #e63946;
  --text:    #1a1a2e;
  --muted:   #666666;
  --border:  #d1d5db;
  --bg:      #f0f2f5;
}

body {
  font-family:      'Segoe UI', Arial, sans-serif;
  background-color: var(--bg);
}

.page {
  display:          flex;
  justify-content:  center;
  align-items:      center;
  min-height:       100vh;
  padding:          20px;
}

.login-card {
  background:    white;
  border-radius: 16px;
  box-shadow:    0 8px 30px rgba(0, 0, 0, 0.1);
  width:         100%;
  max-width:     420px;
  padding:       40px;
}

.login-header {
  text-align:    center;
  margin-bottom: 32px;
}

.login-header h1 {
  font-size:     26px;
  color:         var(--text);
  margin-bottom: 6px;
}

.login-header p {
  color:     var(--muted);
  font-size: 15px;
}

.login-form {
  display:        flex;
  flex-direction: column;
  gap:            20px;
}

.form-group {
  display:        flex;
  flex-direction: column;
  gap:            6px;
}

.form-group label {
  font-size:   14px;
  font-weight: 600;
  color:       var(--text);
}

.form-input {
  border:        1px solid var(--border);
  border-radius: 8px;
  padding:       12px 14px;
  font-size:     15px;
  outline:       none;
  transition:    border-color 0.2s;
  width:         100%;
}

.form-input:focus {
  border-color: var(--primary);
}

.form-options {
  display:         flex;
  justify-content: space-between;
  align-items:     center;
}

.checkbox-label {
  display:     flex;
  align-items: center;
  gap:         6px;
  font-size:   14px;
  color:       var(--muted);
  cursor:      pointer;
}

.forgot-link {
  font-size:       14px;
  color:           var(--primary);
  text-decoration: none;
}

.forgot-link:hover {
  text-decoration: underline;
}

.btn-login {
  background:    var(--primary);
  color:         white;
  border:        none;
  border-radius: 8px;
  padding:       14px;
  font-size:     16px;
  font-weight:   600;
  cursor:        pointer;
  transition:    background 0.2s;
  margin-top:    4px;
}

.btn-login:hover {
  background: #3451d1;
}

.signup-text {
  text-align:  center;
  font-size:   14px;
  color:       var(--muted);
  margin-top:  24px;
}

.signup-text a {
  color:           var(--primary);
  font-weight:     600;
  text-decoration: none;
}

.signup-text a:hover {
  text-decoration: underline;
}
```

---
---

# Case Study 3: Student Dashboard Page

---

## What We Are Building

A full dashboard page layout with a sidebar and a card grid — the same structure you will build in React.

---

## HTML

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Student Dashboard</title>
  <link rel="stylesheet" href="dashboard.css" />
</head>
<body>

  <!-- Top Navigation -->
  <header class="navbar">
    <div class="navbar-brand">StudentApp</div>
    <nav class="navbar-links">
      <a href="#" class="nav-link active">Dashboard</a>
      <a href="#" class="nav-link">Students</a>
      <a href="#" class="nav-link">Courses</a>
    </nav>
    <div class="navbar-user">Arjun S.</div>
  </header>

  <!-- Page Layout -->
  <div class="layout">

    <!-- Sidebar -->
    <aside class="sidebar">
      <ul class="sidebar-menu">
        <li class="menu-item active">Overview</li>
        <li class="menu-item">Students</li>
        <li class="menu-item">Courses</li>
        <li class="menu-item">Reports</li>
        <li class="menu-item">Settings</li>
      </ul>
    </aside>

    <!-- Main Content -->
    <main class="main-content">
      <h2 class="page-title">Dashboard Overview</h2>

      <!-- Stats Row -->
      <div class="stats-row">
        <div class="stat-card">
          <p class="stat-label">Total Students</p>
          <p class="stat-number">128</p>
        </div>
        <div class="stat-card">
          <p class="stat-label">Courses Active</p>
          <p class="stat-number">12</p>
        </div>
        <div class="stat-card">
          <p class="stat-label">Avg. Grade</p>
          <p class="stat-number">B+</p>
        </div>
        <div class="stat-card">
          <p class="stat-label">Placements</p>
          <p class="stat-number">84%</p>
        </div>
      </div>

      <!-- Student Cards -->
      <h3 class="section-title">Recent Students</h3>
      <div class="card-grid">
        <div class="student-card">
          <div class="student-avatar">AS</div>
          <div class="student-info">
            <p class="student-name">Arjun Sharma</p>
            <p class="student-course">Computer Science</p>
          </div>
          <span class="grade-badge">A</span>
        </div>
        <div class="student-card">
          <div class="student-avatar">PP</div>
          <div class="student-info">
            <p class="student-name">Priya Patel</p>
            <p class="student-course">Data Science</p>
          </div>
          <span class="grade-badge">B+</span>
        </div>
        <div class="student-card">
          <div class="student-avatar">RM</div>
          <div class="student-info">
            <p class="student-name">Rahul Menon</p>
            <p class="student-course">Cybersecurity</p>
          </div>
          <span class="grade-badge">A-</span>
        </div>
      </div>
    </main>

  </div>

</body>
</html>
```

---

## CSS

```css
/* dashboard.css */

* {
  box-sizing: border-box;
  margin:     0;
  padding:    0;
}

:root {
  --primary:    #4361ee;
  --sidebar-bg: #1a1a2e;
  --text:       #1a1a2e;
  --muted:      #666666;
  --bg:         #f0f2f5;
  --white:      #ffffff;
  --radius:     10px;
}

body {
  font-family: 'Segoe UI', Arial, sans-serif;
  background:  var(--bg);
  color:       var(--text);
}

/* Navbar */
.navbar {
  display:          flex;
  justify-content:  space-between;
  align-items:      center;
  background:       var(--sidebar-bg);
  padding:          14px 28px;
  position:         sticky;
  top:              0;
  z-index:          100;
}

.navbar-brand {
  color:       white;
  font-size:   20px;
  font-weight: 700;
}

.navbar-links {
  display: flex;
  gap:     24px;
}

.nav-link {
  color:           #aaa;
  text-decoration: none;
  font-size:       15px;
  transition:      color 0.2s;
}

.nav-link:hover,
.nav-link.active {
  color: white;
}

.navbar-user {
  color:       #aaa;
  font-size:   14px;
}

/* Two-column layout: sidebar + main */
.layout {
  display: flex;
  min-height: calc(100vh - 50px);
}

/* Sidebar */
.sidebar {
  width:      220px;
  background: var(--sidebar-bg);
  padding:    24px 0;
  flex-shrink: 0;
}

.sidebar-menu {
  list-style: none;
}

.menu-item {
  padding:     12px 24px;
  color:       #aaaaaa;
  cursor:      pointer;
  font-size:   15px;
  transition:  all 0.2s;
}

.menu-item:hover {
  background: rgba(255, 255, 255, 0.07);
  color:      white;
}

.menu-item.active {
  background:  rgba(67, 97, 238, 0.2);
  color:       white;
  border-left: 3px solid var(--primary);
}

/* Main content */
.main-content {
  flex:    1;
  padding: 28px 32px;
}

.page-title {
  font-size:     24px;
  margin-bottom: 24px;
  color:         var(--text);
}

/* Stats row */
.stats-row {
  display:               grid;
  grid-template-columns: repeat(4, 1fr);
  gap:                   20px;
  margin-bottom:         32px;
}

.stat-card {
  background:    var(--white);
  border-radius: var(--radius);
  padding:       20px 24px;
  box-shadow:    0 2px 8px rgba(0, 0, 0, 0.06);
}

.stat-label {
  font-size:     13px;
  color:         var(--muted);
  margin-bottom: 8px;
}

.stat-number {
  font-size:   28px;
  font-weight: 700;
  color:       var(--primary);
}

/* Student cards */
.section-title {
  font-size:     18px;
  margin-bottom: 16px;
}

.card-grid {
  display:        flex;
  flex-direction: column;
  gap:            12px;
}

.student-card {
  background:    var(--white);
  border-radius: var(--radius);
  padding:       16px 20px;
  display:       flex;
  align-items:   center;
  gap:           16px;
  box-shadow:    0 2px 8px rgba(0, 0, 0, 0.06);
  transition:    transform 0.2s;
}

.student-card:hover {
  transform: translateX(4px);
}

.student-avatar {
  width:            44px;
  height:           44px;
  border-radius:    50%;
  background:       var(--primary);
  color:            white;
  font-size:        16px;
  font-weight:      bold;
  display:          flex;
  justify-content:  center;
  align-items:      center;
  flex-shrink:      0;
}

.student-info {
  flex: 1;
}

.student-name {
  font-weight:   600;
  font-size:     15px;
  margin-bottom: 2px;
}

.student-course {
  font-size: 13px;
  color:     var(--muted);
}

.grade-badge {
  background:    #eef2ff;
  color:         var(--primary);
  font-weight:   700;
  font-size:     14px;
  padding:       4px 14px;
  border-radius: 20px;
}
```

---
---

# Part 4 — Practice Tasks

---

## Task 1 — HTML Structure Only

Build a webpage for a fictional restaurant called "Spice Garden" using only HTML (no CSS):
- `<header>` with restaurant name and navigation links: Menu, About, Contact
- `<main>` with:
  - A hero section with an `<h1>` and a short description paragraph
  - A `<section>` called "Our Menu" with three `<article>` elements, each having a dish name, price, and description
  - A `<section>` called "Contact" with an address, phone number, and a contact form (name, email, message, submit button)
- `<footer>` with copyright text

---

## Task 2 — Add CSS to Task 1

Style the Spice Garden restaurant page:
- Warm colour scheme using CSS variables
- Flexbox navbar with restaurant name on the left and links on the right
- CSS Grid for the menu section (3 cards on desktop, 1 on mobile with media queries)
- Styled contact form with focus states on inputs
- Consistent padding and spacing throughout

---

## Task 3 — Personal Portfolio Page

Build a personal portfolio page with HTML and CSS:
- Sticky navigation bar with smooth scrolling links to sections on the same page
- Hero section with your name, role, and a call-to-action button
- Skills section with styled badges (similar to the skill badges in Case Study 1)
- Projects section with a CSS Grid of project cards (image, title, description, link)
- Contact section with a form
- Footer
- Fully responsive using media queries

---

## Task 4 — Replicate a UI

Find any simple webpage you use regularly (a college portal, a food delivery app listing, a news site). Pick one screen and recreate it as closely as possible using only HTML and CSS. Do not look at the original's code — just look at what it looks like and build it yourself.

This exercise trains your eye for layout and teaches you to break a design down into HTML structure.

---

## Task 5 — Component Library

Create a single HTML file called `components.html` and a `components.css` file. In it, build a collection of reusable styled components — the kind you will use in React:

- Two button styles: primary (filled) and secondary (outlined)
- An input field with label and focus state
- An alert/notification box in three variants: success (green), warning (yellow), error (red)
- A card component with image placeholder, title, description, and a button
- A navigation bar
- A footer

Display all components on the page like a design reference sheet. This is exactly how component libraries like Material UI and Bootstrap are organised.

---
---

# Summary — What You Now Know

| Concept | Summary |
|---------|---------|
| HTML structure | `<!DOCTYPE html>`, `<html>`, `<head>`, `<body>` |
| Common elements | headings, paragraphs, links, images, lists, forms, buttons, divs |
| Semantic HTML | `<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<footer>` |
| Attributes | `class`, `id`, `href`, `src`, `alt`, `type`, `placeholder` |
| CSS syntax | `selector { property: value; }` |
| Selectors | element, `.class`, `#id`, descendant, `:hover`, `:focus` |
| Box model | content, padding, border, margin |
| `box-sizing: border-box` | Makes sizing predictable — always include |
| Flexbox | `display: flex`, `justify-content`, `align-items`, `gap`, `flex-wrap` |
| Grid | `display: grid`, `grid-template-columns`, `repeat`, `auto-fill`, `minmax` |
| Media queries | `@media (min-width: 600px) { ... }` |
| CSS variables | `--name: value` in `:root`, used with `var(--name)` |
| Transitions | `transition: property duration` — smooth state changes |

---

## What Comes Next — React

Now that you understand HTML and CSS, React will make complete sense:

| HTML/CSS | React equivalent |
|----------|-----------------|
| `<div class="card">` | `<div className="card">` |
| Copy-paste the same card 10 times | Create a `Card` component and reuse it |
| Change text in HTML directly | Change state → React updates the HTML for you |
| Static hardcoded data | Dynamic data from an API |
| Clicking shows/hides a div with JS | `useState` toggles conditional rendering |
| Navigating to a new `.html` file | React Router shows a different component |

Every UI you will build in React is HTML and CSS — React just makes it dynamic, reusable, and connected to real data. The HTML and CSS you have learned are the output React produces. Now you will learn to produce it programmatically.

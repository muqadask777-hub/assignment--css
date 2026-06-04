# CSS Theory Assignment

## Q1: What is CSS and how do you add it to an HTML page?

### Points Covered
* **What does CSS stand for?**
  <br>CSS stands for **Cascading Style Sheets**.
  
* **What problem does CSS solve?**
  <br>HTML was only made to build the basic structure of a webpage. Without CSS, developers had to add colors to every single element manually. This made the code very messy and hard to change. CSS solves this by separating the content from the design.

* **Three methods of adding CSS:**
  <br>1. **Inline CSS:** Adding style inside the HTML tag using the `style` attribute.
  <br>2. **Internal CSS:** Writing styles inside a `<style>` tag in the `<head>` section.
  <br>3. **External CSS:** Putting styles in a separate `.css` file and linking it with the `<link>` tag.

* **Why External CSS is preferred over Inline CSS:**
  <br>External CSS keeps the HTML code clean. If you want to change the design of the whole website, you only change one file instead of updating every page. It also makes the website load faster.

### Code Task

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>My CSS Assignment</title>

    <!-- External CSS -->
    <link rel="stylesheet" href="style.css">

    <!-- Internal CSS -->
    <style>
        h1 {
            color: blue;
            font-family: sans-serif;
        }
    </style>
</head>
<body>

    <h1>Hello! Welcome to My Assignment</h1>

    <!-- Inline CSS -->
    <p style="color: red; font-size: 16px;">
        This paragraph uses inline styling.
    </p>

</body>
</html>
```
## Q2: Explain CSS Selectors with examples.
### Comparison: Direct Child vs Descendant Selector
| Selector Type | Syntax | Description | Target Range |
|---|---|---|---|
| **Direct Child** | div > p | Targets only the immediate children. | Stricter (Only 1st level down) |
| **Descendant** | div p | Targets any matching element inside the parent, no matter how deep. | Broader (Deep nested elements too) |
### Points Covered
 * **Which selector has the highest specificity — class or ID?**
   
   The **ID selector** has higher specificity than a class selector. If you apply both to the same element, the ID style wins.
 * **Can you use the same class on multiple elements?**
   
   Yes, you can use the same class name on as many elements as you want.
 * **Can you use the same ID on multiple elements?**
   
   No, an ID must be completely unique. You can only use it once on a page.
### Code Task
```css
/* 1. Universal Selector (Applies to everything) */
* {
    margin: 0;
    padding: 0;
}

/* 2. Element Selector */
h2 {
    color: blue;
}

/* 3. Class Selector */
.my-card {
    background-color: yellow;
}

/* 4. ID Selector */
#main-banner {
    border: 2px solid black;
}

/* 5. Group Selector */
h1, p, span {
    font-family: Arial;
}

/* 6. Descendant Selector (Any span inside a div) */
div span {
    color: red;
}

/* 7. Child Selector (Only direct p inside a section) */
section > p {
    color: green;
}

```
## Q3: What is the CSS Box Model? Explain each layer.
### Points Covered
 * **Which layer is the innermost?**
   
   The **Content** layer is the absolute innermost part where text or images live.
 * **Padding is inside or outside the border?**
   
   Padding is **inside** the border. It adds space between the content and the border.
 * **What does margin: 0 auto do to a block element?**
   
   It sets the top/bottom margin to 0 and automatically divides the left/right margin equally. This **centers** the block element horizontally.
 * **With border-box, does width include padding?**
   
   Yes, when you use box-sizing: border-box, the padding and border are included inside the total width.
### Code Task
```css
.box {
    width: 300px;
    padding: 20px;
    border: 2px solid black;
    margin: 16px;
    box-sizing: border-box; /* Includes padding and border in 300px width */
}

```
## Q4: Explain CSS Colors. What are the different ways to define a color?
### Points Covered
 * **Which format is most commonly used by developers?**
   
   **HEX codes** and **RGB/RGBA** are the most common formats developers use every day.
 * **What does the 'A' in RGBA stand for?**
   
   The 'A' stands for **Alpha**, which controls the transparency from 0.0 to 1.0.
 * **Does opacity affect child elements?**
   
   Yes, if you use opacity: 0.5 on a parent div, everything inside it also becomes see-through.
 * **Does rgba affect child elements?**
   
   No, rgba() only makes the background or text color transparent. Child items stay solid.
### Code Task
```css
/* Writing the same Red color in 5 different ways */
.color-name { color: red; }
.color-hex  { color: #FF0000; }
.color-rgb  { color: rgb(255, 0, 0); }
.color-rgba { color: rgba(255, 0, 0, 1); }
.color-hsl  { color: hsl(0, 100%, 50%); }

```
## Q5: What are CSS Units? Explain px, %, rem, em, vh, and vw.
### Comparison: px vs rem for Accessibility

| Unit | Nature | Accessibility Behavior | Best Used For |
|---|---|---|---|
| **px** | Absolute / Fixed | Fixed unit that does not depend on the root font size. Browser zoom still affects it. | Borders, icons, precise spacing |
| **rem** | Relative to Root (<html>) | Scales according to the root font size and improves accessibility. | Font sizes, responsive layouts |
### Points Covered
 * **What is 1rem equal to by default?**
   
   By default, 1rem is equal to **16px**.
 * **% is relative to the parent or the root?**
   
   Percentage (%) is always relative to its immediate **parent** element.
 * **vh stands for what?**
   
   vh stands for **Viewport Height** (1vh means 1% of the screen's height).
### Code Task
```css
.hero-section {
    height: 100vh; /* Takes full screen height */
    font-size: 2rem; /* Scales up nicely based on root size */
    max-width: 70rem; /* Max width using rem for responsiveness */
    width: 100%;
    margin: 0 auto;
}

```
## Q6: What is CSS Specificity and how does the Cascade work?
### Points Covered
 * **Which has higher specificity — a class or an element selector?**
   
   A **class selector** wins over a basic HTML element selector because it has higher specificity.
 * **What specificity score does an inline style have?**
   
   Inline style has the highest priority, scored as **(1, 0, 0, 0)**.
 * **If two rules have equal specificity, which one wins?**
   
   The rule written **at the bottom (last)** in the CSS file will win.
 * **What does !important override?**

  `!important` overrides normal CSS specificity rules. If multiple rules use `!important`, then specificity and source order are used to decide which rule wins.
### Code Task
```css
/* HTML: <p id='intro' class='text'>Hello</p> */

p {
    color: red; /* Tag score is lowest */
}

.text {
    color: blue; /* Class wins over tag */
}

#intro {
    color: green; /* ID wins over class and tag */
}

/* Explanation: The paragraph color will be GREEN because the ID selector 
   (#intro) has a higher specificity score than classes or tags. */

```
## Q7: Explain CSS Flexbox. How does it differ from block layout?
### Comparison: justify-content vs align-items

| Property | Purpose | Axis Controlled |
|---|---|---|
| **justify-content** | Aligns and distributes items along the main axis. | Main Axis |
| **align-items** | Aligns items along the cross axis. | Cross Axis |

> **Note:** With the default `flex-direction: row`, the main axis is horizontal and the cross axis is vertical.
### Points Covered
 * **What does flex: 1 do to an item?**
   
   It tells the item to grow and take up all the leftover empty space inside the container.
 * **How do you center an element both horizontally and vertically with Flexbox?**
   
   Give the parent display: flex, then add justify-content: center and align-items: center.
 * **What does flex-wrap: wrap do?**
   
   If there is no space left on the row, it automatically pushes the extra items to the next line.
### Code Task
```html
<nav class="my-navbar">
    <div class="logo">MyBrand</div>
    <ul class="links">
        <li><a href="#">Home</a></li>
        <li><a href="#">About</a></li>
        <li><a href="#">Contact</a></li>
    </ul>
</nav>

```
```css
.my-navbar {
    display: flex;
    justify-content: space-between; /* Logo on left, links on right */
    align-items: center;            /* Centers them vertically */
    padding: 10px 20px;
    background-color: white;
}

.links {
    display: flex;
    gap: 15px;                      /* Adds spacing between items */
    list-style: none;
}

```
## Q8: What are CSS Pseudo-classes and Pseudo-elements?
### Points Covered
 * **Does ::before add a real HTML element?**
   
   No, it does not add a real tag to the HTML code. It just creates a virtual element through CSS.
 * **What CSS property is required for ::before/::after to appear?**
   
   The **content** property is strictly required. Even if it is empty like content: "";.
 * **:nth-child(2n) selects which elements?**
   
   It selects all the **even** sibling items (like 2nd, 4th, 6th, etc.).
 * **How would you style every 3rd list item?**
   
   By writing the **:nth-child(3n)** selector.
### Code Task
```css
/* 1. Change button to red on hover */
button:hover {
    background-color: red;
}

/* 2. Add a star before every featured item */
.featured::before {
    content: "★ ";
    color: red;
}

/* 3. Make placeholder text black inside input fields */
input::placeholder {
    color: black;
}

```
## Q9: Explain CSS Transitions and Animations.
### Points Covered
 * **A transition needs a trigger — what are common triggers?**
   
   Common triggers are user actions like **:hover** or **:focus**.
 * **Can you have multiple transitions on one element?**
   
   Yes, you can add commas to transition multiple properties together (like transition: width 0.3s, color 0.2s).
 * **What does animation-iteration-count: infinite do?**
   
   It makes the keyframe animation loop **forever** without stopping.
 * **Why is animating transform faster than animating width?**
   
   transform is handled by the GPU without causing a page layout recalculation. Changing width forces a slow layout redraw.
### Code Task
```css
.cool-card {
    width: 250px;
    padding: 15px;
    background: white;
    box-shadow: 0 4px 5px rgba(0,0,0,0.1);
    
    /* Smooth lift up effect transition */
    transition: transform 0.3s ease, box-shadow 0.3s ease;
    
    /* Fade in animation on load */
    animation: slideUp 1s ease-out forwards;
}

/* Hover effect */
.cool-card:hover {
    transform: translateY(-5px);
    box-shadow: 0 10px 15px rgba(0,0,0,0.2);
}

/* Animation timeline configuration */
@keyframes slideUp {
    from {
        opacity: 0;
        transform: translateY(20px);
    }
    to {
        opacity: 1;
        transform: translateY(0);
    }
}

```
## Q10: What is Responsive Web Design? Explain Media Queries, CSS Variables, and Mobile-First approach.
### Points Covered
 * **In mobile-first, do you use min-width or max-width in media queries?**
   
   In mobile-first design, we code for small screens first and use **min-width** to scale up.
 * **What does @media (prefers-color-scheme: dark) do?**
   
   It detects if the user's operating system has **Dark Mode** enabled to update colors automatically.
 * **Can JavaScript read and change CSS variables?**
   
   Yes, JavaScript can read and dynamically update custom properties.
 * **What is the difference between var(--color) and var(--color, fallback)?**
   
   var(--color) loads that variable, while var(--color, fallback) provides a **safe backup color** if the variable is missing.
### Code Task
```css
/* Base variables for layout styling */
:root {
    --primary-color: blue;
    --main-bg: white;
    --text-color: black;
}

/* Dark mode attribute setup */
[data-theme='dark'] {
    --main-bg: black;
    --text-color: white;
    --primary-color: red;
}

body {
    background-color: var(--main-bg);
    color: var(--text-color);
    font-family: sans-serif;
}

/* Mobile-First Query for Tablets */
@media (min-width: 768px) {
    body {
        padding: 20px;
    }
}

/* Mobile-First Query for Desktops */
@media (min-width: 1024px) {
    body {
        padding: 40px;
    }
}


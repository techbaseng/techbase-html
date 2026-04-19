---
render_with_liquid: false
title: "HTML Canvas and SVG Graphics"
nav_order: 32
---

# Lesson 32: HTML Canvas and SVG Graphics

---

## Lesson Introduction

Until now, every visual element you've placed on a web page has been something that already existed — text, images loaded from files, coloured boxes created with CSS. But what if you wanted to **draw something entirely from scratch**, right inside the browser, using code?

That is exactly what this lesson is about. HTML gives you two powerful tools for creating graphics directly in your web pages:

- **`<canvas>`** — a blank drawing surface where you use JavaScript to paint shapes, lines, text, gradients, and images pixel by pixel
- **`<svg>`** — a system for describing shapes using special HTML-like tags that the browser draws for you — no JavaScript required for simple shapes

These technologies are used everywhere in the real world: interactive charts in business dashboards, animated game characters, data visualisations in science apps, icons on websites, and much more.

By the end of this lesson, you will be able to:

- Understand what Canvas and SVG are and how they differ
- Create a Canvas element and use JavaScript to draw lines, circles, text, and gradients
- Create SVG graphics including circles, rectangles, polygons, ellipses, and styled text
- Decide which tool (Canvas vs SVG) is right for a given task
- Build a complete mini project that uses both technologies

---

## Prerequisite Concepts

Before diving in, let's quickly review a few ideas that underpin this lesson.

### What is a Coordinate System?

When you draw on a canvas or define SVG shapes, you use **x** and **y** coordinates to place things. In HTML graphics, the coordinate system works like this:

- The **top-left corner** of the drawing area is the point `(0, 0)`
- Moving **right** increases the x value
- Moving **down** increases the y value

```
(0,0) ─────────────→ x increases
  │
  │
  ↓
  y increases
```

So the point `(100, 50)` means: 100 pixels from the left edge and 50 pixels from the top edge.

> 💡 This is different from the maths coordinate system you may have used at school, where y increases upward. In HTML graphics, y increases downward.

### What is JavaScript?

**JavaScript** is a programming language that runs inside the browser. It can change HTML, respond to user actions, and — most importantly for this lesson — **draw graphics on a Canvas element**. You don't need to be a JavaScript expert for this lesson. Each script will be explained line by line.

### What is XML?

**XML** (Extensible Markup Language) is a way of writing structured information using tags, similar to HTML. SVG uses XML format — you describe shapes using tags like `<circle>`, `<rect>`, and `<polygon>` directly inside your HTML file.

### What Does "Resolution Independent" Mean?

An image made of **pixels** (dots of colour) gets blurry when you make it bigger — like zooming in on a photo on your phone. An image that is **resolution independent** (like SVG) stays sharp no matter how much you zoom in, because it is described mathematically rather than as a grid of dots.

---

## Part 1 — HTML Canvas

### What Is the Canvas Element?

The HTML `<canvas>` element is a **rectangular blank area** on your web page where you can draw anything you want using JavaScript. Think of it like a digital whiteboard: the canvas is the whiteboard itself, and JavaScript is the marker you use to draw on it.

> 💡 **Analogy:** Canvas is like an artist's blank canvas. The canvas does nothing on its own — you need a brush (JavaScript) to actually paint something on it.

### Why Does Canvas Exist?

Before HTML5, creating interactive graphics on a web page required special browser plugins (like Flash). The `<canvas>` element was introduced to allow graphics directly in the browser without any plugins — all you need is HTML and JavaScript.

It is ideal for: games, real-time data animations, image editing tools, and any graphic that needs to change rapidly or respond to user input.

---

### Step 1 — Creating the Canvas Element

The `<canvas>` tag creates the drawing area. By itself, it shows nothing (or just a blank rectangle if you add a border).

```html
<canvas id="myCanvas" width="200" height="100" style="border:1px solid #000000;">
</canvas>
```

Let's break down every part of this tag:

- `<canvas>` — the opening tag that tells the browser to create a drawing area
- `id="myCanvas"` — a unique name for this canvas. JavaScript will use this name to find and draw on this specific canvas
- `width="200"` — the canvas is 200 pixels wide
- `height="100"` — the canvas is 100 pixels tall
- `style="border:1px solid #000000;"` — adds a thin black border so you can see the canvas area (otherwise it's invisible)
- `</canvas>` — the closing tag

> ⚠️ **Important:** Always give your canvas an `id`, a `width`, and a `height`. Without these, your JavaScript won't know what to draw on, or how big the drawing area is.

**Expected Output in Browser:**

A plain empty white rectangle with a thin black border, 200 pixels wide and 100 pixels tall.

---

### Step 2 — The Three-Step Drawing Pattern

Every Canvas drawing follows the same three-step pattern:

**Step 1:** Find the canvas using its `id`
**Step 2:** Get the drawing tool (called the "context")
**Step 3:** Use the drawing tool to draw

```html
<script>
  // Step 1: Find the canvas by its id
  var c = document.getElementById("myCanvas");

  // Step 2: Get the 2D drawing context (the drawing tool)
  var ctx = c.getContext("2d");

  // Step 3: Draw something
  ctx.fillRect(10, 10, 150, 80);
</script>
```

Let's understand each line:

- `var c = document.getElementById("myCanvas");` — This finds the canvas element on the page using its id `"myCanvas"` and stores it in the variable `c`. Think of this as picking up the whiteboard.
- `var ctx = c.getContext("2d");` — This gets the **2D drawing context** — the actual drawing tool. The string `"2d"` means we want to draw in two dimensions (flat graphics). The variable `ctx` is short for "context".
- `ctx.fillRect(10, 10, 150, 80);` — This draws a solid filled rectangle. The four numbers mean: start at x=10, y=10, make it 150 pixels wide, 80 pixels tall.

> 💡 **Analogy:** `getElementById` picks up the whiteboard. `getContext("2d")` picks up the marker. Then you use the marker (`ctx`) to actually draw.

---

### Canvas Drawing Example 1 — Drawing a Line

A line is the simplest thing you can draw. You set a starting point, set an ending point, then draw the line.

```html
<!DOCTYPE html>
<html>
<body>

<canvas id="myCanvas" width="200" height="100" style="border:1px solid #000000;">
</canvas>

<script>
  var c = document.getElementById("myCanvas");
  var ctx = c.getContext("2d");

  ctx.moveTo(0, 0);       // Start the "pen" at position (0, 0) — top-left corner
  ctx.lineTo(200, 100);   // Draw a line to position (200, 100) — bottom-right corner
  ctx.stroke();           // Actually draw/display the line on screen
</script>

</body>
</html>
```

**Line-by-line explanation:**

- `ctx.moveTo(0, 0);` — Picks up the invisible "pen" and places it at coordinates (0, 0) — the top-left corner of the canvas. No line is drawn yet.
- `ctx.lineTo(200, 100);` — Draws an imaginary line from the current pen position to position (200, 100) — the bottom-right corner. Still not visible yet.
- `ctx.stroke();` — This is the command that actually makes the line appear on screen. Without `stroke()`, the line remains invisible.

**Expected Output:**

A diagonal line running from the top-left corner to the bottom-right corner of the canvas.

> 🤔 **Thinking Prompt:** What would happen if you changed `ctx.moveTo(0, 0)` to `ctx.moveTo(100, 0)`? Where would the line start?

---

### Canvas Drawing Example 2 — Drawing a Circle

Circles use a method called `arc()`. This works by defining the centre point of the circle and its radius.

```html
<script>
  var c = document.getElementById("myCanvas");
  var ctx = c.getContext("2d");

  ctx.beginPath();                         // Start a new drawing path (clear any previous path)
  ctx.arc(95, 50, 40, 0, 2 * Math.PI);    // Draw an arc (circle)
  ctx.stroke();                            // Make the circle appear
</script>
```

**Line-by-line explanation:**

- `ctx.beginPath();` — Clears any previously drawn path so the new shape starts fresh. Always use this before drawing a new shape.
- `ctx.arc(95, 50, 40, 0, 2 * Math.PI);` — This draws an arc (portion of a circle). Let's break down the five arguments:
  - `95` — the x position of the centre of the circle
  - `50` — the y position of the centre of the circle
  - `40` — the radius (how big the circle is, in pixels)
  - `0` — where to start the arc (0 = the 3 o'clock position, measured in radians)
  - `2 * Math.PI` — where to end the arc. `Math.PI` is approximately 3.14159 (π). Multiplying by 2 gives a full circle (360 degrees).
- `ctx.stroke();` — Draws the outline of the circle.

**Expected Output:**

A circle outline centred roughly in the middle of the canvas.

> 💡 **Quick Maths Note:** Angles in Canvas are measured in **radians**, not degrees. One full circle = 2π radians ≈ 6.28 radians. This is why we write `2 * Math.PI` for a full circle.

---

### Canvas Drawing Example 3 — Drawing Filled Text

You can draw text directly onto the canvas using `fillText()`.

```html
<script>
  var c = document.getElementById("myCanvas");
  var ctx = c.getContext("2d");

  ctx.font = "30px Arial";              // Set the font size and family
  ctx.fillText("Hello World", 10, 50); // Draw filled text at position (10, 50)
</script>
```

**Line-by-line explanation:**

- `ctx.font = "30px Arial";` — Sets the text style. `30px` is the font size (30 pixels tall), `Arial` is the font family. This must be set before drawing text.
- `ctx.fillText("Hello World", 10, 50);` — Draws the text `"Hello World"` on the canvas. The position `(10, 50)` is where the **bottom-left** of the text begins.

**Expected Output:**

The text "Hello World" appears in 30px Arial font on the canvas.

---

### Canvas Drawing Example 4 — Drawing Outline (Stroke) Text

Instead of filled text, you can draw just the outline of the letters using `strokeText()`.

```html
<script>
  var c = document.getElementById("myCanvas");
  var ctx = c.getContext("2d");

  ctx.font = "30px Arial";
  ctx.strokeText("Hello World", 10, 50); // Draw only the outline of the text
</script>
```

**Expected Output:**

The text "Hello World" appears with just the outline of each letter — the insides of the letters are hollow/transparent.

**Comparison:**

| Method | Effect |
|--------|--------|
| `fillText()` | Solid, filled text |
| `strokeText()` | Hollow outline text |

---

### Canvas Drawing Example 5 — Linear Gradient

A **gradient** is a smooth colour transition from one colour to another. A **linear gradient** goes in a straight line direction (e.g., left to right, or top to bottom).

```html
<script>
  var c = document.getElementById("myCanvas");
  var ctx = c.getContext("2d");

  // Step 1: Create the gradient object
  // Arguments: (startX, startY, endX, endY) — defines the direction
  var grd = ctx.createLinearGradient(0, 0, 200, 0);

  // Step 2: Add colour stops (points where the colour is defined)
  grd.addColorStop(0, "red");    // At the very start (0%), use red
  grd.addColorStop(1, "white");  // At the very end (100%), use white

  // Step 3: Apply the gradient as the fill colour
  ctx.fillStyle = grd;

  // Step 4: Draw a rectangle filled with the gradient
  ctx.fillRect(10, 10, 150, 80);
</script>
```

**Line-by-line explanation:**

- `ctx.createLinearGradient(0, 0, 200, 0)` — Creates a gradient that runs from point `(0, 0)` to point `(200, 0)`. Both points have `y=0`, so this goes purely left-to-right (horizontal).
- `grd.addColorStop(0, "red")` — At position 0 (0% of the way along — the start), use red.
- `grd.addColorStop(1, "white")` — At position 1 (100% of the way along — the end), use white.
- `ctx.fillStyle = grd` — Sets the current fill colour to be the gradient we just created.
- `ctx.fillRect(10, 10, 150, 80)` — Draws a filled rectangle at (10, 10), 150px wide and 80px tall, filled with the gradient.

**Expected Output:**

A rectangle that starts red on the left and fades to white on the right.

> 🤔 **Thinking Prompt:** What would happen if you changed `grd.addColorStop(0, "red")` to `grd.addColorStop(0, "blue")`? What would the rectangle look like then?

---

### Canvas Drawing Example 6 — Radial (Circular) Gradient

A **radial gradient** radiates outward from a centre point, like rings on water after dropping a stone.

```html
<script>
  var c = document.getElementById("myCanvas");
  var ctx = c.getContext("2d");

  // Create a radial gradient
  // Arguments: (innerCenterX, innerCenterY, innerRadius, outerCenterX, outerCenterY, outerRadius)
  var grd = ctx.createRadialGradient(75, 50, 5, 90, 60, 100);

  grd.addColorStop(0, "red");    // Red at the centre
  grd.addColorStop(1, "white");  // White at the outer edge

  ctx.fillStyle = grd;
  ctx.fillRect(10, 10, 150, 80);
</script>
```

**Understanding `createRadialGradient(75, 50, 5, 90, 60, 100)`:**

- `75, 50` — the centre of the inner (small) circle
- `5` — the radius of the inner circle (5 pixels)
- `90, 60` — the centre of the outer (large) circle
- `100` — the radius of the outer circle (100 pixels)

The gradient transitions from red (at the inner circle) to white (at the outer circle).

**Expected Output:**

A rectangle with a red glow in the middle that fades to white at the edges.

---

### Canvas Drawing Example 7 — Drawing an Image

You can draw images (like photo files) onto a canvas using `drawImage()`.

```html
<!DOCTYPE html>
<html>
<body>

<!-- First, place an image on the page (it can be hidden) -->
<img id="scream" src="img_the_scream.jpg" alt="The Scream" width="220" height="277">

<canvas id="myCanvas" width="240" height="297" style="border:1px solid #d3d3d3;">
</canvas>

<script>
  var c = document.getElementById("myCanvas");
  var ctx = c.getContext("2d");
  var img = document.getElementById("scream");  // Find the image by its id
  ctx.drawImage(img, 10, 10);                   // Draw the image at position (10, 10)
</script>

</body>
</html>
```

**Line-by-line explanation:**

- `var img = document.getElementById("scream");` — Finds the `<img>` element with id `"scream"` and stores it in the variable `img`.
- `ctx.drawImage(img, 10, 10);` — Draws that image onto the canvas, with its top-left corner placed at position (10, 10).

**Expected Output:**

The image "img_the_scream.jpg" appears drawn onto the canvas at position (10, 10).

---

### Full Canvas Code Structure

Now that you've seen all the individual techniques, here is the complete structure of a Canvas page:

```html
<!DOCTYPE html>
<html>
<body>

<!-- 1. Create the canvas element -->
<canvas id="myCanvas" width="300" height="200" style="border:1px solid black;">
</canvas>

<!-- 2. Write the JavaScript to draw on it -->
<script>
  // Always start with these two lines
  var c = document.getElementById("myCanvas");
  var ctx = c.getContext("2d");

  // Then draw whatever you want below this line
  ctx.fillStyle = "blue";
  ctx.fillRect(20, 20, 100, 80);
</script>

</body>
</html>
```

**Expected Output:**

A solid blue rectangle, 100px wide and 80px tall, appearing inside the canvas at position (20, 20).

---

## Part 2 — HTML SVG

### What Is SVG?

**SVG** stands for **Scalable Vector Graphics**. It is a way to define graphics using XML-based tags directly inside your HTML. You describe what you want to draw (a circle, a rectangle, a line), and the browser does the drawing — no JavaScript needed for basic shapes.

> 💡 **Analogy:** SVG is like ordering from a menu. You write down "one circle, radius 40, colour yellow" and the browser delivers exactly that. Canvas is like cooking from scratch — you write all the step-by-step instructions yourself.

### Why SVG Is "Scalable"

Because SVG shapes are described mathematically (not as pixels), they can be scaled to any size without losing sharpness. A circle described as "radius 40" stays perfectly round whether displayed at 100px or 1000px. This is why SVG is perfect for logos, icons, and illustrations that need to look good at any size.

### SVG Key Facts

- SVG stands for **Scalable Vector Graphics**
- SVG is used to define **vector-based graphics** for the web
- SVG defines graphics in **XML format**
- Each element and attribute in SVG files **can be animated**
- SVG is a **W3C recommendation** (an official web standard)
- SVG integrates with other standards such as **CSS, DOM, XSL, and JavaScript**

---

### The `<svg>` Container Element

All SVG shapes must be placed inside an `<svg>` element. This element acts as the container (or canvas) for all your SVG shapes.

```html
<svg width="400" height="200">
  <!-- Shapes go here -->
</svg>
```

- `width="400"` — the SVG drawing area is 400px wide
- `height="200"` — the SVG drawing area is 200px tall

---

### SVG Example 1 — Drawing a Circle

```html
<!DOCTYPE html>
<html>
<body>

<svg width="100" height="100">
  <circle cx="50" cy="50" r="40" stroke="green" stroke-width="4" fill="yellow" />
</svg>

</body>
</html>
```

**Attribute-by-attribute explanation of `<circle>`:**

- `cx="50"` — the **centre x** position of the circle (50px from the left)
- `cy="50"` — the **centre y** position of the circle (50px from the top)
- `r="40"` — the **radius** of the circle (40 pixels)
- `stroke="green"` — the **outline colour** of the circle (green)
- `stroke-width="4"` — the **thickness** of the outline (4 pixels)
- `fill="yellow"` — the **fill colour** inside the circle (yellow)

**Expected Output:**

A yellow circle with a green border, centred in the SVG area.

> 🤔 **Thinking Prompt:** What would happen if you changed `fill="yellow"` to `fill="none"`? The inside of the circle would become transparent — you'd see only the green outline ring.

---

### SVG Example 2 — Drawing a Rectangle

```html
<svg width="400" height="120">
  <rect x="10" y="10" width="200" height="100" stroke="red" stroke-width="6" fill="blue" />
</svg>
```

**Attribute-by-attribute explanation of `<rect>`:**

- `x="10"` — how far from the left edge the rectangle starts (10px)
- `y="10"` — how far from the top edge the rectangle starts (10px)
- `width="200"` — how wide the rectangle is (200px)
- `height="100"` — how tall the rectangle is (100px)
- `stroke="red"` — the outline colour is red
- `stroke-width="6"` — the outline is 6 pixels thick
- `fill="blue"` — the inside of the rectangle is filled with blue

**Expected Output:**

A blue-filled rectangle with a thick red border.

---

### SVG Example 3 — Rectangle with Rounded Corners and Opacity

You can add rounded corners and transparency to SVG shapes.

```html
<svg width="400" height="180">
  <rect x="50" y="20" rx="20" ry="20" width="150" height="150"
    style="fill:red;stroke:black;stroke-width:5;opacity:0.5" />
</svg>
```

**New attributes explained:**

- `rx="20"` — rounds the corners horizontally (20px radius on the corner curves)
- `ry="20"` — rounds the corners vertically (20px radius on the corner curves)
- `style="..."` — instead of separate attributes, you can use a CSS `style` attribute:
  - `fill:red` — red fill
  - `stroke:black` — black outline
  - `stroke-width:5` — outline is 5px thick
  - `opacity:0.5` — 50% transparent (so you can see through the shape)

**Expected Output:**

A red rectangle with softly rounded corners, a black border, and 50% transparency (slightly see-through).

> 💡 **Opacity Note:** `opacity:1` = fully visible, `opacity:0` = completely invisible, `opacity:0.5` = half-transparent.

---

### SVG Example 4 — Drawing a Star (Polygon)

The `<polygon>` element draws a shape by connecting a series of points.

```html
<svg width="300" height="200">
  <polygon points="100,10 40,198 190,78 10,78 160,198"
    style="fill:lime;stroke:purple;stroke-width:5;fill-rule:evenodd;" />
</svg>
```

**Attribute explanation:**

- `points="100,10 40,198 190,78 10,78 160,198"` — a list of x,y coordinate pairs. The browser connects them in order, then closes the shape back to the first point. These specific coordinates produce a 5-pointed star.
- `fill:lime` — filled with bright lime green
- `stroke:purple` — purple outline
- `stroke-width:5` — 5px thick outline
- `fill-rule:evenodd` — this controls how the overlapping areas of a star's interior are filled. `evenodd` gives the classic star appearance with a hollow centre.

**Expected Output:**

A lime-coloured 5-pointed star with a purple border and hollow centre.

---

### SVG Example 5 — Gradient Ellipse with Text

This example shows multiple SVG elements working together: a gradient definition, an ellipse, and text.

```html
<svg height="130" width="500">

  <!-- Define a gradient to use later -->
  <defs>
    <linearGradient id="grad1">
      <stop offset="0%" stop-color="yellow" />
      <stop offset="100%" stop-color="red" />
    </linearGradient>
  </defs>

  <!-- Draw an ellipse using the gradient as its fill -->
  <ellipse cx="100" cy="70" rx="85" ry="55" fill="url(#grad1)" />

  <!-- Draw text on top -->
  <text fill="#ffffff" font-size="45" font-family="Verdana" x="50" y="86">SVG</text>

  <!-- Fallback message for browsers that don't support SVG -->
  Sorry, your browser does not support inline SVG.

</svg>
```

**Explanation of each piece:**

- `<defs>...</defs>` — a section where you **define reusable things** (like gradients, patterns) without drawing them yet. Things defined here are referenced by `id` later.
- `<linearGradient id="grad1">` — defines a linear gradient named `grad1`
- `<stop offset="0%" stop-color="yellow" />` — at the start (0%), use yellow
- `<stop offset="100%" stop-color="red" />` — at the end (100%), use red
- `<ellipse cx="100" cy="70" rx="85" ry="55" fill="url(#grad1)" />` — draws an ellipse (oval):
  - `cx="100"` — centre x position
  - `cy="70"` — centre y position
  - `rx="85"` — horizontal radius (how wide)
  - `ry="55"` — vertical radius (how tall)
  - `fill="url(#grad1)"` — fill with the gradient we defined as `grad1`
- `<text fill="#ffffff" font-size="45" font-family="Verdana" x="50" y="86">SVG</text>` — draws white text saying "SVG":
  - `fill="#ffffff"` — white text
  - `font-size="45"` — 45px font
  - `font-family="Verdana"` — Verdana typeface
  - `x="50" y="86"` — position of the text

**Expected Output:**

A yellow-to-red gradient oval with white "SVG" text written across it.

---

## Part 3 — Canvas vs SVG: Understanding the Difference

This is one of the most important sections in this lesson. Canvas and SVG can both draw graphics, but they work in completely different ways and are suited for different purposes.

### How They Work Differently

**Canvas:**
- Draws graphics **pixel by pixel** using JavaScript
- Once something is drawn, the browser **forgets about it** — it's just pixels on a screen
- If you want to change or move something, you must **erase and redraw** the entire scene
- Like painting on a real canvas — once paint is dry, you paint over it to change it

**SVG:**
- Draws graphics by **describing objects** in XML (like a list of shapes)
- Every shape is remembered as an **object in the browser's memory** (part of the DOM)
- You can change, move, hide, or animate individual shapes without redrawing everything
- Like placing cut-out shapes on a desk — you can move each piece independently

### Event Handlers

Because SVG shapes are objects in the DOM, you can attach JavaScript event handlers directly to them. For example: "when the user clicks this circle, change its colour." This is not easily possible with Canvas, where the shapes are just pixels.

### Text Quality

SVG has better built-in text rendering because text is described as a shape definition and scales perfectly. Canvas text can appear blurry at different zoom levels.

### When to Use Each

**Use Canvas when:**
- You are building a game with fast-moving graphics (many updates per second)
- You need to save the output as a `.png` or `.jpg` image
- You are processing pixel-level image data (like applying filters to photos)
- Performance matters more than interactivity with individual shapes

**Use SVG when:**
- You are creating logos, icons, or illustrations that need to scale perfectly
- You need shapes that respond to mouse/touch events individually
- You are creating charts or diagrams where elements may need to be animated or updated
- You need good text rendering within graphics

### Side-by-Side Comparison Table

| Feature | SVG | Canvas |
|---------|-----|--------|
| **Resolution** | Resolution independent (always sharp) | Resolution dependent (can be pixelated) |
| **Event handlers** | Supported — each shape can respond to clicks | Not natively supported |
| **Text quality** | Good text rendering | Poor text rendering at different sizes |
| **Performance** | Slower if very complex | Better for graphic-intensive games |
| **Save as image** | Not easily | Can save as .png or .jpg |
| **How shapes are stored** | As objects in the DOM (remembered) | As pixels (forgotten after drawing) |
| **Best for** | Scalable graphics, diagrams, icons | Games, image processing, heavy animations |

---

## Guided Practice Exercises

### Exercise 1 — Your First Canvas Drawing

**Objective:** Set up a canvas and draw a filled blue square.

**Scenario:** You are building a landing page and want a simple coloured block as a design element.

**Steps:**
1. Create an HTML file with the basic structure
2. Add a `<canvas>` element with `id="box"`, `width="200"`, `height="200"`, and a visible border
3. Add a `<script>` that gets the canvas context
4. Set `ctx.fillStyle` to `"blue"` and draw a filled rectangle

**Starter Code:**

```html
<!DOCTYPE html>
<html>
<body>

<canvas id="box" width="200" height="200" style="border:1px solid black;">
</canvas>

<script>
  var c = document.getElementById("box");
  var ctx = c.getContext("2d");

  ctx.fillStyle = "blue";          // Set the fill colour to blue
  ctx.fillRect(25, 25, 150, 150);  // Draw a square: start (25,25), 150px wide, 150px tall
</script>

</body>
</html>
```

**Expected Output:**

A blue square centred within the canvas area.

**Self-Check Questions:**
- What would happen if you changed `fillStyle` to `"red"` before drawing?
- What would happen if you set `ctx.fillRect(0, 0, 200, 200)`? Try it!
- Can you draw two rectangles of different colours, one after the other?

---

### Exercise 2 — Drawing Shapes on Canvas

**Objective:** Practice drawing a line, a circle, and text all on the same canvas.

```html
<!DOCTYPE html>
<html>
<body>

<canvas id="myDraw" width="400" height="300" style="border:1px solid black;">
</canvas>

<script>
  var c = document.getElementById("myDraw");
  var ctx = c.getContext("2d");

  // Draw a diagonal line from top-left to middle
  ctx.moveTo(0, 0);
  ctx.lineTo(200, 150);
  ctx.stroke();

  // Draw a circle in the centre
  ctx.beginPath();
  ctx.arc(200, 150, 50, 0, 2 * Math.PI);
  ctx.strokeStyle = "red";   // Make the circle outline red
  ctx.stroke();

  // Draw some text
  ctx.fillStyle = "black";
  ctx.font = "20px Arial";
  ctx.fillText("Canvas Drawing!", 100, 270);
</script>

</body>
</html>
```

**Expected Output:**

A canvas showing a diagonal line from top-left to the centre, a red circle outline centred at (200, 150), and the text "Canvas Drawing!" near the bottom.

**New concepts used:**
- `ctx.strokeStyle = "red"` — sets the outline/line colour (just like `fillStyle` sets the fill colour)

**Self-Check Questions:**
- What is the difference between `fillStyle` and `strokeStyle`?
- What does `beginPath()` do and why is it important before drawing a new shape?
- What would happen if you removed `ctx.beginPath()` before the circle?

---

### Exercise 3 — Gradient Rectangle

**Objective:** Create a canvas with a left-to-right colour gradient filling a rectangle.

```html
<!DOCTYPE html>
<html>
<body>

<canvas id="gradCanvas" width="300" height="150" style="border:1px solid black;">
</canvas>

<script>
  var c = document.getElementById("gradCanvas");
  var ctx = c.getContext("2d");

  // Create a gradient from left (x=0) to right (x=300)
  var gradient = ctx.createLinearGradient(0, 0, 300, 0);
  gradient.addColorStop(0, "purple");   // Start with purple
  gradient.addColorStop(0.5, "white");  // Transition through white at 50%
  gradient.addColorStop(1, "orange");   // End with orange

  ctx.fillStyle = gradient;
  ctx.fillRect(0, 0, 300, 150);         // Fill the whole canvas
</script>

</body>
</html>
```

**Expected Output:**

A canvas filled with a smooth gradient: purple on the left, blending through white in the middle, and ending with orange on the right.

**What-If Challenge:** Change the gradient direction to run top-to-bottom by changing `createLinearGradient(0, 0, 300, 0)` to `createLinearGradient(0, 0, 0, 150)`. What changes?

---

### Exercise 4 — SVG Shapes Showcase

**Objective:** Create a page with three different SVG shapes: a circle, a rectangle, and a polygon.

```html
<!DOCTYPE html>
<html>
<body>

<h2>SVG Shapes Showcase</h2>

<!-- Shape 1: A circle -->
<svg width="120" height="120">
  <circle cx="60" cy="60" r="50" stroke="darkblue" stroke-width="3" fill="lightblue" />
</svg>

<!-- Shape 2: A rectangle with rounded corners -->
<svg width="200" height="100">
  <rect x="10" y="10" rx="15" ry="15" width="180" height="80"
    style="fill:lightgreen;stroke:darkgreen;stroke-width:3;" />
</svg>

<!-- Shape 3: A triangle using polygon -->
<svg width="200" height="180">
  <polygon points="100,10 10,170 190,170"
    style="fill:gold;stroke:darkorange;stroke-width:3;" />
</svg>

</body>
</html>
```

**Expected Output:**

Three separate SVG images on the page: a light blue circle with a dark blue border, a light green rounded rectangle with a dark green border, and a gold triangle with a dark orange border.

**Self-Check Questions:**
- How do `cx` and `cy` differ from `x` and `y` in SVG attributes?
- The `<polygon>` for the triangle has 3 points. Can you add a 4th point to make it a quadrilateral?
- What does `rx` and `ry` do to the rectangle?

---

### Exercise 5 — SVG vs Canvas: Draw the Same Shape Both Ways

**Objective:** Draw a filled red circle with both Canvas and SVG to see the difference in approach.

**Using Canvas:**

```html
<canvas id="circleCanvas" width="120" height="120" style="border:1px solid black;">
</canvas>

<script>
  var c = document.getElementById("circleCanvas");
  var ctx = c.getContext("2d");

  ctx.beginPath();
  ctx.arc(60, 60, 50, 0, 2 * Math.PI); // Circle: centre (60,60), radius 50
  ctx.fillStyle = "red";
  ctx.fill();          // Fill with colour (not just outline)
  ctx.strokeStyle = "black";
  ctx.lineWidth = 3;
  ctx.stroke();        // Also draw the outline
</script>
```

**Using SVG:**

```html
<svg width="120" height="120">
  <circle cx="60" cy="60" r="50" fill="red" stroke="black" stroke-width="3" />
</svg>
```

**Expected Output (both):**

A red-filled circle with a black border, 50px radius, centred in a 120x120 area.

**Self-Check Questions:**
- Which approach uses more code — Canvas or SVG? Why?
- Which approach is easier to read and understand?
- Which approach would be better for animating the circle? (Hint: SVG objects can be moved with CSS or JavaScript without redrawing.)

---

## Mini Project: Interactive Science Dashboard Illustration

In this project, you will build a **Science Dashboard Illustration** page that displays:
1. A Canvas section with a gradient background and title text (representing a "graph area")
2. An SVG section showing a solar system diagram with labelled circles

This project uses both Canvas and SVG to demonstrate their different strengths.

---

### Stage 1 — Page Setup

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Science Dashboard</title>
  <style>
    body { font-family: Arial, sans-serif; padding: 20px; background: #f5f5f5; }
    h1 { color: #333; }
    h2 { color: #555; }
    .section { margin-bottom: 30px; padding: 15px; background: white; border-radius: 8px; }
  </style>
</head>
<body>

<h1>Science Dashboard Illustration</h1>
<p>Demonstrating HTML Canvas and SVG graphics together.</p>

<!-- Canvas section and SVG section will go here -->

</body>
</html>
```

**Milestone:** A styled page with a title and description.

---

### Stage 2 — Canvas: Temperature Graph Area

Add a canvas that looks like a data visualisation panel — a gradient background with labels drawn on it.

```html
<div class="section">
  <h2>Canvas: Temperature Data Panel</h2>

  <canvas id="tempCanvas" width="500" height="200" style="border:1px solid #ccc;">
  </canvas>

  <script>
    var c = document.getElementById("tempCanvas");
    var ctx = c.getContext("2d");

    // Background gradient (cool blue to warm orange — like temperature range)
    var bg = ctx.createLinearGradient(0, 0, 500, 0);
    bg.addColorStop(0, "#4fc3f7");   // Cool blue
    bg.addColorStop(1, "#ff8a65");   // Warm orange
    ctx.fillStyle = bg;
    ctx.fillRect(0, 0, 500, 200);    // Fill entire canvas as background

    // Draw a horizontal white centre line (like a baseline on a graph)
    ctx.strokeStyle = "white";
    ctx.lineWidth = 2;
    ctx.moveTo(0, 100);
    ctx.lineTo(500, 100);
    ctx.stroke();

    // Draw data point circles
    var dataPoints = [
      {x: 50,  y: 120},
      {x: 120, y: 90},
      {x: 200, y: 60},
      {x: 280, y: 75},
      {x: 360, y: 50},
      {x: 440, y: 30}
    ];

    ctx.fillStyle = "white";
    for (var i = 0; i < dataPoints.length; i++) {
      ctx.beginPath();
      ctx.arc(dataPoints[i].x, dataPoints[i].y, 6, 0, 2 * Math.PI);
      ctx.fill();
    }

    // Draw connecting lines between data points
    ctx.strokeStyle = "rgba(255,255,255,0.7)";
    ctx.lineWidth = 2;
    ctx.beginPath();
    ctx.moveTo(dataPoints[0].x, dataPoints[0].y);
    for (var j = 1; j < dataPoints.length; j++) {
      ctx.lineTo(dataPoints[j].x, dataPoints[j].y);
    }
    ctx.stroke();

    // Draw title text
    ctx.fillStyle = "white";
    ctx.font = "bold 18px Arial";
    ctx.fillText("Temperature Trend (°C)", 10, 190);
  </script>
</div>
```

**Milestone Output:**

A canvas with a blue-to-orange gradient background, white data point dots connected by a white line, and a title at the bottom — resembling a stylised temperature trend chart.

---

### Stage 3 — SVG: Solar System Diagram

Add an SVG section showing a simplified solar system with labelled planets.

```html
<div class="section">
  <h2>SVG: Solar System Diagram</h2>

  <svg width="560" height="200" style="background:#0d1b2a; border-radius:8px;">

    <!-- The Sun -->
    <circle cx="60" cy="100" r="40" fill="url(#sunGrad)" />
    <defs>
      <radialGradient id="sunGrad">
        <stop offset="0%" stop-color="white" />
        <stop offset="40%" stop-color="yellow" />
        <stop offset="100%" stop-color="orange" />
      </radialGradient>
    </defs>
    <text x="35" y="157" fill="white" font-size="12" font-family="Arial">Sun</text>

    <!-- Orbit lines -->
    <ellipse cx="60" cy="100" rx="100" ry="15" fill="none" stroke="#334" stroke-width="1" />
    <ellipse cx="60" cy="100" rx="175" ry="25" fill="none" stroke="#334" stroke-width="1" />
    <ellipse cx="60" cy="100" rx="265" ry="40" fill="none" stroke="#334" stroke-width="1" />

    <!-- Mercury -->
    <circle cx="160" cy="100" r="8" fill="#b0b0b0" />
    <text x="148" y="125" fill="#aaa" font-size="10" font-family="Arial">Mercury</text>

    <!-- Venus -->
    <circle cx="235" cy="100" r="12" fill="#e8c77a" />
    <text x="226" y="127" fill="#aaa" font-size="10" font-family="Arial">Venus</text>

    <!-- Earth -->
    <circle cx="325" cy="100" r="13" fill="#4a90d9" stroke="#27ae60" stroke-width="2" />
    <text x="318" y="150" fill="#aaa" font-size="10" font-family="Arial">Earth</text>

  </svg>
</div>
```

**Milestone Output:**

A dark space-themed SVG panel showing the Sun glowing with a radial gradient, three orbital ellipses, and three planets (Mercury, Venus, Earth) with labels — all as clean, scalable vector graphics.

---

### Stage 4 — Complete Final Page

Assembling both sections into the complete project:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Science Dashboard</title>
  <style>
    body { font-family: Arial, sans-serif; padding: 20px; background: #f0f4f8; }
    h1 { color: #222; }
    h2 { color: #444; margin-top: 0; }
    .section {
      margin-bottom: 30px;
      padding: 20px;
      background: white;
      border-radius: 10px;
      box-shadow: 0 2px 6px rgba(0,0,0,0.1);
    }
    p.note { font-size: 13px; color: #888; margin-top: 10px; }
  </style>
</head>
<body>

<h1>Science Dashboard Illustration</h1>
<p>This page demonstrates both HTML Canvas (JavaScript-drawn graphics) and SVG (markup-described graphics).</p>

<!-- === CANVAS SECTION === -->
<div class="section">
  <h2>Canvas: Temperature Trend Panel</h2>

  <canvas id="tempCanvas" width="500" height="200" style="border:1px solid #ddd; border-radius:6px;">
  </canvas>
  <p class="note">Drawn with HTML Canvas + JavaScript. Pixel-based. Fast for changing data.</p>

  <script>
    var c = document.getElementById("tempCanvas");
    var ctx = c.getContext("2d");

    var bg = ctx.createLinearGradient(0, 0, 500, 0);
    bg.addColorStop(0, "#4fc3f7");
    bg.addColorStop(1, "#ff8a65");
    ctx.fillStyle = bg;
    ctx.fillRect(0, 0, 500, 200);

    ctx.strokeStyle = "rgba(255,255,255,0.4)";
    ctx.lineWidth = 1;
    for (var gridY = 25; gridY < 200; gridY += 25) {
      ctx.beginPath();
      ctx.moveTo(0, gridY);
      ctx.lineTo(500, gridY);
      ctx.stroke();
    }

    var dataPoints = [
      {x:50,y:140},{x:120,y:110},{x:200,y:80},
      {x:280,y:95},{x:360,y:60},{x:440,y:40}
    ];

    ctx.strokeStyle = "rgba(255,255,255,0.8)";
    ctx.lineWidth = 2;
    ctx.beginPath();
    ctx.moveTo(dataPoints[0].x, dataPoints[0].y);
    for (var j = 1; j < dataPoints.length; j++) {
      ctx.lineTo(dataPoints[j].x, dataPoints[j].y);
    }
    ctx.stroke();

    ctx.fillStyle = "white";
    for (var i = 0; i < dataPoints.length; i++) {
      ctx.beginPath();
      ctx.arc(dataPoints[i].x, dataPoints[i].y, 6, 0, 2 * Math.PI);
      ctx.fill();
    }

    ctx.fillStyle = "white";
    ctx.font = "bold 16px Arial";
    ctx.fillText("Temperature Trend (°C)", 10, 188);
  </script>
</div>

<!-- === SVG SECTION === -->
<div class="section">
  <h2>SVG: Solar System Diagram</h2>

  <svg width="560" height="220" style="background:#0d1b2a; border-radius:8px; display:block;">

    <defs>
      <radialGradient id="sunGrad">
        <stop offset="0%" stop-color="white" />
        <stop offset="40%" stop-color="yellow" />
        <stop offset="100%" stop-color="orange" />
      </radialGradient>
    </defs>

    <!-- Sun -->
    <circle cx="60" cy="110" r="45" fill="url(#sunGrad)" />
    <text x="40" y="170" fill="yellow" font-size="12" font-family="Arial" font-weight="bold">Sun</text>

    <!-- Orbit paths -->
    <ellipse cx="60" cy="110" rx="110" ry="18" fill="none" stroke="#1c3a5e" stroke-width="1" />
    <ellipse cx="60" cy="110" rx="190" ry="30" fill="none" stroke="#1c3a5e" stroke-width="1" />
    <ellipse cx="60" cy="110" rx="280" ry="45" fill="none" stroke="#1c3a5e" stroke-width="1" />

    <!-- Mercury -->
    <circle cx="170" cy="110" r="8" fill="#9e9e9e" />
    <text x="156" y="135" fill="#9e9e9e" font-size="10" font-family="Arial">Mercury</text>

    <!-- Venus -->
    <circle cx="250" cy="110" r="13" fill="#e8c77a" />
    <text x="240" y="135" fill="#e8c77a" font-size="10" font-family="Arial">Venus</text>

    <!-- Earth -->
    <circle cx="340" cy="110" r="14" fill="#4a90d9" stroke="#27ae60" stroke-width="3" />
    <text x="330" y="140" fill="#4a90d9" font-size="10" font-family="Arial">Earth</text>

    <!-- Mars -->
    <circle cx="455" cy="110" r="10" fill="#c0392b" />
    <text x="444" y="135" fill="#c0392b" font-size="10" font-family="Arial">Mars</text>

  </svg>
  <p class="note">Drawn with SVG markup. Resolution-independent. Each planet is a clickable DOM object.</p>
</div>

</body>
</html>
```

**Milestone Output:**

A polished two-section science dashboard page:
- Top section: A gradient temperature trend chart drawn with Canvas
- Bottom section: A space-themed solar system diagram drawn with SVG

**Reflection Questions:**
1. Which section was easier to write — Canvas or SVG? Why?
2. If you wanted to make the Earth circle change colour when you hover over it, which approach (Canvas or SVG) would make this easier?
3. If you wanted this page to update the temperature chart every second with new data, which technology would handle that better?
4. What would happen to the SVG solar system diagram if you zoomed in on your browser? What about the Canvas one?

**Optional Advanced Extensions:**
- Add Mars and Jupiter to the SVG solar system with appropriate sizes and colours
- Add a `<title>` tag inside each SVG planet circle (like `<title>Earth - third planet</title>`) — this creates a browser tooltip on hover
- Make the Canvas draw a new random temperature point each time the user clicks on it

---

## Common Beginner Mistakes

### Mistake 1: Forgetting to Call `getContext("2d")` Before Drawing

**Wrong:**

```html
<script>
  var c = document.getElementById("myCanvas");
  c.fillRect(10, 10, 100, 50);   // ERROR! You're calling on the canvas, not the context
</script>
```

**What happens:** You get a JavaScript error: `c.fillRect is not a function`

**Correct:**

```html
<script>
  var c = document.getElementById("myCanvas");
  var ctx = c.getContext("2d");  // Get the drawing context first
  ctx.fillRect(10, 10, 100, 50); // Now draw on the context
</script>
```

**Why:** The `<canvas>` element itself has no drawing methods. Drawing methods belong to the **context** object, which you get by calling `getContext("2d")`.

---

### Mistake 2: Forgetting `ctx.stroke()` or `ctx.fill()`

**Wrong:**

```html
<script>
  var c = document.getElementById("myCanvas");
  var ctx = c.getContext("2d");
  ctx.beginPath();
  ctx.arc(95, 50, 40, 0, 2 * Math.PI);
  // Forgot to call stroke() or fill() — nothing appears!
</script>
```

**What happens:** The canvas appears blank. The path is defined but never rendered.

**Correct:**

```html
  ctx.beginPath();
  ctx.arc(95, 50, 40, 0, 2 * Math.PI);
  ctx.stroke(); // This line makes it actually appear
```

**Rule:** Paths (lines, arcs, shapes) are invisible until you call `stroke()` (for outlines) or `fill()` (for filled shapes).

---

### Mistake 3: Using Wrong Canvas Attribute Names

**Wrong:**

```html
<canvas id="myCanvas" width="200px" height="100px">
```

**What happens:** The `px` unit is ignored or misread. Canvas dimensions should be plain numbers.

**Correct:**

```html
<canvas id="myCanvas" width="200" height="100">
```

**Rule:** Canvas `width` and `height` attributes take plain numbers (pixels are assumed). Do not add `px`.

---

### Mistake 4: Placing `<script>` Before the Canvas Element

**Wrong:**

```html
<script>
  var c = document.getElementById("myCanvas"); // Runs before canvas exists!
  var ctx = c.getContext("2d");
</script>

<canvas id="myCanvas" width="200" height="100"></canvas>
```

**What happens:** `document.getElementById("myCanvas")` returns `null` because the canvas doesn't exist in the HTML yet when the script runs.

**Correct:**

```html
<canvas id="myCanvas" width="200" height="100"></canvas>

<script>
  // Now the canvas exists, so getElementById finds it
  var c = document.getElementById("myCanvas");
  var ctx = c.getContext("2d");
</script>
```

**Rule:** Always place your `<script>` tag **after** the `<canvas>` element in the HTML.

---

### Mistake 5: Mixing Up SVG Shape Attributes

**Wrong:**

```html
<svg>
  <circle x="50" y="50" r="40" fill="red" />  <!-- x and y are wrong for circles! -->
</svg>
```

**What happens:** The circle either doesn't appear or appears in the wrong place.

**Correct:**

```html
<svg>
  <circle cx="50" cy="50" r="40" fill="red" />  <!-- Use cx and cy for circles -->
</svg>
```

**Rule:** For `<circle>`, always use `cx` (centre-x) and `cy` (centre-y). For `<rect>`, use `x` and `y` (top-left corner).

| Element | Position Attributes |
|---------|---------------------|
| `<rect>` | `x`, `y` (top-left corner) |
| `<circle>` | `cx`, `cy` (centre point) |
| `<ellipse>` | `cx`, `cy` (centre point) |

---

### Mistake 6: Forgetting `<defs>` for SVG Gradients

**Wrong:**

```html
<svg>
  <linearGradient id="grad1">   <!-- Put directly in SVG without defs -->
    <stop offset="0%" stop-color="red" />
    <stop offset="100%" stop-color="blue" />
  </linearGradient>
  <rect fill="url(#grad1)" width="200" height="100" />
</svg>
```

**What may happen:** The gradient may not render correctly in all browsers.

**Correct:**

```html
<svg>
  <defs>
    <linearGradient id="grad1">
      <stop offset="0%" stop-color="red" />
      <stop offset="100%" stop-color="blue" />
    </linearGradient>
  </defs>
  <rect fill="url(#grad1)" width="200" height="100" />
</svg>
```

**Rule:** Always put SVG gradient definitions inside `<defs>...</defs>`.

---

## Reflection Questions

Think carefully about these before moving on:

1. **What is the main difference** between how Canvas and SVG store graphic information after drawing?

2. **Why does Canvas need JavaScript** to draw, while SVG does not (for basic shapes)?

3. **If you were building a map application** where the user can click on countries and each country lights up when clicked, would you use Canvas or SVG? Why?

4. **If you were building a fast-action video game** where 60 things move and update every second, would you use Canvas or SVG? Why?

5. **The SVG `<defs>` section** defines things without displaying them. Can you think of another situation in HTML where you define something without displaying it immediately? (Hint: think about the `<head>` section and `<style>` tags.)

6. **What does `2 * Math.PI` represent** in the Canvas `arc()` method? Why is `Math.PI` used instead of a plain number?

7. **In the SVG solar system mini project**, the Earth planet is an SVG `<circle>` element in the DOM. What does that mean practically — what things could you do to it that you couldn't easily do to a Canvas-drawn planet?

---

## Completion Checklist

Review this list before finishing the lesson:

- [ ] I understand what the `<canvas>` element is and what it does
- [ ] I know that Canvas requires JavaScript to draw — the element itself does nothing alone
- [ ] I understand the three-step Canvas drawing pattern: get element → get context → draw
- [ ] I can draw a line on Canvas using `moveTo()`, `lineTo()`, and `stroke()`
- [ ] I can draw a circle on Canvas using `beginPath()`, `arc()`, and `stroke()` or `fill()`
- [ ] I can draw text on Canvas using `fillText()` and `strokeText()`
- [ ] I can create linear and radial gradients on Canvas
- [ ] I know that Canvas can draw images using `drawImage()`
- [ ] I understand what SVG stands for and what "scalable" means
- [ ] I can create an SVG circle using `<circle cx cy r>`
- [ ] I can create an SVG rectangle using `<rect x y width height>`
- [ ] I can add rounded corners to SVG rectangles using `rx` and `ry`
- [ ] I can create an SVG polygon and know how `points` works
- [ ] I can define and use SVG gradients with `<defs>` and `<linearGradient>`
- [ ] I can add text inside SVG using the `<text>` element
- [ ] I understand the differences between Canvas and SVG (pixel-based vs object-based)
- [ ] I know which technology is better suited for games vs scalable diagrams
- [ ] I have completed all guided exercises
- [ ] I have built the Science Dashboard mini project
- [ ] I can identify and fix the 6 common beginner mistakes

---

## Lesson Summary

This lesson introduced you to two powerful HTML graphics technologies: **Canvas** and **SVG**.

**HTML Canvas** provides a blank rectangular area that you paint on using JavaScript commands. You get the canvas element, obtain its drawing context with `getContext("2d")`, then use methods like `fillRect()`, `arc()`, `lineTo()`, `fillText()`, and `createLinearGradient()` to draw shapes, lines, circles, text, and colour transitions. Once something is drawn on Canvas, the browser treats it as pixels and remembers nothing about it — making Canvas fast for animations and games, but less flexible for interactive individual shapes.

**HTML SVG** lets you describe graphics directly in your HTML using tags like `<circle>`, `<rect>`, `<polygon>`, `<ellipse>`, and `<text>`. Every SVG shape is a real object in the browser's DOM — it can be individually styled, animated, and made to respond to user events. SVG graphics are resolution-independent, meaning they look perfectly sharp at any zoom level, making SVG ideal for logos, icons, charts, and diagrams.

The two technologies are complementary: Canvas excels at fast, pixel-level drawing and game graphics; SVG excels at scalable, interactive, and accessible vector illustrations. Knowing when to reach for each one is an essential skill for web development.

---

## Quick Reference Tables

### Canvas Drawing Methods

| Method | What It Does |
|--------|-------------|
| `getContext("2d")` | Gets the 2D drawing tool |
| `fillRect(x, y, w, h)` | Draws a filled rectangle |
| `strokeRect(x, y, w, h)` | Draws a rectangle outline |
| `moveTo(x, y)` | Moves the "pen" without drawing |
| `lineTo(x, y)` | Draws a line to this point |
| `stroke()` | Renders lines/outlines |
| `fill()` | Fills a closed path with colour |
| `beginPath()` | Starts a new drawing path |
| `arc(x, y, r, start, end)` | Draws a circle or arc |
| `fillText(text, x, y)` | Draws filled text |
| `strokeText(text, x, y)` | Draws outlined text |
| `createLinearGradient(...)` | Creates a linear gradient |
| `createRadialGradient(...)` | Creates a radial gradient |
| `drawImage(img, x, y)` | Draws an image onto the canvas |

### SVG Shape Elements

| Element | What It Draws | Key Attributes |
|---------|--------------|----------------|
| `<circle>` | Circle | `cx`, `cy`, `r` |
| `<rect>` | Rectangle | `x`, `y`, `width`, `height`, `rx`, `ry` |
| `<ellipse>` | Oval | `cx`, `cy`, `rx`, `ry` |
| `<polygon>` | Many-sided shape | `points` |
| `<line>` | Straight line | `x1`, `y1`, `x2`, `y2` |
| `<text>` | Text | `x`, `y`, `font-size`, `fill` |

### Canvas vs SVG Decision Guide

| If you need... | Use... |
|----------------|--------|
| A game with fast graphics | Canvas |
| Save output as PNG/JPG | Canvas |
| Pixel-level image editing | Canvas |
| A scalable logo or icon | SVG |
| Clickable, interactive shapes | SVG |
| A chart with hover effects | SVG |
| Sharp graphics at any zoom | SVG |
| Many shapes updating per second | Canvas |

---

*End of Lesson 32 — You're ready for Lesson 33: HTML Media!*

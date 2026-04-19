---
render_with_liquid: false
title: "HTML5 Web APIs — Geolocation, Drag & Drop, Web Storage, Web Workers, and Server-Sent Events"
nav_order: 34
---

# Lesson 34 — HTML5 Web APIs: Supercharging Your Web Pages

---

## Lesson Introduction

You already know how to build web pages with HTML, style them with CSS, and add interaction with JavaScript. But did you know that browsers come with a set of **built-in superpowers** you can tap into — completely for free?

These superpowers are called **Web APIs**. In this lesson, you will learn what a Web API is, and then master five of the most important ones: Geolocation, Drag and Drop, Web Storage, Web Workers, and Server-Sent Events.

By the end of this lesson, you will be able to:
- Explain what a Web API is and why it matters
- Build a page that detects a user's location
- Create draggable elements that can be dropped into target zones
- Store data in the browser so it survives page refreshes
- Run background tasks without freezing the page
- Receive live updates from a server without reloading the page

---

## Prerequisite Concepts

Before diving in, let us quickly cover the ideas you need to understand this lesson.

### What is JavaScript?

JavaScript is the programming language of the web. It lets you make web pages respond to user actions — clicking a button, typing in a form, hovering over an image. If you have written a little JavaScript before (like `document.getElementById()` or `alert()`), you are ready for this lesson.

### What is an Event?

An **event** is something that happens in the browser — a click, a keypress, a page load, a timer firing. In JavaScript, you can "listen" for these events and run code when they happen.

### What is a Function?

A **function** is a named block of code you can run whenever you need it:

```javascript
function sayHello() {
  alert("Hello!");
}
// Call it like this:
sayHello();
```

**Output:** An alert box saying "Hello!"

### What is an Object?

An object is a container that holds related data and actions. For example, `navigator.geolocation` is an object — it holds everything you need to work with location data.

---

## Part 1 — What is a Web API?

### 1.1 The Big Idea

Let us start with a simple real-world analogy.

Imagine you work at a restaurant. You don't need to know how the kitchen prepares every dish — you just pick up the phone (the **interface**), say what you want, and the kitchen takes care of the rest.

A **Web API (Application Programming Interface)** works exactly the same way. It is a ready-made set of tools built into the browser that allows your JavaScript code to ask the browser to do complex things — like find the user's location, store data, or draw graphics — without you having to build that complex machinery yourself.

> **API** stands for **Application Programming Interface**. Think of it as a "remote control" for features built into the browser or operating system.

### 1.2 HTML5 Built-in APIs

All modern browsers come with a collection of built-in Web APIs. Here are the main HTML5 APIs:

| API | What It Does |
|-----|-------------|
| **Geolocation API** | Finds the user's current GPS location (latitude and longitude) |
| **Drag and Drop API** | Lets users grab elements and drag them to new positions |
| **Web Storage API** | Stores key/value data in the browser (better than cookies) |
| **Web Workers API** | Runs JavaScript in the background without freezing the page |
| **Server-Sent Events API** | Lets the server push live updates to the web page automatically |

### 1.3 Third-Party APIs

Beyond built-in APIs, there are also **third-party APIs** — services provided by other companies. Examples include the YouTube API (embed videos), the Twitter API (display tweets), and the Facebook API (show social data). You would download code from those services to use them. This lesson focuses entirely on built-in browser APIs.

### 1.4 Three Golden Rules When Using Any API

Before you write a single line of code using any Web API, always follow these three rules:

**Rule 1 — Check Browser Capability:** Not every browser supports every API. Always check whether the browser supports it before trying to use it.

**Rule 2 — Add Error Handling:** APIs can fail (user denies permission, network error, etc.). Always have a plan for when things go wrong.

**Rule 3 — Request User Permission:** Some APIs access sensitive data (like location). You must always ask the user for permission first. Never access private data silently.

---

## Part 2 — The HTML5 Geolocation API

### 2.1 What is Geolocation?

**Geolocation** means "finding where something is on Earth." The Geolocation API lets your web page ask the browser: "Where is this device right now?"

The browser will then use one or more of these methods to figure out the location:
- **GPS** (most accurate, used on phones and watches)
- **Wi-Fi triangulation** (uses nearby Wi-Fi networks)
- **Cell tower triangulation** (uses mobile network signals)
- **IP address lookup** (least accurate, used on desktops)

> **Important:** The Geolocation API only works on **HTTPS** (secure) connections, not on plain HTTP. This is a browser security requirement to protect user privacy.

### 2.2 How It Works — The Simple Version

Think of it like calling a taxi dispatcher:
1. You call the dispatcher (`navigator.geolocation`) and say "send me my position"
2. The dispatcher checks with the driver and sends back coordinates
3. If the driver is unavailable (error), you get an error message instead

### 2.3 Accessing the Geolocation API

The Geolocation API lives inside the `navigator` object in JavaScript. `navigator` is a built-in browser object that holds information about the browser itself.

```javascript
navigator.geolocation
```

If the browser supports Geolocation, this will be an object with methods. If not, it will be `undefined`.

### 2.4 Step 1 — Check Browser Support

Before using Geolocation, always check if it is supported:

```javascript
if (navigator.geolocation) {
  console.log("Geolocation is supported!");
} else {
  console.log("Geolocation is NOT supported in this browser.");
}
```

**Output (if supported):** `Geolocation is supported!`

### 2.5 Step 2 — Get the Current Position

The main method is `getCurrentPosition()`. It takes two arguments:
1. A **success function** — runs when location is found
2. An **error function** — runs when something goes wrong

```javascript
navigator.geolocation.getCurrentPosition(successFunction, errorFunction);
```

### 2.6 A Complete Geolocation Example

Let us put it all together:

```html
<!DOCTYPE html>
<html>
<body>

<p id="demo">Click the button to get your location.</p>
<button onclick="getLocation()">Get My Location</button>

<script>
const display = document.getElementById("demo");

function getLocation() {
  if (navigator.geolocation) {
    navigator.geolocation.getCurrentPosition(success, error);
  } else {
    display.innerHTML = "Geolocation is not supported by this browser.";
  }
}

function success(position) {
  display.innerHTML =
    "Latitude: " + position.coords.latitude +
    "<br>Longitude: " + position.coords.longitude;
}

function error() {
  display.innerHTML = "Sorry, unable to retrieve your location.";
}
</script>

</body>
</html>
```

**Expected Output (if user allows and has GPS):**
```
Latitude: 6.5244
Longitude: 3.3792
```
*(The numbers will match your actual location.)*

### 2.7 Line-by-Line Explanation

```javascript
const display = document.getElementById("demo");
```
This finds the paragraph element with `id="demo"` and stores it in the `display` variable so we can update it later.

```javascript
function getLocation() {
```
We define a function called `getLocation` that runs when the user clicks the button.

```javascript
  if (navigator.geolocation) {
```
This checks whether the `geolocation` object exists inside `navigator`. If it does, the browser supports Geolocation.

```javascript
    navigator.geolocation.getCurrentPosition(success, error);
```
This calls `getCurrentPosition()`. The browser will ask the user for permission to access their location. If they allow it, `success` is called. If anything goes wrong, `error` is called.

```javascript
function success(position) {
  display.innerHTML =
    "Latitude: " + position.coords.latitude +
    "<br>Longitude: " + position.coords.longitude;
}
```
The `success` function receives a `position` object automatically. This object has a `coords` property which contains `latitude`, `longitude`, `accuracy`, and more. We display the two most important ones.

### 2.8 What Data Does `getCurrentPosition()` Return?

The `position` object contains these properties:

| Property | Description | Always Returned? |
|---------|-------------|-----------------|
| `coords.latitude` | The latitude (north-south position) as a decimal | ✅ Yes |
| `coords.longitude` | The longitude (east-west position) as a decimal | ✅ Yes |
| `coords.accuracy` | How accurate the position is, in meters | ✅ Yes |
| `coords.altitude` | Height above sea level in metres | ⚠️ If available |
| `coords.altitudeAccuracy` | Accuracy of the altitude value | ⚠️ If available |
| `coords.heading` | Direction of travel in degrees (0 = North) | ⚠️ If available |
| `coords.speed` | Speed of travel in metres per second | ⚠️ If available |
| `timestamp` | When the position was determined | ⚠️ If available |

### 2.9 Better Error Handling

The error function can receive an `error` object that tells you *why* it failed. There are four possible error codes:

```javascript
function error(err) {
  switch(err.code) {
    case err.PERMISSION_DENIED:
      display.innerHTML = "User denied permission to access location.";
      break;
    case err.POSITION_UNAVAILABLE:
      display.innerHTML = "Location information is unavailable.";
      break;
    case err.TIMEOUT:
      display.innerHTML = "The request to get location timed out.";
      break;
    case err.UNKNOWN_ERROR:
      display.innerHTML = "An unknown error occurred.";
      break;
  }
}
```

> **Thinking Prompt:** What happens if the user is indoors with no GPS signal and weak Wi-Fi? Which error case might fire?

### 2.10 Watching the User Move — `watchPosition()`

If you want to keep tracking the user's position as they move (like a navigation app), use `watchPosition()` instead of `getCurrentPosition()`. It works the same way but keeps firing the success function every time the position changes.

```javascript
// Start watching
let watchID = navigator.geolocation.watchPosition(success, error);

// To stop watching:
navigator.geolocation.clearWatch(watchID);
```

The `watchID` is a number that identifies this specific watch. You pass it to `clearWatch()` when you want to stop.

### 2.11 Real-World Uses of Geolocation

- Delivery apps (show rider's live position on a map)
- Restaurant finders ("restaurants near me")
- Weather apps (get weather for the user's city automatically)
- Turn-by-turn navigation (Google Maps, Waze)
- Fitness trackers (map your running route)

---

## Part 3 — The HTML5 Drag and Drop API

### 3.1 What is Drag and Drop?

You already use drag and drop every day. When you move a file from your Downloads folder to your Desktop, you are dragging and dropping. When you rearrange apps on your phone's home screen — that is drag and drop too.

The HTML5 Drag and Drop API lets you build the same behaviour directly in web pages. Users can click (or touch) an element, hold it, drag it across the screen, and release it somewhere else.

### 3.2 The Three Key Players

Every drag and drop interaction involves three things:

1. **The draggable element** — the thing you pick up and move
2. **The drop zone** — the area where you can release it
3. **JavaScript event handlers** — the code that runs during each stage

### 3.3 The Drag and Drop Events

| Event | When It Fires | Attached To |
|-------|--------------|-------------|
| `ondragstart` | When the user starts dragging an element | The draggable element |
| `ondragover` | When a dragged element is moved over a drop target | The drop zone |
| `ondrop` | When the dragged element is released over a drop target | The drop zone |

### 3.4 Step 1 — Make an Element Draggable

To make any HTML element draggable, add the `draggable="true"` attribute:

```html
<img id="myImage" src="logo.gif" draggable="true">
```

or for a paragraph:

```html
<p id="myText" draggable="true">Drag me!</p>
```

By default, HTML elements are **not draggable**. You must explicitly set `draggable="true"`.

### 3.5 Step 2 — The `ondragstart` Handler

When dragging starts, you need to tell the browser **what data to carry** with the dragged element. You do this using `dataTransfer.setData()`:

```javascript
function dragstartHandler(event) {
  // Store the id of the element being dragged
  event.dataTransfer.setData("text", event.target.id);
}
```

Breaking this down:
- `event` — the drag event object, automatically passed in
- `event.dataTransfer` — a special object for passing data between the drag source and the drop target
- `setData("text", value)` — stores a piece of data with the key "text" and the value of the element's `id`
- `event.target.id` — the `id` attribute of the element being dragged

### 3.6 Step 3 — Allow Dropping with `ondragover`

By default, browsers **do not allow** dropping elements onto other elements. To allow it, you must prevent the default behaviour in `ondragover`:

```javascript
function dragoverHandler(event) {
  event.preventDefault();  // This is what allows the drop!
}
```

Without `event.preventDefault()` here, the `ondrop` event will never fire.

### 3.7 Step 4 — Handle the Drop with `ondrop`

When the user releases the dragged element over a valid drop target, `ondrop` fires. Here you grab the data and move the element:

```javascript
function dropHandler(event) {
  event.preventDefault();  // Prevent browser default (opening as link)

  // Retrieve the id we stored during dragstart
  const draggedId = event.dataTransfer.getData("text");

  // Move the dragged element into the drop zone
  event.target.appendChild(document.getElementById(draggedId));
}
```

Breaking this down:
- `event.dataTransfer.getData("text")` — retrieves the id we stored during `dragstart`
- `document.getElementById(draggedId)` — finds the dragged element in the DOM
- `event.target.appendChild(...)` — moves that element inside the drop zone

### 3.8 A Complete Drag and Drop Example

```html
<!DOCTYPE HTML>
<html>
<head>
<style>
  #dropZone {
    width: 200px;
    height: 100px;
    border: 3px dashed #555;
    background-color: #f9f9f9;
    padding: 10px;
  }
</style>
<script>
  function dragstartHandler(ev) {
    ev.dataTransfer.setData("text", ev.target.id);
  }

  function dragoverHandler(ev) {
    ev.preventDefault();
  }

  function dropHandler(ev) {
    ev.preventDefault();
    const data = ev.dataTransfer.getData("text");
    ev.target.appendChild(document.getElementById(data));
  }
</script>
</head>
<body>

<div id="dropZone"
     ondrop="dropHandler(event)"
     ondragover="dragoverHandler(event)">
  Drop here!
</div>

<br>

<img id="dragImage"
     src="https://www.w3schools.com/html/img_w3slogo.gif"
     draggable="true"
     ondragstart="dragstartHandler(event)"
     width="100"
     height="50">

</body>
</html>
```

**Expected behaviour:** The W3Schools logo image starts below the dashed box. When you drag it and drop it onto the dashed box, it moves inside the box permanently.

### 3.9 Drag and Drop Back and Forth

You can make two zones where an element can be moved between them in either direction. Just attach `ondragover` and `ondrop` handlers to **both** drop zones:

```html
<div id="zone1" ondrop="dropHandler(event)" ondragover="dragoverHandler(event)">
  <img id="myImg" draggable="true" ondragstart="dragstartHandler(event)" src="logo.gif">
</div>

<div id="zone2" ondrop="dropHandler(event)" ondragover="dragoverHandler(event)">
  <!-- Drop here to move the image -->
</div>
```

The exact same three JavaScript functions work for both zones — no changes needed!

### 3.10 Real-World Uses of Drag and Drop

- Kanban boards (Trello-style task management — drag cards between columns)
- File uploaders (drag files from desktop into a web browser upload zone)
- Image galleries (reorder photos)
- Shopping carts (drag products into the cart)
- Calendar apps (drag events to new time slots)

---

## Part 4 — The HTML5 Web Storage API

### 4.1 The Problem With Cookies

Before HTML5, if a web page needed to remember something about you (like your name or preferences), it used **cookies** — small pieces of text stored in your browser. But cookies have big problems:
- They are sent to the server on **every single request**, even when the server doesn't need them (slows down your page)
- They can only hold about **4KB** of data
- They are hard to work with in JavaScript

**Web Storage** solves all of these problems.

### 4.2 What is Web Storage?

The **Web Storage API** lets web pages store data directly in the user's browser as simple key-value pairs. It is faster, more secure, and can hold at least **5MB** of data — over 1000 times more than cookies.

Web Storage is also **per origin** — data stored by `mywebsite.com` can only be read by `mywebsite.com`. Other websites cannot access it.

### 4.3 Two Types of Web Storage

| Object | Where Data Lives | When Data Disappears |
|--------|-----------------|---------------------|
| `localStorage` | Browser storage | Never (until user clears browser data) |
| `sessionStorage` | Browser storage | When the current browser tab is closed |

Think of it this way:
- `localStorage` is like saving a note to a file — it persists forever
- `sessionStorage` is like writing on a whiteboard — it disappears when you leave

### 4.4 Check for Web Storage Support

```html
<script>
const output = document.getElementById("result");

if (typeof(Storage) !== "undefined") {
  output.innerHTML = "Great! Your browser supports Web Storage.";
} else {
  output.innerHTML = "Sorry, no Web Storage support.";
}
</script>
```

**Output (modern browser):** `Great! Your browser supports Web Storage.`

> **Why `typeof(Storage) !== "undefined"`?** We check the type of `Storage` rather than just `if (Storage)` because if `Storage` doesn't exist, accessing it directly might throw an error. `typeof` safely returns the string `"undefined"` without crashing.

### 4.5 The localStorage Object — Storing Data

`localStorage` has three key methods:

**`setItem(key, value)`** — saves a key-value pair:
```javascript
localStorage.setItem("username", "Chidi");
localStorage.setItem("theme", "dark");
```

**`getItem(key)`** — retrieves a value:
```javascript
let name = localStorage.getItem("username");
console.log(name);
```
**Output:** `Chidi`

**`removeItem(key)`** — deletes one item:
```javascript
localStorage.removeItem("theme");
```

### 4.6 A Full localStorage Example

```html
<!DOCTYPE html>
<html>
<body>

<div id="result"></div>

<script>
const output = document.getElementById("result");

if (typeof(Storage) !== "undefined") {
  // Store data
  localStorage.setItem("lastname", "Smith");
  localStorage.setItem("bgcolor", "lightblue");

  // Retrieve and display data
  output.innerHTML = "Last name: " + localStorage.getItem("lastname");
  output.style.backgroundColor = localStorage.getItem("bgcolor");

} else {
  output.innerHTML = "Sorry, no Web storage support!";
}
</script>

</body>
</html>
```

**Expected Output:**
- The text "Last name: Smith" appears inside a light-blue-coloured `div`

> **Note:** Open your browser's DevTools (F12) → Application tab → Local Storage to see the stored data visually!

> **Thinking Prompt:** What happens if you close the tab, reopen it, and run the `getItem("lastname")` line again? Does it still work? Try it!

### 4.7 Counting Clicks with localStorage

This example demonstrates that data in `localStorage` persists even after the page is refreshed:

```html
<!DOCTYPE html>
<html>
<body>

<p>You have clicked the button
   <strong id="count">0</strong> time(s).</p>
<button onclick="countClick()">Click Me</button>

<script>
// Restore previous count on page load
document.getElementById("count").innerHTML =
  localStorage.getItem("clickcount") || 0;

function countClick() {
  // Get current count (convert string to number with Number())
  let current = Number(localStorage.getItem("clickcount")) || 0;

  // Increase by 1 and save
  current = current + 1;
  localStorage.setItem("clickcount", current);

  // Update the display
  document.getElementById("count").innerHTML = current;
}
</script>

</body>
</html>
```

**Expected behaviour:** Each button click increases the counter. If you refresh the page, the counter continues from where it left off — because the data is stored in `localStorage`.

**Why `Number(...)`?** Everything stored in Web Storage is saved as a **string**. `localStorage.getItem("clickcount")` returns `"3"` (a string), not `3` (a number). Adding `"3" + 1` in JavaScript gives `"31"` (string concatenation), not `4` (addition). Wrapping with `Number()` converts `"3"` to `3` first.

### 4.8 The sessionStorage Object

`sessionStorage` works exactly like `localStorage` — same methods (`setItem`, `getItem`, `removeItem`) — but the data vanishes when the browser tab is closed.

```html
<script>
function countSessionClick() {
  if (sessionStorage.clickcount) {
    sessionStorage.clickcount = Number(sessionStorage.clickcount) + 1;
  } else {
    sessionStorage.clickcount = 1;
  }

  document.getElementById("result").innerHTML =
    "You clicked " + sessionStorage.clickcount + " time(s) this session!";
}
</script>
```

**Expected behaviour:** Click the button several times. The counter works just like localStorage. But close the tab and open the page again — the counter resets to 0!

### 4.9 Storing Complex Data (Objects)

Web Storage only stores strings. To store an object or array, convert it to JSON first:

```javascript
// Storing an object
let user = { name: "Amara", age: 25, city: "Lagos" };
localStorage.setItem("user", JSON.stringify(user));

// Retrieving the object
let storedUser = JSON.parse(localStorage.getItem("user"));
console.log(storedUser.name);
```

**Output:** `Amara`

- `JSON.stringify(user)` — converts the object to a string: `'{"name":"Amara","age":25,"city":"Lagos"}'`
- `JSON.parse(...)` — converts the string back to a proper JavaScript object

### 4.10 Clearing All Storage

```javascript
// Remove one item
localStorage.removeItem("lastname");

// Remove ALL items
localStorage.clear();
```

### 4.11 Real-World Uses of Web Storage

- Remember a user's dark mode/light mode preference
- Save a partially filled form so it does not disappear on refresh
- Store a user's reading progress in an article
- Cache data to reduce server requests
- Remember a shopping cart between page visits

---

## Part 5 — The HTML5 Web Workers API

### 5.1 The Problem — JavaScript is Single-Threaded

Here is something important to understand: by default, JavaScript runs on a **single thread**. This means it can only do **one thing at a time**. 

Imagine you are cooking and you also need to answer the phone. If cooking requires 100% of your attention, you cannot pick up the phone at all. The same problem happens in JavaScript — if your code is busy doing a heavy calculation, the entire web page freezes. Users cannot click buttons, scroll the page, or do anything until the calculation finishes.

A **Web Worker** solves this by letting you run JavaScript in a separate background thread — like hiring a second cook to handle the phone while you keep cooking.

### 5.2 What is a Web Worker?

A Web Worker is a JavaScript file that runs in the **background**, completely separate from your main page. While the worker is running, users can still interact normally with the page.

> **Analogy:** Think of the main page as a cashier serving customers. The Web Worker is a back-office employee doing heavy paperwork. They work independently without blocking the cashier.

**Web workers are useful for:**
- Large data calculations
- Image processing
- Sorting massive datasets
- Parsing large files

### 5.3 What Web Workers Cannot Access

Because workers run in a separate environment, they do **not** have access to:
- The `window` object (the browser's main global object)
- The `document` object (the HTML page's DOM)
- The `parent` object

Workers communicate with the main page only through **messages**.

### 5.4 How Workers Communicate — postMessage

Workers and the main page talk to each other using a simple messaging system:

- **Main page → Worker:** `worker.postMessage(data)`
- **Worker → Main page:** `postMessage(data)` (called from inside the worker file)
- **Main page listens to worker:** `worker.onmessage = function(event) { ... }`

### 5.5 Step 1 — Create the Worker File

Workers live in a separate `.js` file. Let us create `demo_workers.js`:

```javascript
// demo_workers.js
var i = 0;

function timedCount() {
  i = i + 1;
  postMessage(i);               // Send the current count back to the main page
  setTimeout("timedCount()", 500);  // Run again after 500 milliseconds
}

timedCount();   // Start counting
```

Line-by-line:
- `var i = 0;` — a counter variable, starts at 0
- `postMessage(i)` — sends the current value of `i` back to the main HTML page
- `setTimeout("timedCount()", 500)` — waits 500ms (half a second) then calls `timedCount` again
- `timedCount()` at the end — starts the whole process

### 5.6 Step 2 — Use the Worker in Your HTML Page

```javascript
let w;  // Will hold our worker object

function startWorker() {
  const output = document.getElementById("result");

  if (typeof(Worker) !== "undefined") {
    // Only create a new worker if one doesn't already exist
    if (typeof(w) == "undefined") {
      w = new Worker("demo_workers.js");   // Create the worker
    }

    // Listen for messages from the worker
    w.onmessage = function(event) {
      output.innerHTML = event.data;       // Display the count
    };

  } else {
    output.innerHTML = "Sorry, no Web Worker support in this browser.";
  }
}

function stopWorker() {
  w.terminate();    // Stop the worker immediately
  w = undefined;   // Reset so a new one can be created later
}
```

### 5.7 The Full Web Worker HTML Page

```html
<!DOCTYPE html>
<html>
<body>

<p>Count: <output id="result"></output></p>
<button onclick="startWorker()">Start Worker</button>
<button onclick="stopWorker()">Stop Worker</button>
<br><br>
<p>Try clicking and scrolling while the worker runs!</p>

<script>
let w;

function startWorker() {
  const output = document.getElementById("result");

  if (typeof(Worker) !== "undefined") {
    if (typeof(w) == "undefined") {
      w = new Worker("demo_workers.js");
    }
    w.onmessage = function(event) {
      output.innerHTML = event.data;
    };
  } else {
    output.innerHTML = "Sorry! No Web Worker support.";
  }
}

function stopWorker() {
  w.terminate();
  w = undefined;
}
</script>

</body>
</html>
```

**Expected behaviour:**
- Click "Start Worker" → the counter starts updating every half-second
- While counting, scroll the page, click other things — the page stays responsive
- Click "Stop Worker" → counting stops

> **Thinking Prompt:** What would happen to the page if we ran this counting loop in the main page's JavaScript instead of in a worker?

### 5.8 Browser Support Check

```javascript
if (typeof(Worker) !== "undefined") {
  // Web Workers are supported
} else {
  // No support — show a fallback message
}
```

### 5.9 Real-World Uses of Web Workers

- Spell-checking a document (run in background as user types)
- Encoding/decoding video files
- Processing large CSV files without freezing the interface
- Running machine learning predictions in the browser
- Compressing images before upload

---

## Part 6 — The HTML5 Server-Sent Events API

### 6.1 The Problem — Pages Don't Update Automatically

Normally, a web page only shows new information when **you** ask for it — by clicking a button or refreshing the page. But what about live stock prices, news headlines, football scores, or notifications? You want the page to update **automatically** when the server has new information.

Before Server-Sent Events, developers used messy workarounds like polling (asking the server every few seconds: "Anything new?"). This wastes bandwidth and creates unnecessary server load.

### 6.2 What are Server-Sent Events?

**Server-Sent Events (SSE)** allow a server to **push** (send) updates to a web page automatically whenever new data is available — without the page needing to ask.

> **Analogy:** Traditional requests are like sending a letter and waiting for a reply. SSE is like subscribing to a newspaper — the newspaper arrives at your door every morning without you having to ask.

**Key characteristic:** SSE is **one-way** — the server sends to the client. The client cannot send messages back through SSE (for two-way communication, use WebSockets instead).

### 6.3 The EventSource Object

The SSE API uses the built-in `EventSource` object. You create one and point it at a server-side script that sends event stream data:

```javascript
var source = new EventSource("demo_sse.php");
```

- `"demo_sse.php"` — the URL of a server-side script that generates the stream

### 6.4 Receiving Messages

You listen for messages using the `onmessage` event handler:

```javascript
source.onmessage = function(event) {
  document.getElementById("result").innerHTML += event.data + "<br>";
};
```

- `event.data` — contains the text the server sent
- `+=` — appends each new message to the previous ones (so you see a growing list of updates)

### 6.5 Complete Client-Side SSE Example

```html
<!DOCTYPE html>
<html>
<body>

<h1>Server Updates</h1>
<div id="result"></div>

<script>
const output = document.getElementById("result");

// Check browser support
if (typeof(EventSource) !== "undefined") {

  // Connect to the server-side script
  var source = new EventSource("demo_sse.php");

  // When a message arrives from the server, display it
  source.onmessage = function(event) {
    output.innerHTML += event.data + "<br>";
  };

} else {
  output.innerHTML = "Sorry, your browser does not support server-sent events.";
}
</script>

</body>
</html>
```

**Expected behaviour:** The page connects to `demo_sse.php`. Each time the server sends a new message, it appears in the div without any page reload.

### 6.6 Server-Side Code (PHP)

The server-side script must set the content type to `text/event-stream` and send data in a specific format:

```php
<?php
// demo_sse.php

// Tell the browser this is an event stream
header('Content-Type: text/event-stream');

// Prevent page caching
header('Cache-Control: no-cache');

// Get the current time
$time = date('r');

// Send the data — MUST start with "data: " and end with "\n\n"
echo "data: The server time is: {$time}\n\n";

// Flush output immediately to the browser
flush();
?>
```

Line-by-line:
- `header('Content-Type: text/event-stream')` — tells the browser to expect a streaming event feed
- `header('Cache-Control: no-cache')` — prevents the browser from caching the response
- `echo "data: ..."` — sends a message. The format MUST start with `data: ` and end with TWO newline characters (`\n\n`)
- `flush()` — forces PHP to immediately send the output to the browser rather than buffering it

### 6.7 Server-Side Code (ASP/VBScript)

```asp
<%
Response.ContentType = "text/event-stream"
Response.Expires = -1
Response.Write("data: The server time is: " & now())
Response.Flush()
%>
```

### 6.8 The EventSource Object Events

The `EventSource` object has three events you can listen to:

| Event | When It Fires |
|-------|--------------|
| `onopen` | When the connection to the server is successfully opened |
| `onmessage` | When a new message arrives from the server |
| `onerror` | When a connection error occurs |

```javascript
source.onopen = function() {
  console.log("Connected to server stream.");
};

source.onmessage = function(event) {
  console.log("Message received: " + event.data);
};

source.onerror = function() {
  console.log("Connection error occurred.");
};
```

### 6.9 SSE vs. Web Workers — What is the Difference?

| Feature | Web Workers | Server-Sent Events |
|---------|------------|-------------------|
| Who initiates? | The web page | The server |
| Where does processing happen? | In the browser (background thread) | On the server |
| Direction | Background task → main page | Server → browser |
| Use case | Heavy JavaScript tasks | Live data updates from server |

### 6.10 Real-World Uses of Server-Sent Events

- Live news feed updates
- Social media notification counters
- Live sports scores
- Stock market price tickers
- Server-side log monitoring dashboards
- Live auction bid updates

---

## Guided Practice Exercises

### Exercise 1 — Geolocation Display

**Objective:** Build a page that displays the user's latitude, longitude, and accuracy.

**Scenario:** You are building a weather app. The first step is to get the user's coordinates.

**Steps:**
1. Create an HTML page with a button labeled "Find My Location"
2. Create a paragraph with `id="locationInfo"`
3. Write a `getLocation()` function that calls `navigator.geolocation.getCurrentPosition()`
4. In the success function, display latitude, longitude, and `coords.accuracy` in the paragraph
5. Handle all four error cases

**Hint:** Access accuracy with `position.coords.accuracy`.

**Expected Output (if user allows):**
```
Latitude: 6.5244
Longitude: 3.3792
Accuracy: 20 metres
```

**Self-check Questions:**
- Did you check for browser support before calling `getCurrentPosition`?
- Did you handle the error cases?
- What unit is `coords.accuracy` in?

---

### Exercise 2 — Drag and Drop List Reorder

**Objective:** Create a list of 3 coloured `div` boxes that can be dragged and dropped into a target area.

**Steps:**
1. Create three coloured `div` elements (e.g., red, blue, green), each `draggable="true"`
2. Create a drop zone `div` with a dashed border
3. Wire up `ondragstart`, `ondragover`, and `ondrop`
4. When a box is dropped into the zone, it should move there

**What-if Challenge:** Can you modify the code so the boxes can also be dragged back out of the drop zone to their original position?

---

### Exercise 3 — Personal Notes App with localStorage

**Objective:** Build a simple note-saving app that persists notes even after the page is refreshed.

**Scenario:** A student wants to save quick study notes in the browser.

**Steps:**
1. Create an `<input>` field for the note title
2. Create a `<textarea>` for the note content
3. Create a "Save Note" button that stores both values in `localStorage`
4. On page load, automatically retrieve and display any previously saved note
5. Create a "Clear Note" button that removes the saved note

**Expected behaviour:** Type a note, click Save. Refresh the page. The note reappears automatically.

**Self-check Questions:**
- Why must you convert stored numbers back to a number type when doing arithmetic?
- What happens when you call `localStorage.clear()`?

---

### Exercise 4 — Temperature Converter Worker

**Objective:** Create a Web Worker that converts a temperature from Celsius to Fahrenheit.

**Worker file (`temp_worker.js`):**
```javascript
onmessage = function(event) {
  const celsius = event.data;
  const fahrenheit = (celsius * 9/5) + 32;
  postMessage(fahrenheit);
};
```

**Main page:**
1. Create an `<input>` for Celsius value
2. Create a button "Convert in Worker"
3. Create a paragraph to show the Fahrenheit result
4. Write JavaScript that creates a worker, sends the Celsius value to it, and displays the result

**Expected Output (input: 100):**
```
100°C = 212°F
```

---

## Mini Project — "Smart Dashboard" Using Multiple APIs

Let us combine everything we have learned into one project: a personal smart dashboard that uses Geolocation, Web Storage, and displays a simulated server update.

### Project Overview

The dashboard will:
- Display the user's coordinates (Geolocation)
- Let users save a personal display name to localStorage
- Show a simulated live clock update (mimicking Server-Sent Events behaviour using `setInterval`)

### Stage 1 — Setup the HTML Structure

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <title>My Smart Dashboard</title>
  <style>
    body { font-family: Arial, sans-serif; padding: 20px; max-width: 600px; }
    .card {
      border: 1px solid #ddd;
      border-radius: 8px;
      padding: 15px;
      margin: 15px 0;
      background: #f9f9f9;
    }
    h2 { color: #333; border-bottom: 2px solid #4CAF50; padding-bottom: 5px; }
    button {
      background: #4CAF50;
      color: white;
      border: none;
      padding: 8px 16px;
      border-radius: 4px;
      cursor: pointer;
    }
    input { padding: 6px; margin-right: 8px; border: 1px solid #ccc; border-radius: 4px; }
  </style>
</head>
<body>

  <h1>🌐 My Smart Dashboard</h1>

  <!-- Section 1: Personal Name (Web Storage) -->
  <div class="card">
    <h2>👤 My Profile</h2>
    <input type="text" id="nameInput" placeholder="Enter your name">
    <button onclick="saveName()">Save Name</button>
    <p>Welcome, <strong id="displayName">Guest</strong>!</p>
  </div>

  <!-- Section 2: My Location (Geolocation) -->
  <div class="card">
    <h2>📍 My Location</h2>
    <button onclick="getLocation()">Detect My Location</button>
    <p id="locationDisplay">Click the button to get your coordinates.</p>
  </div>

  <!-- Section 3: Live Updates (Simulated SSE) -->
  <div class="card">
    <h2>🕐 Live Server Time</h2>
    <button onclick="startUpdates()">Start Live Updates</button>
    <button onclick="stopUpdates()">Stop</button>
    <p id="liveTime">Not started yet.</p>
  </div>

</body>
</html>
```

### Stage 2 — Add the JavaScript

```html
<script>
// ============ WEB STORAGE SECTION ============

// On page load, restore saved name from localStorage
window.onload = function() {
  const savedName = localStorage.getItem("dashboardName");
  if (savedName) {
    document.getElementById("displayName").innerHTML = savedName;
    document.getElementById("nameInput").value = savedName;
  }
};

function saveName() {
  const name = document.getElementById("nameInput").value;
  if (name.trim() !== "") {
    localStorage.setItem("dashboardName", name);
    document.getElementById("displayName").innerHTML = name;
    alert("Name saved! It will still be here after you refresh the page.");
  } else {
    alert("Please enter a name first.");
  }
}


// ============ GEOLOCATION SECTION ============

function getLocation() {
  const display = document.getElementById("locationDisplay");

  if (navigator.geolocation) {
    display.innerHTML = "Detecting location...";
    navigator.geolocation.getCurrentPosition(showPosition, showError);
  } else {
    display.innerHTML = "Geolocation is not supported by this browser.";
  }
}

function showPosition(position) {
  document.getElementById("locationDisplay").innerHTML =
    "📍 Latitude: " + position.coords.latitude.toFixed(4) +
    "<br>📍 Longitude: " + position.coords.longitude.toFixed(4) +
    "<br>Accuracy: ±" + Math.round(position.coords.accuracy) + " metres";
}

function showError(error) {
  const display = document.getElementById("locationDisplay");
  switch(error.code) {
    case error.PERMISSION_DENIED:
      display.innerHTML = "❌ Location access was denied."; break;
    case error.POSITION_UNAVAILABLE:
      display.innerHTML = "❌ Location information unavailable."; break;
    case error.TIMEOUT:
      display.innerHTML = "❌ Location request timed out."; break;
    default:
      display.innerHTML = "❌ Unknown error occurred."; break;
  }
}


// ============ SIMULATED SERVER UPDATE SECTION ============

let updateInterval;

function startUpdates() {
  if (updateInterval) return;  // Don't start a second one

  updateInterval = setInterval(function() {
    const now = new Date();
    document.getElementById("liveTime").innerHTML =
      "🕐 Server time: " + now.toLocaleTimeString() +
      "<br>📅 Date: " + now.toLocaleDateString();
  }, 1000);  // Update every second
}

function stopUpdates() {
  clearInterval(updateInterval);
  updateInterval = undefined;
  document.getElementById("liveTime").innerHTML = "Updates stopped.";
}
</script>
```

### Stage 3 — Milestone Check

After building this, you should see:
- A text input where you can type your name, click Save, and have it persist after page refresh
- A location button that shows your coordinates when clicked
- A live-updating time display that can be started and stopped

### Reflection Questions

1. After saving your name and refreshing the page, where does the `window.onload` function get the name from?
2. Why does `.toFixed(4)` in `showPosition` display the coordinates with only 4 decimal places?
3. What is the difference between `setInterval` (which we used here) and a real SSE connection?
4. If you opened a second browser tab for this page, would it see the same stored name? Why?

### Optional Enhancements

- Add a "Clear My Data" button that calls `localStorage.clear()` and resets the dashboard
- Add a drag-and-drop feature that lets users rearrange the three cards
- Connect to a real server-sent events endpoint instead of the simulated timer

---

## Common Beginner Mistakes

### Mistake 1 — Forgetting to Check Browser Support

**Wrong:**
```javascript
navigator.geolocation.getCurrentPosition(success, error);
// If geolocation isn't supported, this crashes!
```

**Correct:**
```javascript
if (navigator.geolocation) {
  navigator.geolocation.getCurrentPosition(success, error);
} else {
  console.log("Geolocation not supported.");
}
```

---

### Mistake 2 — Forgetting `event.preventDefault()` in `ondragover`

**Wrong:**
```javascript
function dragoverHandler(ev) {
  // Nothing here!
}
// Result: The ondrop event NEVER fires — the drop is blocked.
```

**Correct:**
```javascript
function dragoverHandler(ev) {
  ev.preventDefault();  // This is what enables dropping!
}
```

---

### Mistake 3 — Doing Math on localStorage Strings

**Wrong:**
```javascript
localStorage.setItem("count", 1);
let c = localStorage.getItem("count");
c = c + 1;  // Result: "11" (string concatenation!) not 2
```

**Correct:**
```javascript
let c = Number(localStorage.getItem("count")) || 0;
c = c + 1;  // Result: 2 (arithmetic)
localStorage.setItem("count", c);
```

---

### Mistake 4 — Trying to Access the DOM From a Web Worker

**Wrong (inside worker file):**
```javascript
document.getElementById("result").innerHTML = "done";
// ERROR: document is not defined inside a worker
```

**Correct:**
```javascript
// Workers communicate via messages, not DOM access
postMessage("done");  // Send message to main page
// Main page handles DOM updates in its onmessage handler
```

---

### Mistake 5 — Using HTTP Instead of HTTPS for Geolocation

**Wrong:** Testing Geolocation on `http://mysite.com` — the browser will block it.

**Correct:** Test on `https://mysite.com`, or test locally using `localhost` (which browsers treat as secure).

---

### Mistake 6 — Starting Two Web Workers by Accident

**Wrong:**
```javascript
function startWorker() {
  w = new Worker("worker.js");  // Creates a new worker every call!
}
```

**Correct:**
```javascript
function startWorker() {
  if (typeof(w) == "undefined") {  // Only create if none exists
    w = new Worker("worker.js");
  }
}
```

---

### Mistake 7 — Forgetting the Double Newline in SSE Data

**Wrong (server-side PHP):**
```php
echo "data: Hello\n";  // Single newline — browser waits for more
```

**Correct:**
```php
echo "data: Hello\n\n";  // Double newline — signals end of one event
```

---

## Reflection Questions

1. What is the difference between `localStorage` and `sessionStorage`? When would you choose one over the other?

2. In the Drag and Drop API, why must `event.preventDefault()` be called in the `ondragover` handler, not just in the `ondrop` handler?

3. Imagine a social media app like Twitter. Which API would be most appropriate for automatically loading new tweets as they are posted — Web Workers or Server-Sent Events? Explain your reasoning.

4. A friend says "I don't need Web Workers because my computer is fast." What would you tell them about why Web Workers are still important?

5. What happens to `sessionStorage` data when a user:
   a) Refreshes the page (F5)?
   b) Closes the tab?
   c) Closes the entire browser?

6. Why does the Geolocation API require HTTPS? What privacy risk would it pose without it?

7. In the Web Workers API, why can't a worker access `document` or `window`?

---

## Completion Checklist

Before moving on, confirm that you can:

- [ ] Explain what a Web API is and give at least two examples
- [ ] State the three golden rules when using any Web API
- [ ] Write code that checks for Geolocation support and gets the user's coordinates
- [ ] Handle all four Geolocation error cases by name
- [ ] Use `watchPosition()` to track continuous location updates
- [ ] Make an HTML element draggable using the `draggable` attribute
- [ ] Implement the three drag-and-drop handlers (`ondragstart`, `ondragover`, `ondrop`)
- [ ] Explain why `event.preventDefault()` is required in both `ondragover` and `ondrop`
- [ ] Use `localStorage.setItem()` and `localStorage.getItem()` to save and retrieve data
- [ ] Explain the difference between `localStorage` and `sessionStorage`
- [ ] Convert stored strings back to numbers before doing arithmetic
- [ ] Create a Web Worker `.js` file with `postMessage()` and `timedCount()`
- [ ] Instantiate a Worker, attach `onmessage`, and terminate it with `terminate()`
- [ ] Explain why Web Workers cannot access `document` or `window`
- [ ] Create an `EventSource` object pointing to a server-side script
- [ ] Handle `onmessage`, `onopen`, and `onerror` events from SSE
- [ ] Write a PHP SSE endpoint with the correct `Content-Type` header and `data: ` format
- [ ] Distinguish between SSE (server → client) and Web Workers (background thread)

---

## Lesson Summary

In this lesson, you explored the powerful world of HTML5 Web APIs — built-in browser tools that supercharge your web pages with real-world capabilities.

**Web APIs** are ready-made interfaces built into every modern browser. They let your JavaScript code access complex features without building them from scratch. You learned the three golden rules: always check browser support, add error handling, and request user permission for sensitive data.

The **Geolocation API** (`navigator.geolocation`) finds the user's physical location using GPS, Wi-Fi, or cell towers. `getCurrentPosition()` retrieves the location once, while `watchPosition()` tracks it continuously. It only works over HTTPS.

The **Drag and Drop API** enables users to pick up HTML elements and move them to drop zones. It requires three coordinated event handlers: `ondragstart` (marks what to drag), `ondragover` (enables dropping), and `ondrop` (performs the move). `dataTransfer.setData()` and `getData()` carry data between the drag source and drop target.

The **Web Storage API** provides `localStorage` (permanent storage) and `sessionStorage` (tab-session storage) as superior replacements for cookies. Both use the same `setItem()`, `getItem()`, and `removeItem()` methods. Always remember that stored values are strings — use `Number()` before arithmetic.

The **Web Workers API** runs JavaScript in a background thread, keeping the page responsive during heavy computations. Workers live in separate `.js` files, communicate via `postMessage()` and `onmessage`, and cannot access the DOM. Use `terminate()` to stop them.

The **Server-Sent Events API** lets servers push live updates to web pages using an `EventSource` connection. The server sends data as `text/event-stream` content with lines starting with `data:`. It is perfect for live news feeds, sports scores, stock prices, and notifications.

Together, these APIs are the foundation of dynamic, interactive, and intelligent modern web applications.

---

*Sources: W3Schools HTML5 Web APIs Tutorial (https://www.w3schools.com/html/)*

---
render_with_liquid: false
title: "HTML Colors — Named Colors, RGB, HEX, and HSL"
nav_order: 11
---

# Lesson 11 — HTML Colors: Named Colors, RGB, HEX, and HSL

---

## Lesson Introduction

Have you ever wondered how websites get their beautiful blues, warm reds, cool greens, and everything in between? Color is one of the most powerful tools in web design. It guides the reader's eye, creates emotions, and makes a website feel professional and alive.

In this lesson, you will learn **every single way** HTML lets you define a color. There are five main methods, and by the end of this lesson, you will understand all of them deeply:

1. **Color Names** — simple English words like `red` or `Tomato`
2. **RGB** — mixing Red, Green, and Blue light values
3. **RGBA** — RGB with added transparency control
4. **HEX** — a compact code using letters and numbers
5. **HSL** — describing color by Hue, Saturation, and Lightness
6. **HSLA** — HSL with added transparency control

You do not need any prior knowledge beyond what was covered in earlier lessons (HTML elements and the `style` attribute). Everything will be taught step by step from scratch.

---

## Prerequisite Concepts

Before we begin, let's quickly confirm you understand these two ideas from earlier lessons:

### What is the `style` attribute?

The `style` attribute is how you apply visual formatting directly to an HTML element. It goes inside the opening tag of any element, like this:

```html
<p style="color:red;">This text is red.</p>
```

- `style` — the attribute name
- `color:red;` — a CSS **property** (`color`) set to a **value** (`red`)
- The semicolon `;` ends each property-value pair

### What is a CSS property?

A **CSS property** is an instruction that tells the browser how to display something. Common color-related properties include:

| Property | What it Controls |
|---|---|
| `color` | The color of text |
| `background-color` | The background color of an element |
| `border` | The border around an element |

You already know how to use these! In this lesson, you will learn all the different **values** you can give them to produce any color you want.

---

## Part 1 — Color Names

### What Are Color Names?

The simplest way to add color in HTML is to use a **color name** — a plain English word that the browser already understands.

**Why do color names exist?** Because when the web was first built, developers wanted a quick, human-readable way to specify common colors without needing to memorize numbers. So a list of standard names was created.

> **Key Fact:** HTML supports **140 standard color names**. These are names every major browser recognizes automatically.

Some examples of color names:

| Color Name | What Color It Produces |
|---|---|
| `Red` | Bright red |
| `Blue` | Bright blue |
| `Green` | Medium green |
| `Tomato` | A reddish-orange, like a tomato |
| `DodgerBlue` | A vivid sky blue |
| `MediumSeaGreen` | A calm, medium green |
| `SlateBlue` | A blue-purple |
| `Violet` | A bright purple-pink |
| `LightGray` | A very light grey |
| `Orange` | Bright orange |

Color names are **not case-sensitive**, meaning `Red`, `red`, and `RED` all work the same way. However, using proper capitalization (like `DodgerBlue`) makes your code easier to read.

---

### Example 1 — Applying a Color Name as a Background

**Scenario:** You want to give a heading a blue background.

```html
<h1 style="background-color:DodgerBlue;">Hello World</h1>
```

**Expected Output:** A heading that displays the text "Hello World" with a vivid blue background behind it.

**Line-by-line explanation:**
- `<h1` — opens a level-1 heading tag
- `style=` — starts the style attribute
- `"background-color:DodgerBlue;"` — sets the background color to the named color "DodgerBlue"
- `>Hello World</h1>` — the text content and closing tag

---

### Example 2 — Applying a Color Name as Text Color

**Scenario:** You want your paragraph text to appear in a tomato-red color.

```html
<p style="color:Tomato;">This paragraph has tomato-red text.</p>
```

**Expected Output:** The paragraph text appears in a reddish-orange color.

---

### Example 3 — Multiple Elements with Different Color Names

```html
<h1 style="color:Tomato;">Hello World</h1>
<p style="color:DodgerBlue;">This is a blue paragraph.</p>
<p style="color:MediumSeaGreen;">This is a green paragraph.</p>
```

**Expected Output:**
- The heading displays in tomato-red
- First paragraph displays in vivid blue
- Second paragraph displays in medium sea-green

---

### Example 4 — Adding a Colored Border

Borders can also receive color names. The `border` property takes three values: thickness, style, and color.

```html
<h1 style="border:2px solid Tomato;">Hello World</h1>
<h1 style="border:2px solid DodgerBlue;">Hello World</h1>
<h1 style="border:2px solid Violet;">Hello World</h1>
```

**Line-by-line explanation:**
- `border:` — the CSS property for borders
- `2px` — the border is 2 pixels thick
- `solid` — the border is a solid line (not dashed or dotted)
- `Tomato` / `DodgerBlue` / `Violet` — the color of the border

**Expected Output:** Three headings, each with a 2-pixel solid border, colored red, blue, and purple respectively.

> **Thinking Prompt:** What happens if you change `solid` to `dashed`? Try it and observe the difference!

---

### Where Are Color Names Used in the Real World?

- **Quick prototyping:** Developers use color names when building rough drafts of a website because they are fast to type.
- **Learning and teaching:** Color names make code examples readable to beginners.
- **Simple projects:** A personal blog or hobby site might use color names throughout.

**Limitation of color names:** There are only 140 of them. If you want a very specific shade — like a particular pink from your company's brand guide — a color name may not exist. That's where RGB, HEX, and HSL come in.

---

## Part 2 — RGB Color Values

### What is RGB?

**RGB** stands for **Red, Green, Blue**. It is a method of describing color by specifying how much of each of three primary light colors to mix together.

**The real-world analogy:** Imagine you have three spotlights pointing at a wall — one red, one green, one blue. By turning each spotlight's brightness up or down, you can create millions of different colors on the wall. RGB works exactly the same way.

The format is:

```
rgb(red, green, blue)
```

Each of the three values is a number from **0 to 255**:
- `0` means that color is completely OFF (none of it)
- `255` means that color is at its MAXIMUM brightness

> **Why 0–255?** Because computers store each color value in 8 binary bits, and 2⁸ = 256 possible values (0 through 255). This is a fundamental fact of how digital color works in computing and photography.

### How Many Colors Can RGB Make?

256 × 256 × 256 = **16,777,216 possible colors!** That is over 16 million unique colors — far more than the 140 color names.

---

### Understanding RGB Through Examples

#### Pure Colors

| Color | RGB Value | Why? |
|---|---|---|
| Red | `rgb(255, 0, 0)` | Red is MAX, Green and Blue are OFF |
| Green | `rgb(0, 255, 0)` | Green is MAX, Red and Blue are OFF |
| Blue | `rgb(0, 0, 255)` | Blue is MAX, Red and Green are OFF |
| Black | `rgb(0, 0, 0)` | ALL channels OFF = no light = black |
| White | `rgb(255, 255, 255)` | ALL channels MAX = all light = white |

> **Why does mixing all three lights at max give white?** Think of sunlight — it contains all colors of the rainbow combined. When all three light colors are at full power, the result is white light.

> **Why does having all three at zero give black?** Because there is no light at all — complete darkness looks black.

---

### Example 5 — Basic RGB Colors

```html
<h1 style="background-color:rgb(255, 0, 0);">Pure Red</h1>
<h1 style="background-color:rgb(0, 0, 255);">Pure Blue</h1>
<h1 style="background-color:rgb(60, 179, 113);">Medium Sea Green</h1>
<h1 style="background-color:rgb(238, 130, 238);">Violet</h1>
<h1 style="background-color:rgb(255, 165, 0);">Orange</h1>
<h1 style="background-color:rgb(106, 90, 205);">Slate Blue</h1>
```

**Expected Output:** Six headings, each with a different background color.

**Let's decode `rgb(60, 179, 113)`:**
- Red = 60 (a small amount of red)
- Green = 179 (a medium-large amount of green)
- Blue = 113 (a medium amount of blue)
- The result is a soft sea-green — because green dominates, but red and blue soften and cool it.

> **Thinking Prompt:** What happens if you change `rgb(255, 0, 0)` to `rgb(128, 0, 0)`? The red will be darker, like maroon. The lower the number, the darker/dimmer that channel.

---

### Shades of Gray with RGB

A special and very useful trick: **any time all three RGB values are equal**, the result is a shade of gray.

| RGB Value | Result |
|---|---|
| `rgb(0, 0, 0)` | Black |
| `rgb(60, 60, 60)` | Very dark gray |
| `rgb(128, 128, 128)` | Medium gray |
| `rgb(200, 200, 200)` | Light gray |
| `rgb(240, 240, 240)` | Very light gray |
| `rgb(255, 255, 255)` | White |

```html
<p style="background-color:rgb(60, 60, 60);">Dark Gray</p>
<p style="background-color:rgb(140, 140, 140);">Medium Gray</p>
<p style="background-color:rgb(220, 220, 220);">Light Gray</p>
```

**Expected Output:** Three paragraphs with progressively lighter gray backgrounds.

> **Why does equal R, G, B always give gray?** Because gray is what you see when red, green, and blue light are balanced equally — none of the three stands out, so there is no hue, just brightness.

---

## Part 3 — RGBA Color Values (RGB + Transparency)

### What is RGBA?

**RGBA** is RGB with an extra value called **Alpha**, which controls how transparent (see-through) the color is.

The format is:

```
rgba(red, green, blue, alpha)
```

- The first three values are the same as RGB: numbers from 0–255.
- The **alpha** value is a decimal number from **0.0** to **1.0**:
  - `0.0` = completely transparent (invisible)
  - `0.5` = 50% transparent (half see-through)
  - `1.0` = completely solid (no transparency)

**The real-world analogy:** Imagine placing a piece of colored glass in front of a white wall. The transparency of the glass determines how much you can see through it. Alpha works the same way.

---

### Example 6 — RGBA Transparency Scale

```html
<p style="background-color:rgba(255, 99, 71, 0);">Alpha = 0 (invisible)</p>
<p style="background-color:rgba(255, 99, 71, 0.2);">Alpha = 0.2 (very faint)</p>
<p style="background-color:rgba(255, 99, 71, 0.4);">Alpha = 0.4 (light)</p>
<p style="background-color:rgba(255, 99, 71, 0.6);">Alpha = 0.6 (medium)</p>
<p style="background-color:rgba(255, 99, 71, 0.8);">Alpha = 0.8 (mostly solid)</p>
<p style="background-color:rgba(255, 99, 71, 1);">Alpha = 1 (fully solid)</p>
```

**Expected Output:** Six paragraphs using the same tomato-red color, but each one progressively more visible as the alpha increases from 0 to 1.

**Breaking down `rgba(255, 99, 71, 0.4)`:**
- `255` — red is at maximum
- `99` — a little bit of green
- `71` — a little bit of blue
- `0.4` — the color is 40% solid and 60% transparent

---

### When is RGBA Used in Real Projects?

- **Overlay effects:** A semi-transparent dark overlay placed over an image to make white text readable
- **Hover effects:** Buttons that become slightly transparent when you hover your mouse over them
- **Design layers:** Multiple colored elements stacked on top of each other with partial transparency for depth effects

---

## Part 4 — HEX Color Values

### What is a HEX Color?

A **HEX color** (short for **hexadecimal**) is another way to write an RGB color — but using a different number system. Instead of writing `rgb(255, 0, 0)`, you write `#ff0000`. They produce the exact same color.

The format is:

```
#rrggbb
```

Where:
- `#` — the hash symbol marks the start of a hex color
- `rr` — two characters for the Red value
- `gg` — two characters for the Green value
- `bb` — two characters for the Blue value

---

### Understanding Hexadecimal Numbers

This is the part most beginners find confusing, so let's go slowly.

**Normal counting (decimal) uses digits: 0, 1, 2, 3, 4, 5, 6, 7, 8, 9**
- After 9, you go to 10, 11, 12... etc.

**Hexadecimal counting uses: 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, a, b, c, d, e, f**
- After 9, instead of going to "10", hexadecimal uses letters: a=10, b=11, c=12, d=13, e=14, f=15
- So in hex, after `f`, you go to `10` (which equals 16 in decimal)

In HEX colors, each pair of characters (`rr`, `gg`, `bb`) can go from `00` to `ff`:
- `00` in hex = `0` in decimal (minimum, no color)
- `ff` in hex = `255` in decimal (maximum, full color)

| HEX Pair | Decimal Equivalent | Meaning |
|---|---|---|
| `00` | 0 | None of this color |
| `80` | 128 | Half of this color |
| `ff` | 255 | Maximum of this color |

**Important:** HEX colors are NOT case sensitive. `#FF0000` and `#ff0000` produce the same red.

---

### Example 7 — Basic HEX Colors

```html
<h1 style="background-color:#ff0000;">Red (#ff0000)</h1>
<h1 style="background-color:#0000ff;">Blue (#0000ff)</h1>
<h1 style="background-color:#3cb371;">Green (#3cb371)</h1>
<h1 style="background-color:#ee82ee;">Violet (#ee82ee)</h1>
<h1 style="background-color:#ffa500;">Orange (#ffa500)</h1>
<h1 style="background-color:#6a5acd;">Slate Blue (#6a5acd)</h1>
```

**Expected Output:** Six headings with different background colors, identical to the RGB examples from Part 2 — because HEX and RGB describe the same thing.

**Decoding `#3cb371`:**
- `3c` = Red channel = 60 in decimal
- `b3` = Green channel = 179 in decimal
- `71` = Blue channel = 113 in decimal
- This is the same as `rgb(60, 179, 113)` — Medium Sea Green!

---

### Shades of Gray with HEX

Just like with RGB, equal values for red, green, and blue produce gray:

```html
<p style="background-color:#404040;">Dark Gray</p>
<p style="background-color:#686868;">Medium-Dark Gray</p>
<p style="background-color:#a0a0a0;">Medium Gray</p>
<p style="background-color:#bebebe;">Light-Medium Gray</p>
<p style="background-color:#dcdcdc;">Light Gray</p>
<p style="background-color:#f8f8f8;">Very Light Gray</p>
```

**Expected Output:** Six paragraphs progressing from dark gray to nearly white.

Note that `#404040` has `40` repeated three times — equal R, G, B = gray.

---

### HEX vs RGB — Which Should You Use?

Both produce the exact same colors. The difference is purely in format:

| Feature | RGB | HEX |
|---|---|---|
| Readability | Easier for beginners | Compact and professional |
| Used in design tools | Often | Almost always |
| Copy-paste from image editors | Rarely | Very common |
| Real-world usage | Common in CSS | Extremely common |

> **Real-world tip:** When a graphic designer hands you a brand's color palette, the colors are almost always given as HEX codes (like `#2d6cdf` for a company blue). Knowing how to read and use HEX codes is essential for real web work.

---

## Part 5 — HSL Color Values

### What is HSL?

**HSL** stands for **Hue, Saturation, Lightness**. It is a completely different way of thinking about color — one that is much more natural for human beings.

Think about how a painter would describe a color: "It's a dark, muted blue." A painter would never say "it's 0 red, 0 green, 200 blue." HSL uses terms that humans naturally understand.

The format is:

```
hsl(hue, saturation, lightness)
```

Let's learn each part separately.

---

### Understanding Hue

**Hue** is the actual color — the position on the rainbow spectrum. It is measured as a degree on a color wheel from **0 to 360**.

Think of a clock face, but instead of time, it shows colors:

| Degree | Color |
|---|---|
| 0° | Red |
| 30° | Orange |
| 60° | Yellow |
| 120° | Green |
| 180° | Cyan (blue-green) |
| 240° | Blue |
| 300° | Magenta (pink-purple) |
| 360° | Red again (full circle) |

```html
<!-- Red: Hue = 0 -->
<p style="background-color:hsl(0, 100%, 50%);">Red</p>

<!-- Green: Hue = 120 -->
<p style="background-color:hsl(120, 100%, 50%);">Green</p>

<!-- Blue: Hue = 240 -->
<p style="background-color:hsl(240, 100%, 50%);">Blue</p>
```

**Expected Output:** Three paragraphs — red, green, and blue — created just by changing the hue value.

---

### Understanding Saturation

**Saturation** controls how **vivid or washed out** a color appears. It is expressed as a percentage from **0% to 100%**.

Think of saturation like a color slider:
- **100% saturation** = the color at its most vivid and pure
- **50% saturation** = the color is faded, mixed with gray
- **0% saturation** = the color has completely faded to gray

```html
<p style="background-color:hsl(0, 100%, 50%);">100% - Full Color Red</p>
<p style="background-color:hsl(0, 80%, 50%);">80% - Slightly Muted</p>
<p style="background-color:hsl(0, 60%, 50%);">60% - More Muted</p>
<p style="background-color:hsl(0, 40%, 50%);">40% - Quite Muted</p>
<p style="background-color:hsl(0, 20%, 50%);">20% - Very Muted</p>
<p style="background-color:hsl(0, 0%, 50%);">0% - Pure Gray</p>
```

**Expected Output:** Six paragraphs, all using hue 0 (red), but each progressively more washed out until the last one is pure gray.

> **Thinking Prompt:** Why does 0% saturation produce gray, regardless of the hue? Because saturation is what makes a color look like a color. Remove all saturation and you remove the color entirely — leaving only the lightness value, which produces gray.

---

### Understanding Lightness

**Lightness** controls how **dark or bright** a color appears. It is expressed as a percentage from **0% to 100%**.

Think of it like a light dimmer switch:
- **0% lightness** = completely black (no light)
- **50% lightness** = the color at its normal, natural brightness
- **100% lightness** = completely white (blinding light)

```html
<p style="background-color:hsl(0, 100%, 0%);">0% - Black</p>
<p style="background-color:hsl(0, 100%, 25%);">25% - Very Dark Red</p>
<p style="background-color:hsl(0, 100%, 50%);">50% - Normal Red</p>
<p style="background-color:hsl(0, 100%, 75%);">75% - Light Pink-Red</p>
<p style="background-color:hsl(0, 100%, 90%);">90% - Very Pale Pink</p>
<p style="background-color:hsl(0, 100%, 100%);">100% - White</p>
```

**Expected Output:** Six paragraphs showing the same hue (red) going from black at 0% to white at 100%.

---

### Example 8 — Various HSL Colors

```html
<h1 style="background-color:hsl(0, 100%, 50%);">Red</h1>
<h1 style="background-color:hsl(240, 100%, 50%);">Blue</h1>
<h1 style="background-color:hsl(147, 50%, 47%);">Green (muted)</h1>
<h1 style="background-color:hsl(300, 76%, 72%);">Pink-Purple</h1>
<h1 style="background-color:hsl(39, 100%, 50%);">Orange</h1>
<h1 style="background-color:hsl(248, 53%, 58%);">Slate Blue</h1>
```

**Expected Output:** Six colorful headings.

---

### Shades of Gray with HSL

To make any shade of gray in HSL, simply set hue to **0** and saturation to **0%**, then adjust lightness:

```html
<p style="background-color:hsl(0, 0%, 20%);">Very Dark Gray</p>
<p style="background-color:hsl(0, 0%, 40%);">Dark Gray</p>
<p style="background-color:hsl(0, 0%, 60%);">Medium Gray</p>
<p style="background-color:hsl(0, 0%, 80%);">Light Gray</p>
<p style="background-color:hsl(0, 0%, 90%);">Very Light Gray</p>
```

**Expected Output:** Five paragraphs with progressively lighter gray backgrounds.

---

### Why is HSL Useful?

HSL is especially popular with **designers** because it maps closely to how humans perceive and describe color:
- Want a darker version of a color? Just reduce the lightness.
- Want a more muted version? Just reduce the saturation.
- Want a slightly different hue? Just shift the hue value.

This is far more intuitive than adjusting three separate RGB channels.

> **Real-world use:** HSL is widely used in design systems and CSS frameworks where designers need to programmatically create color variations (like a "dark mode" version of every color on a website).

---

## Part 6 — HSLA Color Values (HSL + Transparency)

### What is HSLA?

Just like RGBA adds transparency to RGB, **HSLA** adds an **Alpha channel** to HSL. The alpha value controls transparency from `0.0` (invisible) to `1.0` (fully solid).

The format is:

```
hsla(hue, saturation, lightness, alpha)
```

---

### Example 9 — HSLA Transparency Scale

```html
<p style="background-color:hsla(9, 100%, 64%, 0);">Alpha = 0 (invisible)</p>
<p style="background-color:hsla(9, 100%, 64%, 0.2);">Alpha = 0.2 (very faint)</p>
<p style="background-color:hsla(9, 100%, 64%, 0.4);">Alpha = 0.4</p>
<p style="background-color:hsla(9, 100%, 64%, 0.6);">Alpha = 0.6</p>
<p style="background-color:hsla(9, 100%, 64%, 0.8);">Alpha = 0.8</p>
<p style="background-color:hsla(9, 100%, 64%, 1);">Alpha = 1 (fully solid)</p>
```

**Expected Output:** Six paragraphs using the same warm orange-red color (hue 9°), but each progressively more visible as alpha increases from 0 to 1.

---

## Part 7 — Quick Reference: All Color Systems

Here is a complete summary table of all the color systems you have learned:

| Format | Example | Transparency? | Use Case |
|---|---|---|---|
| Color Name | `Tomato` | No | Quick, simple projects |
| `rgb()` | `rgb(255, 99, 71)` | No | When thinking in light channels |
| `rgba()` | `rgba(255, 99, 71, 0.5)` | Yes | Semi-transparent effects |
| `#rrggbb` | `#ff6347` | No | Industry standard; from design tools |
| `hsl()` | `hsl(9, 100%, 64%)` | No | Design-friendly; intuitive adjustments |
| `hsla()` | `hsla(9, 100%, 64%, 0.5)` | Yes | Transparent design-friendly colors |

> **Key Insight:** `rgb(255, 99, 71)`, `#ff6347`, and `hsl(9, 100%, 64%)` all produce the exact same tomato-red color. They are just three different ways of describing the same thing.

---

## Guided Practice Exercises

### Exercise 1 — Color Name Practice

**Objective:** Practice applying named colors to different HTML elements.

**Scenario:** You are building a simple homepage for a fruit stand. Style the following HTML using color names.

**Your Task:** Copy this HTML and add colors using the `style` attribute:

```html
<!DOCTYPE html>
<html>
<body>

  <h1>Welcome to Fresh Fruits!</h1>
  <p>We sell the freshest fruits in town.</p>
  <h2>Today's Specials</h2>
  <p>Mangoes, Oranges, and Watermelon!</p>

</body>
</html>
```

**Instructions:**
1. Give the `<h1>` a background color of `Tomato`
2. Give the first `<p>` a text color of `DodgerBlue`
3. Give the `<h2>` a border of `2px solid MediumSeaGreen`
4. Give the second `<p>` a background color of `LightGray`

**Expected Result:**

```html
<!DOCTYPE html>
<html>
<body>

  <h1 style="background-color:Tomato;">Welcome to Fresh Fruits!</h1>
  <p style="color:DodgerBlue;">We sell the freshest fruits in town.</p>
  <h2 style="border:2px solid MediumSeaGreen;">Today's Specials</h2>
  <p style="background-color:LightGray;">Mangoes, Oranges, and Watermelon!</p>

</body>
</html>
```

**Self-Check Questions:**
- Does the heading have a red-orange background?
- Is the first paragraph text in blue?
- Is there a green border around the subheading?
- Does the last paragraph have a light gray background?

---

### Exercise 2 — RGB Color Practice

**Objective:** Use RGB values to create specific colors for a weather report card.

**Scenario:** You are styling a weather report that shows different sections for conditions.

**Instructions:** Create three styled sections:

1. A heading reading "Sunny Day" with a background of `rgb(255, 220, 50)` (golden yellow)
2. A paragraph reading "Temperature: 35°C" with text color `rgb(220, 50, 50)` (warm red)
3. A paragraph reading "Humidity: 80%" with a background of `rgb(100, 160, 255)` (sky blue)

**Solution:**

```html
<h1 style="background-color:rgb(255, 220, 50);">Sunny Day</h1>
<p style="color:rgb(220, 50, 50);">Temperature: 35°C</p>
<p style="background-color:rgb(100, 160, 255);">Humidity: 80%</p>
```

**Expected Output:** A golden-yellow heading, red temperature text, and blue humidity section.

**What-if Challenge:** What happens if you change the humidity paragraph to `rgb(100, 100, 100)`? It turns medium gray — because all three channels are equal!

---

### Exercise 3 — HEX Color Practice

**Objective:** Translate between RGB and HEX.

**Scenario:** A designer gave you these color specifications for a product card. They are in RGB. Convert them to HEX.

| Color | RGB | Your HEX Answer |
|---|---|---|
| Brand Blue | `rgb(0, 102, 204)` | `#0066cc` |
| Light Gray | `rgb(240, 240, 240)` | `#f0f0f0` |
| Success Green | `rgb(34, 139, 34)` | `#228b22` |

**Conversion method:**
- For `rgb(0, 102, 204)`:
  - Red: 0 ÷ 16 = 0 remainder 0 → `00`
  - Green: 102 = (6 × 16) + 6 → `66`
  - Blue: 204 = (12 × 16) + 12 = `cc`
  - Result: `#0066cc`

**Apply one of these to HTML:**

```html
<h2 style="background-color:#0066cc; color:#f0f0f0;">Product: Premium Widget</h2>
<p style="color:#228b22;">In Stock ✓</p>
```

**Expected Output:** A blue heading with light gray text, and a green "In Stock" line.

---

### Exercise 4 — HSL Color Practice

**Objective:** Use HSL to build a color palette for a social media profile page.

**Scenario:** You want to create three variations of the same blue color — a dark version, a normal version, and a light version — for a profile card header, body, and footer.

```html
<!-- Dark Blue Header -->
<div style="background-color:hsl(210, 80%, 25%); color:white; padding:10px;">
  <h2>Profile Header (Dark Blue)</h2>
</div>

<!-- Normal Blue Body -->
<div style="background-color:hsl(210, 80%, 50%); color:white; padding:10px;">
  <p>Profile Body (Normal Blue)</p>
</div>

<!-- Light Blue Footer -->
<div style="background-color:hsl(210, 80%, 80%); padding:10px;">
  <p>Profile Footer (Light Blue)</p>
</div>
```

**Notice:** All three use hue 210 (blue) and saturation 80% — only the lightness changes! This is the power of HSL.

**Expected Output:** Three sections of the same blue at different brightness levels — dark, normal, light.

**Self-Check Questions:**
- Are all three sections clearly the same "family" of blue?
- Does changing only the lightness value demonstrate how HSL makes color variations easy?

---

## Mini Project — Personal Profile Card

Let's combine everything you have learned to build a complete, styled HTML profile card.

### Project Goal

Create a simple personal profile card for a fictional person that uses at least four different color methods: a color name, RGB, HEX, and HSL.

### Stage 1 — Setup the HTML Structure

```html
<!DOCTYPE html>
<html>
<body>

  <div>
    <h1>Alex Johnson</h1>
    <p>Web Developer | Lagos, Nigeria</p>
    <hr>
    <h2>About Me</h2>
    <p>I build beautiful websites and love learning new technologies.</p>
    <h2>Skills</h2>
    <p>HTML, CSS, JavaScript, Python</p>
    <p>Contact: alex@example.com</p>
  </div>

</body>
</html>
```

**Milestone Output:** A plain, unstyled page with name, job, bio, skills.

---

### Stage 2 — Add Color Name and HEX Colors

Now add color names and HEX codes:

```html
<!DOCTYPE html>
<html>
<body>

  <!-- Outer card: HEX color background -->
  <div style="background-color:#f0f4ff; border:3px solid #0066cc; padding:20px;">

    <!-- Name: HEX color text -->
    <h1 style="color:#0066cc;">Alex Johnson</h1>

    <!-- Tagline: Color name for text -->
    <p style="color:SlateGray;">Web Developer | Lagos, Nigeria</p>

    <hr style="border:1px solid #cccccc;">

    <h2 style="color:#0066cc;">About Me</h2>
    <p>I build beautiful websites and love learning new technologies.</p>

    <h2 style="color:#0066cc;">Skills</h2>
    <p>HTML, CSS, JavaScript, Python</p>

    <!-- Contact line with named color -->
    <p style="background-color:LightYellow;">Contact: alex@example.com</p>

  </div>

</body>
</html>
```

**Milestone Output:** A card with a light blue background, blue headings, gray tagline, and a yellow-tinted contact line.

---

### Stage 3 — Add RGB and HSL Colors

Now enhance with RGB and HSL:

```html
<!DOCTYPE html>
<html>
<body>

  <div style="background-color:#f0f4ff; border:3px solid #0066cc; padding:20px;">

    <!-- Name with HSL color -->
    <h1 style="color:hsl(210, 90%, 35%);">Alex Johnson</h1>

    <!-- Tagline with RGB color -->
    <p style="color:rgb(100, 100, 120);">Web Developer | Lagos, Nigeria</p>

    <hr style="border:1px solid #cccccc;">

    <!-- Section headers with HEX -->
    <h2 style="color:#0066cc; border-left:4px solid hsl(210, 90%, 35%); padding-left:8px;">About Me</h2>
    <p>I build beautiful websites and love learning new technologies.</p>

    <h2 style="color:#0066cc; border-left:4px solid hsl(210, 90%, 35%); padding-left:8px;">Skills</h2>

    <!-- Skills with RGBA highlight -->
    <p style="background-color:rgba(0, 102, 204, 0.1); padding:8px;">HTML, CSS, JavaScript, Python</p>

    <!-- Contact with named color + HSL border -->
    <p style="background-color:LightYellow; border-left:3px solid hsl(45, 100%, 50%); padding:8px;">
      Contact: alex@example.com
    </p>

  </div>

</body>
</html>
```

**Milestone Output:** A polished profile card using four different color systems: `#hex`, `rgb()`, `hsl()`, `rgba()`, and a named color — all working together.

---

### Stage 4 — Reflection

Look at your finished card and answer these questions:

1. Which color method do you find easiest to write? Why?
2. Which method do you think is most precise for creating custom colors?
3. Where did you use RGBA and why was transparency useful there?
4. How did HSL make it easy to create the "same blue" used across multiple elements?

**Optional Extension:** Add a photo placeholder using a gray `div` with `background-color:rgb(200, 200, 200)` and dimensions `width:80px; height:80px;`.

---

## Common Beginner Mistakes

### Mistake 1 — Forgetting the # in HEX Colors

❌ Wrong:
```html
<p style="background-color:ff0000;">Red</p>
```

✅ Correct:
```html
<p style="background-color:#ff0000;">Red</p>
```

**Why:** The browser only recognizes a HEX color when it starts with the `#` symbol. Without it, the browser will not know what `ff0000` means and will ignore the color.

---

### Mistake 2 — Writing RGB Values Outside the 0–255 Range

❌ Wrong:
```html
<p style="color:rgb(300, 0, 0);">Red</p>
```

✅ Correct:
```html
<p style="color:rgb(255, 0, 0);">Red</p>
```

**Why:** RGB values must be between 0 and 255. A value of 300 is out of range. The browser may clamp it to 255, or simply ignore the entire rule. Either way, it's incorrect and unpredictable.

---

### Mistake 3 — Using RGBA Alpha Values Greater Than 1

❌ Wrong:
```html
<p style="background-color:rgba(255, 0, 0, 1.5);">Red</p>
```

✅ Correct:
```html
<p style="background-color:rgba(255, 0, 0, 1);">Red</p>
```

**Why:** The alpha value must be between 0.0 and 1.0. A value of 1.5 is out of range.

---

### Mistake 4 — Forgetting the % Sign in HSL

❌ Wrong:
```html
<p style="background-color:hsl(0, 100, 50);">Red</p>
```

✅ Correct:
```html
<p style="background-color:hsl(0, 100%, 50%);">Red</p>
```

**Why:** The saturation and lightness values in HSL **must** include the percentage sign `%`. Without it, the browser does not understand the value.

---

### Mistake 5 — Misspelling a Color Name

❌ Wrong:
```html
<p style="color:DodgersBlue;">Text</p>
```

✅ Correct:
```html
<p style="color:DodgerBlue;">Text</p>
```

**Why:** Color names must be spelled exactly as defined in the HTML specification. A typo like "DodgersBlue" will simply not work — the browser will ignore it and use the default color.

---

### Mistake 6 — Using a Decimal Point in RGB Values

❌ Wrong:
```html
<p style="color:rgb(255.5, 0, 0);">Red</p>
```

✅ Correct:
```html
<p style="color:rgb(255, 0, 0);">Red</p>
```

**Why:** RGB values must be whole numbers (integers). Decimal values like `255.5` are not valid.

---

### Mistake 7 — Confusing HEX with RGB Ranges

Remember: In HEX, the maximum value for each channel is `ff` (= 255 in decimal). A common confusion is trying to write `rgb(ff, 0, 0)` or `#(255, 0, 0)`. These mix up the two systems.

✅ RGB: `rgb(255, 0, 0)`
✅ HEX: `#ff0000`

---

## Reflection Questions

Answer these questions after completing the lesson. Writing your answers down will help you remember:

1. What are the five main ways to specify color in HTML?
2. In RGB, what does the value `0` mean for a channel? What does `255` mean?
3. What is the difference between `rgb()` and `rgba()`?
4. In HEX, what is the decimal equivalent of `ff`?
5. In HSL, what does setting saturation to 0% always produce, regardless of the hue?
6. If a designer gives you a color code like `#3498db`, what system is that using?
7. What value would you use for the alpha channel to make a color exactly 50% transparent?
8. Why is HSL considered more "human-friendly" than RGB?

---

## Completion Checklist

Before moving to the next lesson, confirm you can do all of the following:

- [ ] Apply color to an HTML element using a color name
- [ ] Apply color using `rgb()` with correct 0–255 values
- [ ] Apply transparent color using `rgba()` with a 0.0–1.0 alpha value
- [ ] Apply color using a `#rrggbb` HEX code
- [ ] Apply color using `hsl()` with hue (0–360), saturation (%), and lightness (%)
- [ ] Apply transparent color using `hsla()` with a 0.0–1.0 alpha value
- [ ] Use `color`, `background-color`, and `border` properties with all color formats
- [ ] Create shades of gray using any of the three numeric systems
- [ ] Explain the real-world use case for each color method
- [ ] Avoid the six common mistakes listed above

---

## Lesson Summary

Congratulations — you have now mastered every color system used in HTML!

Here is what you learned in this lesson:

**Color Names** are the simplest approach — 140 English words like `Tomato`, `DodgerBlue`, and `MediumSeaGreen`. Great for quick, readable code but limited in range.

**RGB** mixes Red, Green, and Blue light values from 0 to 255. It can produce over 16 million different colors and is directly tied to how screens display color.

**RGBA** extends RGB with an Alpha (transparency) channel from 0.0 to 1.0, enabling semi-transparent color effects.

**HEX** is the same as RGB but written as a compact 6-character code preceded by `#`. It is the industry standard, commonly found in design tools and professional codebases.

**HSL** describes color in human-intuitive terms: Hue (which color), Saturation (how vivid), and Lightness (how dark or bright). It is especially powerful when making color variations in a design system.

**HSLA** extends HSL with the same Alpha transparency channel as RGBA.

All three numeric systems — RGB, HEX, and HSL — can describe the same color from different angles. Learning which to use in which situation is a skill that comes with practice.

In the next lesson, we will explore how to link CSS stylesheets to HTML documents, allowing you to apply colors and other styles to entire pages rather than one element at a time.

---

*Sources: W3Schools HTML Colors Tutorial — html_colors.asp, html_colors_rgb.asp, html_colors_hex.asp, html_colors_hsl.asp*

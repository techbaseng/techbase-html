---
render_with_liquid: false
title: "Lesson 33: HTML Media — Video, Audio, Plug-ins & YouTube"
nav_order: 33
---

# Lesson 33: HTML Media — Video, Audio, Plug-ins & YouTube

---

## Lesson Introduction

Think about how you experience content on the internet every day. You watch a tutorial on YouTube, listen to a podcast, watch a short clip on a news website, or hear a notification sound when a new message arrives. All of that happens inside a web browser — and it is HTML that makes it possible.

Before HTML5 arrived (around 2008–2010), adding video or audio to a webpage was a huge headache. You needed special third-party software called **plug-ins** — most famously Adobe Flash — just to play a video. Users had to install Flash Player, keep it updated, and hope it did not crash their browser. It was fragile, slow, and insecure.

HTML5 changed everything. It introduced two native elements — `<video>` and `<audio>` — that let browsers play media **directly**, with no plug-ins, no extra software, nothing to install. Today, embedding video and audio is almost as simple as embedding an image.

This lesson will teach you everything you need to know about HTML media:

- What **multimedia** is and how files are stored
- Which **file formats** browsers support (and why it matters)
- The `<video>` element — every attribute, every option
- The `<audio>` element — every attribute, every option
- The `<object>` and `<embed>` elements — what they are and when (and when not) to use them
- How to embed **YouTube videos** cleanly and professionally using `<iframe>`
- All YouTube `<iframe>` parameters: autoplay, mute, loop, controls, and more
- Exercises, a mini project, and common mistakes

By the end, you will confidently embed any type of media — video, audio, or external content — into any webpage you build.

---

## Prerequisite Concepts

Before we explore HTML media, you need to understand three basic ideas.

### What is a File Format?

A **file format** is the way data is organised and stored inside a file. Different formats use different methods to compress and store data. The file extension (the letters after the dot in a filename) tells you the format: `.mp4`, `.mp3`, `.ogg`, and so on.

Different browsers understand different formats. This is why HTML lets you list **multiple source files** for the same video or audio — so every browser can find one it can play.

### What is a MIME Type?

A **MIME type** (pronounced "mime") is a label that tells the browser what kind of data it is receiving. It has two parts: a category and a subtype, separated by a slash.

Examples:
- `video/mp4` means: "this is video data, stored in MP4 format"
- `audio/mpeg` means: "this is audio data, stored in MP3/MPEG format"
- `audio/ogg` means: "this is audio data, stored in Ogg format"

You will use MIME types in the `type` attribute of `<source>` elements.

### What is a Codec?

A **codec** is the algorithm used to compress and decompress media. MP4 video is usually compressed with a codec called H.264. Ogg video uses a codec called Theora. You do not need to memorise codecs — just know they exist and that matching format + codec is why some browsers play some files and not others.

---

## Part 1: HTML Multimedia — The Big Picture

### What is Multimedia?

The word **multimedia** simply means content that uses more than one medium — combinations of text, images, audio, video, and animation.

On the web, multimedia elements (audio and video) are stored in **media files**. The most common way to identify the type of a file is by its **file extension** — the letters after the dot in the filename.

Here are common multimedia file extensions:

| Extension | Type | Notes |
|---|---|---|
| `.mp4` | Video | Most widely used video format on the web |
| `.webm` | Video | Open, royalty-free format from Google |
| `.ogg` | Video or Audio | Open format, used in Firefox |
| `.mp3` | Audio | Most widely used audio format |
| `.wav` | Audio | High quality, large file size |
| `.avi` | Video | Older format, not ideal for web |
| `.wmv` | Video | Windows Media Video, older format |
| `.mpg` / `.mpeg` | Video | Older compressed video |

> **Important Note:** Only **MP4, WebM, and Ogg** video formats are officially supported by the HTML standard for use in `<video>` elements.
>
> Only **MP3, WAV, and Ogg** audio formats are officially supported for use in `<audio>` elements.

### Why Does Format Support Matter?

Different browsers support different formats. Here is the current browser support:

**Video format support:**

| Format | Chrome | Firefox | Safari | Edge |
|---|---|---|---|---|
| MP4 | ✅ | ✅ | ✅ | ✅ |
| WebM | ✅ | ✅ | ✅ | ✅ |
| Ogg | ✅ | ✅ | ❌ | ✅ |

**Audio format support:**

| Format | Chrome | Firefox | Safari | Edge |
|---|---|---|---|---|
| MP3 | ✅ | ✅ | ✅ | ✅ |
| WAV | ✅ | ✅ | ✅ | ✅ |
| Ogg | ✅ | ✅ | ❌ | ✅ |

**The practical lesson here:** Always provide your video in **MP4** format at minimum — it works everywhere. For audio, use **MP3** as your first choice. Offering a second format as a fallback (like Ogg) gives you wider coverage.

> **MP3 Note:** The term "MP3" has become nearly synonymous with digital music in general. If your website delivers recorded music, MP3 is the most practical choice because of its widespread support and efficient compression.

---

## Part 2: The HTML `<video>` Element

### What Is It?

The `<video>` element is a native HTML5 element that lets you embed a video directly into a webpage. The browser plays it using its built-in media player — no plugins, no Flash, no extra downloads needed.

**Real-world analogy:** Think of `<video>` as an `<img>` tag for moving pictures. Just like `<img src="photo.jpg">` displays a photo, `<video>` displays a playable video.

### The Simplest Video

```html
<video width="320" height="240" controls>
  <source src="movie.mp4" type="video/mp4">
  <source src="movie.ogg" type="video/ogg">
  Your browser does not support the video tag.
</video>
```

Let us go through **every single part** of this code:

| Part | Explanation |
|---|---|
| `<video>` | Opens the video element |
| `width="320"` | Sets the video player width to 320 pixels |
| `height="240"` | Sets the video player height to 240 pixels |
| `controls` | Tells the browser to show the play/pause button, volume slider, and timeline bar |
| `<source src="movie.mp4" type="video/mp4">` | Tells the browser: "Try playing this MP4 file first" |
| `<source src="movie.ogg" type="video/ogg">` | Tells the browser: "If MP4 does not work, try this Ogg file" |
| `Your browser does not support the video tag.` | Fallback text — only shown if the browser cannot play ANY of the sources |
| `</video>` | Closes the video element |

**Expected output in the browser:**
```
┌──────────────────────────────────┐
│                                  │
│         [Video plays here]       │
│                                  │
│  ▶  ━━━━━━━━━━━━━━━━  🔊  ⛶   │
└──────────────────────────────────┘
```
(A video player with a play button, timeline scrubber, volume control, and fullscreen button)

### How the Browser Chooses a Source

When you provide multiple `<source>` elements, the browser reads them **from top to bottom** and plays the **first one it can handle**. It does not "choose the best one" — it picks the first one it understands.

```html
<video controls>
  <source src="movie.mp4" type="video/mp4">   <!-- Browser tries this first -->
  <source src="movie.webm" type="video/webm"> <!-- Falls back to this if MP4 fails -->
  <source src="movie.ogg" type="video/ogg">   <!-- Last resort -->
  Your browser does not support video.
</video>
```

> **Why is the `type` attribute important?**
> Without `type`, the browser must download the beginning of each file to figure out its format — which wastes bandwidth and slows page loading. With `type="video/mp4"`, the browser instantly knows whether it can play the file without downloading anything.

---

### Video Attributes — Complete Guide

The `<video>` element has several powerful attributes. Let us learn each one.

#### `controls` — Show the Playback Controls

Without `controls`, the video has no play button, volume slider, or timeline. The user cannot interact with it at all.

```html
<!-- No controls — video just sits there, user cannot play it -->
<video width="320" height="240">
  <source src="movie.mp4" type="video/mp4">
</video>

<!-- With controls — full playback interface shown -->
<video width="320" height="240" controls>
  <source src="movie.mp4" type="video/mp4">
</video>
```

> **Tip:** Always include `controls` unless you have a very specific reason not to (like a silent background video). Without controls, users feel trapped and frustrated.

---

#### `width` and `height` — Dimensions

```html
<video width="640" height="360" controls>
  <source src="movie.mp4" type="video/mp4">
</video>
```

**Why always set width and height?**

If you do not set width and height, the page will **flicker** while the video loads — the browser will not know how much space to reserve, so the page layout will shift suddenly when the video data arrives. Setting dimensions prevents this layout jump.

**Common video sizes:**
- `320×240` — small (quarter HD)
- `640×360` — medium (SD)
- `1280×720` — large (HD 720p)
- `1920×1080` — full HD (1080p)

---

#### `autoplay` — Start Playing Immediately

```html
<video width="320" height="240" autoplay>
  <source src="movie.mp4" type="video/mp4">
</video>
```

**Important browser rule about autoplay:**

Chromium-based browsers (Chrome, Edge, Brave) **block autoplay with sound** by default. This is because auto-playing audio is annoying to users. However, **muted autoplay is always allowed**.

**The correct way to autoplay:**

```html
<!-- WRONG: Will be blocked by Chrome/Edge in most cases -->
<video width="320" height="240" autoplay>
  <source src="movie.mp4" type="video/mp4">
</video>

<!-- CORRECT: Muted autoplay works everywhere -->
<video width="320" height="240" autoplay muted>
  <source src="movie.mp4" type="video/mp4">
</video>
```

This combination (`autoplay muted`) is the standard pattern for background videos.

---

#### `muted` — Start with Sound Off

```html
<video width="320" height="240" controls muted>
  <source src="movie.mp4" type="video/mp4">
</video>
```

The video starts with the sound turned off. The user can unmute it manually using the volume controls. This is commonly used for hero background videos on websites.

---

#### `loop` — Play Endlessly

```html
<video width="320" height="240" controls loop>
  <source src="movie.mp4" type="video/mp4">
</video>
```

When the video finishes, it automatically restarts from the beginning and plays again. Great for background animations, product demos, and looping clips.

---

#### `poster` — Show a Thumbnail Before Playing

```html
<video width="320" height="240" controls poster="thumbnail.jpg">
  <source src="movie.mp4" type="video/mp4">
</video>
```

The `poster` attribute specifies an image file to display in the video area while:
- The video is loading
- The video has not been played yet

**Real-world analogy:** The thumbnail image you see on YouTube before you click play. Without a poster, the video area is blank or shows the first frame of the video (which might be black).

**Expected output:**
```
┌──────────────────────────────────┐
│                                  │
│   [thumbnail.jpg displayed here] │
│                                  │
│  ▶  ━━━━━━━━━━━━━━━━  🔊  ⛶   │
└──────────────────────────────────┘
```

---

#### `preload` — Hint the Browser About Loading

```html
<video width="320" height="240" controls preload="metadata">
  <source src="movie.mp4" type="video/mp4">
</video>
```

The `preload` attribute gives the browser a hint about how much of the video to load when the page opens. It has three possible values:

| Value | What it means |
|---|---|
| `"none"` | Do not load anything until the user presses play. Saves bandwidth. |
| `"metadata"` | Only load the video's metadata (duration, dimensions, first frame). Good default. |
| `"auto"` | Load the entire video immediately. Fast playback, but wastes bandwidth if the user never plays it. |

> **Note:** The `preload` attribute is ignored if `autoplay` is present. If autoplay is set, the browser will load the video regardless.

---

### Combining Multiple Attributes

You can use any combination of attributes:

```html
<!-- A background hero video: autoplay, muted, looping, no controls, with poster -->
<video width="1280" height="720"
       autoplay
       muted
       loop
       poster="hero-thumbnail.jpg">
  <source src="hero-video.mp4" type="video/mp4">
  <source src="hero-video.webm" type="video/webm">
</video>
```

**What this does:**
- Starts playing automatically as soon as the page loads
- Plays with the sound off (so autoplay is not blocked)
- Repeats forever
- Shows `hero-thumbnail.jpg` while loading
- Has no play/pause controls shown to the user
- Tries MP4 first, falls back to WebM

---

### The `<video>` Element and the DOM

The HTML DOM (Document Object Model) provides JavaScript methods and events for the `<video>` element. This means you can control videos with JavaScript — without any plug-ins.

Some useful DOM methods for `<video>`:

| Method / Property | What it does |
|---|---|
| `.play()` | Starts playback |
| `.pause()` | Pauses playback |
| `.volume` | Gets/sets volume (0.0 to 1.0) |
| `.muted` | Gets/sets muted state (true/false) |
| `.currentTime` | Gets/sets position in seconds |
| `.duration` | Gets total video length in seconds |
| `.paused` | Returns true if the video is paused |

Simple JavaScript example:

```html
<video id="myVideo" width="320" height="240">
  <source src="movie.mp4" type="video/mp4">
</video>

<button onclick="document.getElementById('myVideo').play()">▶ Play</button>
<button onclick="document.getElementById('myVideo').pause()">⏸ Pause</button>
```

**Expected output:**
```
[Video area — no controls shown]

▶ Play    ⏸ Pause
(Two clickable buttons below the video)
```

> **Thinking Prompt:** Why would you want JavaScript buttons instead of the default `controls` bar? Answer: Custom-designed video players that match your website's visual style exactly.

---

### All `<video>` Attributes — Reference Table

| Attribute | What it does |
|---|---|
| `src` | Path to the video file (used directly on `<video>`, instead of `<source>`) |
| `width` | Width of the video player in pixels |
| `height` | Height of the video player in pixels |
| `controls` | Shows the browser's default playback controls |
| `autoplay` | Starts playing immediately on page load (requires `muted` in Chrome/Edge) |
| `muted` | Starts with audio turned off |
| `loop` | Replays video from the start when it ends |
| `poster` | Image shown while video is loading or before playback |
| `preload` | Loading hint: `"none"`, `"metadata"`, or `"auto"` |

---

## Part 3: The HTML `<audio>` Element

### What Is It?

The `<audio>` element is the companion to `<video>` — it embeds a playable audio file directly into a webpage. No plugins, no Flash, just native browser audio.

**Real-world analogy:** If `<video>` is a TV set built into your webpage, then `<audio>` is a radio or music player built into your webpage.

### The Simplest Audio Player

```html
<audio controls>
  <source src="horse.ogg" type="audio/ogg">
  <source src="horse.mp3" type="audio/mpeg">
  Your browser does not support the audio element.
</audio>
```

Let us go through every part:

| Part | Explanation |
|---|---|
| `<audio>` | Opens the audio element |
| `controls` | Shows the browser's built-in audio player interface |
| `<source src="horse.ogg" type="audio/ogg">` | Try this Ogg file first |
| `<source src="horse.mp3" type="audio/mpeg">` | If Ogg fails, try this MP3 |
| `Your browser does not support the audio element.` | Fallback text for very old browsers |
| `</audio>` | Closes the audio element |

**Expected output in the browser:**
```
[━━━━━━━━━━━━━━━━━ 0:00 / 0:12 🔊]
  ▶  ●━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```
(A compact audio player bar with play button, timeline, time counter, and volume)

Notice that `<audio>` does not have `width` and `height` attributes — because it does not display video. The audio player is just a small control bar.

---

### Audio Attributes — Complete Guide

The `<audio>` element shares most of its attributes with `<video>`. Here they are:

#### `controls` — Show the Audio Player

```html
<audio controls>
  <source src="song.mp3" type="audio/mpeg">
</audio>
```

Without `controls`, nothing is visible and the user cannot interact with the audio at all. Always include `controls` unless you have a specific design reason not to.

---

#### `autoplay` — Start Playing Immediately

```html
<audio autoplay muted>
  <source src="background-music.mp3" type="audio/mpeg">
</audio>
```

Same rule as with video: Chrome and Edge block autoplay with sound. Use `autoplay muted` together for reliable results across browsers. The user can then choose to unmute.

---

#### `loop` — Repeat Continuously

```html
<audio controls loop>
  <source src="ambient-sound.mp3" type="audio/mpeg">
</audio>
```

When the audio finishes, it automatically starts over from the beginning. Perfect for background music or ambient sounds.

---

#### `muted` — Start Silently

```html
<audio controls muted>
  <source src="narration.mp3" type="audio/mpeg">
</audio>
```

The audio player appears but starts with the volume off. The user unmutes manually.

---

#### `preload` — Loading Hint

```html
<!-- Load only metadata (duration, format info) on page load -->
<audio controls preload="metadata">
  <source src="podcast.mp3" type="audio/mpeg">
</audio>

<!-- Do not load anything until user presses play (saves bandwidth) -->
<audio controls preload="none">
  <source src="podcast.mp3" type="audio/mpeg">
</audio>
```

Same three values as with `<video>`: `"none"`, `"metadata"`, `"auto"`.

---

### Providing Multiple Audio Formats

For maximum compatibility, provide both MP3 and Ogg:

```html
<audio controls>
  <source src="song.mp3" type="audio/mpeg">
  <source src="song.ogg" type="audio/ogg">
  <source src="song.wav" type="audio/wav">
  Your browser does not support the audio element.
</audio>
```

The browser plays the first one it supports. If it supports MP3 (virtually all do), it uses that.

---

### Common Audio Type Values

| Format | `type` Attribute Value |
|---|---|
| MP3 | `type="audio/mpeg"` |
| Ogg Vorbis | `type="audio/ogg"` |
| WAV | `type="audio/wav"` |

---

### All `<audio>` Attributes — Reference Table

| Attribute | What it does |
|---|---|
| `src` | Path to the audio file (used directly on `<audio>` instead of `<source>`) |
| `controls` | Shows the browser's default audio player controls |
| `autoplay` | Starts playing immediately on page load (use with `muted` in Chrome/Edge) |
| `muted` | Starts with audio turned off |
| `loop` | Repeats audio from the start when it ends |
| `preload` | Loading hint: `"none"`, `"metadata"`, or `"auto"` |

---

### `<video>` vs `<audio>` — Side-by-Side Comparison

| Feature | `<video>` | `<audio>` |
|---|---|---|
| Displays visual content | ✅ Yes | ❌ No |
| `width` and `height` attributes | ✅ Yes | ❌ Not needed |
| `poster` attribute | ✅ Yes | ❌ No |
| `controls` attribute | ✅ Yes | ✅ Yes |
| `autoplay` attribute | ✅ Yes | ✅ Yes |
| `muted` attribute | ✅ Yes | ✅ Yes |
| `loop` attribute | ✅ Yes | ✅ Yes |
| `preload` attribute | ✅ Yes | ✅ Yes |
| Supported formats | MP4, WebM, Ogg | MP3, WAV, Ogg |

---

## Part 4: HTML Plug-ins — `<object>` and `<embed>`

### The History: What Were Plug-ins?

Before HTML5, browsers could not play video or audio on their own. They relied on third-party **plug-ins** — separate software programs that extended the browser's abilities.

Common plug-ins included:
- **Adobe Flash** — played Flash video and animations
- **Java Applets** — ran Java programs inside the browser
- **Windows Media Player** — played Windows media formats
- **RealPlayer** — played Real Media files
- **ActiveX controls** — Windows-specific interactive content

Plug-ins were embedded using the `<object>` element (and sometimes `<embed>`).

**Why are plug-ins mostly gone today?**
- Most browsers (Chrome, Firefox, Edge, Safari) have **removed plug-in support**
- Java Applets are no longer supported in any modern browser
- ActiveX controls are no longer supported in any browser
- Adobe Flash reached end-of-life in December 2020 and is completely blocked in modern browsers
- HTML5 `<video>` and `<audio>` can do everything Flash used to do, natively

Understanding `<object>` and `<embed>` is still useful for:
- Embedding PDFs
- Embedding another HTML page within a page
- Maintaining older web projects

---

### The `<object>` Element

#### What Is It?

The `<object>` element defines a container for an **external resource**. That resource can be a web page, an image, a PDF, or (historically) a plug-in.

**Syntax:**

```html
<object data="URL_of_file" type="media_type" width="500" height="400">
  Fallback content: shown if the object cannot be displayed.
</object>
```

Key attributes:
- `data` — the URL (path) to the resource
- `type` — the MIME type of the resource
- `width` and `height` — the display dimensions in pixels

**Important:** At least one of `data` or `type` MUST be present.

#### Embedding an Image with `<object>`

```html
<object data="photo.jpg" type="image/jpeg" width="400" height="300">
  <p>Your browser cannot display this image.</p>
</object>
```

**Expected output:**
```
[Photo displayed in 400×300 area]
```

If the image fails to load, the user sees the fallback paragraph instead.

---

#### Embedding Another HTML Page with `<object>`

You can embed one webpage inside another:

```html
<object width="100%" height="500px" data="snippet.html">
</object>
```

**Expected output:**
A 500px tall box showing the full contents of `snippet.html` rendered inside your current page.

---

#### Embedding a PDF with `<object>`

```html
<object data="annual_report.pdf" type="application/pdf" width="800" height="600">
  <p>Your browser does not support embedded PDFs.
  <a href="annual_report.pdf">Click here to download the PDF.</a></p>
</object>
```

**Expected output:**
A large embedded PDF viewer showing the document directly on your page. If the browser cannot render it, the user sees a helpful download link instead.

> **Why `<object>` is great for PDFs:** Instead of forcing users to download a file and open it in a separate program, you display it right in your page. The fallback link ensures users on older browsers can still access the content.

---

#### The `<param>` Element — Passing Parameters to Plug-ins

When `<object>` was used with plug-ins, `<param>` elements inside it could pass settings to the plug-in:

```html
<object data="movie.swf" type="application/x-shockwave-flash"
        width="400" height="300">
  <param name="quality" value="high">
  <param name="autoplay" value="true">
  <p>Flash is not supported by your browser.</p>
</object>
```

Each `<param>` has a `name` and `value` pair. Today, Flash is blocked everywhere, so this pattern is mostly historical — but `<param>` still works with `<object>` for other use cases.

---

### The `<embed>` Element

#### What Is It?

The `<embed>` element embeds external content into an HTML document, similar to `<object>`. It is a **self-closing tag** (no closing `</embed>` tag).

Key difference from `<object>`: `<embed>` does **not** support fallback content inside it. If the embedded content fails, nothing is shown.

**Syntax:**

```html
<embed src="URL_of_file" type="media_type" width="500" height="400">
```

Note: no closing tag, and no fallback content.

`<embed>` has been supported by browsers for a long time but only officially became part of the HTML specification in HTML5.

#### Embedding HTML with `<embed>`

```html
<embed width="100%" height="500px" src="snippet.html">
```

This does the same thing as `<object data="snippet.html">` — it shows `snippet.html` inside your page.

---

### `<object>` vs `<embed>` — Key Differences

| Feature | `<object>` | `<embed>` |
|---|---|---|
| Fallback content | ✅ Yes — content between tags | ❌ No — self-closing |
| Closing tag | ✅ Yes — `</object>` | ❌ No — self-closing |
| `<param>` support | ✅ Yes | ❌ No |
| Official HTML5 standard | ✅ Yes | ✅ Yes (added in HTML5) |
| `data` attribute | ✅ Yes | ❌ No — uses `src` |
| Preferred for PDFs | ✅ Yes | Sometimes |

> **Recommendation:** For modern web development, prefer `<object>` over `<embed>` because it supports fallback content. If a PDF fails to load in `<object>`, the user sees your fallback message. With `<embed>`, they see nothing.

---

## Part 5: Embedding YouTube Videos

### Why Use YouTube Instead of Self-Hosted Video?

You might wonder: "Why would I use YouTube instead of just uploading my video file and using `<video>`?"

Here are compelling reasons:

1. **No format conversion headaches.** YouTube handles all the format transcoding. You upload one file and YouTube creates MP4, WebM, and other formats automatically.

2. **Zero storage cost.** Video files are huge. Hosting them on your own server is expensive. YouTube hosts them for free.

3. **No bandwidth costs.** When users play your video, YouTube pays for the bandwidth — not you.

4. **Built-in player.** YouTube's player is professionally designed with quality controls, captions, full-screen, etc.

5. **Better performance.** YouTube has servers all over the world (CDN). Users get the video from the closest server, so it loads fast anywhere.

6. **Cross-browser compatibility.** YouTube handles all the browser differences for you.

The trade-off: you give up some control (the YouTube branding, recommendations at the end, etc.). For professional projects, weigh these factors carefully.

---

### How YouTube Embedding Works: Finding the Video ID

Every YouTube video has a unique **video ID** — a short string of random characters in the video's URL.

For example, in this URL:
```
https://www.youtube.com/watch?v=tgbNymZ7vqY
```

The video ID is: `tgbNymZ7vqY`

You use this ID to construct the embed URL:
```
https://www.youtube.com/embed/tgbNymZ7vqY
```

---

### The Basic YouTube Embed

To embed a YouTube video, you use the `<iframe>` element (not `<video>`):

```html
<iframe width="420" height="315"
  src="https://www.youtube.com/embed/tgbNymZ7vqY">
</iframe>
```

**What each part means:**

| Part | Explanation |
|---|---|
| `<iframe>` | "Inline Frame" — embeds another webpage inside your page |
| `width="420"` | Width of the video player in pixels |
| `height="315"` | Height of the video player in pixels |
| `src="https://www.youtube.com/embed/tgbNymZ7vqY"` | The embed URL with the video ID |

**Expected output:**
```
┌─────────────────────────────────────────┐
│                                         │
│         [YouTube video player]          │
│                                         │
│  ▶  ━━━━━━━━━━━━━━━━  🔊  ⚙  ⛶  YT  │
└─────────────────────────────────────────┘
```
A YouTube player appears directly on your page with the full YouTube control bar.

---

### YouTube `<iframe>` Parameters

You can customise the YouTube player's behaviour by adding **parameters** to the embed URL. Parameters are added after a `?` and are separated by `&`.

#### Parameter 1: `autoplay=1` — Auto-Start the Video

```html
<iframe width="420" height="315"
  src="https://www.youtube.com/embed/tgbNymZ7vqY?autoplay=1&mute=1">
</iframe>
```

- `autoplay=1` — the video starts playing as soon as the page loads
- `mute=1` — the video starts muted (required for autoplay to work in most browsers)

> **Important:** YouTube also requires `mute=1` for autoplay to work reliably in modern browsers, just like the native `<video>` element.

**Expected output:** The YouTube player appears and begins playing immediately (silently).

---

#### Parameter 2: `loop=1` — Loop the Video Forever

```html
<iframe width="420" height="315"
  src="https://www.youtube.com/embed/tgbNymZ7vqY?playlist=tgbNymZ7vqY&loop=1">
</iframe>
```

Two parameters together:
- `loop=1` — enables looping
- `playlist=tgbNymZ7vqY` — required for looping to work; must be set to the **same video ID**

Without `playlist`, YouTube's loop feature does not work correctly.

**Expected output:** The video plays, and when it ends, it automatically starts again.

---

#### Parameter 3: `controls=0` — Hide the Control Bar

```html
<iframe width="420" height="315"
  src="https://www.youtube.com/embed/tgbNymZ7vqY?controls=0">
</iframe>
```

- `controls=0` — hides all the playback controls (play, pause, timeline, volume)
- `controls=1` (default) — shows the controls

**Expected output:** The YouTube video plays but with no visible control bar. The user cannot pause, adjust volume, or seek.

> **When to use this:** Background videos in banners or decorative use cases where you do not want the player interface to show.

---

### Combining Multiple YouTube Parameters

You can chain multiple parameters together using `&`:

```html
<!-- Autoplay, muted, looping, no controls -->
<iframe width="420" height="315"
  src="https://www.youtube.com/embed/tgbNymZ7vqY?autoplay=1&mute=1&playlist=tgbNymZ7vqY&loop=1&controls=0">
</iframe>
```

**All parameters joined:**
```
?autoplay=1&mute=1&playlist=tgbNymZ7vqY&loop=1&controls=0
```

---

### Complete YouTube Parameter Reference

| Parameter | Values | What it does |
|---|---|---|
| `autoplay` | `0` (default), `1` | Auto-start the video on page load |
| `mute` | `0` (default), `1` | Mute the audio (required for autoplay in most browsers) |
| `loop` | `0` (default), `1` | Loop the video (also requires `playlist=VIDEO_ID`) |
| `playlist` | Video ID | Required companion for `loop=1` |
| `controls` | `0`, `1` (default) | Show or hide the player control bar |
| `start` | Seconds | Start video at a specific time (e.g., `start=30` = start at 30s) |
| `end` | Seconds | Stop video at a specific time |
| `rel` | `0`, `1` (default) | `rel=0` = show only related videos from same channel at end |

**Example using `start` and `end`:**

```html
<!-- Play only from 30 seconds to 90 seconds of the video -->
<iframe width="420" height="315"
  src="https://www.youtube.com/embed/tgbNymZ7vqY?start=30&end=90">
</iframe>
```

---

### Responsive YouTube Embed (Bonus)

By default, the `<iframe>` has a fixed pixel size. On small screens, this can cause horizontal scrolling. A CSS trick makes the embed responsive:

```html
<style>
  .video-container {
    position: relative;
    padding-bottom: 56.25%; /* 16:9 aspect ratio */
    height: 0;
    overflow: hidden;
  }

  .video-container iframe {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
  }
</style>

<div class="video-container">
  <iframe src="https://www.youtube.com/embed/tgbNymZ7vqY"
    frameborder="0" allowfullscreen>
  </iframe>
</div>
```

**Expected output:** The video fills 100% of its container and maintains a 16:9 ratio on any screen size.

---

## Guided Practice Exercises

### Exercise 1: Embed a Simple Video

**Objective:** Write the HTML for a basic video player.

**Scenario:** You are building a cooking website. You have a recipe video saved as `pasta.mp4` and also as `pasta.ogg` (for Firefox compatibility). The video should show controls, be 640 pixels wide and 360 pixels tall, and show a thumbnail image `pasta-thumbnail.jpg` before the user plays it.

**Steps:**
1. Open a `<video>` element with width and height
2. Add the `controls` attribute
3. Add the `poster` attribute pointing to your thumbnail
4. Add a `<source>` for the MP4 file
5. Add a `<source>` for the Ogg file
6. Add fallback text
7. Close the `</video>` element

**Solution:**

```html
<video width="640" height="360" controls poster="pasta-thumbnail.jpg">
  <source src="pasta.mp4" type="video/mp4">
  <source src="pasta.ogg" type="video/ogg">
  Your browser does not support the video tag.
  <a href="pasta.mp4">Download the video instead.</a>
</video>
```

**Expected output:**
```
┌──────────────────────────────────────┐
│                                      │
│   [pasta-thumbnail.jpg shown here]   │
│                                      │
│  ▶  ━━━━━━━━━━━━━━━━  🔊 0:00 ⛶   │
└──────────────────────────────────────┘
```

> **Self-check questions:**
> - Did you set both `width` and `height`? (Prevents page flicker)
> - Did you include the `poster` image? (Better user experience)
> - Did you list MP4 first? (MP4 works in all browsers)
> - Did you include fallback text? (For very old browsers)

---

### Exercise 2: Build a Background Hero Video

**Objective:** Create a muted, auto-playing, looping background video for a landing page.

**Scenario:** You have a `hero.mp4` and `hero.webm` file. You want the video to play automatically and silently when the page loads, loop forever, and not show any controls. Size it at 1280×720.

**Solution:**

```html
<video width="1280" height="720"
       autoplay
       muted
       loop>
  <source src="hero.mp4" type="video/mp4">
  <source src="hero.webm" type="video/webm">
</video>
```

**Expected output:**
```
[Full-width video playing silently and automatically — no controls visible]
```

> **Self-check questions:**
> - Is `muted` present alongside `autoplay`? (Required for autoplay in Chrome/Edge)
> - Is `loop` present? (Endless playback)
> - Is `controls` absent? (No visible player interface)

---

### Exercise 3: Add a Music Player

**Objective:** Embed an audio player for a podcast page.

**Scenario:** You have an episode file `episode12.mp3` and `episode12.ogg`. You want a visible player, the audio should NOT autoplay (let the user decide), and it should NOT loop.

**Solution:**

```html
<p>Episode 12: The Future of Web Design</p>

<audio controls preload="metadata">
  <source src="episode12.mp3" type="audio/mpeg">
  <source src="episode12.ogg" type="audio/ogg">
  Your browser does not support the audio element.
  <a href="episode12.mp3">Download Episode 12</a>
</audio>
```

**Expected output:**
```
Episode 12: The Future of Web Design

[▶  ●━━━━━━━━━━━━━━━━━━  0:00 / 45:23  🔊]
```
(Audio player bar — user must press play manually)

---

### Exercise 4: Embed a YouTube Video with Parameters

**Objective:** Embed a YouTube video with autoplay, muted, and no controls.

**Scenario:** You want to embed a YouTube video with ID `abc123XYZ` on your homepage. It should auto-play silently and not show the controls bar. Size it 560×315.

**Solution:**

```html
<iframe width="560" height="315"
  src="https://www.youtube.com/embed/abc123XYZ?autoplay=1&mute=1&controls=0">
</iframe>
```

**Expected output:**
```
[YouTube video begins playing silently — no control bar visible]
```

> **Self-check questions:**
> - Did you use `/embed/` in the URL (not `/watch?v=`)?
> - Did you include `mute=1` with `autoplay=1`?
> - Did you add `controls=0`?

---

### Exercise 5: Embed a PDF Document

**Objective:** Embed a PDF with a fallback download link.

**Scenario:** You want to show a company brochure `brochure.pdf` directly on your contact page. Provide a fallback download link in case the browser cannot display it.

**Solution:**

```html
<object data="brochure.pdf" type="application/pdf" width="800" height="600">
  <p>Your browser does not support embedded PDFs.
  <a href="brochure.pdf">Click here to download the brochure (PDF).</a></p>
</object>
```

**Expected output:**
```
[Full PDF viewer showing brochure.pdf in an 800×600 box]
OR (if PDF rendering fails):
Your browser does not support embedded PDFs.
Click here to download the brochure (PDF).   (clickable link)
```

---

## Mini Project: A Complete Media Page

Let us build a **complete media-rich webpage** for a fictitious music school called **"Harmony Academy"** that uses all the media elements from this lesson.

### Project Overview

The page will contain:
- A muted auto-playing background video
- A section with multiple embedded video lessons
- An audio player for a podcast episode
- An embedded YouTube tutorial video
- An embedded PDF curriculum document

### Stage 1: Page Shell with Background Video

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Harmony Academy — Media Centre</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 0;
      padding: 20px;
      background-color: #1a1a2e;
      color: #eaeaea;
    }

    header {
      text-align: center;
      padding: 20px;
    }

    .hero-video {
      width: 100%;
      max-height: 400px;
      object-fit: cover;
    }

    section {
      margin: 30px 0;
    }

    h2 {
      color: #e94560;
      border-bottom: 1px solid #e94560;
      padding-bottom: 5px;
    }
  </style>
</head>
<body>

  <!-- Hero Background Video -->
  <video class="hero-video" autoplay muted loop poster="academy-thumbnail.jpg">
    <source src="academy-intro.mp4" type="video/mp4">
    <source src="academy-intro.webm" type="video/webm">
  </video>

  <header>
    <h1>🎵 Harmony Academy — Media Centre</h1>
    <p>Learn music through video lessons, podcasts, and tutorials</p>
  </header>

  <!-- Content will be added in the stages below -->

</body>
</html>
```

---

### Stage 2: Video Lessons Section

Add this inside `<body>`, after the header:

```html
<section>
  <h2>📹 Video Lessons</h2>

  <article>
    <h3>Lesson 1: Introduction to the Piano</h3>
    <p>Learn the basic layout of the piano keyboard and how to position your hands.</p>

    <video width="560" height="315" controls poster="piano-lesson-thumb.jpg" preload="metadata">
      <source src="piano-intro.mp4" type="video/mp4">
      <source src="piano-intro.ogg" type="video/ogg">
      Your browser does not support the video tag.
      <a href="piano-intro.mp4">Download this lesson.</a>
    </video>
  </article>

  <article>
    <h3>Lesson 2: Basic Guitar Chords</h3>
    <p>Master the three beginner chords that unlock hundreds of songs.</p>

    <video width="560" height="315" controls poster="guitar-lesson-thumb.jpg" preload="metadata">
      <source src="guitar-chords.mp4" type="video/mp4">
      <source src="guitar-chords.webm" type="video/webm">
      Your browser does not support the video tag.
      <a href="guitar-chords.mp4">Download this lesson.</a>
    </video>
  </article>
</section>
```

**Milestone output:**
```
📹 Video Lessons

Lesson 1: Introduction to the Piano
Learn the basic layout of the piano keyboard...
[Video player with piano-lesson-thumb.jpg shown as thumbnail]

Lesson 2: Basic Guitar Chords
Master the three beginner chords...
[Video player with guitar-lesson-thumb.jpg shown as thumbnail]
```

---

### Stage 3: Podcast Audio Player

Add this section after the video lessons:

```html
<section>
  <h2>🎙 Music Theory Podcast</h2>

  <article>
    <h3>Episode 7: Why Does Music Make Us Feel Emotions?</h3>
    <p>In this episode, Professor Adaeze Obi explores the psychology of
    music and how rhythm and melody trigger emotional responses in the brain.</p>

    <audio controls preload="metadata">
      <source src="episode7-emotions.mp3" type="audio/mpeg">
      <source src="episode7-emotions.ogg" type="audio/ogg">
      Your browser does not support the audio element.
      <a href="episode7-emotions.mp3">Download Episode 7 (MP3)</a>
    </audio>

    <p><small>Duration: 38 minutes | Published: April 2025</small></p>
  </article>
</section>
```

**Milestone output:**
```
🎙 Music Theory Podcast

Episode 7: Why Does Music Make Us Feel Emotions?
In this episode, Professor Adaeze Obi explores...

[▶  ●━━━━━━━━━━━━━━━━━━  0:00 / 38:12  🔊]

Duration: 38 minutes | Published: April 2025
```

---

### Stage 4: YouTube Tutorial Section

```html
<section>
  <h2>▶ YouTube Tutorials</h2>
  <p>We have partnered with some excellent YouTube creators.
  These tutorials open right here — no need to leave the page.</p>

  <article>
    <h3>How to Read Sheet Music (Beginner's Guide)</h3>

    <!-- Standard YouTube embed with controls -->
    <iframe width="560" height="315"
      src="https://www.youtube.com/embed/tgbNymZ7vqY"
      allowfullscreen>
    </iframe>
  </article>

  <article>
    <h3>Practice Metronome — 60 BPM Loop</h3>
    <p>Use this silent metronome loop while practising.</p>

    <!-- Autoplay + muted + looping metronome video -->
    <iframe width="560" height="315"
      src="https://www.youtube.com/embed/tgbNymZ7vqY?autoplay=1&mute=1&loop=1&playlist=tgbNymZ7vqY&controls=0">
    </iframe>
  </article>
</section>
```

---

### Stage 5: PDF Curriculum

```html
<section>
  <h2>📄 Course Curriculum</h2>
  <p>Read our full course outline below, or download it for reference.</p>

  <object data="harmony-academy-curriculum.pdf"
          type="application/pdf"
          width="100%"
          height="600">
    <p>Your browser does not support embedded PDFs.
    <a href="harmony-academy-curriculum.pdf">
      Download the curriculum PDF here.
    </a></p>
  </object>
</section>
```

---

### Final Complete Page

Assembling all stages:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Harmony Academy — Media Centre</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 0;
      padding: 20px;
      background-color: #1a1a2e;
      color: #eaeaea;
    }
    header { text-align: center; padding: 20px; }
    .hero-video { width: 100%; max-height: 400px; object-fit: cover; }
    section { margin: 30px 0; }
    article { margin: 20px 0; background: #16213e; padding: 15px; border-radius: 8px; }
    h2 { color: #e94560; border-bottom: 1px solid #e94560; padding-bottom: 5px; }
    iframe, video, audio { display: block; margin: 10px 0; }
  </style>
</head>
<body>

  <!-- Hero video -->
  <video class="hero-video" autoplay muted loop poster="academy-thumbnail.jpg">
    <source src="academy-intro.mp4" type="video/mp4">
    <source src="academy-intro.webm" type="video/webm">
  </video>

  <header>
    <h1>🎵 Harmony Academy — Media Centre</h1>
    <p>Learn music through video lessons, podcasts, and tutorials</p>
  </header>

  <!-- Video Lessons -->
  <section>
    <h2>📹 Video Lessons</h2>

    <article>
      <h3>Lesson 1: Introduction to the Piano</h3>
      <p>Learn the basic layout of the piano keyboard and hand positioning.</p>
      <video width="560" height="315" controls poster="piano-lesson-thumb.jpg" preload="metadata">
        <source src="piano-intro.mp4" type="video/mp4">
        <source src="piano-intro.ogg" type="video/ogg">
        Your browser does not support the video tag.
        <a href="piano-intro.mp4">Download this lesson.</a>
      </video>
    </article>

    <article>
      <h3>Lesson 2: Basic Guitar Chords</h3>
      <p>Master the three beginner chords that unlock hundreds of songs.</p>
      <video width="560" height="315" controls poster="guitar-lesson-thumb.jpg" preload="metadata">
        <source src="guitar-chords.mp4" type="video/mp4">
        <source src="guitar-chords.webm" type="video/webm">
        Your browser does not support the video tag.
        <a href="guitar-chords.mp4">Download this lesson.</a>
      </video>
    </article>
  </section>

  <!-- Podcast -->
  <section>
    <h2>🎙 Music Theory Podcast</h2>
    <article>
      <h3>Episode 7: Why Does Music Make Us Feel Emotions?</h3>
      <p>Professor Adaeze Obi explores music psychology and emotional response.</p>
      <audio controls preload="metadata">
        <source src="episode7-emotions.mp3" type="audio/mpeg">
        <source src="episode7-emotions.ogg" type="audio/ogg">
        Your browser does not support the audio element.
        <a href="episode7-emotions.mp3">Download Episode 7</a>
      </audio>
      <p><small>Duration: 38 minutes | Published: April 2025</small></p>
    </article>
  </section>

  <!-- YouTube -->
  <section>
    <h2>▶ YouTube Tutorials</h2>
    <article>
      <h3>How to Read Sheet Music</h3>
      <iframe width="560" height="315"
        src="https://www.youtube.com/embed/tgbNymZ7vqY"
        allowfullscreen>
      </iframe>
    </article>
    <article>
      <h3>Practice Metronome Loop</h3>
      <iframe width="560" height="315"
        src="https://www.youtube.com/embed/tgbNymZ7vqY?autoplay=1&mute=1&loop=1&playlist=tgbNymZ7vqY&controls=0">
      </iframe>
    </article>
  </section>

  <!-- PDF -->
  <section>
    <h2>📄 Course Curriculum</h2>
    <object data="harmony-academy-curriculum.pdf" type="application/pdf"
            width="100%" height="600">
      <p>Your browser does not support embedded PDFs.
      <a href="harmony-academy-curriculum.pdf">Download the curriculum PDF.</a></p>
    </object>
  </section>

</body>
</html>
```

> **Reflection Questions:**
> - Why do we provide two `<source>` elements for the video files?
> - Why does the hero video have both `autoplay` and `muted` but no `controls`?
> - What would happen to the podcast section if you replaced `<audio>` with a plain text link?
> - Why is the YouTube video using `<iframe>` rather than `<video>`?
> - What does the user see if the PDF cannot be rendered by their browser?

---

## Common Beginner Mistakes

### Mistake 1: Using `autoplay` Without `muted`

**Wrong:**
```html
<video width="320" height="240" autoplay controls>
  <source src="intro.mp4" type="video/mp4">
</video>
```

**Right:**
```html
<video width="320" height="240" autoplay muted controls>
  <source src="intro.mp4" type="video/mp4">
</video>
```

**Why it's wrong:** Chrome and Edge block autoplay with sound. The video will silently fail to autoplay in most browsers. Always pair `autoplay` with `muted`.

---

### Mistake 2: Forgetting `width` and `height` on `<video>`

**Wrong:**
```html
<video controls>
  <source src="movie.mp4" type="video/mp4">
</video>
```

**Right:**
```html
<video width="640" height="360" controls>
  <source src="movie.mp4" type="video/mp4">
</video>
```

**Why it's wrong:** Without dimensions, the page layout will jump and flicker as the video loads, because the browser did not reserve space for it.

---

### Mistake 3: Using `/watch?v=` Instead of `/embed/` for YouTube

**Wrong:**
```html
<iframe src="https://www.youtube.com/watch?v=tgbNymZ7vqY"></iframe>
```

**Right:**
```html
<iframe src="https://www.youtube.com/embed/tgbNymZ7vqY"></iframe>
```

**Why it's wrong:** The `/watch?v=` URL opens the full YouTube website — which cannot be embedded inside an `<iframe>`. The `/embed/` URL is specifically designed for embedding and has no navigation bars or related pages around it.

---

### Mistake 4: Adding a Closing Tag to `<embed>`

**Wrong:**
```html
<embed src="snippet.html" width="100%" height="500px"></embed>
```

**Right:**
```html
<embed src="snippet.html" width="100%" height="500px">
```

**Why it's wrong:** `<embed>` is a void element (self-closing). It has no closing tag. Adding `</embed>` creates invalid HTML.

---

### Mistake 5: Forgetting the `type` Attribute on `<source>`

**Wrong:**
```html
<video width="320" height="240" controls>
  <source src="movie.mp4">
  <source src="movie.ogg">
</video>
```

**Right:**
```html
<video width="320" height="240" controls>
  <source src="movie.mp4" type="video/mp4">
  <source src="movie.ogg" type="video/ogg">
</video>
```

**Why it's wrong:** Without the `type` attribute, the browser must partially download each file to discover its format. This wastes bandwidth and slows page loading. With `type`, the browser instantly knows whether it can play the format.

---

### Mistake 6: Using YouTube's `loop=1` Without `playlist`

**Wrong:**
```html
<iframe src="https://www.youtube.com/embed/tgbNymZ7vqY?loop=1"></iframe>
```

**Right:**
```html
<iframe src="https://www.youtube.com/embed/tgbNymZ7vqY?loop=1&playlist=tgbNymZ7vqY"></iframe>
```

**Why it's wrong:** YouTube's `loop=1` only works when `playlist` is also specified and set to the same video ID. Without `playlist`, the loop does not work.

---

### Mistake 7: Using `<object>` or `<embed>` to Embed Flash or Java

**Wrong (outdated):**
```html
<object data="animation.swf" type="application/x-shockwave-flash"
        width="400" height="300">
  <param name="movie" value="animation.swf">
</object>
```

**Right (modern alternative):**
Use `<video>` for video content, CSS animations for visual effects, or JavaScript for interactive content.

**Why it's wrong:** Adobe Flash was end-of-lifed in December 2020. It is completely blocked in all modern browsers. Java Applets are also blocked. `<object>` for these use cases simply does not work anymore.

---

## Reflection Questions

1. **Why did plug-ins like Flash eventually get replaced?** What problems did they create that native HTML5 elements solved?

2. **You have a video in `.avi` format.** Can you use it directly in a `<video>` element? What would you need to do?

3. **Why is the fallback text inside `<video>` and `<audio>` important?** Who sees it, and in what situation?

4. **A video on your page has `autoplay` but users complain it never auto-plays.** What is the most likely cause, and what is the fix?

5. **When would you choose to embed a video with YouTube `<iframe>` instead of using a self-hosted `<video>` element?** List at least three factors you would consider.

6. **Your colleague says:** "The `<object>` element is useless — just use `<iframe>` for everything." Do you agree? What can `<object>` do that `<iframe>` cannot? (Hint: think about fallback content and PDFs.)

7. **What is the purpose of the `poster` attribute on `<video>`?** What does the user see without it?

8. **Explain the `preload` attribute values.** When would you use `preload="none"` instead of `preload="auto"`?

---

## Completion Checklist

- [ ] I can explain what multimedia is and name common media file formats
- [ ] I know which video formats (MP4, WebM, Ogg) and audio formats (MP3, WAV, Ogg) HTML supports
- [ ] I can write a `<video>` element with `<source>` elements and fallback text
- [ ] I understand all `<video>` attributes: `controls`, `width`, `height`, `autoplay`, `muted`, `loop`, `poster`, `preload`
- [ ] I know why `autoplay` must be paired with `muted` in modern browsers
- [ ] I can write an `<audio>` element with `<source>` elements and fallback text
- [ ] I understand all `<audio>` attributes: `controls`, `autoplay`, `muted`, `loop`, `preload`
- [ ] I know the difference between `<object>` and `<embed>`
- [ ] I can use `<object>` to embed a PDF with a fallback download link
- [ ] I understand the history of plug-ins and why they are no longer used
- [ ] I can find a YouTube video ID and construct the embed URL
- [ ] I can embed a YouTube video with `<iframe>`
- [ ] I know the key YouTube parameters: `autoplay`, `mute`, `loop`, `playlist`, `controls`
- [ ] I know that `loop=1` requires `playlist=VIDEO_ID` to work
- [ ] I have completed all five practice exercises
- [ ] I have studied the mini project and understand each section
- [ ] I can name at least five common beginner mistakes with HTML media

---

## Lesson Summary

HTML provides everything you need to enrich your webpages with video, audio, and embedded external content — all without any plugins.

**`<video>`** is the native HTML5 element for embedding video. It uses `<source>` child elements to list one or more video files in different formats, so every browser can find one it supports. Key attributes include `controls` (shows the player), `autoplay muted` (silent auto-play), `loop` (endless repeat), `poster` (thumbnail before play), and `preload` (loading strategy).

**`<audio>`** works almost identically to `<video>`, just without visual dimensions. It embeds playable audio using `<source>` child elements. The same attributes — `controls`, `autoplay`, `muted`, `loop`, `preload` — work the same way.

**`<object>` and `<embed>`** are older elements originally designed for browser plug-ins. Plug-ins (Flash, Java, ActiveX) are now completely unsupported in modern browsers. However, `<object>` remains useful today for embedding PDFs and other external documents, because it supports fallback content inside its tags. `<embed>` is simpler but has no fallback capability.

**YouTube `<iframe>` embedding** is the easiest way to add video to any page without file hosting or format concerns. You use the embed URL `https://www.youtube.com/embed/VIDEO_ID` and can add URL parameters to control behaviour: `autoplay=1`, `mute=1`, `loop=1` (with `playlist=VIDEO_ID`), and `controls=0`.

The key principle across all media: **always provide fallbacks**. Give `<video>` and `<audio>` fallback text with a download link. Give `<object>` a fallback message with a download link. For YouTube `<iframe>`, keep your embeds clean with the right parameters. Your media should degrade gracefully so every user — regardless of browser, device, or connection — has a usable experience.

---

*Sources: W3Schools — HTML Media (https://www.w3schools.com/html/html_media.asp), HTML Video (https://www.w3schools.com/html/html5_video.asp), HTML Audio (https://www.w3schools.com/html/html5_audio.asp), HTML Plug-ins (https://www.w3schools.com/html/html_object.asp), HTML YouTube (https://www.w3schools.com/html/html_youtube.asp)*

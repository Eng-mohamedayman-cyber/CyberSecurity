# 🌐 Full Stack Website Development Guide

This repository contains a comprehensive summary of web development fundamentals, covering Frontend and Backend technologies, with a deep dive into **HTML5** structure and tags.

---

## 🛠️ Web Development Roadmap

| 🎨 Frontend Technologies | ⚙️ Backend Technologies |
| :--- | :--- |
| 1. **HTML** (Structure) | 1. **PHP** (Programming Language) |
| 2. **CSS** (Styling & Design) | 2. **MySQL** (Database Management) |
| 3. **JavaScript (JS)** (Interactivity) | 3. **Laravel** (PHP Framework) |
| 4. **Libraries** (Helper Tools) | |
| 5. **React** (UI Library/Framework) | |

---

## 💻 Environment Setup & Best Practices

* 💻 **For Laptops/Desktops:** Use **VS Code** (Visual Studio Code).
  * *Tip:* Open the project folder on your Desktop, right-click, and select `Open with Code`.
* 📱 **For Mobile Devices:** Use **Spck Editor**.
* 📌 **Crucial Rule:** The entry-point file of any web project must be named exactly **`index.html`** in the root directory.

### Project Directory Structure
When starting a project, organize your workspace by creating these subfolders:
* `css/` (For stylesheets)
* `js/` (For scripts)
* `uploads/` (For uploaded user media)
* `libs/` (For external libraries)
* `index.html` (Main HTML document)

---

## 🏗️ Basic HTML5 Boilerplate Structure

In VS Code, you can instantly generate the standard formal page layout by pressing **`Shift + 1`** (which types `!`) and hitting `Enter`:

```html
<!DOCTYPE html> <!-- Instructs the browser to run the latest HTML5 engine -->
<html lang="en"> <!-- Sets the primary language of the website to English -->
<head>
    <meta charset="UTF-8">
    <!-- Configures responsive dimensions to scale perfectly on mobile screens -->
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Name of Website</title>
</head>
<body>

    <!-- All visible website content goes inside the body tag -->

</body>
</html>
```

---

## 🏷️ Essential HTML Tags Reference

### 1. Text Formatting
* `<p>`Text paragraph`</p>`: Defines a standard block-level paragraph.
* `<b>`Bold Text`</b>` or `<strong>`Important Bold Text`</strong>`: Makes text bold.
* `<i>`Italic Text`</i>` or `<em>`Emphasized Italic Text`</em>`: Italicizes text.
* `<big>`Large Text`</big>`: Increases the text size.
* `<small>`Small Text`</small>`: Decreases the text size.
* `<mark>`Highlighted Text`</mark>`: Highlights text with a yellow background marker.
* `<del>`Strikethrough Text`</del>`: Draws a line through text (e.g., Original Price: ~~100~~ ➡️ New Price: 80).
* `<u>`Underlined Text`</u>` or `<ins>`Inserted Text`</ins>`: Places a line underneath the text.
* `<sub>`H2O`</sub>`: Subscript (lowers text/numbers below the baseline).
* `<sup>`510`</sup>`: Superscript (raises text/numbers above the baseline, ideal for exponents).
* `<br>`: Line break element (moves to the next line; identical to `\n` in C++).
* `<hr>`: Horizontal rule (creates a solid dividing divider across the layout).
* `<center>`Centered Text`</center>`: Aligns containing elements to the middle of the screen.
* `&nbsp;`: Non-breaking space character entity used to insert physical spacing (not widely used nowadays).

### 2. Heading Tags
Headings establish content hierarchy and range from largest to smallest size:
* `<h1>`Heading 1 (Largest size / main document title)`</h1>`
* `<h2>` through `<h5>`: Various intermediate heading scales
* `<h6>`Heading 6 (Smallest available heading size)`</h6>`

### 3. Marquee, Hyperlinks & Images
* **Moving Text:** `<marquee direction="left">Text sweeps across the screen here</marquee>`.
* **Hyperlinks:** `<a href="URL_LINK">Clickable display text displayed to user</a>` *(where `href` means Hypertext Reference).*
* **Images:** `<img src="image_path_or_url" alt="fallback text description of the image">`.

---

## 📊 Table Architecture

Tables group tabular data using structural row and column wrappers:

```html
<table border="1"> <!-- Outer table container with a default visible border profile -->
    <thead> <!-- Groups header content (Historically heavily relied on for custom formatting) -->
        <tr> <!-- Declares a table row -->
            <th>Column Title A</th> <!-- Renders bold, centered column headings -->
            <th>Column Title B</th>
        </tr>
    </thead>
    <tbody> <!-- Contains primary table payload; reads data left-to-right -->
        <tr>
            <td>Standard Data 1</td>
            <!-- Merges two adjacent columns horizontally -->
            <td colspan="2">Merged Cells Payload</td> 
        </tr>
    </tbody>
    <tfoot> <!-- Groups summary footer details at the very end of the dataset -->
        <tr>
            <td>Summary Total</td>
            <td>00.00</td>
        </tr>
    </tfoot>
</table>
```

---

## 📜 Lists Reference

### Ordered Lists (Numbered)
Supports attributes like `start` (numerical starting point) and `type` (defines numbering styles like standard integers, Roman numerals, or letters):
```html
<ol start="1" type="1">
    <li>First Sequential Item</li>
    <li>Second Sequential Item</li>
</ol>
```

### Unordered Lists (Bulleted)
```html
<ul>
    <li>Bullet item</li>
    <li>Bullet item</li>
</ul>
```

### Description / Definition Lists
```html
<dl>
    <dt>Product Title (Definition Term)</dt>
    <dd>Product Specs and Specs Data (Definition Description)</dd>
</dl>
```

---

## 🎬 Multimedia Integration

* **Embedding Third-Party/YouTube Video:** In VS Code, rather than a raw address link, click Share ➡️ Embed ➡️ Copy the auto-generated code snippet containing an `<iframe>` container.
```html
<iframe src="embed_link" width="560" height="315" title="YouTube video player"></iframe>
```

* **Local Machine Video Files:** Render natively using `<video>` with optional media configuration controls:
```html
<!-- Direct source method -->
<video src="video_file.mp4" controls muted autoplay loop></video>

<!-- Robust multi-source professional method -->
<video controls>
    <source src="video_file.mp4" type="video/mp4">
    Your browser does not support the video tag.
</video>
```
*(Attributes explanation: `controls` displays native players, `muted` suppresses audio tracks, `autoplay` initializes playback on page load, `loop` restarts playback indefinitely).*

* **Local Machine Audio Files:** Uses the `<audio>` tag:
```html
<audio src="audio_file.mp3" controls></audio>
```

---

## 📝 Form Elements & User Input Control

Forms accept user submissions and rely on two primary `method` configurations:
1. **GET:** Appends input fields directly to the browser URL address line. Insecure and highly discouraged for processing credentials.
2. **POST:** Packages submission payloads privately inside the request payload body, keeping data hidden from URL logs.

*🔒 **Security Note:** Anyone can locally inspect masked input fields by right-clicking on a password textbox ➡️ choosing **Inspect**, and manually editing `type="password"` to `type="text"` to reveal input values.*

```html
<fieldset>
    <legend>Secure User Data Form Zone</legend> <!-- Outlines fields with a perimeter border and a caption heading -->
    
    <form action="processing_endpoint.php" method="POST">
        
        <!-- Standard Alphanumeric Text Input Field -->
        <label for="username">Username:</label>
        <input type="text" name="user_var" id="username" placeholder="Enter username inside box" maxlength="15" minlength="5">
        <br><br>
        
        <!-- Email Input Validation Control -->
        <label for="usermail">Email:</label>
        <input type="email" name="email_var" id="usermail" placeholder="user@domain.com">
        <br><br>
        
        <!-- Masked Sensitive Password Fields -->
        <label for="pass">Password:</label>
        <input type="password" name="pass_var" id="pass" placeholder="password">
        <br><br>
        
        <!-- Specialized Form Fields and Attributes -->
        <input type="date"> <!-- Calendar picker component -->
        <input type="datetime-local"> <!-- Aggregated regional date and clock selector -->
        <input type="week"> <!-- Picks a specific calendar week block -->
        <input type="time"> <!-- Standalone hours/minutes interface clock -->
        <input type="number"> <!-- Numeric restriction dial -->
        <input type="file"> <!-- Native device filesystem file upload button -->
        <input type="search"> <!-- Contextually styled query bar input search field -->
        <input type="url"> <!-- Target address hyperlink format constraint checking -->
        <br><br>

        <!-- Exclusive Selection Groups (Radio buttons require identical name scopes to enforce single selection) -->
        <label>Gender:</label>
        <input type="radio" name="gender" id="male" value="male">
        <label for="male">Male</label>
        
        <input type="radio" name="gender" id="female" value="female">
        <label for="female">Female</label>
        <br><br>

        <!-- Inclusive Multi-Selection Checkbox States -->
        <input type="checkbox" name="hobbies" id="ride" value="cycling">
        <label for="ride">Bike Riding</label>
        <br><br>

        <!-- Dropdown Selector Matrices (Select lists & structured Option Groups) -->
        <label>Select Track:</label>
        <select name="course_selection">
            <option value="">-- Choose Option --</option>
            <optgroup label="Frontend Basics">
                <option value="react">React Library</option>
                <option value="js">Core JavaScript</option>


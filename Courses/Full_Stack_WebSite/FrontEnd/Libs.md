# 📦 External Web Libraries Integration Guide (Libs)

This guide covers how to install, manage, and link external open-source front-end libraries (such as **Bootstrap** for responsive styling and **WOW.js** for scroll-triggered animations) in your web development projects.

---

## 🅰️ Bootstrap Integration Guide

Bootstrap is a powerful frontend library used for building fast, responsive, and mobile-first web pages.

### Method 1: Local Installation (Offline Files)
1. **Download:** Go to the official documentation website at [getbootstrap.com](https://getbootstrap.com).
2. **Extract:** Download the production source package, extract the compiled `.zip` bundle file, and navigate to the internal folders.
3. **Move Assets:** Copy the vital CSS and JS production asset files into your local project's `css/` and `js/` subfolders:
   * 📄 **`bootstrap.min.css`** (Move to your `css/` directory)
   * 📄 **`bootstrap.bundle.min.js`** (Move to your `js/` directory)

### Method 2: Remote Installation (Using CDN URLs)
Instead of hosting local copies, you can link directly to remote Content Delivery Network (CDN) links to save storage and optimize caching speeds.

```html
<!-- Place this inside your HTML <head> for styles -->
<link rel="stylesheet" href="https://jsdelivr.net">

<!-- Place this at the bottom of your <body> for functionality -->
<script src="https://jsdelivr.net"></script>
```

---

## 🅱️ WOW.js & Animate.css Integration Guide

**WOW.js** works alongside **Animate.css** to reveal rich, scroll-triggered visual micro-animations as a user moves down your page.

### Step 1: Downloading the Assets
1. Visit the official platform website at [wowjs.uk](https://wowjs.uk).
2. Click on the **GitHub** link option to view the open-source repository.
3. Click the green **`Code`** dropdown button and choose **`Download ZIP`**.
4. Unpack the zip file folder and retrieve these necessary files:
   * 📄 **`animate.css`** (The styling animation configuration stylesheet)
   * 📄 **`wow.js`** or the compressed production alternative **`wow.min.js`**

### Step 2: Linking Assets in your HTML Document
To ensure everything initializes smoothly, link your assets using this strict hierarchy:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Web Page with Libraries</title>

    <!-- 1. LINK CSS STYLESHEETS INSIDE THE HEAD TAG -->
    <!-- Bootstrap CSS -->
    <link rel="stylesheet" href="css/bootstrap.min.css">
    <!-- Animate CSS (Required for WOW.js) -->
    <link rel="stylesheet" href="css/animate.css">
</head>
<body>

    <!-- HTML Content goes here -->
    <h1 class="wow fadeInDown">Animated Title on Scroll</h1>

    <!-- 2. LINK JAVASCRIPT SCRIPTS AT THE VERY BOTTOM OF THE BODY TAG -->
    <!-- Bootstrap Bundle JS -->
    <script src="js/bootstrap.bundle.min.js"></script>
    
    <!-- WOW.js Library File -->
    <script src="js/wow.min.js"></script>
    
    <!-- 3. INITIALIZE WOW.JS ACTIVATION -->
    <script>
        new WOW().init();
    </script>
</body>
</html>
```

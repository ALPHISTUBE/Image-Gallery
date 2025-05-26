# Image Gallery with Auto & Manual Folders and Night Mode Toggle

## Overview

This is a simple and elegant client-side image gallery web application that supports:

- Uploading multiple images from your computer.
- Automatic grouping into folders based on filename patterns (auto-folders).
- Creating, editing, and managing manual folders.
- Importing images directly into manual folders.
- Marking images as favorites and filtering by favorites.
- Sorting images by date, name, or favorites.
- Viewing images in a fullscreen modal with navigation and favorite toggling.
- A dark/light mode toggle with saved preferences.
- Persistent data storage in browser localStorage.

---

## Important Note About Image Paths

**Must remember:** For images to load correctly by their paths (e.g., `/photo1.jpg`), the `index.html` file **and all image files must reside in the same folder** on your local machine or server.

If the images are located elsewhere or you open `index.html` directly as a file (without a local web server), the paths may not resolve correctly, causing images not to display.

For best results:

- Keep `index.html` and your image files in the **same folder**.
- Open the project through a local web server (e.g., VS Code Live Server extension or `python -m http.server`) rather than opening the HTML file directly.

---

## Auto Folder Naming & Customization

The application automatically groups images into **auto-folders** by extracting a cleaned folder name from each image filename.

This is done using the `extractAutoFolderName(filename)` function:

```js
function extractAutoFolderName(filename) {
    let name = filename.replace(/^\d{6}-/, '');               // Remove date prefix (e.g., '180525-')
    name = name.replace(/-\d+(?=\.\w+$)/, '');               // Remove trailing dash + digits before extension
    name = name.replace(/\.\w+$/, '');                        // Remove the file extension at the end
    name = name.replace(/-/g, " ");                            // Replace dashes with spaces
    return name;
}

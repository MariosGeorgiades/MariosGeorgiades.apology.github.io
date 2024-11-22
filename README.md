# Apology App

## Overview

The Apology App is a heartfelt interactive website designed to help you apologize and reconnect with a loved one. The site features interactive tabs for sharing your story, collecting suggestions for improvement, and reminiscing over shared memories. The purpose is to provide a creative and meaningful way to express your feelings and commitment.

## Features

- **Heart Animation and Background Elements**: A beautiful animated heart and flower backgrounds to convey emotions visually.
- **Dark Mode**: A toggle button allows the user to switch between light and dark themes for better accessibility and user comfort.
- **Tabs for Interaction**:
  - **Η Ιστορία μας**: A section to share the story of your relationship.
  - **Προτάσεις**: A place for your loved one to submit suggestions to improve your relationship, complete with a form for capturing names and messages.
  - **Αναμνήσεις**: A gallery of photo memories to relive happy moments.
- **Background Music**: Users can add their own background music by providing an mp3 file URL in the provided `<audio>` element.

## How to Use

1. **Open the App**: Open the HTML file in any modern web browser.
2. **Toggle Dark Mode**: Click the "Toggle Dark Mode" button in the top right corner to switch between light and dark themes.
3. **Interact with Tabs**: Click on the tab buttons to navigate between different sections ("Η Ιστορία μας", "Προτάσεις", "Αναμνήσεις").
4. **Submit Suggestions**: In the "Προτάσεις" tab, your loved one can fill in their name and provide suggestions to help improve the relationship. The suggestions are sent to a specified server endpoint.

## Adding Music

To add custom background music:

- Replace the `src` attribute in the `<audio>` tag with the URL of your preferred mp3 file.

```html
<audio id="backgroundMusic" loop autoplay>
    <!-- Add your music file link here -->
    <source src="https://www.example.com/your-song.mp3" type="audio/mpeg">
    Your browser does not support the audio element.
</audio>
```

## Adding Memories

You can add new images to the "Αναμνήσεις" section by modifying the following part of the HTML code:

```html
<div id="memories" class="tab-content">
    <h2>Αναμνήσεις</h2>
    <div class="memory-gallery">
        <img src="https://www.example.com/photo1.jpg" alt="Memory 1">
        <!-- Add more photos here -->
    </div>
</div>
```

Replace the `src` attributes with links to your own images.

## Server Setup for Suggestions

The "Προτάσεις" tab allows your loved one to submit suggestions. To handle these suggestions, you'll need to set up a server endpoint. Here's a basic example using Node.js and Express:

1. **Install Express**:
   ```bash
   npm install express
   ```
2. **Create a Server File (e.g., **``**)**:
   ```javascript
   const express = require('express');
   const bodyParser = require('body-parser');
   const app = express();
   const PORT = 3000;

   app.use(bodyParser.json());

   app.post('/submit-suggestion', (req, res) => {
       const { name, suggestion } = req.body;
       console.log(`Suggestion received from ${name}: ${suggestion}`);
       res.json({ status: 'success' });
   });

   app.listen(PORT, () => {
       console.log(`Server running on http://localhost:${PORT}`);
   });
   ```
3. **Update the HTML File**:
   - Replace `'https://your-server-endpoint.com/submit-suggestion'` with your server's URL.


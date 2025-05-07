# 📺 YouTube Fullscreen Enhancer

A simple CSS userscript/snippet that hides YouTube's fullscreen UI elements (controls, title, share/watch later buttons, etc.) by default — showing them only on hover. Perfect for users who want a cleaner and more immersive fullscreen video experience.

## ✨ Features

* Hides bottom chrome, title, and control icons in fullscreen mode
* Restores visibility only when any control is hovered
* Adds a smooth transition for better UX
* Lightweight and non-intrusive

## 🔧 How It Works

The CSS uses the `:has()` pseudo-class and a custom CSS variable (`--show-opacity`) to dynamically show/hide elements based on hover states. The transition ensures smooth appearance/disappearance.

## 📄 Code Explanation

```css
/* Hide everything by default in fullscreen */
.html5-video-player.ytp-fullscreen .ytp-chrome-bottom,
.html5-video-player.ytp-fullscreen .ytp-chrome-controls,
.html5-video-player.ytp-fullscreen .ytp-title,
.html5-video-player.ytp-fullscreen .ytp-progress-bar-container,
.html5-video-player.ytp-fullscreen .ytp-watch-later-icon,
.html5-video-player.ytp-fullscreen .ytp-share-icon {
  opacity: 0 !important; /* Make them invisible */
  transition: opacity 0.3s ease !important; /* Smooth transition */
  pointer-events: auto !important; /* Allow hovering */
}

/* Show everything if any one of them is hovered */
.html5-video-player.ytp-fullscreen:hover:has(.ytp-chrome-bottom:hover),
.html5-video-player.ytp-fullscreen:hover:has(.ytp-chrome-controls:hover),
.html5-video-player.ytp-fullscreen:hover:has(.ytp-title:hover),
.html5-video-player.ytp-fullscreen:hover:has(.ytp-progress-bar-container:hover),
.html5-video-player.ytp-fullscreen:hover:has(.ytp-gradient-bottom:hover),
.html5-video-player.ytp-fullscreen:hover:has(.ytp-gradient-top:hover),
.html5-video-player.ytp-fullscreen:hover:has(.ytp-watch-later-icon:hover),
.html5-video-player.ytp-fullscreen:hover:has(.ytp-share-icon:hover) {
  --show-opacity: 1; /* Set variable to show */
}

/* Apply that show-opacity to controls */
.html5-video-player.ytp-fullscreen .ytp-chrome-bottom,
.html5-video-player.ytp-fullscreen .ytp-chrome-controls,
.html5-video-player.ytp-fullscreen .ytp-title,
.html5-video-player.ytp-fullscreen .ytp-progress-bar-container,
.html5-video-player.ytp-fullscreen .ytp-gradient-bottom,
.html5-video-player.ytp-fullscreen .ytp-gradient-top,
.html5-video-player.ytp-fullscreen .ytp-watch-later-icon,
.html5-video-player.ytp-fullscreen .ytp-share-icon {
  opacity: var(--show-opacity, 0) !important; /* Use the variable to toggle visibility */
}
```

## 🛠 How to Activate

You can apply this style using any of the following methods:

### Option 1: Custom Browser Extension (like Stylus)

1. Install [Stylus](https://add0n.com/stylus.html) browser extension.
2. Create a new style for `youtube.com`.
3. Paste the CSS code from `style.css`.
4. Save and enable.

### Option 2: Inject via DevTools (temporary)

1. Open YouTube and press `F12` or `Ctrl+Shift+I`.
2. Go to the **Elements** tab → click on `+` in the Styles pane.
3. Paste the CSS code to see it in action.

## 📜 License

MIT License — feel free to use, modify, and share.

**Created by [letsconfuse](https://github.com/letsconfuse)**

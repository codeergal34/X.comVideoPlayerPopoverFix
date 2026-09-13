# X.com (Twitter) Video Player Popover Fix — Browser Extension

A lightweight, high-performance browser extension (Manifest V3) designed to fix the annoying white square box artifact (`div[popover]`) on [x.com](https://x.com/) video players across all Chromium-based browsers.

---

## 🎯 What This Extension Fixes

On **x.com** (formerly Twitter), users often encounter an unstyled white square box overlaying the video player and video controls. This issue is caused by a native `div[popover]` element rendering with default browser user-agent styles (opaque white background, borders, and padding).
 
## 🌐 Supported Browsers

Works with any **Chromium-based browser**:
- **Google Chrome**
- **Brave Browser**
- **Microsoft Edge**
- **Arc Browser**
- **Opera / Opera GX**
- **Vivaldi**

---

## ⚡ Injected Code Snippet

Upon page load on `https://x.com/*`, the extension runs:

```javascript
(function fixWhiteSquare() {
  const popover = document.querySelector('div[popover]');
  if (popover) {
    popover.style.setProperty('background-color', 'transparent', 'important');
    popover.style.setProperty('border', 'none', 'important');
    popover.style.setProperty('padding', '0', 'important');
    console.log('✅ Fix applied: The white square box is now hidden.');
  } else {
    console.log('❌ Could not find the popover element.');
  }
})();
```

And applies the companion instant stylesheet:

```css
div[popover] {
  background-color: transparent !important;
  border: none !important;
  padding: 0 !important;
}
```

---

## 📦 How to Install in Your Browser

### In Google Chrome / Brave / Edge / Arc:

1. Download or clone this repository to your computer.
2. Open your browser's extension management page:
   - **Chrome**: `chrome://extensions/`
   - **Brave**: `brave://extensions/`
   - **Edge**: `edge://extensions/`
   - **Arc**: `arc://extensions/`
3. Enable **Developer mode** (toggle switch in the top right or bottom left).
4. Click **Load unpacked** (top left).
5. Select the folder containing this extension:
   ```
   twitter-videoplayerfix
   ```
6. The extension **X Video Player Popover Fix** is now installed and active!

---
 

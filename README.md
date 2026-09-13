# X.com (Twitter) Video Player Popover Fix — Browser Extension

A lightweight, high-performance browser extension (Manifest V3) designed to fix the annoying white square box artifact (`div[popover]`) on [x.com](https://x.com/) video players across all Chromium-based browsers.

---

## 🎯 What This Extension Fixes

On **x.com** (formerly Twitter), users often encounter an unstyled white square box overlaying the video player and video controls. This issue is caused by a native `div[popover]` element rendering with default browser user-agent styles (opaque white background, borders, and padding).

This browser extension eliminates the issue by:
1. **Zero-Latency CSS Override**: Injects a declarative stylesheet that makes any `div[popover]` element transparent before it ever paints on screen (eliminating white flash).
2. **Page Load Script Injection**: Executes the fix function immediately on page load as requested.
3. **Dynamic SPA Observer**: Watches for newly mounted video players and tweet modals as you scroll through your feed using an efficient `MutationObserver` debounced with `requestAnimationFrame`.

---

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

## 🔍 How to Verify the Fix

1. Open [https://x.com](https://x.com) in your browser.
2. Open the Developer Tools console:
   - **macOS**: `Cmd + Option + I` (then click the **Console** tab)
   - **Windows / Linux**: `F12` or `Ctrl + Shift + I`
3. You will see the console confirmation:
   ```
   ✅ Fix applied: The white square box is now hidden.
   ```
4. Play any video on X — the white square artifact will be completely gone!
5. Click the extension icon in your browser toolbar to view the live status popup and manually re-test the fix at any time.

---

## 🔒 Privacy & Permissions

- **100% Local & Offline**: Operates strictly within your browser.
- **No Data Collection**: Does not track, store, or transmit any user information or browsing history.
- **Strict Scope**: Only activates on `https://x.com/*`.

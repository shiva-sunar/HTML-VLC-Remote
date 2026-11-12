# Modern VLC Mobile Web Remote

A clean, modern, and beautiful mobile web remote for VLC Media Player designed for Android and mobile browsers.

Designed specifically to run smoothly from mobile browsers over your local Wi-Fi network with touch-friendly controls, tactile feedback, and minimal in-file code using lightweight external libraries (Tailwind CSS, Font Awesome 6, and Alpine.js).

---

## ✨ Features

- **📱 Sleek Modern Mobile UI**: Tailored for Android phones with dark mode, high contrast, tactile active feedback, and thumb-friendly touch targets.
- **⚡ Reactive & Minimal In-file Code**: Uses Alpine.js and Tailwind CSS via CDN so in-file HTML/CSS/JS is concise, declarative, and easy to read.
- **⏸ Essential Quick Controls**: 
  - Main row: **Browse (📂)**, **Play / Pause (▶/⏸)**, and **Fullscreen (⛶)** toggle.
  - Seek slider flanked by **10s Backward & Forward Buttons** (hold for ~1s to choose jump intervals: 10s, 30s, 1m, 5m).
  - Volume control with dynamic percentage display.
- **⏱ Smart Local Time Progression**:
  - Automatically advances the seek bar and timestamp locally during playback without spamming your network with continuous background polling requests.
  - Automatically synchronizes with VLC upon interacting with controls or buttons.
- **📁 File & Folder Browser**:
  - In-page filesystem navigator (`requests/browse.xml`).
  - Remembers your **last opened folder** using `localStorage`.
- **⚙ Collapsible Advanced Controls**:
  - Playback navigation: **Previous**, **Backward (Speed Selector)**, **Stop**, **Forward (Speed Selector)**, and **Next**.
  - **Video Aspect Ratio & Crop**: Select aspect ratios (16:9, 4:3, 16:10, 2.35:1, Default, etc.) and a single-press **Crop** button that cycles through crop ratios with VLC's on-screen display.
  - **Dynamic Theme Switcher**: Choose between **Dark** (OLED/Zinc), **Light**, **Blueish** (Midnight Navy), and **Purple** (Amethyst) with instant switching and persistence in `localStorage`.
  - Delays & Speed: Audio delay, Subtitle delay, Playback speed slider (0.25x – 4x).
  - Modes: Shuffle, Loop, Repeat toggles.
  - **Subtitle & Audio Track Selector**: Lists all available audio and subtitle tracks (with language/description/codec information, compatible with multi-language VLC localizations) and highlights the currently selected track with checkmarks.

---

## 🚀 Setup & Installation

### Step 1: Enable VLC Web Interface
1. Open **VLC Media Player**.
2. Go to **Tools** > **Preferences** (or press `Ctrl + P`).
3. At the bottom left under **Show settings**, choose **All**.
4. In the left sidebar, navigate to **Interface** > **Main interfaces**.
5. Check the box for **Web** (`http`).
6. Expand **Main interfaces** in the tree and click on **Lua**.
7. Under **Lua HTTP**, set a **Password** of your choice (e.g., `vlc` or any password).
8. Click **Save** and **restart VLC**.

### Step 2: Install `vlc_remote.html`
Copy `vlc_remote.html` into your VLC HTTP web folder:

- **Windows**:
  ```text
  C:\Program Files\VideoLAN\VLC\lua\http\
  ```
  *(or `C:\Program Files (x86)\VideoLAN\VLC\lua\http\` for 32-bit installations)*

- **Linux**:
  ```text
  /usr/share/vlc/lua/http/
  ```

- **macOS**:
  ```text
  /Applications/VLC.app/Contents/MacOS/share/lua/http/
  ```

> *Tip: You can rename `vlc_remote.html` to `index.html` or `mobile.html` if you want it to load as default, or keep it named as `vlc_remote.html` to use alongside the default interface.*

### Step 3: Access the Remote from Mobile

1. Make sure your phone is connected to the **same Wi-Fi network** as your PC.
2. Find your computer's local IP address (e.g., `192.168.1.50`):
   - On Windows: Run `ipconfig` in Command Prompt.
3. Open your mobile browser and navigate to:
   ```text
   http://<YOUR-PC-IP>:8080/vlc_remote.html
   ```
4. When prompted for credentials by the browser:
   - **Username**: leave blank (empty)
   - **Password**: enter the password you configured in Step 1.

---

## 🛠 Tech Stack & Implementation Details

- **Single-File Architecture**: Self-contained `.html` file ready to drop into VLC's HTTP directory.
- **Modern Libraries (CDN)**:
  - **Tailwind CSS**: Eliminates custom inline CSS while providing a responsive Android-style dark aesthetic.
  - **Font Awesome 6**: Crisp, universally recognizable media and system icons.
  - **Alpine.js**: Lightweight declarative reactivity that replaces imperative DOM manipulation.
- **Backend Communication**: Directly interfaces with VLC's built-in HTTP Lua API:
  - `requests/status.json` & `requests/status.xml` for status updates & commands.
  - `requests/browse.xml` for browsing local storage directories.
- **Multi-language VLC Support**: Detects and parses audio/subtitle streams regardless of VLC's system language (English `Stream`, French `Flux`, German `Strom`, etc.).

---

## 📄 License

This project is licensed under the [GNU General Public License v2.0 (GPL-2.0)](LICENSE) — matching VLC's built-in Lua HTTP interface license.

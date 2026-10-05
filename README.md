# 🏀 Basketball Scorecard

A lightweight, responsive basketball scoreboard built with **HTML**, **CSS**, and **JavaScript**.

Track points for the **Home** and **Guest** teams, see who's in the lead at a glance, and run a game clock, all from your phone, tablet, or desktop.

---

## ✨ Features

- **Two-team scoring**: separate Home and Guest score displays.
- **Quick-score buttons**: add `+1` (free throw), `+2` (field goal), or `+3` (three-pointer) with one tap.
- **Live lead indicator**: automatically shows `Home`, `Guest`, or `Tied` after every score change.
- **Game timer**: counts up in `MM:SS` format once started; pressing Start again won't create duplicate timers.
- **New Game reset**: clears both scores, the lead indicator, and the timer in one click.
- **Responsive layout**: separate styles for small phones, with breakpoints ready for larger screens.
- **Installable icons**: favicon, Apple touch icon, and web app manifest included.

---

## 🛠️ Tech Stack

| Layer      | Technology                                                                 |
| ---------- | -------------------------------------------------------------------------- |
| Markup     | HTML5 (semantic `main`, `section`, `article`)                              |
| Styling    | Vanilla CSS3 (Flexbox, media queries)                                      |
| Logic      | Vanilla JavaScript (ES6+, DOM API, `setInterval`)                          |
| Fonts      | [Google Fonts](https://fonts.google.com/): **Michroma** (scores), **Roboto** (UI) |
| Background | [Unsplash](https://unsplash.com/) image (loaded via URL)                   |

---

## 📁 Project Structure

```
Basketball Scorecard/
├── index.html                   # App markup
├── styles.css                   # Styles + responsive breakpoints
├── script.js                    # Scoring, lead, and timer logic
├── site.webmanifest             # Web app manifest
├── favicon.ico                  # Browser favicon
├── favicon.svg                  # Scalable favicon
├── favicon-96x96.png            # PNG favicon
├── apple-touch-icon.png         # iOS home-screen icon
├── web-app-manifest-192x192.png # Manifest icon (192px)
└── web-app-manifest-512x512.png # Manifest icon (512px)
```

---

## 🚀 Getting Started

### Prerequisites

Any modern web browser (Chrome, Edge, Firefox, Safari). No installs required.

### Run Locally

**Option 1: Open directly**

Double-click `index.html` to open it in your browser.

> **Note:** Icon paths start with `/` (e.g. `/favicon.svg`), so favicons may not load when opening the file directly. The app itself still works.

**Option 2: Use a local server (recommended)**

Using the VS Code **Live Server** extension:

1. Open the project folder in VS Code.
2. Right-click `index.html` → **Open with Live Server**.

Or with Node.js:

```bash
npx serve .
```

Or with Python:

```bash
python -m http.server 8000
```

Then visit `http://localhost:8000` (or the URL shown in your terminal).

---

## 🎮 How to Use

1. Press **Start** to begin the game clock.
2. Tap **+1**, **+2**, or **+3** under a team to add points.
3. Watch the **Lead** display update automatically.
4. Press **New Game** to reset scores, lead, and timer.

---

## ⚙️ How It Works

All logic lives in [`script.js`](script.js):

| Function / Handler     | Responsibility                                                              |
| ---------------------- | --------------------------------------------------------------------------- |
| Score button listeners | Read `data-team` and `data-points` from each button and call `addScore()`.  |
| `addScore(team, pts)`  | Adds points to the correct team's score.                                    |
| `updateScore()`        | Writes the scores to the display inputs and calls `updateLead()`.           |
| `updateLead()`         | Compares scores and shows `Home`, `Guest`, or `Tied`.                       |
| Start listener         | Starts a 1-second `setInterval` that updates the `MM:SS` timer. Guarded by `isRunning`. |
| `endTimer()`           | Clears the interval and resets the running flag.                            |
| New Game listener      | Resets all state and the UI, then stops the timer.                          |

Score buttons are driven by **`data-*` attributes**, so adding a new point value only needs new HTML, not new JavaScript:

```html
<button class="scorecard-btn" data-team="home" data-points="1">+1</button>
```

---

## 📱 Responsive Breakpoints

| Device                | Range           | Status                    |
| --------------------- | --------------- | ------------------------- |
| Extra Small Mobile    | `≤ 480px`       | ✅ Styled                 |
| Small Mobile          | `481px – 767px` | 🧩 Breakpoint ready       |
| Medium / Tablet       | `768px – 1023px`| 🧩 Breakpoint ready       |
| Large / Desktop       | `1024px – 1279px`| 🧩 Breakpoint ready      |
| Extra Large           | `≥ 1280px`      | 🧩 Breakpoint ready       |

Base (non-media-query) styles act as the default for all screens wider than 480px.

---

## 🧭 Known Limitations

- The timer can't be paused; it only stops when **New Game** is pressed.
- Scores aren't saved, so refreshing the page resets the game.
- There is no way to undo or subtract points.

## 🔮 Possible Improvements

- [ ] Pause / resume for the game clock
- [ ] Undo last score / `-1` correction button
- [ ] Persist game state with `localStorage`
- [ ] Quarter / period tracking and countdown clock
- [ ] Fouls and timeouts counters
- [ ] Editable team names
- [ ] Full offline PWA support with a service worker

---

## 🤝 Contributing

Contributions, issues, and feature requests are welcome!

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/my-feature`
3. Commit your changes: `git commit -m "Add my feature"`
4. Push to the branch: `git push origin feature/my-feature`
5. Open a Pull Request

---

## 🙏 Credits

- Fonts: [Michroma](https://fonts.google.com/specimen/Michroma) & [Roboto](https://fonts.google.com/specimen/Roboto) via Google Fonts
- Background photo: [Unsplash](https://unsplash.com/)

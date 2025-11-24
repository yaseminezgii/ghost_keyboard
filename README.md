# 👻 Ghost Keyboard

**Ghost Keyboard** is a tiny browser game that tests your real typing skills:  
no key labels, no mercy, just your muscle memory.

Read the phrase, type it on a **blank virtual keyboard**, then see your **WPM**, **accuracy**, and a brutally honest **roast** at the end.

---

## 🎮 Gameplay Overview

1. **Choose Difficulty**
   - **NOOB (easy)** – Backspace enabled, chill neon theme.
   - **PRO (normal)** – Still fair, but longer phrases and quotes.
   - **HACKER (hard)** – **Backspace disabled**, aggressive red theme, serious phrases.

2. **Pick Language**
   - 🇺🇸 **ENG** – English geek/coding/pop culture phrases.
   - 🇹🇷 **TUR** – Turkish tech, memes, movie & series references.

3. **Start Game**
   - Tap **START GAME** to jump in.
   - A random phrase is shown in the **TARGET** box.
   - A ghost keyboard appears at the bottom — keys are mostly invisible.

4. **Type Blindly**
   - Tap the keys on the on-screen keyboard.
   - Your input is shown in the **YOU** line with a blinking cursor.
   - In **HACKER** mode, **Backspace is disabled** (you’ll see a warning).

5. **Finish & Score**
   - Hit **GO** (Enter key) to submit.
   - See:
     - **WPM (Words Per Minute)**
     - **Accuracy (%)**
     - Your **target phrase** vs **what you typed**
     - A random roast/message based on how well (or badly) you did.

6. **Share or Try Again**
   - **TRY AGAIN**: reloads and lets you play another round.
   - **SHARE RESULT**:
     - Uses the **Web Share API** on supported devices.
     - Falls back to copying a sharable text + URL to clipboard.

---

## ✨ Features

- **Invisible keyboard** – Letter keys are hidden until pressed.
- **3 difficulty levels** with different visual themes:
  - `theme-easy`, `theme-normal`, `theme-hard`.
- **English & Turkish phrase pools**:
  - Mix of coding terms, memes, movie/series quotes, and nerd culture.
- **Mobile-friendly UI**:
  - `viewport` meta tuned for mobile.
  - Larger touch targets and `touch-action: none`.
- **Haptics & Audio**
  - Uses `AudioContext` to play short “beep” sounds on keypress.
  - Uses `navigator.vibrate` where supported.
- **Live timer**
  - Real-time timer (seconds) while you type.
- **WPM & Accuracy calculation**
  - WPM is computed by standard `chars / 5 / minutes`.
  - Accuracy is per-character comparison of target vs input.
- **Roast system**
  - Different roast sets depending on accuracy, WPM, and difficulty.
- **Zero dependencies**
  - Pure **HTML + CSS + Vanilla JS**. No build step, no bundler, no framework.

---

## 🧱 Tech Stack

- **HTML5**
- **Modern CSS** (CSS variables, gradients, animations)
- **Vanilla JavaScript**
  - DOM manipulation only, no frameworks.
  - `AudioContext` for sound.
  - `navigator.share` and `navigator.clipboard` for sharing.
  - `navigator.vibrate` for feedback on supported devices.

---

## 🚀 Getting Started

### 1. Clone or Download

```bash
git clone <your-repo-url>.git
cd ghost-keyboard

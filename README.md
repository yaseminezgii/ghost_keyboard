# 👻 Ghost Keyboard

**Ghost Keyboard** is a tiny browser game that tests your *real* typing skills:  
no key labels, no mercy, just your muscle memory.

You read the phrase, type it on a blank virtual keyboard, then see your **WPM**, **accuracy**, **total score**, and a brutally honest **roast** at the end.

> Current version: **v2.6 – Daily Leaderboard + Challenge Links + Auto Reset**

---

## 🎮 Gameplay Overview

### Choose Difficulty

- **NOOB (easy)**  
  - Backspace **enabled**  
  - Chill neon theme  

- **PRO (normal)**  
  - Backspace **enabled**  
  - Longer phrases, more quotes & memes  

- **HACKER (hard)**  
  - Backspace **disabled** (🔒 key instead of ⌫)  
  - Aggressive red theme  
  - More chaotic / serious phrases  

Difficulty also affects how punishing the **live feedback** feels (screen shake + red glow on mistakes).

---

### Pick Language

- 🇺🇸 **ENG** – English geek / coding / pop culture phrases  
- 🇹🇷 **TUR** – Turkish tech, memes, movie & series references (and some inside jokes)

---

### Enter Username

- Type a username (min **2**, max **12** characters)  
- It’s stored in `localStorage` as `ghostUsername`, so it’s remembered next time  
- Used on the **daily leaderboard** (TOP HACKERS)

---

### Start Game

1. Tap **START GAME**  
2. A phrase appears in the **TARGET** box  
3. A ghost keyboard shows up at the bottom
   - **Letter keys are invisible** until you press them  
   - Special keys (⇧, ⌫/🔒, 123, space, GO) are always visible

---

### Type Blindly

- Tap the keys on the on-screen keyboard  
- Your input appears in the **YOU** line with a blinking cursor  
- In **HACKER** mode:
  - Backspace is completely disabled (🔒 key)  
- On each wrong character:
  - The screen **shakes** briefly  
  - Your input line gets a red **error glow**

---

### Finish & Score

- Hit **GO** (Enter key) to submit  
- You’ll see:

  - **WPM** – Words Per Minute  
    - Computed as `chars / 5 / minutes`  
  - **Accuracy (%)** – per-character comparison of target vs input  
    - Easy/Normal: case-insensitive  
    - Hard: case-sensitive  
  - **Time** – typing time in seconds  
  - **Total Score** – `WPM × (Accuracy / 100)`  
  - A **roast/message** based on how well (or badly) you did

---

### Share or Try Again

- **TRY AGAIN**
  - Sends you back to the start screen (auto reset)  
  - Refreshes the daily leaderboard  
  - Restores normal menu if you were in **Challenge Mode**

- **SHARE RESULT**
  - Uses the **Web Share API** on supported devices  
  - Fallback:
    - Copies a text summary + **challenge link** to clipboard  
    - Button text changes to `COPIED!` briefly

---

## 🏆 Daily Leaderboard & Challenge Links

### Daily Leaderboard

Scores are stored in **Supabase** in the `scores` table:

- The **TOP HACKERS** panel shows today’s best scores (top 10)  
- Leaderboard behavior:
  - Only shows scores from **today**  
  - Resets every midnight (local time)  
  - Has a live **countdown**: `RESET: HH:MM:SS`  
  - Highlights **your username** if you’re on the list  
- Uses **Supabase Realtime** to update automatically when new scores are inserted

Each record contains:

- `username`
- `score`
- `wpm`
- `accuracy`
- `time_taken`
- `created_at`

---

### Challenge Links (`?c=`)

When you share your result, the game generates a **challenge URL**:

- Pattern:  
  `https://ghostkeyboard.net...?c=<urlencoded phrase>`

When someone opens that link:

- The game goes into **Challenge Mode**:
  - Title changes from `GHOST / KEYBOARD` to `GHOST / CHALLENGE`  
  - Difficulty & language selectors are **hidden**  
  - Tutorial box shows a warning:
    - _“⚠️ CHALLENGE ACCEPTED – Friend sent you a specific phrase.”_  
- The target phrase is **exactly** the phrase from the link (instead of a random one)

After they finish:

- Challenge phrase is cleared in memory  
- URL is cleaned (`history.replaceState`)  
- **Reset Game** returns to normal mode with difficulty & language selectors visible again

---

## ✨ Features

- **Invisible keyboard**  
  - Letter keys start with `opacity: 0` and become visible only when pressed  
  - Special keys always visible (⇧, ⌫/🔒, 123, space, GO)

- **Three difficulty levels & themes**
  - `theme-easy`, `theme-normal`, `theme-hard`  
  - Each changes:
    - Accent color  
    - Glow color  
    - Background radial gradient  

- **Bilingual phrase pools**
  - English & Turkish  
  - Mixed with:
    - Coding & terminal jokes (`sudo rm -rf /`, `kubectl get pods`, SQL, git, npm…)  
    - Movie / series quotes  
    - Internet culture and meme lines  

- **Mobile-friendly UI**
  - `meta viewport` tuned for phones  
  - Large touch targets  
  - `touch-action: manipulation` for smoother taps

- **Haptics & Audio**
  - `AudioContext` for short “beep” sounds:
    - Different envelope for normal keys vs Enter  
  - `navigator.vibrate` used where supported

- **Live timer**
  - Big digital timer at the top (tabular numbers)  
  - Updates every 50 ms while playing

- **WPM & Accuracy calculation**
  - WPM: `chars / 5 / minutes`  
  - Accuracy: per-character comparison of target vs input  
  - Case-insensitive on Easy/Normal, case-sensitive on Hard

- **Roast system**
  - Different message pools depending on:
    - WPM range  
    - Accuracy range  
    - Extreme values (e.g. WPM = 0, ACC = 0, WPM > 250)  
  - Examples:
    - “AFK? Did you fall asleep? 💤”
    - “CYBORG DETECTED 🤖”
    - “You shall not pass! 🧙‍♂️”
    - “Toaster typing? 🍞”
    - “Emotional Damage. 💔”

- **Zero frontend dependencies**
  - Pure **HTML + CSS + Vanilla JS**  
  - One `index.html` file with everything inside  
  - No bundler, no framework, no build step

---

## 🧱 Tech Stack

- **HTML5**
- **Modern CSS**
  - CSS variables
  - Gradients
  - Animations
  - Responsive flexbox layout
- **Vanilla JavaScript**
  - DOM manipulation only
  - `localStorage` for username
  - `URLSearchParams` for challenge mode (`?c=...`)
- **Supabase**
  - Postgres table `scores`  
  - Inserts via JS client  
  - Realtime subscription for leaderboard updates
- **Web APIs**
  - `AudioContext` for sounds  
  - `navigator.share` for native share  
  - `navigator.clipboard` for copy fallback  
  - `navigator.vibrate` for subtle haptics  

---

## 🚀 Getting Started

### 1. Clone or Download

```bash
git clone https://github.com/yaseminezgii/ghost_keyboard.git
cd ghost-keyboard

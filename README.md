# Dice Roller

A simple, lightweight web app that simulates rolling one or more six-sided dice. Built with vanilla HTML, CSS, and JavaScript — no frameworks, libraries, or build tools required.

## Overview

The user specifies how many dice to roll, clicks a button, and sees the result both as text (e.g., `dice: 4, 2, 6`) and as a row of dice-face images. It's a useful small project for practicing DOM manipulation, randomization in JavaScript, and basic CSS styling.

## Features

- Roll any number of dice at once, set via a number input
- Generates a random value from 1–6 for each die rolled
- Displays results as plain text
- Displays a matching dice-face image for each roll
- Clean, centered layout with a styled button (hover/active states)

## File Structure

```
dice-roller/
├── Dice.html      # Page structure / markup
├── Dice.css       # Styling for layout, button, input, and dice images
├── Dice.js        # Dice-rolling logic and DOM updates
├── Images/        # Dice face images (not included — see Setup)
│   ├── 1.png
│   ├── 2.png
│   ├── 3.png
│   ├── 4.png
│   ├── 5.png
│   └── 6.png
└── README.md      # This file
```

## Technologies Used

- HTML5
- CSS3
- Vanilla JavaScript (ES6) — no external libraries or frameworks

## Setup / Installation

This is a static front-end project. No build step, package manager, or server is strictly required.

1. Put `Dice.html`, `Dice.css`, and `Dice.js` together in one folder.
2. Create an `Images` subfolder inside that same folder.
3. Add six dice-face images named `1.png` through `6.png` to the `Images` folder — one per possible roll value. The script expects this exact naming convention and the `.png` extension.
4. Open `Dice.html` in a web browser (double-click it, or right-click → Open With → your browser).

If your browser restricts local script/file access, you can instead serve the folder locally:

```bash
npx serve .
```

or

```bash
python -m http.server
```

then open the address it prints in your browser.

## Usage

1. Enter the number of dice to roll in the input field (defaults to 1).
2. Click **Roll Dice**.
3. The text result and matching dice-face images appear below the button.

## How It Works

### Dice.html

Defines the page structure: a heading, a label, a number input (`#numOfDice`) for choosing how many dice to roll, a **Roll Dice** button wired to call `rollDice()` on click, and two empty containers — `#diceResult` and `#diceImages` — that JavaScript fills in after each roll.

### Dice.css

Centers the `#container` and applies bold, sans-serif text for a clean, game-like look. The button uses a blue background with lighter hover and active states for click feedback. The number input is enlarged and centered to match. Dice images are fixed at 150px wide with small margins so multiple dice line up in a row.

### Dice.js

The `rollDice()` function is meant to:

1. Read the requested number of dice from the input field.
2. Loop that many times, generating a random integer from 1–6 each iteration via `Math.floor(Math.random() * 6) + 1`.
3. Collect each result and build an `<img>` tag pointing to `Images/{value}.png`.
4. Write the text summary into `#diceResult` and the image tags into `#diceImages`.

## Known Issues

The uploaded `Dice.js` currently has a few bugs that stop it from running correctly as-is:

1. **Variable name mismatch.** The results array is declared as `const value = []`, but later code calls `values.push(...)` and `values.join(...)`. Since `values` (plural) was never declared, this throws a `ReferenceError` and the function stops before finishing.
2. **Malformed image tag.** The template string for each `<img>` element is missing the closing quotation mark after the file extension and the closing `>` of the tag, producing invalid HTML once inserted into the page.
3. **No input validation.** There's no check for an empty, zero, negative, or non-numeric value in the dice-count field, so unusual input could produce no dice or unexpected behavior.

Let me know if you'd like these fixed.

## Customization Ideas

- Swap in custom dice-face artwork by replacing the images in `Images/` (keep the `1.png`–`6.png` naming).
- Support dice with a different number of sides by changing the `6` in the random-number calculation and adding matching images.
- Add a short roll animation or sound effect.
- Style each result as a card rather than plain text for a more polished feel.

## Browser Compatibility

Works in any modern browser that supports ES6 JavaScript (Chrome, Firefox, Edge, Safari). No polyfills needed.

## License

No license specified. Add one here (e.g., MIT) if you plan to share or open-source this project.

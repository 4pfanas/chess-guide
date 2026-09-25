<div align="center">

# ♔ Chess Guide

### A complete beginner's guide to the royal game, in one page.

Tap a piece. See exactly where it can go. Learn the rules that trip up every beginner.

![HTML5](https://img.shields.io/badge/HTML5-E34F26?logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?logo=javascript&logoColor=black)
![Dependencies](https://img.shields.io/badge/dependencies-none-2f8f79)
![Version](https://img.shields.io/badge/version-1.0-blue)

</div>

---

## Table of contents

1. [The idea](#the-idea)
2. [What it does](#what-it-does)
3. [What you learn](#what-you-learn)
4. [How it works](#how-it-works)
5. [Tech stack](#tech-stack)
6. [Project structure](#project-structure)
7. [Run it locally](#run-it-locally)
8. [Design notes](#design-notes)
9. [Limitations](#limitations)
10. [Roadmap](#roadmap)
11. [Related](#related)

---

## The idea

Most chess tutorials for beginners are either walls of text or videos you can't skim. Chess is a *spatial* game, so the fastest way to learn how a piece moves is to **see the squares light up**.

This guide puts one interactive board at the top of the page. Pick a piece, and its movement pattern is highlighted straight away. Below it are the rules and habits a new player needs, written in short, scannable lines.

It is the first version of a two-part project. The redesigned version is [chess-guide-v2](https://github.com/4pfanas/chess-guide-v2).

## What it does

- Draws a full **8×8 board** in the standard starting position using Unicode chess pieces.
- Lets you tap **any of the six piece cards** (King, Queen, Rook, Bishop, Knight, Pawn) to highlight where that piece can move.
- Labels every square with its **algebraic coordinate** (a1 to h8), so you learn board notation as you go.
- Explains the **goal of the game**, **seven core rules**, and **five beginner tips**.
- Works on phones and desktops, with no install.

## What you learn

| Section | Covers |
|---|---|
| **The Goal** | 8×8 board, 16 pieces each, White moves first, win by checkmate |
| **How Pieces Move** | Interactive highlighting for all six piece types |
| **Key Rules** | Check, checkmate, stalemate, capture, promotion, castling, en passant |
| **Beginner Tips** | Control the centre, develop knights and bishops, castle early, don't waste tempo, check opponent threats |

## How it works

**1. The board is generated, not hand-written.**
A 2D array called `START` holds the opening position. A nested loop builds 64 `div` squares, alternating light and dark using `(row + file) % 2`, and writes each square's coordinate label from the string `'abcdefgh'` plus `8 - row`.

```js
const START = [
  ['♜','♞','♝','♛','♚','♝','♞','♜'],
  ['♟','♟','♟','♟','♟','♟','♟','♟'],
  // ... four empty ranks ...
  ['♖','♘','♗','♕','♔','♗','♘','♖'],
];
```

**2. Piece cards drive the highlights.**
Each card is wired to a click handler. `clearHighlights()` removes the previous selection from every square and card, then the chosen piece's move squares get a `highlight` class, and its card gets `active`. CSS does the rest.

**3. The explanation updates alongside.**
The text panel below the board swaps to a short description of the selected piece, so what you see and what you read always match.

## Tech stack

| Layer | Choice | Why |
|---|---|---|
| Markup | HTML5 | A single self-contained page |
| Styling | CSS3 (Grid for the board) | An 8×8 grid maps naturally onto CSS Grid |
| Logic | Vanilla JavaScript | The state is tiny: one selected piece |
| Pieces | Unicode chess glyphs (♔ ♕ ♖ ♗ ♘ ♙) | No image assets, scales perfectly |
| Type | Playfair Display and Source Serif 4 | A classic, book-like feel that suits chess |

## Project structure

```text
chess-guide/
├── index.html   # markup, styles and script in one file
└── README.md
```

## Run it locally

```bash
git clone https://github.com/4pfanas/chess-guide.git
cd chess-guide
open index.html
```

No server, build tool or package install required.

## Design notes

- **Serif typography** was chosen on purpose: chess has a long literary tradition, and the serif faces make it feel like a well-made guide, not a web app.
- **Unicode pieces** keep the page to a single file and make the board crisp on any screen density.
- **One idea per screen section**, so a beginner never has to scroll through a wall of rules to find what they need.

## Limitations

- It is a **teaching aid, not a chess engine**. You can't play a game on it.
- The highlighted moves show the *pattern* of each piece; they don't account for other pieces blocking the way.
- No opening theory, endgames or tactics yet.

## Roadmap

- [ ] Playable two-player mode with legal-move checking
- [ ] Interactive examples for castling and en passant
- [ ] Simple tactic puzzles (forks, pins, skewers)
- [ ] Opening cheat sheet for beginners
- [ ] Dark mode

## Related

- [chess-guide-v2](https://github.com/4pfanas/chess-guide-v2): the redesigned version with collapsible sections and a piece-value table.

---

<div align="center">

Built by **[Anas Aslam](https://github.com/4pfanas)** · *Played for over 1,500 years.*

</div>

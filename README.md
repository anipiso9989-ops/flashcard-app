# Flashcard-Project

A local-first, single-file flashcard application built with vanilla HTML, CSS, and JavaScript. Designed with a severe modernist/editorial aesthetic, it focuses on bulk card creation, keyboard navigation, and simple spaced repetition without dependencies, accounts, or build pipelines.

---

## Features

### 1. Deck Library (Home View)

* Lists all decks alongside total card counts and due card counts.
* Minimalist layout: deck titles serve as the primary visual architecture with no dashboard widgets, sidebars, or complex charts.
* Quick entry points to create new decks or view existing ones.

### 2. Fast Bulk Card Entry

* Add cards rapidly during deck creation or append them to existing decks via the `+ ADD CARDS` modal.
* **Strict Line-by-Line Syntax:**
```text
Front Content::Back Content
```

* **Validation & Parsing:**
* Real-time card counter.
* Live error detection highlighting lines missing the `::` separator.
* Blocks submission if malformed lines exist (prevents silent data loss).
* Automatically trims whitespace and ignores blank lines.

### 3. Markdown & KaTeX Math Rendering

* Full rich-text support on both card faces using lightweight CDN dependencies (Marked and KaTeX).
* Supports standard Markdown (bold, italic, code spans, lists, links) alongside inline (`$...$`) and block (`$$...$$`) math formulas.
* HTML sanitization to guard against arbitrary script injection.

### 4. Deck Management & Inline Editing

* View the complete card inventory of any deck.
* Inline card editing for quick front/back corrections without dedicated edit screens.
* Rename decks or delete cards individually.
* Guarded destructive actions (deck/card deletions require explicit confirmation).

### 5. Distraction-Free Study Mode

* Reviews only cards that are currently due.
* Shows cards one at a time, displaying the front face first.
* Binary grading system (`DON'T KNOW` vs. `KNOW`) with no intermediate ease tiers.
* **Keyboard-First Controls:**
* `Space` — Reveal answer
* `ArrowLeft` — Don't Know
* `ArrowRight` — Know
* `Escape` — Exit / Cancel active dialog

* Clean progress counter (`07 / 12`) and a dedicated session-complete screen.

### 6. Transparent Spaced Repetition System (SRS)

* Simple laddered interval progression: **1d → 3d → 7d → 14d → 30d → 60d → 120d**.
* **Know:** Moves the card to the next interval step and calculates the next calendar due date.
* **Don't Know:** Resets the interval, marks the card due immediately, and recycles it back into the current study queue until answered correctly.
* New cards are immediately due upon creation.

### 7. Local-First Persistence & Portability

* **IndexedDB Storage:** Persists all decks, cards, edits, and SRS review metadata locally in the browser across reloads.
* **JSON Backup:** Built-in secondary import/export utility to backup or restore full application state.

---

## Tech Stack & Architecture

* **Architecture:** Single self-contained file (`index.html`). No build tooling, bundlers, or frameworks.
* **Core:** Semantic HTML5, Vanilla JavaScript (ES6+), and CSS3.
* **Typography & Styling:** Native system font stack (`Inter`, `SF Pro Display`, `Helvetica Neue`, `Arial`, sans-serif), strict black/white/gray color scheme, and whitespace-driven layouts.
* **External Dependencies (CDN only):**
* [Marked](https://marked.js.org/?utm_source=gemini) (Markdown parser)
* [KaTeX](https://katex.org/?utm_source=gemini) (LaTeX math typesetting)

---

## Getting Started

1. Download or save the app source as `index.html`.
2. Double-click or open `index.html` directly in any modern desktop or mobile web browser. No local web server (`http-server`, Node, etc.) required.

# Quiet — Version 2: a real web app, hosted on GitHub

The single HTML file became a proper project (Vite + TypeScript) on a better e-book engine
([foliate-js](https://github.com/johnfactotum/foliate-js)), published free on GitHub Pages.

**Try it:** https://2n0m0a5.github.io/quiet-reader-version-2/

**New since v1:** a library that keeps your books with covers and "Continue reading"; remembers where you stopped;
EPUB, MOBI, AZW3, FB2 and CBZ; page mode; line spacing; sub-chapters in the contents; scripts inside books blocked.

## The series

I'm building a calm, simple e-book reader in public, one version per video.

| # | Version | Code |
|---|---|---|
| 1 | One HTML file | [quiet-reader-version-1](https://github.com/2n0m0a5/quiet-reader-version-1) |
| 2 | A real web app, hosted on GitHub | [quiet-reader-version-2](https://github.com/2n0m0a5/quiet-reader-version-2) |
| 3 | Installable, works offline | [quiet-reader-version-3](https://github.com/2n0m0a5/quiet-reader-version-3) |
| 4 | Android app | [quiet-reader-version-4](https://github.com/2n0m0a5/quiet-reader-version-4) |
| 5 | Android app, version 2 | [quiet-reader-version-5](https://github.com/2n0m0a5/quiet-reader-version-5) |

## Run it on your computer

You need [Node.js](https://nodejs.org) (LTS) installed.

```sh
npm install     # first time only: downloads the tools
npm run dev     # starts Quiet at http://localhost:5173
```

Open the link it prints in Chrome. Changes to the code show up instantly.
Press `Ctrl+C` in the terminal to stop it.

## Other commands

| Command | What it does |
|---|---|
| `npm run build` | Checks the code for errors and builds the final app into `dist/` |
| `npm run preview` | Serves the built app from `dist/`, to check it before publishing |

## Where things are

```
index.html              The page layout
src/main.ts             Switches between library and reader; connects buttons and settings
src/settings.ts         Reading preferences (theme, font size, mode) and saving them
src/library/db.ts       The library database (books, covers, reading positions) in IndexedDB
src/library/import.ts   Adding a book: reads its title, author and cover
src/library/library-view.ts  The library screen
src/reader/reader.ts    Opens a book, turns pages, continuous scroll
src/reader/book-css.ts  How the text inside the book is styled
src/ui/toc.ts           The contents list
src/ui/toast.ts         Short messages at the bottom of the screen
src/styles/tokens.css   Colours and themes — the design system
src/styles/app.css      Layout and components
vendor/foliate-js/      The e-book engine (see QUIET_VENDOR.md inside)
.github/workflows/      Builds and publishes the website
```

Books are stored in the browser on the device that added them. Nothing is uploaded anywhere.

## Security

Books can contain JavaScript. The Content-Security-Policy in `index.html` makes sure
only Quiet's own code runs. Do not remove it.

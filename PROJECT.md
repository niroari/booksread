# Books Read — Personal Website

## What It Is
A personal website displaying books Nir has read, pulled live from a Google Sheet.

## Data Source
Google Sheet (public, view-only):
https://docs.google.com/spreadsheets/d/1zuRalFET71bg02sjHAr2xlv_8WeTi_5mESLWvjCZREc

Spreadsheet columns: Book Title | Author | Genre
124 books: 78 English + 46 Hebrew

## Design Decisions
- Warm, cozy wooden library vibe
- Dark espresso + cream color palette
- Books displayed as cards with covers (auto-fetched by title)
- Separated by language: English section / Hebrew section (RTL)
- Genre shown as a color-coded badge on each card
- Genre filter + search bar per section
- Plain HTML + CSS + vanilla JavaScript (no frameworks)
- Hosted on GitHub Pages

## Build Plan
- [x] Step 1 — Add Genre column to spreadsheet + fill all 124 books
- [x] Step 1b — Style the spreadsheet (warm brown theme, genre badge colors)
- [x] Step 1c — Add genre dropdown validation to Excel file (C3:C200)
- [x] Step 2 — Build HTML/CSS website skeleton (layout + visual design)
- [x] Step 3 — Connect to Google Sheets (live data pull via CSV export URL)
- [ ] Step 4 — Book covers (pre-fetch via Python script → covers.json, avoids live API issues)
- [ ] Step 5 — Search + genre filter (wired up, visual only for now)
- [ ] Step 6 — Deploy to GitHub Pages

## Tech Stack
- Plain HTML + CSS + vanilla JavaScript
- Google Sheets CSV export as data source
- Google Books API + Open Library API for covers (to be pre-fetched)
- GitHub Pages for hosting

## Cover Strategy (decided)
Live API calls for Hebrew books are unreliable (Google Books indexes Hebrew poorly).
Plan: run a one-time Python script to fetch covers for all 124 books → save to covers.json.
Website reads from covers.json instead of making live API calls.
This also makes the site load faster.

## How to Run Locally
```
cd "/Users/nirozari/Projects/Books Read"
python3 -m http.server 8080
```
Then open http://localhost:8080 in your browser.
(Must use a local server — opening index.html directly blocks network requests.)

## File Structure
```
/Users/nirozari/Projects/Books Read/
├── CLAUDE.md               # Nir's preferences and working rules
├── PROJECT.md              # This file
├── index.html              # The website (HTML + CSS + JS in one file)
└── ספרים שקראתי.xlsx       # Source spreadsheet (also lives on Google Sheets)
```

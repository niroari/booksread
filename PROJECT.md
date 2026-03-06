# Books Read — Personal Website

## What It Is
A personal website displaying books Nir has read, with live data from Firebase Firestore.
Books are separated into English and Hebrew sections, searchable and filterable by genre.
Clicking a book shows a summary pulled from Wikipedia, Google Books, or Open Library.

## Live URLs
- Site: https://booksread-pi.vercel.app/
- Repo: https://github.com/niroari/booksread

## Data Source
Firebase Firestore — `books` collection.
Each document: `{ title, author, genre, language, createdAt }`

Original 124 books (78 English + 46 Hebrew) imported from Google Sheets via one-time migration.
Google Sheets URL (kept for reference):
https://docs.google.com/spreadsheets/d/1zuRalFET71bg02sjHAr2xlv_8WeTi_5mESLWvjCZREc

## Design
- Dark editorial aesthetic — deep warm black, amber accents, film grain
- Fonts: Cormorant (display) + IBM Plex Mono (labels/data)
- Text-only book cards in a tight grid (no covers — APIs were too unreliable)
- Two sections: English (LTR) / Hebrew (RTL)
- Genre color-coded badges on each card
- Search + genre filter + sort (title / author / genre) per section
- Click a card → side panel slides in with book summary

## Features Built
- [x] Book grid — English + Hebrew sections, RTL support
- [x] Search, genre filter, sort per section
- [x] Add Book modal — auto-detects Hebrew/English from title, switches genre list accordingly
- [x] Book summary panel — slides in from right on card click
- [x] Summary sources: Hebrew Wikipedia (he) → Google Books → Open Library (Hebrew books); Google Books → English Wikipedia → Open Library (English books)
- [x] Summary caching in Firestore (`summaries` collection) — first fetch hits API, all subsequent clicks are instant
- [x] Firebase Firestore as data backend
- [x] Deployed on Vercel (auto-deploys on push to main)

## Tech Stack
- Plain HTML + CSS + vanilla JavaScript (no frameworks)
- Firebase Firestore (data + summary cache)
- Vercel (hosting, auto-deploy from GitHub)
- APIs: Google Books, Wikipedia (he + en), Open Library

## Firebase Collections
- `books` — all books: `{ title, author, genre, language, createdAt }`
- `summaries` — cached summaries: `{ text, source, title, author, cachedAt }`

## How to Run Locally
```
cd "/Users/nirozari/Projects/Books Read"
python3 -m http.server 8080
```
Open http://localhost:8080 — must use a local server (direct file open blocks Firebase requests).

## How to Deploy
```
git add index.html
git commit -m "description"
git push
```
Vercel auto-deploys on push to main. No build step needed.

## One-Time Migration (already done)
To import books from Google Sheets into Firestore, run in the browser console:
```
importBooksFromSheets()
```

## File Structure
```
/Users/nirozari/Projects/Books Read/
├── CLAUDE.md               # Nir's preferences and working rules
├── PROJECT.md              # This file
├── index.html              # The entire website (HTML + CSS + JS)
└── ספרים שקראתי.xlsx       # Original spreadsheet (reference only)
```

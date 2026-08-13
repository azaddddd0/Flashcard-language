# Casual Oral 0711 — flashcards

A single-page flashcard app for a bilingual English–Chinese phrase list.
No build step, no dependencies. Everything is in `index.html`.

## Files

| File | What it does |
|---|---|
| `index.html` | The whole app: 547 cards, all logic, all styling |
| `manifest.webmanifest` | Lets the phone install it to the home screen |
| `sw.js` | Service worker, so it opens offline |
| `icon-*.png` | Home screen icons |

## Put it online (GitHub Pages)

1. Create a new repository, e.g. `casual-oral`. Public. Tick nothing else.
2. Upload all six files to the root of the repository, not inside a folder.
3. Go to **Settings → Pages**. Under *Build and deployment*, set Source to
   **Deploy from a branch**, branch `main`, folder `/ (root)`. Save.
4. Wait one or two minutes. The URL appears at the top of that same page:
   `https://<your-username>.github.io/casual-oral/`

## Install it on the phone

Open the URL in **Safari** (iOS) or **Chrome** (Android), then:

- iOS: Share button → *Add to Home Screen*
- Android: menu → *Install app* / *Add to home screen*

It then opens full screen with no address bar, and works without a signal.

## Updating the vocabulary

Replace `index.html` with the newly generated file, and bump the version
number in `sw.js` (`casual-oral-v1` → `casual-oral-v2`). Without that bump,
phones that already installed the app may keep serving the old cached deck.

Progress is stored in the browser under the key prefix `co0711:`, keyed by the
English text of each phrase. Replacing the deck does not wipe your stars or
your snoozed words, and newly added phrases simply show up unmarked.

## Controls

| Action | Effect |
|---|---|
| Tap card | Flip between English and Chinese |
| Swipe left | Next card |
| Swipe right | Previous card |
| ✕ | Add a star (max 5), goes to 生词本 |
| ✓ | Mark as well known, hidden for 7 days |

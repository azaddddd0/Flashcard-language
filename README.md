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
| Tap card | Flip between English and Chinese (or the detail view, if the word has one) |
| Swipe left | Next card |
| Swipe right | Previous card |
| Hold (long-press) | Open this word in the edit form |
| ✕ | Add a star (max 5), goes to Wordbook |
| 🗑 | Send to the Bin — won't show up in study again until you restore it |

## Managing the vocabulary in-app

**+ Vocab** opens two tabs:

- **Add / Edit** — add a brand-new word (English, Chinese, an optional English
  explanation and example sentence, and a section — with an option to type a
  new section name), or edit one you already have. Long-pressing any card
  during study also opens straight into this form for that word.
- **Search** — search existing words by English or Chinese, tap a result to
  edit it.

Editing a *built-in* word can't change its English text (that's its lookup
key), but you can correct its Chinese translation, explanation, example, or
section, or hide it from the deck entirely. Editing a *custom* word (one you
added yourself) lets you change everything, including deleting it outright.

**Review** browses the entire deck as a plain list — filter by section, or
sort by date added to see what's newest. Tap any entry to edit it.

**Daily** sets a daily word-count goal and tracks a streak, similar to
百词斩/扇贝单词. "Start today's session" builds a queue of words you
haven't studied yet, topped up with starred words if needed, and every ✕ or
🗑 during that session (or any normal study session) counts toward the day's
total.

**CH** toggles the Chinese translation on or off everywhere in the app —
useful once you know a word well enough to test yourself in English only.

**★ Wordbook** has two tabs: **Starred** (words you've marked as tricky, up
to five stars each) and **Bin** (words you've said you don't need to learn
anymore — tap the ✕ next to any binned word to restore it to the deck).

All of this is saved in the same per-device storage as your stars and bin,
so it survives closing the app but stays local to that browser/device — it
does not sync back to this repository or to Notion.

## Updating the vocabulary from Notion

Replace `index.html` with the newly generated file, and bump the version
number in `sw.js` (`casual-oral-v4` → `casual-oral-v5`, and so on). Without
that bump, phones that already installed the app may keep serving the old
cached deck. Progress is stored under the key prefix `co0711:`, keyed by the
English text of each phrase, so replacing the deck does not wipe your stars,
your snoozed words, or any custom words/edits you've added in-app — as long
as the English text of a word doesn't change between versions, its stars
carry over automatically.

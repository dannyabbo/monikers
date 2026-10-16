# Monikers at Home

A pass-the-phone web version of the party game [Monikers](https://boardgamegeek.com/boardgame/156546/monikers) (Alex Hague & Justin Vickers). Unofficial; all card text is original.

One deck, three rounds:

1. **Anything goes**: say anything except the name.
2. **One word**: exactly one word per card.
3. **Charades**: no words.

## Features
- Deck building by **draft** (each player secretly keeps favorites from a hand), **quick deal**, or **write your own** names (Celebrity style)
- 2 to 4 teams, 30/45/60/90 second turns, cards worth 1 to 4 points
- Skip, end-of-turn undo, "did they get it at the buzzer?" check, leftover-time carry-over
- Survives a reload or locked phone (comes back paused), keeps the screen awake during turns
- Installable to the home screen and works offline (PWA)

## Play on your phones
It's a static site: `index.html` plus a manifest, service worker and icons. No build step.

**GitHub Pages:** repo Settings → Pages → Source "Deploy from a branch" → pick the branch and `/ (root)`. The game is then at `https://<user>.github.io/monikers/`. On iPhone, open it in Safari → Share → Add to Home Screen.

**Locally:** `python3 -m http.server` and open `http://localhost:8000`.

# Monikers at Home

A pass-the-phone web version of the party game [Monikers](https://boardgamegeek.com/boardgame/156546/monikers) (Alex Hague & Justin Vickers). Unofficial; all card text is original.

One deck, three rounds:

1. **Anything goes**: say anything except the name.
2. **One word**: exactly one word per card.
3. **Charades**: no words.

## Features
- **Multi-phone play:** the host taps *Host a game* and gets a 4-letter room code. Everyone else opens the site on their own phone, taps *Join a game* and types the code (or opens the invite link). Everyone drafts on their own phone at the same time. During a turn the clue-giver sees the card, their teammates see "Guess!", and the other team sees the card so they can keep it honest.
- **One-phone mode:** pass a single phone around, no internet needed
- Deck building by **draft** (each player secretly keeps favorites from a hand), **quick deal**, or **write your own** names (Celebrity style)
- 2 to 4 teams, 30/45/60/90 second turns, cards worth 1 to 4 points
- Skip, end-of-turn undo, "did they get it at the buzzer?" check, leftover-time carry-over
- Survives a reload or locked phone (comes back paused), keeps the screen awake during turns
- Installable to the home screen and works offline (PWA)

## How multi-phone works
The host's phone runs the game. Other phones connect to it directly (WebRTC) using [PeerJS](https://peerjs.com/) 1.5.5, which is bundled in `vendor/` (MIT license). The PeerJS free cloud server only introduces the phones to each other. There are no accounts and no database.

- The host's phone has to keep the page open for the whole game. If the host reloads, the room reopens with the same code and everyone reconnects.
- A player who reloads or whose phone sleeps rejoins automatically.
- Some strict networks block peer-to-peer connections. PeerJS falls back to its free relay server, but if a phone still can't connect, switching it from Wi-Fi to cellular (or the other way) usually helps.
- To test against your own PeerServer, add `?peer=host:port` to the URL.

## Play on your phones
It's a static site: `index.html` plus a manifest, service worker and icons. No build step.

**GitHub Pages:** repo Settings → Pages → Source "Deploy from a branch" → pick the branch and `/ (root)`. The game is then at `https://<user>.github.io/monikers/`. On iPhone, open it in Safari → Share → Add to Home Screen.

**Locally:** `python3 -m http.server` and open `http://localhost:8000`.

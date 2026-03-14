# 🎮 Tank Rivals

A local-network turn-based artillery game for 2 players. Pick a skin, customize your tank in the Garage, then battle across procedurally generated terrain.

## Features

- **8 battle skins** — Tanks, Gorillas (banana throws), Halloween, Christmas, 4th of July, Valentine's, St. Patrick's Day, Space
- **Garage upgrade system** — 7 points per player across Hull, Barrel, Engine, Scope, Treads, Ammo, Coating
- **8 tank colors** per player
- **Local network multiplayer** via WebRTC (PeerJS) — works on any device on the same WiFi
- **Hot-seat mode** — same device, pass-and-play
- **Procedural terrain** that deforms on hit
- **Wind system** that changes each turn
- **Trajectory preview** line

## How to Play

### Same Device (Hot-seat)
1. Open the page in a browser
2. Pick a skin → click **Same Device (Hot-seat)**
3. Both players customize in the Garage → **BATTLE!**
4. Take turns adjusting angle/power and firing

### Local Network (different devices on same WiFi)
1. **Player 1** opens the page → picks skin → clicks **Create Room (Host)**
2. Share the 6-character room code with Player 2
3. **Player 2** opens the page on their device → enters the code → **Join Room**
4. Game starts automatically when both players are connected

### Controls
| Key | Action |
|-----|--------|
| `← →` | Adjust angle |
| `↑ ↓` | Adjust power |
| `Space` | Fire |
| Sliders | Mouse control for angle/power |

## Running Locally

### Option 1 — Node `serve` (recommended)
```bash
npx serve . -l 3000
```
Then open http://localhost:3000

### Option 2 — Python
```bash
python3 -m http.server 3000
```
Then open http://localhost:3000

### Option 3 — VS Code Live Server
Install the **Live Server** extension, right-click `index.html` → Open with Live Server.

## Project Structure

```
tank-rivals/
├── index.html      # Entire game — single self-contained file
├── .gitignore
└── README.md
```

The game is intentionally a **single HTML file** with no build step, no dependencies to install, and no server-side code. Everything runs in the browser. PeerJS handles WebRTC signaling through their free public server.

## Push to GitHub

```bash
# 1. Create a new repo on github.com (name it e.g. tank-rivals)
#    Do NOT add a README or .gitignore — the repo must be empty

# 2. Add the remote (replace YOUR_USERNAME and YOUR_REPO)
git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO.git

# 3. Push
git push -u origin master
```

### Enable GitHub Pages (free hosting)
1. Go to your repo on GitHub → **Settings** → **Pages**
2. Source: **Deploy from a branch** → branch `master` → folder `/ (root)`
3. Click **Save** — your game is live at `https://YOUR_USERNAME.github.io/YOUR_REPO/`

Share that URL with your siblings — anyone on any device can open it.

---

## Deployment

The file deploys as-is to any static host:
- **GitHub Pages** — push to a `gh-pages` branch or enable Pages on `main`
- **Netlify / Vercel** — drag & drop the folder
- **S3** — upload `index.html` with public-read ACL

## Network Notes

- Uses **PeerJS** (peerjs.com) for WebRTC signaling — requires internet access for the initial handshake even on LAN
- Once connected, gameplay data flows peer-to-peer (direct device to device)
- Works across different devices on the same WiFi, or even over the internet

## License

MIT

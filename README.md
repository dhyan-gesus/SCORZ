# SCORZ

**Voxel football for the browser.** Play 3v3 to 5v5 matches, master a style, use abilities, and climb ranked. Play solo, with friends online, or offline.

## Features

- Fast 3D football with keyboard, controller, and phone touch controls
- 10 player styles, each with abilities
- Ranked play, Flow, skins, clubs, kits, and a game pass
- Quick matches, featured modes, replays, and item-based Lawless matches
- Online rooms for playing with friends

## Play

Open [`docs/index.html`](docs/index.html) in Chrome or Edge. The built game is a single file and can be played offline.

## Run locally

Install [Node.js](https://nodejs.org/) (LTS), then open this project folder in a terminal and run:

```bash
npm install
npm run build
```

Open `docs/index.html` in your browser to play.

To run the automated tests:

```bash
npx playwright install chromium
npm test
```

The Playwright browser installation is only needed once.

## Play online with friends

Online rooms require the SCORZ server. To run it locally:

```bash
npm install
npm run build
npm run server
```

Open [http://localhost:8787](http://localhost:8787) in your browser and choose **PLAY WITH FRIENDS**. Keep the terminal running while you play. Press `Ctrl+C` to stop the server.

To let friends join over the internet, deploy the server to a Node.js host such as Render, Railway, or Fly.io. Use:

- **Build command:** `npm install && npm run build`
- **Start command:** `npm run server`

The host must support WebSockets. When the server is available over HTTPS, the game connects securely over WSS. For a static copy hosted elsewhere, enter the server’s WSS address under **PLAY WITH FRIENDS → SERVER ADDRESS**.

Player accounts are stored on the server. Set `DATA_DIR` to persistent storage if your host can erase local files when restarting. Keep account and report data out of public repositories.

## Build for CrazyGames

Create the CrazyGames build and its cover images with:

```bash
npm run build:crazygames
npm run covers
```

The game file is generated at `dist/crazygames/index.html`; cover images are generated in `dist/covers/`.

To enable online rooms in that build, set the server address before building:

```powershell
$env:SCORZ_SERVER="wss://your-server-address/ws"; npm run build:crazygames
```

Without a server address, online rooms are hidden in the CrazyGames build. Check [CrazyGames’ current submission requirements](https://docs.crazygames.com/requirements/intro/) before submitting.

## Project layout

```text
src/               Game source files
build.js           Builds the browser game
docs/index.html    Built game for local play and static hosting
server/            Online multiplayer server
test/              Automated tests
tools/covers.js    Generates CrazyGames cover images
CLAUDE.md          Project guidance for Claude Code
ROADMAP.md         Planned features and prompts
```

Edit files in `src/`, then run `npm run build` to regenerate `docs/index.html`.

## Credits

- [Three.js](https://threejs.org/) r128 — MIT License
- Jersey 10, Jersey 15, and Silkscreen fonts — SIL Open Font License 1.1

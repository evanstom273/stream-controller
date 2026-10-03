# Silverbullet Stream Controller

Mobile-first OBS remote + animated overlay system.

**Stack:** Vite, React, TypeScript, Tailwind CSS, Node/Express, obs-websocket-js.

## Architecture
Phone/browser → local bridge → OBS WebSocket  
OBS Browser Source → React overlay → local bridge

The bridge is intentional: OBS is local software, and a hosted HTTPS page talking directly to a local insecure `ws://` endpoint is fragile in modern browsers. The bridge also keeps the OBS password off the frontend. OBS 28+ already includes obs-websocket; v5 normally uses port 4455.

## v0.1
- OBS status
- Studio Mode-aware scene buttons (scene → Preview)
- Transition button
- Mic/music mute
- Stream Plan editor
- 450px animated Stream Plan overlay
- persistent global Questionable Decisions counter scaffold
- mobile-first UI

## Run
1. Clone the repo and run `npm install`.
2. OBS → Tools → WebSocket Server Settings → enable it and keep authentication on.
3. Run `npm run dev`.
4. PC controller: `http://localhost:5173`
5. Phone: `http://YOUR-PC-IP:5173` or your Tailscale IP.
6. OBS Browser Source: `http://127.0.0.1:5173/overlay`, 1920×1080.
7. First bridge launch creates `data/config.json`. Add the OBS WebSocket password there. Default audio names are `Mic/Aux` and `Media`.

`data/` is gitignored so credentials and live state never go to GitHub.

## Planned
Settings UI + OBS input dropdowns; generic counters; temporary cards / Currently Doing; animated Questionable Decisions + history; Hardcore world tracker; game profiles; YouTube/Twitch chat; PWA install.

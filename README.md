# Silverbullet Stream Controller

A zero-backend, mobile-first OBS remote built with **Vite + React + TypeScript + Tailwind CSS**.

The browser connects **directly to OBS WebSocket** using `obs-websocket-js`. No Python script, Node bridge, or helper process is required while streaming.

## v0.2

- direct phone/browser → OBS connection
- connection address + password stored only in that browser's local storage
- Studio Mode-aware scene buttons: scenes go to **Preview**
- big **Transition** button
- Studio Mode toggle
- OBS input discovery + selectable mic/music controls
- Stream Plan editor state
- global persistent **Questionable Decisions** counter
- mobile-first UI

## OBS setup

OBS 28+ includes obs-websocket.

1. OBS → **Tools → WebSocket Server Settings**
2. Enable WebSocket server.
3. Keep authentication enabled and copy the password.
4. Default port is **4455**.
5. On the controller, enter the streaming PC's LAN/Tailscale address, for example:
   `ws://192.168.1.123:4455`
6. Enter the OBS WebSocket password and connect.

## Development

```bash
npm install
npm run dev
```

Open the Vite URL from your phone using the PC's LAN IP while developing.

## Hosting

The frontend is fully static and can be deployed to GitHub Pages/Vercel/etc. One browser caveat: a page served over HTTPS may refuse an insecure `ws://` connection. If that happens on the target browser, use a secure `wss://` endpoint or serve the controller over HTTP on the trusted LAN. This is a browser security restriction, not an OBS limitation.

## Security

The OBS password is **never committed to this repository**. It is stored locally in the browser that you use to control OBS. Keep OBS WebSocket authentication enabled.

## Next

The old Stream Plan overlay needs a new cross-browser state transport now that the backend has deliberately been removed. Planned after that:

- PWA/installable phone UI
- generic counters + animated OBS cards
- Questionable Decisions animation/history
- temporary lower-thirds / Currently Doing
- Hardcore world tracker
- game profiles
- YouTube/Twitch chat

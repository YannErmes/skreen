# ScreenDrop

**Fast, secure, browser-based screen sharing** for instantly sharing your screen and audio with multiple viewers. Built with WebRTC mesh technology.

**Created by:** YANN ERMES KOFFI

## Features

- ✨ Instant screen sharing without installation
- 🔒 Private and secure peer-to-peer connections
- 🎬 Share your screen and system audio
- 👥 Multiple viewers support (mesh topology)
- 🌐 Works directly in the browser
- 📱 Cross-platform compatible

## Structure

```
/client   React + Vite + Tailwind + TypeScript (Frontend)
/server   Node + Express + Socket.IO (Signaling Server)
```

## Quick Start

### Server (Signaling)

```bash
cd server
npm install
npm run dev    # http://localhost:3001
```

### Client (Frontend)

```bash
cd client
npm install
npm run dev    # http://localhost:5173
```

Then open the client, click **Start Sharing**, and share the link to invite viewers.

**Optional:** Set `VITE_SIGNAL_URL` environment variable to point to a non-local signaling server.

## Docker Deployment

```bash
docker compose up --build
```

- Client: http://localhost:5173
- Signaling: http://localhost:3001

## Production Deployment

### Vercel Deployment

See [VERCEL_DEPLOYMENT.md](./VERCEL_DEPLOYMENT.md) for complete setup instructions.

Key requirements:
- Set all environment variables in Vercel Project Settings
- Node.js 20 or higher
- Supabase credentials configured

## Technical Notes

- **Audio**: System audio is only exposed on certain platforms:
  - Chrome/Edge on Windows: Full screen sharing with audio
  - All platforms: Chrome tab sharing with "Share tab audio" option
- **NAT Traversal**: Currently uses Google STUN. For production with strict NATs, add a TURN server for better connectivity.
- **Topology**: Mesh network - optimal for rooms with <10 viewers. Larger rooms may benefit from other topologies.

## Architecture

- **WebRTC**: Peer-to-peer video/audio streaming
- **Socket.IO**: Real-time signaling and room management
- **Server Stack**: Node.js + Express
- **Client Stack**: React + TanStack Router + Tailwind CSS
- **Auth**: Supabase integration

## License

Created by YANN ERMES KOFFI

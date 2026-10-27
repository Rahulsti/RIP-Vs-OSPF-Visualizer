# RIP vs OSPF Convergence Visualizer

**Live demo:** https://ripvsospf.netlify.app/

An interactive web app that shows how **RIP** (distance-vector, Bellman-Ford) and **OSPF** (link-state, Dijkstra) react when a network link fails. You can step through convergence one update at a time and watch problems like **count-to-infinity** and **routing loops** appear, then see how split horizon, poison reverse and OSPF avoid them.

## Features

- **Interactive simulator:** fail and restore links, then step, play or fast-forward convergence and watch routing tables update hop by hop
- **Four protocol modes:**
  - RIP with no loop prevention
  - RIP + Split Horizon
  - RIP + Poison Reverse
  - OSPF (LSA flooding + Dijkstra SPF)
- **Topology presets:** 6-node mesh, linear chain, 6-node ring, and a dual-homed tail that triggers count-to-infinity and loops
- **Custom topologies:** add or remove nodes and links and set link costs
- **Benchmark lab:** runs all four modes on the same failure and compares convergence steps and routing updates
- **Reference tab:** protocol notes based on RFC 2453 (RIP) and RFC 2328 (OSPF)
- Light and dark themes

## Tech stack

React 18 · TypeScript · Vite · Tailwind CSS · lucide-react

## Run locally

Requires Node.js 18 or newer.

```
npm install
npm run dev
```

Then open the local URL Vite prints (usually http://localhost:5173).

## Build

```
npm run build
npm run preview
```

The production build goes to `dist/`. `netlify.toml` is included for one-click deployment on Netlify.

## Project structure

| File | Purpose |
|---|---|
| `src/App.tsx` | Simulator, routing algorithms (Bellman-Ford and Dijkstra), benchmark and reference tabs |
| `src/main.tsx` | React entry point |
| `index.html` | Page shell |
| `netlify.toml` | Netlify build settings |

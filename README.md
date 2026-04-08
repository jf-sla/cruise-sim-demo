# ShipSense™ — Passenger Intelligence Platform Demo

An interactive 3D simulation demo for **Carnival Cruise Line** showcasing a concept called **ShipSense™**: a real-time passenger intelligence and flow analytics platform for cruise ships.

The demo simulates live passenger movement aboard the **Carnival Sylndeor** on a Port Canaveral → Nassau route, visualizing crowd density, venue occupancy, and AI-generated operational insights across multiple cruise-day scenarios.

---

## What It Does

The simulation renders a full 3D cruise ship model with multiple decks and animates passenger agents moving between venues in real time. A control panel surfaces:

- **Live metrics** — passengers on board, congestion hotspot count, average restaurant wait time, and estimated F&B + activities revenue per hour
- **Heatmap overlay** — color-coded density map across all decks
- **AI Insights** — auto-generated alerts, warnings, and recommendations (e.g., crew redeployment suggestions, congestion warnings, revenue opportunities)
- **Venue occupancy bars** — real-time fill levels for all ship venues (pool, casino, dining rooms, bars, sports court, etc.)
- **Timeline scrubber** — simulate an entire cruise day (2,400 ticks) with scrubbing, pause/play, and speed controls

---

## Scenarios

Switch between five pre-built scenarios to see how passenger distribution and operational metrics change:

| Scenario | Description |
|---|---|
| 🚢 Normal Cruise | Typical passenger distribution across all decks |
| ⚓ Port Day | Most passengers ashore; low on-board occupancy |
| 🍽️ Dinner Rush | High restaurant demand; long queue wait times |
| 🆘 Muster Drill | Full ship assembly at emergency stations |
| ⛈️ Weather Event | Outdoor venues empty; indoor venues heavily congested |

---

## Deck Views

Filter the visualization to a specific deck:

- **All Decks** — full ship overview
- **Lido Pool (Top)** — pool deck and outdoor areas
- **Carnival Blvd** — main promenade with bars and casual dining
- **Casino Deck** — entertainment and casino floor
- **Dining (Lower)** — main dining rooms and specialty restaurants

---

## Technology Stack

- **Rendering**: [Three.js](https://threejs.org/) r128 — WebGL 3D scene with shadow mapping, fog, and animated ocean
- **3D Model**: GLTF ship model (`carnival_sylndeor/`) loaded via `GLTFLoader` + `DRACOLoader`; a procedural fallback ship is shown if the model is unavailable
- **Simulation**: Custom JavaScript agent-based passenger simulation — 180 agents with scenario-weighted venue attraction
- **UI**: Pure HTML/CSS — no framework dependencies; glass-morphism dark UI with Carnival brand colors
- **Fonts**: DM Sans + DM Mono (Google Fonts)

---

## Technology Roadmap (embedded in demo)

The demo includes a panel describing the intended real-world implementation path:

| Phase | Timeline | Capability |
|---|---|---|
| Phase 1 | Now | Existing CCTV + computer vision headcount |
| Phase 2 | 6 months | Zone-level flow analytics + automated alerts |
| Phase 3 | 18 months | Predictive simulation + crew optimization |
| Phase 4 | 3 years | Generative ship design feedback loop |

---

## Repo Structure

```
carnival_demo_v2.html       # Main demo — single self-contained HTML file
carnival_sylndeor/
  license.txt               # License for the 3D ship model assets
  textures/                 # PBR texture maps for the GLTF ship model
README.md
```

---

## How to Run

1. In your terminal, navigate to this project folder and start a local server:

```bash
python -m http.server 8080
```

2. Open your browser and go to:

```
http://localhost:8080/carnival_demo_v2.html
```

> A local server is required (rather than opening the file directly) because the 3D ship model is loaded via relative paths using the Fetch API, which is blocked by browsers for `file://` URLs.

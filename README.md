
# 🏰 PALE WALKER

> A survival-horror retro dungeon crawler featuring dual-perspective gameplay (2D Top-Down and 3D Pseudo-Raycaster), procedural room-first generation, dynamic torch lighting, and an relentless hunting entity powered by BFS pathfinding.

---

## 🎮 Overview

**PALE WALKER** places you inside an ancient, procedurally generated stone labyrinth. Trapped in the dark corridors with an ominous stalking entity, your objective is simple yet terrifying:
1. Find the **Torch** to navigate pitch-black dark zones.
2. Locate all **3 Keys** scattered across the dungeon chambers.
3. Reach the **Exit Stairs** before the hunter catches you.

Switch seamlessly at any time between a classic **2D top-down dungeon crawler** and an immersive **3D retro first-person raycaster** (Wolfenstein/Daggerfall style).

---

## ✨ Features

- **Dual Viewing Modes (2D & 3D)**:
  - **2D Top-Down**: High-visibility tactical map view with smooth autotiled pixel art, dynamic shadow casting, and overhead spatial awareness.
  - **3D Raycaster**: Fast, retro pseudo-3D first-person view using real-time DDA (Digital Differential Analyzer) raycasting and depth buffering.
- **Room-First Procedural Dungeon Generator**:
  - Generates spacious stone halls (5×5 to 11×9 cells) connected by wide (2–3 cell) corridors.
  - Eliminates cramped 1-cell maze strips in favor of natural dungeon pacing: `ROOM → CORRIDOR → ROOM → CORRIDOR → LARGE ROOM`.
  - Natural dead ends, side alcoves, and loop paths allowing strategic evasion and kiting.
  - 100% reachability guaranteed by graph connectivity checks.
- **Intelligent Stalker AI (SCP-096 Inspired)**:
  - **IDLE**: Dormant until you pick up your first key.
  - **STALK**: Actively stalks toward your position through corridors using optimal BFS pathfinding.
  - **WINDUP**: When the stalker establishes line-of-sight, it shrieks and charges adrenaline before bursting into a sprint.
  - **CHASE**: High-speed pursuit that outruns your normal walking speed.
  - **STUN**: Can be temporarily incapacitated with defensive tools or traps.
- **Dynamic Lighting & Darkness**:
  - Substantially dark unlit zones with isolated pools of warm orange torchlight.
  - Organic torch flickering and soft radial lighting cutouts.
  - Ominous dark zones where players are completely blind without the Torch.
- **Survival Tools & Abilities**:
  - **Sprint**: Temporary burst of speed to escape tight encounters.
  - **Stun Shot**: Target-directed blast that freezes the hunter for 3.5 seconds.
  - **Block / Barricade**: Deploy crates in narrow corridors to obstruct the stalker's path.
  - **Traps**: Pre-placed perimeter wards that stun the stalker upon contact.
  - **Map Scroll**: Instantly reveals the entire dungeon floor plan.
- **Cross-Platform & Fullscreen Support**:
  - Auto-scales to fill the entire display (`100vmin`) while maintaining pixel-art aspect ratios.
  - Dedicated **⛶ Fullscreen** toggle utilizing the HTML5 Fullscreen API.
  - On-screen touch D-Pad with collapsible toggle for mobile and keyboard players.
- **Zero Dependencies**: Pure HTML5 Canvas & Vanilla JavaScript. No libraries, node dependencies, or build tools required.

---

## ⌨️ Controls & Keybindings

| Action | Keyboard | Touch / On-Screen |
| :--- | :--- | :--- |
| **Move Up / Forward** | `W` or `▲ Up Arrow` | `▲` |
| **Move Down / Backward**| `S` or `▼ Down Arrow` | `▼` |
| **Move / Turn Left** | `A` or `◀ Left Arrow` | `◀` |
| **Move / Turn Right** | `D` or `▶ Right Arrow` | `▶` |
| **180° Snap Turn** | `Space` | `⟲ 180` |
| **Sprint** | `Shift` | `Sprint` |
| **Interact / Pick Up** | `E` | `E pick up` |
| **Stun Shot** | `1` | `Stun` |
| **Place Barricade** | `2` | `Block` |
| **Toggle 2D / 3D View** | `C` | `View: 2D/3D` |
| **Toggle BFS Path Debug**| `B` | `BFS: ON/OFF` |
| **Restart Game** | `R` | `Restart` |
| **Toggle Fullscreen** | Click button | `⛶ Fullscreen` |
| **Toggle Controls Pad** | Click button | `⌨ Controls: On/Off` |

> *Note on View Modes*:
> - In **2D Mode**, movement is omnidirectional (WASD moves in screen space, items auto-pickup).
> - In **3D Mode**, movement is tank/first-person (◀▶ turn camera, ▲ moves forward, ▼ steps backward, press `E` to pick up).

---

## 🧭 How to Play

1. **Phase 1: Preparation**:
   - Begin in a safe chamber. Look around for the glowing orange **Torch**.
   - Collect defensive supplies: cyan crystals (**Stun Shots**), wooden crates (**Barricades**), and purple crystals (**Map Reveal**).
2. **Phase 2: The Awakening**:
   - Locate the **3 Keys**.
   - As soon as you collect your first key, the stalker awakens and begins hunting you across the labyrinth.
3. **Phase 3: Evasion**:
   - Use wide corridors and room loops to navigate around the creature.
   - If caught in its gaze, the stalker enters **Windup** (giving you 5 seconds of adrenaline rush to break line of sight).
   - If trapped, fire a **Stun Shot** (`1`) directly at it, or drop a **Block** (`2`) to cut off the hallway behind you.
4. **Phase 4: Escape**:
   - Once all 3 keys are in your possession, the exit gates unlock.
   - Race to the glowing **Exit Stairs** to escape the dungeon.

---

## 📁 Project Structure

```text
maze_runner/
├── Assets/
│   └── tiles/                     # 32x32 pixel art tileset assets
│       ├── wall_top.png           # Autotiled wall borders
│       ├── wall_bottom.png
│       ├── wall_left.png
│       ├── wall_right.png
│       ├── wall_corner_*.png      # Inner & outer corner walls
│       ├── wall_solid.png         # Solid stone wall interior
│       ├── floor_normal.png       # Primary stone flooring
│       ├── floor_cracked.png      # Weathered stone variants
│       ├── floor_mossy.png
│       ├── floor_broken.png
│       ├── door_closed.png        # Interactive doorways
│       ├── door_open.png
│       ├── torch.png              # Wall-mounted torch sprites
│       ├── stairs.png             # Exit portal stairs
│       ├── key.png                # Dungeon keys
│       ├── crate.png / barrel.png # Obstacles & barricades
│       ├── bones.png / blood.png  # Atmospheric decor
│       └── crystal_*.png          # Power-up items
├── Backrooms Stalker 2D.html      # Complete standalone game
└── README.md                      # Documentation
```

---

## 🚀 Running the Game

Because the project is built with zero external dependencies, you can run it immediately without installing any build tools:

### Option 1: Direct File Launch
Double-click `Backrooms Stalker 2D.html` or open it directly in any modern browser (Chrome, Firefox, Safari, Edge).

### Option 2: Local HTTP Server (Recommended)
Using Python's built-in server:
```bash
# From the project directory:
python3 -m http.server 8000
```
Then navigate to `http://localhost:8000/Backrooms%20Stalker%202D.html` in your browser.

---

## 🛠️ Technical Details

- **Breadth-First Search (BFS)**:
  - Real-time pathfinding executed dynamically by the AI to track player coordinates through complex interconnected rooms.
  - Visualizable in real time using the `B` debug hotkey (renders animated dashed trail and waypoints).
- **DDA Raycaster (3D Engine)**:
  - Custom raycaster operating on a 186×186 offscreen frame buffer, scaled to viewport.
  - Digital Differential Analysis calculates precise grid intersections with depth sorting (`zb` buffer) for correct sprite billboard scaling.
- **Lighting Pipeline**:
  - Offscreen lighting canvas utilizing `destination-out` blending to dynamically carve glowing radial vision fields out of a `0.93` opacity darkness layer.
  - Additive canvas composition (`lighter`) produces warm orange ambient tints surrounding torch fixtures.
EOF
`
Viewed README.md:1-50

I have created a comprehensive [README.md](file:///home/vanilla/Desktop/hackathon/maze_runner/README.md) for **Backrooms Stalker 2D** without modifying any code files.

### Contents Included in `README.md`:
- **Overview**: Core game concept, survival objectives (find Torch, 3 Keys, reach Exit Stairs).
- **Features**: Dual 2D/3D perspective system, room-first dungeon generator, SCP-096 inspired stalker AI, dynamic torch lighting, abilities & defenses, fullscreen support, and zero-dependency architecture.
- **Controls & Keybindings**: Full reference table for keyboard and touch/on-screen controls, with notes explaining differences between 2D and 3D modes.
- **How to Play**: Phase-by-phase gameplay guide from preparation to escape.
- **Project Structure**: Breakdown of the repository files and asset tileset.
- **Running the Game**: Quickstart instructions for direct file launch and local Python server.
- **Technical Details**: Overview of BFS pathfinding, 3D DDA raycasting, and offscreen lighting composition pipelines.

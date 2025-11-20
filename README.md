<div align="center">

<!-- Hero Header with Name -->
<img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=6,12,20&height=200&section=header&text=Crystal%20Blitz&fontSize=70&fontColor=FFFFFF&animation=twinkling&fontAlignY=25&desc=Arena%20Shooter%20in%20a%20Single%20HTML%20File&descSize=20&descAlignY=50&descAlign=50"/>

<br/>

<!-- Animated Typing Subtitle -->
<img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=22&duration=3000&pause=1000&color=FFFFFF&center=true&vCenter=true&random=false&width=700&lines=60+FPS+%E2%80%A2+200%2B+Entities+%E2%80%A2+347KB;Zero+Dependencies+%E2%80%A2+Zero+Build+Tools;Single+HTML+File+%E2%80%A2+Works+Forever" alt="Typing SVG" />

<br/>

<!-- Main Action Buttons -->
<p align="center">
  <a href="https://zacsluss.github.io/crystal_blitz/"><img src="https://img.shields.io/badge/🎮_PLAY-GAME!-2e8b57?style=for-the-badge&labelColor=000000&logo=vercel&logoColor=white" alt="Play Game"/></a><a href="https://github.com/Zacsluss/crystal_blitz/archive/refs/heads/main.zip"><img src="https://img.shields.io/badge/⬇️_DOWNLOAD-PROJECT-d97706?style=for-the-badge&labelColor=000000&logo=github&logoColor=white" alt="Download"/></a>
</p>

<!-- GitHub Stats Badges -->
<p align="center">
  <img src="https://img.shields.io/github/stars/Zacsluss/crystal_blitz?style=social" alt="Stars"/>
  <img src="https://img.shields.io/github/forks/Zacsluss/crystal_blitz?style=social" alt="Forks"/>
  <img src="https://img.shields.io/github/watchers/Zacsluss/crystal_blitz?style=social" alt="Watchers"/>
  <img src="https://img.shields.io/github/license/Zacsluss/crystal_blitz?style=flat-square&color=555555" alt="License"/>
  <img src="https://img.shields.io/github/last-commit/Zacsluss/crystal_blitz?style=flat-square&color=666666" alt="Last Commit"/>
</p>

</div>

<br/>

---

## 👋 Hey, I'm Zac

**60 FPS arena shooter in a single 347KB HTML file.** Zero dependencies, works offline forever.

<details>
<summary><b>🔽 What makes this different</b></summary>

<br/>

- **200+ entities at locked 60 FPS** - Spatial grid optimization + object pooling
- **11 crystal powerups** - Homing shots, lightning chains, freeze blasts, explosive rounds
- **Zero garbage collection** - Pre-allocated memory, no runtime allocation
- **Works forever** - Download once, play in 10 years (no npm, no build tools, no external dependencies)

Built with vanilla JavaScript, Canvas API, and a lot of caffeine.

</details>

<div align="center">

<img src="assets/gameplay.gif" alt="Project Preview" width="800"/>

*Fast-paced arena combat with dynamic enemy AI, crystal powerups, and 60 FPS performance*

</div>

---

## ⚡ What This Does

<div align="center">

**High-performance arena shooter** • **60 FPS with 200+ entities** • **347KB single file** • **Zero dependencies**

</div>

**Key Features:**
- ✨ **11 Crystal Powerups** - Homing, explosive, lightning, freeze, ricochet, seeking, cluster, and multi-shot patterns
- 🎮 **17 Permanent Upgrades** - Health, speed, fire rate, and damage scaling throughout endless waves
- 🔬 **Advanced Performance** - O(n²)→O(n) collision detection, zero GC loops, 3x gradient caching boost
- 📱 **Full Mobile Support** - Touch controls with virtual joystick and responsive UI
- 🎯 **12+ Enemy AI Types** - Leapers, dashers, volatile chargers, minelayers, healers, and multi-phase bosses

**Tech:** Vanilla JavaScript • Canvas 2D API • Web Audio API • Zero external dependencies

---

## 📚 Table of Contents

<details>
<summary><b>🔽 Jump to a section</b></summary>

- [🛠️ Tech Stack](#️-tech-stack)
- [🏗️ Architecture & Design](#️-architecture--design)
- [🎮 Gameplay Features](#-gameplay-features)
- [💭 Why I Built This](#-why-i-built-this)
- [📊 Performance Benchmarks](#-performance-benchmarks)
- [🚀 Quick Start](#-quick-start)
- [📄 License & Usage](#-license--usage)
- [📬 About & Connect](#-about--connect)

</details>

---

## 🛠️ Tech Stack

<div align="center">

### What I Used to Build This

<img src="https://skillicons.dev/icons?i=js,html,css,git,github,vscode" alt="Tech Stack" />

### Core Dependencies

<table>
<tr>
<td align="center" width="25%">
<img src="https://img.shields.io/badge/JavaScript-ES6+-F7DF1E?style=flat-square&logo=javascript&logoColor=black"/><br/>
<sub><b>Vanilla JS</b></sub>
</td>
<td align="center" width="25%">
<img src="https://img.shields.io/badge/Canvas_API-2D-E34F26?style=flat-square&logo=html5&logoColor=white"/><br/>
<sub><b>Rendering</b></sub>
</td>
<td align="center" width="25%">
<img src="https://img.shields.io/badge/Web_Audio-Procedural-4285F4?style=flat-square&logo=google&logoColor=white"/><br/>
<sub><b>Sound Effects</b></sub>
</td>
<td align="center" width="25%">
<img src="https://img.shields.io/badge/Dependencies-0-28A745?style=flat-square&logo=npm&logoColor=white"/><br/>
<sub><b>Zero Deps</b></sub>
</td>
</tr>
</table>

</div>

<details>
<summary><b>🔽 Why zero dependencies?</b></summary>

<br/>

```json
{
  "dependencies": {},
  "devDependencies": {}
}
```

**Everything self-contained in one HTML file.** No npm packages, no CDN imports, no external assets. Works offline indefinitely without breaking.

</details>

---

## 🏗️ Architecture & Design

### System Overview

Crystal Blitz uses a **fixed-timestep game loop with spatial partitioning** to achieve consistent 60 FPS performance:

```mermaid
graph LR
    A[Input] --> B[Update<br/>Fixed 1/60s]
    B --> C[Collision<br/>Spatial Grid]
    C --> D[Render<br/>Interpolated]

    B --> E[Player AI]
    B --> F[Enemy AI<br/>12 Behaviors]
    B --> G[Bullet Physics]

    C --> H[O n Detection<br/>50×50px Grid]

    D --> I[Gradient Cache<br/>100 LRU entries]
    D --> J[Particle System<br/>500 limit]

    style H fill:#2e8b57
    style I fill:#2e8b57
```

### Key Optimizations

| Technique | Problem Solved | Impact |
|-----------|---------------|--------|
| **Spatial Grid** | O(n²) collision detection | Enables 200+ entities vs ~30 without |
| **Object Pooling** | Garbage collection pauses | 0 GC cycles during gameplay |
| **Gradient Cache** | Expensive Canvas API calls | 3x rendering performance boost |
| **Fixed Timestep** | Frame rate dependent physics | Consistent gameplay 30-240 FPS |

### Entity Component Pattern

All game entities follow a consistent structure:

```javascript
entity = {
  x, y,          // Position
  vx, vy,        // Velocity
  r,             // Collision radius
  hp,            // Health points
  behavior,      // AI type ('leaper', 'dasher', 'boss', etc.)
  effects,       // Active crystal effects (Set for O(1) lookup)
  color,         // Visual appearance
  alive          // Pooling state
}
```

This enables:
- **Polymorphic updates**: All entities update via same interface
- **Efficient collision**: Simple circle-circle checks via radius
- **Memory efficiency**: Dead entities recycled vs reallocated

<details>
<summary><b>🔽 Deep Dive: Performance Optimizations</b></summary>

<br/>

**Critical optimizations for 60 FPS with 200+ entities:**

- ✅ **Zero garbage collection** - All objects pre-allocated and reused via pooling
- ✅ **Cached canvas states** - Track fillStyle/strokeStyle/globalAlpha to avoid redundant sets
- ✅ **Particle limits** - Hard caps at 500 particles, 200 blood stains
- ✅ **Batch rendering** - Single paths for multiple shapes, minimal state changes
- ✅ **Spatial grid lookups** - Query only nearby entities for collision/AI
- ✅ **Gradient computation** - Moved expensive gradient creation to initialization or cached

**Collision Detection:**
- Naive O(n²): ~40,000 checks for 200 entities
- Spatial Grid O(n): ~2,000 checks for 200 entities (20x faster)

</details>

---

## 🎮 Gameplay Features

<details>
<summary><b>🔽 11 Crystal Powerups</b></summary>

<br/>

| Crystal | Effect | Rarity |
|---------|--------|--------|
| **Homing** | Ultra-strong auto-targeting projectiles | Ultra-Rare (0.5%) |
| **Explosive** | Area-of-effect damage on impact | Common |
| **Lightning** | Chains between multiple enemies | Common |
| **Freeze** | Slows enemy movement for 3 seconds | Common |
| **Ricochet** | Bounces between enemies | Common |
| **Seeking** | Weak auto-targeting (tracks nearest) | Common |
| **Cluster** | Splits into 5 fragments on impact | Common |
| **Shotgun** | Fires 5-bullet spread pattern | Common |
| **Dual Shot** | Fires 2 parallel bullets | Upgrade |
| **Triple Shot** | Fires 3 bullets in a cone | Upgrade |
| **Quad Shot** | Fires 4 bullets in X pattern | Upgrade |

Each powerup lasts 25-50 shots before reverting to normal fire.

</details>

<details>
<summary><b>🔽 12+ Enemy AI Behaviors</b></summary>

<br/>

**Wave-Unlocked Behaviors:**
- **Waves 1-2:** Basic, ranged, fast (foundational enemies)
- **Waves 3-4:** +Flank, charge, shields (tactical additions)
- **Waves 5-6:** +Erratic, spiral shooters (unpredictable movement)
- **Waves 7+:** +Leapers, dashers, volatiles, minelayers, healers

**Boss Types:**
- **Mini-Boss** (every 5 waves): 2x HP, golden color, fast movement
- **Super-Boss** (every 10 waves): 9x HP, massive size, multi-phase attacks

</details>

<details>
<summary><b>🔽 Endless Wave Scaling</b></summary>

<br/>

**Enemy Count:**
- Wave 1: 15 enemies
- Wave 10: 30 enemies
- Wave 50: 60 enemies
- Wave 100: 90 enemies (cap)

**Difficulty Scaling:**
- Enemy speed: +4 per wave (capped at 350)
- Enemy damage: +1 every 5 waves
- Boss HP: Scales with wave number
- Drop rates: Special crystals unlock at higher waves

</details>

---

## 💭 Why I Built This

**I manage enterprise platforms by day (3,000+ users, 22 countries).** Built this to keep coding skills sharp—the best leaders never stop building.

<details>
<summary><b>🔽 What I learned from this project</b></summary>

<br/>

- **Performance constraints** - Pushing Canvas 2D to 60 FPS without WebGL
- **Game fundamentals** - Spatial partitioning, object pooling, ECS architecture from scratch
- **Zero dependencies** - Download once, works forever (even in 10 years)
- **Creative problem-solving** - No physics engine? Build delta-time physics. No audio? Procedural synthesis.
- **Maintainable code** - 9,280 lines in one file, but structured with clear patterns

Zero dependencies forced creative solutions. No physics engine → built delta-time physics from first principles. No audio library → synthesized sounds procedurally. No sprites → rendered everything with Canvas primitives. **Constraints became opportunities.**

</details>

---

## 📊 Performance Benchmarks

**60 FPS locked • 200+ entities • 347KB total • <500ms load • ~80MB memory**

<details>
<summary><b>🔽 See detailed benchmarks (Desktop & Mobile)</b></summary>

<br/>

<div align="center">

<table>
<tr>
<td width="50%">

#### Desktop (1920×1080)

<table>
<thead>
<tr>
<th><div align="center">Metric</div></th>
<th><div align="center">Value</div></th>
</tr>
</thead>
<tbody>
<tr>
<td><div align="center"><b>Frame Rate</b></div></td>
<td><div align="center">60 FPS (locked)</div></td>
</tr>
<tr>
<td><div align="center"><b>Max Entities</b></div></td>
<td><div align="center">200+ simultaneous</div></td>
</tr>
<tr>
<td><div align="center"><b>File Size</b></div></td>
<td><div align="center">347KB</div></td>
</tr>
<tr>
<td><div align="center"><b>Load Time</b></div></td>
<td><div align="center">&lt;500ms</div></td>
</tr>
<tr>
<td><div align="center"><b>Memory Usage</b></div></td>
<td><div align="center">~80MB stable</div></td>
</tr>
</tbody>
</table>

</td>
<td width="50%">

#### Mobile (iPhone 12)

<table>
<thead>
<tr>
<th><div align="center">Metric</div></th>
<th><div align="center">Value</div></th>
</tr>
</thead>
<tbody>
<tr>
<td><div align="center"><b>Frame Rate</b></div></td>
<td><div align="center">60 FPS (locked)</div></td>
</tr>
<tr>
<td><div align="center"><b>Max Entities</b></div></td>
<td><div align="center">150+ simultaneous</div></td>
</tr>
<tr>
<td><div align="center"><b>File Size</b></div></td>
<td><div align="center">347KB</div></td>
</tr>
<tr>
<td><div align="center"><b>Load Time</b></div></td>
<td><div align="center">&lt;600ms</div></td>
</tr>
<tr>
<td><div align="center"><b>Touch Latency</b></div></td>
<td><div align="center">&lt;16ms</div></td>
</tr>
</tbody>
</table>

</td>
</tr>
</table>

</div>

</details>

<details>
<summary><b>🔽 Bundle size breakdown</b></summary>

<br/>

```
index.html       347 KB → 93 KB gzipped (73% reduction)
├── HTML/CSS      15 KB → 5 KB gzipped
└── JavaScript   332 KB → 88 KB gzipped
```

**Key optimizations:**
- Minified variables, removed comments, eliminated dead code
- Cached canvas states, pre-computed trig lookups
- Moved expensive computations to initialization

</details>

---

## 🧪 Testing & Quality

Crystal Blitz includes a **comprehensive test suite** with 48 automated assertions:

<div align="center">

![Tests](https://img.shields.io/badge/tests-48%20passing-brightgreen?style=for-the-badge)
![Coverage](https://img.shields.io/badge/coverage-60%25-yellow?style=for-the-badge)

</div>

### Test Categories

| Category | Tests | Coverage |
|----------|-------|----------|
| Core Systems | 15 | ✅ 100% |
| Math Utilities | 7 | ✅ 100% |
| Game Loop | 6 | ✅ 100% |
| Spatial Grid | 8 | ✅ 100% |
| Powerups | 4 | ⚠️ 60% |
| Rendering | 4 | ✅ Smoke tests |
| Save/Load | 5 | ✅ 100% |

### Running Tests

```bash
# Option 1: Open directly in browser
open tests.html

# Option 2: Via local server (recommended)
python -m http.server 8000
# Visit: http://localhost:8000/tests.html
```

### Performance Benchmarks

Tests include real-time performance benchmarks:

- **Spatial Grid Query**: <1ms for 200 entities (vs ~15ms brute force)
- **Gradient Cache Hit Rate**: >95% (3x faster than uncached)
- **Game Loop Overhead**: <2ms per frame (14ms budget for logic at 60 FPS)
- **Object Pool Efficiency**: 0 allocations during gameplay

### What's Tested

✅ **Collision Detection**: Spatial grid insertion, querying, circle-circle checks
✅ **Object Pooling**: Entity recycling, memory reuse
✅ **Game Loop**: Fixed timestep, interpolation, state machine
✅ **Input Handling**: Keyboard, mouse, touch, dead zones
✅ **Persistence**: Save/load, corruption handling, JSON round-trips
✅ **Math Utilities**: Clamping, normalization, distance calculations

⚠️ **Needs More Coverage**:
- Enemy AI behaviors (currently manual testing)
- Powerup effect interactions
- Wave progression edge cases

---

## 🚀 Quick Start

**Clone → Open `index.html` → Play** (30 seconds total)

<details>
<summary><b>🔽 See full setup instructions</b></summary>

<br/>

```bash
# 1️⃣ Clone this repo
git clone https://github.com/Zacsluss/crystal_blitz.git
cd crystal_blitz

# 2️⃣ Open the file
open index.html  # macOS
start index.html # Windows
xdg-open index.html # Linux

# 3️⃣ Play offline anywhere
# Copy index.html to USB, email it, whatever

# 4️⃣ Optional: Serve with local server
python -m http.server 8000

# 5️⃣ Deploy to GitHub Pages
# Commit index.html → Settings → Pages → main branch
```

</details>

<details>
<summary><b>🔽 How to customize it</b></summary>

<br/>

Make it yours (takes about 5 minutes):

1. **Your content:** Edit `index.html` lines 8-9 — swap title/description
2. **Your colors:** Search for hex codes like `#0b0d10` (background), `#5af2c7` (accent)
3. **Your difficulty:** Line 4277 controls enemy count, line 4460 controls speed
4. **Your powerups:** Line 3729+ defines all crystal types and effects
5. **Your domain:** Fork, enable GitHub Pages, optionally add custom domain

The entire game is in one file (`index.html`), so just search for what you want to change and edit it directly. No build process, no compilation.

</details>

---

## 🚀 Deployment

### GitHub Pages (Recommended)

This repo is already deployed via GitHub Pages:
1. Push `index.html` to `main` branch
2. GitHub auto-deploys to `https://username.github.io/repo-name/`
3. No configuration needed (`.nojekyll` file present)

### Custom Domain

```bash
# Add CNAME file:
echo "yourdomain.com" > CNAME
git add CNAME && git commit -m "Add custom domain" && git push
```

Then configure DNS:
- Add CNAME record: `yourdomain.com` → `username.github.io`
- Wait 10-60 minutes for propagation

### Other Static Hosts

<details>
<summary><b>🔽 Netlify, Vercel, Self-Hosted</b></summary>

<br/>

**Netlify**:
```bash
# Drag & drop index.html to Netlify dashboard
# Or CLI:
npm install -g netlify-cli
netlify deploy --prod --dir .
```

**Vercel**:
```bash
npm install -g vercel
vercel --prod
```

**Self-Hosted**:
```bash
# Any static server works:
python -m http.server 8080
# Or nginx, Apache, Caddy, etc.
```

</details>

### Production Checklist

- [ ] Minify `index.html` (optional - gzip handles this)
- [ ] Add CSP headers (see SECURITY.md)
- [ ] Enable HTTPS (required for full mobile features)
- [ ] Test on target browsers (Chrome, Firefox, Safari, Edge)
- [ ] Verify offline functionality (disconnect network, reload)

---

## 🚧 Known Limitations & Future Work

### Current Limitations

**Single-File Constraint**
- **Limitation**: 10,326 lines in one file
- **Trade-off**: Sacrifices modularity for zero-dependency simplicity
- **Mitigation**: Organized with clear section comments, JSDoc on key functions

**Mobile Performance**
- **Limitation**: 30-45 FPS on older mobile devices (iPhone 8, Pixel 3)
- **Trade-off**: Particle effects prioritized over mobile optimization
- **Mitigation**: Adaptive quality settings reduce particles on low-end devices

**No Multiplayer**
- **Limitation**: Single-player only (by design)
- **Why**: Preserves offline-forever architecture
- **Alternative**: High score sharing via screenshot/export

### Potential Improvements

If I were to expand this project (prioritized by impact):

1. **Refactor into Module Pattern** (High Impact, Medium Effort)
   - Extract systems into namespaced objects within same file
   - Improve testability and code navigation
   - **Estimated**: 6-8 hours

2. **Add Achievement System** (Medium Impact, Small Effort)
   - Track milestones (reach wave 20, collect 100 crystals, etc.)
   - Store in localStorage, display in stats screen
   - **Estimated**: 2-3 hours

3. **WebGL Renderer** (Medium Impact, Large Effort)
   - Replace Canvas 2D with WebGL for particle effects
   - Could handle 2000+ particles vs current 500
   - **Estimated**: 20+ hours

4. **Boss Variety** (Medium Impact, Medium Effort)
   - Currently 1 boss type with phases
   - Add 3-5 unique boss designs per milestone wave
   - **Estimated**: 8-10 hours

5. **Leaderboard Export** (Low Impact, Small Effort)
   - Generate shareable PNG with stats
   - No backend needed, keeps offline-first
   - **Estimated**: 2 hours

---

## 📄 License & Usage

**MIT License** — Fork it, customize it, do whatever. No credit needed (⭐ appreciated though).

<details>
<summary><b>🔽 Customization guide (5 minutes)</b></summary>

<br/>

**Make it yours (5 minutes):**
1. Edit `index.html` lines 8-9 — replace title/description
2. Search for hex color codes to change theme (`#0b0d10`, `#5af2c7`, etc.)
3. Line 4277: Change enemy scaling formula
4. Line 3729+: Customize crystal powerup effects
5. Commit to GitHub → Enable Pages → you're live!

**No build process needed** — The entire game is self-contained in a single HTML file. Just edit and reload.

</details>

<br/>

<div align="center">

<img src="https://img.shields.io/badge/License-MIT-555555?style=for-the-badge&logo=opensourceinitiative&logoColor=white"/>

Full license text in [LICENSE](LICENSE) file.

</div>

---

## 📬 About & Connect

**Lead CRM Systems Analyst at Computershare** by day—managing enterprise platforms and Salesforce integrations across global teams. By night, I build projects like this.

Into WebGL, particle systems, shader programming, AI/ML, digital art, and 360° drone photography.

**Connect with me:**

<div align="center">

<a href="https://zacsluss.github.io/portfolio/">
  <img src="https://img.shields.io/badge/Portfolio-zacsluss.github.io-2e7d5a?style=for-the-badge&logo=vercel&logoColor=white"/>
</a>
<a href="https://github.com/Zacsluss">
  <img src="https://img.shields.io/badge/GitHub-@Zacsluss-181717?style=for-the-badge&logo=github&logoColor=white"/>
</a>
<a href="https://linkedin.com/in/zacharyjsluss">
  <img src="https://img.shields.io/badge/LinkedIn-Zachary_Sluss-064789?style=for-the-badge&logo=linkedin&logoColor=white"/>
</a>
<a href="mailto:zacharyjsluss@gmail.com">
  <img src="https://img.shields.io/badge/Email-zacharyjsluss@gmail.com-b91c1c?style=for-the-badge&logo=gmail&logoColor=white"/>
</a>
<a href="https://github.com/Zacsluss/crystal_blitz/raw/main/Zachary_Sluss_Resume.pdf">
  <img src="https://img.shields.io/badge/Download-Resume-7c3aed?style=for-the-badge&logo=adobeacrobatreader&logoColor=white"/>
</a>

<br/>

**Found this helpful?** Give it a ⭐ to show support!

</div>

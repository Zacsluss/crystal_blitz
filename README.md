<div align="center">

<!-- Hero Header with Name -->
<img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=6,12,20&height=200&section=header&text=Crystal%20Blitz&fontSize=70&fontColor=FFFFFF&animation=twinkling&fontAlignY=25&desc=Arena%20Shooter%20in%20a%20Single%20HTML%20File&descSize=20&descAlignY=50&descAlign=50"/>

<br/>

<!-- Animated Typing Subtitle -->
<img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=22&duration=3000&pause=1000&color=FFFFFF&center=true&vCenter=true&random=false&width=700&lines=60+FPS+%E2%80%A2+200%2B+Entities+%E2%80%A2+347KB;Zero+Dependencies+%E2%80%A2+Zero+Build+Tools;Single+HTML+File+%E2%80%A2+Works+Forever" alt="Typing SVG" />

<br/>

<!-- Main Action Buttons -->
<p align="center">
  <a href="https://zacsluss.github.io/crystal_blitz/">
    <img src="https://img.shields.io/badge/🚀_VIEW-LIVE_DEMO-2e8b57?style=for-the-badge&labelColor=000000&logo=vercel&logoColor=white" alt="Live Site"/>
  </a>
  <a href="https://github.com/Zacsluss/crystal_blitz/archive/refs/heads/main.zip">
    <img src="https://img.shields.io/badge/⬇️_DOWNLOAD-PROJECT-d97706?style=for-the-badge&labelColor=000000&logo=github&logoColor=white" alt="Download"/>
  </a>
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

I work on enterprise platforms by day and build unusually fun projects by night. This is **a 60 FPS arena shooter that runs entirely from a single 347KB HTML file** with zero dependencies.

**What makes it interesting:**
- Handles 200+ simultaneous entities at locked 60 FPS using spatial grid optimization
- 11 crystal powerups with effects like homing shots, lightning chains, and freeze blasts
- Zero runtime memory allocation through object pooling (no garbage collection during gameplay)
- Works offline forever—download once, play in 10 years (no npm, no build tools, no external assets)

Built with vanilla JavaScript, Canvas API, and a lot of caffeine.

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
<summary><b>Jump to a section</b></summary>

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
<summary><b>📦 See the full dependency list</b></summary>

```json
{
  "dependencies": {},
  "devDependencies": {}
}
```

**Zero dependencies by design** — Everything is self-contained in a single HTML file. No npm packages, no CDN imports, no external assets. This ensures the game works offline indefinitely without breaking due to external service changes.

</details>

---

## 🏗️ Architecture & Design

<details>
<summary><b>🎯 Entity Component System (ECS)</b></summary>

<br/>

The game uses an **Entity Component System architecture** for managing game objects:

- **Spatial Grid Partitioning** - Divides play area into 50x50px cells for O(n) collision detection instead of O(n²)
- **Object Pooling** - Pre-allocated arrays for entities eliminate runtime memory allocation (zero GC during gameplay)
- **LRU Gradient Cache** - 100-entry cache reduces gradient creation overhead by 3x
- **Delta-Time Physics** - Frame-independent movement ensures consistent gameplay across different refresh rates
- **State Machines** - Each enemy AI uses behavior states (orbiting, telegraphing, charging, retreating)
- **Procedural Audio** - Oscillator-based sound synthesis for beeps, explosions, and effects

</details>

<details>
<summary><b>⚡ Performance Optimizations</b></summary>

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
<summary><b>💎 11 Crystal Powerups</b></summary>

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
<summary><b>👾 12+ Enemy AI Behaviors</b></summary>

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
<summary><b>📈 Endless Wave Scaling</b></summary>

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

As someone who manages enterprise platforms serving 3,000+ users across 22 countries, I built this to maintain hands-on technical skills. The best leaders never stop coding.

**This project specifically explores:**
- ✅ **Performance constraints** - How far can you push Canvas 2D without WebGL?
- ✅ **Game fundamentals** - Spatial partitioning, object pooling, ECS architecture from scratch
- ✅ **Zero dependencies** - Works offline, forever (download today, works in 10 years)
- ✅ **Creative problem-solving** - No physics engine → build delta-time physics. No audio library → procedural synthesis
- ✅ **Maintainable code** - 9,280 lines in a single file, but structured with clear patterns

The constraint of zero dependencies forced creative problem-solving. No physics engine meant building delta-time physics from first principles. No audio library meant synthesizing sounds procedurally. No sprite atlases meant rendering everything with Canvas primitives. These limitations became opportunities to understand the fundamentals.

---

## 📊 Performance Benchmarks

<div align="center">

### Real numbers from my production build

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

<details>
<summary><b>📦 Bundle size breakdown</b></summary>

```
index.html       347 KB → 93 KB gzipped
├── HTML/CSS      15 KB → 5 KB gzipped
├── JavaScript   332 KB → 88 KB gzipped
└── Total        347 KB → 93 KB gzipped (73% reduction)
```

**How I optimized it:**
- ✅ Minified variable names and removed comments
- ✅ Eliminated dead code and unused features
- ✅ Cached canvas states to reduce draw calls
- ✅ Pre-computed trigonometry lookups
- ✅ Moved expensive computations to initialization

</details>

---

## 🚀 Quick Start

<div align="center">

### Want to try it locally? Takes about 30 seconds

</div>

```bash
# 1️⃣ Clone this repo
git clone https://github.com/Zacsluss/crystal_blitz.git
cd crystal_blitz

# 2️⃣ Open the file
# Just double-click index.html or:
open index.html  # macOS
start index.html # Windows
xdg-open index.html # Linux

# 3️⃣ Play offline anywhere
# Copy index.html to USB, email it, whatever
# It works without internet, forever

# 4️⃣ Optional: Serve with local server
python -m http.server 8000
# Opens at http://localhost:8000

# 5️⃣ Deploy to GitHub Pages
# Commit index.html to main branch
# Enable Pages in Settings → Pages → main branch
```

<details>
<summary><b>🔧 How to customize it for yourself</b></summary>

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

## 📄 License & Usage

**MIT License** — Fork it, customize it, do whatever you want with it. No credit needed (but a ⭐ appreciated).

**Quick setup:** `git clone` → open `index.html` → you're playing

<details>
<summary><b>📋 Full customization instructions</b></summary>

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

By day, I work as a Lead CRM Systems Analyst at Computershare, managing enterprise platforms and Salesforce integrations across global teams. By night, I build stuff like this.

I'm into WebGL, particle systems, shader programming, AI/ML, digital art, and 360° drone photography. Always learning, always building.

**Let's connect:**

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

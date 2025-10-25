<div align="center">

# ⚡ CRYSTAL BLITZ

### *A Complete Browser Game in One File. Zero Dependencies.*

[![Play Now](https://img.shields.io/badge/🎮_PLAY_NOW-Live_Demo-00ff88?style=for-the-badge&logo=gamepad&logoColor=white)](https://zacsluss.github.io/CRYSTAL_BLITZ/Crystal_Blitz.html)
[![Download](https://img.shields.io/badge/💾_DOWNLOAD-347KB-ff6b35?style=for-the-badge&logo=download&logoColor=white)](https://github.com/Zacsluss/CRYSTAL_BLITZ/raw/main/Crystal_Blitz.html)
[![Documentation](https://img.shields.io/badge/📖_TECHNICAL_DOCS-Read_More-4078c0?style=for-the-badge&logo=github&logoColor=white)](CRYSTAL_BLITZ_DOCUMENTATION.md)

![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat-square&logo=html5&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black)
![Canvas API](https://img.shields.io/badge/Canvas_API-FF6B6B?style=flat-square&logo=mozilla&logoColor=white)
![Web Audio](https://img.shields.io/badge/Web_Audio_API-5A9FD4?style=flat-square&logo=webaudio&logoColor=white)
![Performance](https://img.shields.io/badge/Performance-60_FPS-green?style=flat-square)

**Portfolio Showcase • Open Source • Production Ready**

</div>

---

## 🎯 The Challenge

**Can you build a AAA-quality game with zero build tools, zero dependencies, and zero external assets?**

*Crystal Blitz is the answer.* A high-performance arena shooter that runs at 60 FPS with 200+ simultaneous entities — all from a single 347KB HTML file you can open directly in any browser.

### Why This Matters

- **No npm install** • No webpack • No frameworks
- **No loading screens** • No asset pipelines • No API calls
- **Just open and play** • Works offline • Works forever

This is what modern web development can achieve when performance and simplicity are the priority.

---

## ⚡ Quick Start

### Play Instantly
**[Click here to play →](https://zacsluss.github.io/CRYSTAL_BLITZ/Crystal_Blitz.html)**
*No installation. No setup. Just click.*

### Download & Run Locally
```bash
# Clone the repo
git clone https://github.com/Zacsluss/CRYSTAL_BLITZ.git

# Open and play (literally just open the file)
open Crystal_Blitz.html
```

That's it. No `npm install`. No build process. No server required.

---

## 🎮 Gameplay

<div align="center">

### Survive. Adapt. Dominate.

*Face endless waves of intelligent enemies in a fast-paced arena shooter where every crystal pickup transforms your playstyle.*

</div>

### Core Loop
1. **Eliminate enemies** to level up and choose permanent upgrades
2. **Collect crystals** for temporary but powerful abilities
3. **Survive waves** that grow progressively more challenging
4. **Face bosses** with unique multi-phase attack patterns

### What Makes It Addictive
- **11 Crystal Powerups** with unique visuals and mechanics
- **17 Permanent Upgrades** for endless build variety
- **12+ Enemy Behaviors** that evolve as you progress
- **Dynamic Difficulty** scaling from 15 to 90 enemies per wave
- **Boss Battles** every 10 waves with escalating complexity

---

## 💎 Crystal System

<div align="center">

| Crystal | Effect | Rarity | Duration |
|---------|--------|--------|----------|
| 🎯 **Homing** | Auto-targeting ammunition | Ultra Rare | 25 shots |
| ⚡ **Lightning** | Chain damage across enemies | Common | 50 shots |
| 💥 **Explosive** | Area-of-effect blasts | Common | 50 shots |
| ❄️ **Freeze** | Slows enemies by 50% | Common | 50 shots |
| 🏀 **Ricochet** | Bullets bounce off walls | Common | 50 shots |
| 💀 **Cluster** | Splits into fragments | Common | 50 shots |
| 🔍 **Seeking** | Curves toward targets | Common | 50 shots |
| 🔥 **Shotgun** | Wide-spread pattern | Common | 50 shots |
| 🔫 **Multi-Shot** | Fire 2x/3x/4x bullets | Common | 50 shots |

*Mix and match for devastating combos*

</div>

---

## 🛠️ Technical Excellence

### Architecture Highlights

<table>
<tr>
<td width="50%">

**Performance**
- 60 FPS locked framerate
- 200+ entities without lag
- Zero garbage collection in game loop
- 347KB total file size
- Sub-16ms frame times

</td>
<td width="50%">

**Code Quality**
- 9,280 lines of optimized JavaScript
- Entity Component System pattern
- Spatial grid collision detection (O(n))
- Object pooling for all entities
- Procedural audio synthesis

</td>
</tr>
</table>

### Advanced Techniques Demonstrated

```javascript
✓ Spatial Grid Partitioning → O(n²) to O(n) collision detection
✓ Object Pools → Zero runtime memory allocation
✓ Gradient Caching → 3x render speed improvement
✓ Delta Time → Frame-independent physics
✓ State Machines → Complex AI behaviors
✓ Touch Controls → Full mobile compatibility
```

### Why It's Fast

| Optimization | Impact |
|--------------|--------|
| **Zero GC in Game Loop** | No frame drops |
| **Gradient Caching (LRU)** | 3x faster rendering |
| **Particle Limits** | Consistent performance |
| **Spatial Grid** | O(n) collision detection |
| **Canvas State Cache** | Minimal draw calls |

---

## 🎮 Controls

<table>
<tr>
<td width="50%">

### 🖥️ Desktop
- **WASD** — Movement
- **Mouse** — Aim & Shoot
- **Shift** — Sprint/Dash
- **Space** — Emergency Leap
- **P / ESC** — Pause Menu

</td>
<td width="50%">

### 📱 Mobile
- **Left Touch** — Virtual Joystick
- **Right Touch** — Aim & Shoot
- **Bottom Left** — Sprint Button
- **Bottom Right** — Leap Button
- **Top Right** — Pause Button

</td>
</tr>
</table>

*Fully responsive. Works on any device.*

---

## 🚀 What's New in v0.99

### Latest Updates
- ✅ Fixed pause menu tab highlighting
- ✅ Fixed tab button sizing inconsistency
- ✅ Improved game over screen layout
- ✅ Added ESC key for pause menu
- ✅ Enhanced restart button visibility

### Major Features (Previous Versions)
- **Crystal Overhaul** — Unique shapes and visual effects for every crystal type
- **Footstep System** — Bipedal tracking with realistic fading
- **Glassmorphism UI** — Modern blur effects and animations
- **Hexagonal Floor** — Dynamic gradient-based floor pattern
- **Tabbed Pause Menu** — Organized Controls, Enemies, Crystals, and Upgrades sections

---

## 📊 Performance Benchmarks

| Scenario | FPS | Active Entities |
|----------|-----|-----------------|
| Normal Combat | **60** | 50-100 |
| Intense Battle | **55-60** | 200+ |
| Boss Fight | **50-60** | 250+ |
| Mobile (2020+) | **45-60** | 100+ |

*Tested on mid-range hardware. Optimized for consistent performance.*

---

## 👨‍💻 For Developers

### What You'll Learn

This project demonstrates production-grade implementations of:

- **Performance Optimization** — Console-quality rendering in a browser
- **Algorithm Design** — Efficient spatial partitioning and AI systems
- **Memory Management** — Zero-allocation game loops
- **Cross-Platform Dev** — Seamless desktop/mobile experience
- **Code Architecture** — Maintainable single-file structure

### Quick Dev Setup

```bash
git clone https://github.com/Zacsluss/CRYSTAL_BLITZ.git
cd CRYSTAL_BLITZ

# Optional: Run local server for testing
python -m http.server 8000
# Open http://localhost:8000/Crystal_Blitz.html
```

### Customization Points

```javascript
bulletPowerups[]  // Add new crystal types
enemy.update()    // Create new AI behaviors
waveScaling()     // Adjust difficulty curve
particleSystem()  // Add visual effects
```

---

## 📈 Project Stats

<div align="center">

| Metric | Value |
|--------|-------|
| **Lines of Code** | 9,280 |
| **File Size** | 347KB |
| **Dependencies** | 0 |
| **Build Steps** | 0 |
| **External Assets** | 0 |
| **Browser Support** | 100% |
| **Target FPS** | 60 |
| **Mobile Compatible** | ✓ |

</div>

---

## 🤝 Connect

<div align="center">

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Zachary_Sluss-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/zacharyjsluss/)
[![GitHub](https://img.shields.io/badge/GitHub-@Zacsluss-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/Zacsluss)
[![Portfolio](https://img.shields.io/badge/Portfolio-View_Projects-FF6B6B?style=for-the-badge&logo=google-chrome&logoColor=white)](https://zacsluss.github.io/Portfolio)

</div>

---

## 📄 License

Open source and free to use. See the code, learn from it, build something better.

---

<div align="center">

### Built with passion. Optimized for performance. Ready to impress.

**[Play Crystal Blitz →](https://zacsluss.github.io/CRYSTAL_BLITZ/Crystal_Blitz.html)**

*No installation required. Just click and play.*

</div>

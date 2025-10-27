<div align="center">

<!-- Hero Header -->
<img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=12,20,24&height=180&section=header&text=Crystal%20Blitz&fontSize=70&fontColor=FFFFFF&animation=twinkling&fontAlignY=30&desc=Arena%20Shooter%20in%20a%20Single%20HTML%20File&descSize=18&descAlignY=55"/>

<br/>

<!-- Animated Subtitle -->
<img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=20&duration=3000&pause=1000&color=2d9a5e&center=true&vCenter=true&random=false&width=600&lines=60+FPS+%E2%80%A2+200%2B+Entities+%E2%80%A2+347KB;Zero+Dependencies+%E2%80%A2+Zero+Build+Tools;Single+HTML+File+%E2%80%A2+Works+Forever" alt="Typing SVG" />

<br/>

<!-- Main Action Buttons -->
<p align="center">
  <a href="https://zacsluss.github.io/CRYSTAL_BLITZ/Crystal_Blitz.html">
    <img src="https://img.shields.io/badge/🎮_PLAY-LIVE_GAME-2d7a3e?style=for-the-badge&labelColor=000000&logo=gamepad&logoColor=white" alt="Play Now"/>
  </a>
  <a href="https://github.com/Zacsluss/CRYSTAL_BLITZ/raw/main/Crystal_Blitz.html">
    <img src="https://img.shields.io/badge/⬇️_DOWNLOAD-347KB_HTML-b5320a?style=for-the-badge&labelColor=000000&logo=download&logoColor=white" alt="Download"/>
  </a>
</p>

<!-- GitHub Stats Badges -->
<p align="center">
  <img src="https://img.shields.io/github/stars/Zacsluss/CRYSTAL_BLITZ?style=social" alt="Stars"/>
  <img src="https://img.shields.io/github/forks/Zacsluss/CRYSTAL_BLITZ?style=social" alt="Forks"/>
  <img src="https://img.shields.io/github/license/Zacsluss/CRYSTAL_BLITZ?style=flat-square&color=555555" alt="License"/>
  <img src="https://img.shields.io/github/last-commit/Zacsluss/CRYSTAL_BLITZ?style=flat-square&color=666666" alt="Last Commit"/>
</p>

</div>

<br/>

---

<div align="center">

![Crystal Blitz Gameplay](assets/gameplay.gif)

*Fast-paced arena combat with dynamic enemy AI, crystal powerups, and 60 FPS performance*

</div>

---

## 🎯 What This Is

**A high-performance arena shooter running at 60 FPS with 200+ simultaneous entities**—all from a single 347KB HTML file with no external dependencies. Open it in any browser and it works. No npm install, no webpack, no asset pipelines.

<div align="center">

```diff
+ 60 FPS locked framerate with 200+ entities
+ 347KB total file size (single HTML file)
+ O(n²) → O(n) collision detection via spatial grid
+ Zero runtime memory allocation (object pooling)
+ 11 crystal powerups + 17 permanent upgrades
+ Full mobile support with touch controls
```

</div>

<br/>

<div align="center">

<!-- Performance Metrics -->
<table>
  <tr>
    <td align="center">
      <img src="https://img.shields.io/badge/Performance-60_FPS-2d7a3e?style=flat-square&logo=speedtest&logoColor=white"/><br/>
      <sub><b>Frame Rate</b></sub>
    </td>
    <td align="center">
      <img src="https://img.shields.io/badge/Entities-200%2B-1E4A6D?style=flat-square&logo=atom&logoColor=white"/><br/>
      <sub><b>Simultaneous</b></sub>
    </td>
    <td align="center">
      <img src="https://img.shields.io/badge/Size-347KB-8B3A3A?style=flat-square&logo=file&logoColor=white"/><br/>
      <sub><b>Single File</b></sub>
    </td>
    <td align="center">
      <img src="https://img.shields.io/badge/Dependencies-0-8B6914?style=flat-square&logo=npm&logoColor=white"/><br/>
      <sub><b>Zero Deps</b></sub>
    </td>
  </tr>
</table>

</div>

<div align="center">
<img width="800" src="https://capsule-render.vercel.app/api?type=rect&color=gradient&customColorList=12,20,24&height=2"/>
</div>

---

## 💡 The Technical Challenge

**Achieving console-quality performance within browser constraints while maintaining code maintainability.** The result is 9,280 lines of optimized JavaScript implementing spatial grid partitioning (reducing collision detection from O(n²) to O(n)), object pooling for zero-allocation game loops, and procedural audio synthesis—all without frameworks or build tools.

<table>
<tr>
<td width="50%">

### 🎮 Gameplay Features

- **11 Crystal Powerups** - Homing shots, lightning chains, explosive blasts, freeze effects, ricochet bullets, cluster fragments
- **17 Permanent Upgrades** - Health, speed, fire rate, damage
- **Endless Waves** - Scale from 15 to 90 enemies
- **Boss Battles** - Every 10 waves with multi-phase patterns
- **12+ Enemy AI Types** - Melee rushers, ranged attackers, healers

</td>
<td width="50%">

### 📈 The Numbers

| Metric                  | Value                   |
| ----------------------- | ----------------------- |
| Frame Rate              | 60 FPS                  |
| Entities                | 200+                    |
| File Size               | 347KB (single HTML)     |
| Lines of Code           | 9,280                   |
| Dependencies            | 0                       |
| Collision Optimization  | O(n²) → O(n)            |
| Rendering Speed Boost   | 3x (gradient caching)   |

</td>
</tr>
</table>

---

## 🚀 Quick Start

<table>
<tr>
<td width="33%" align="center">

### 🌐 Play Online

**[Launch Game](https://zacsluss.github.io/CRYSTAL_BLITZ/Crystal_Blitz.html)**

Instant access, no installation

</td>
<td width="33%" align="center">

### 💾 Play Offline

**[Download HTML](https://github.com/Zacsluss/CRYSTAL_BLITZ/raw/main/Crystal_Blitz.html)**

Open in any browser

</td>
<td width="33%" align="center">

### 👨‍💻 Development

```bash
git clone <repo>
# Open file directly
```

</td>
</tr>
</table>

<br/>

<details>
<summary><b>🎮 Controls</b></summary>

### Desktop

- **WASD** - Movement
- **Mouse** - Aim & Shoot
- **Shift** - Sprint/Dash
- **Space** - Emergency Leap
- **P / ESC** - Pause Menu

### Mobile

- **Left Touch** - Virtual Joystick
- **Right Touch** - Aim & Shoot
- **Bottom Left** - Sprint Button
- **Bottom Right** - Leap Button

</details>

---

## 🛠️ Technical Stack

<div align="center">

![JavaScript](https://img.shields.io/badge/JavaScript-8B7500?style=for-the-badge&logo=javascript&logoColor=white)
![Canvas](https://img.shields.io/badge/Canvas_API-8B3A3A?style=for-the-badge&logo=html5&logoColor=white)
![Web Audio](https://img.shields.io/badge/Web_Audio-2B5A7A?style=for-the-badge&logo=webaudio&logoColor=white)

</div>

<br/>

<table>
<tr>
<td width="50%">

### 🏗️ Architecture

**Entity Component System** with:

- Spatial grid partitioning for collision
- Object pooling for bullets/particles/enemies
- LRU gradient cache (3x render speed)
- Delta-time physics (frame-independent)
- State machines for AI behaviors
- Procedural audio synthesis

</td>
<td width="50%">

### ⚡ Performance Optimizations

- **Zero GC** during gameplay (pre-allocated pools)
- **Cached canvas states** minimize draw calls
- **Particle limits** maintain 60 FPS
- **Spatial grid lookups** for efficient queries
- **Gradient computation** moved to init time
- **O(n) collision detection** vs O(n²)

</td>
</tr>
</table>

---

## 💭 Why I Built This

**As someone who manages enterprise platforms serving 3,000+ users across 22 countries, I built this to maintain hands-on technical skills. The best leaders never stop coding.**

This project specifically explores:

- ✅ **Performance constraints** - How far can you push browser rendering without WebGL?
- ✅ **Game fundamentals** - Spatial partitioning, object pooling, ECS architecture from scratch
- ✅ **Zero dependencies** - Works offline, forever (download today, works in 10 years)
- ✅ **Creative problem-solving** - No physics engine → build delta-time physics. No audio library → procedural synthesis
- ✅ **Maintainable code** - 9,280 lines in a single file, but structured with clear patterns

**The constraint of zero dependencies forced creative problem-solving.** No physics engine meant building delta-time physics from first principles. No audio library meant synthesizing sounds procedurally. No sprite atlases meant rendering everything with Canvas primitives. These limitations became opportunities to understand the fundamentals.

---

## 🤝 Contributing

Bug reports and feature suggestions welcome. See [CRYSTAL_BLITZ_DOCUMENTATION.md](CRYSTAL_BLITZ_DOCUMENTATION.md) for detailed technical documentation.

<div align="center">

### Fork it, make it yours! No credit needed. 🚀

</div>

---

<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=12,20,24&height=100&section=footer"/>

**Built by [Zachary Sluss](https://github.com/Zacsluss)** • MIT License

[![Portfolio](https://img.shields.io/badge/🌐_My_Portfolio-2d7a3e?style=flat-square)](https://zacsluss.github.io/portfolio)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0055A4?style=flat-square&logo=linkedin&logoColor=white)](https://linkedin.com/in/zacharyjsluss)
[![Email](https://img.shields.io/badge/Email-8B2E0F?style=flat-square&logo=gmail&logoColor=white)](mailto:zacsluss@yahoo.com)

</div>

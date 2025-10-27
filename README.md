<div align="center">

# Crystal Blitz

### High-performance arena shooter in a single HTML file—zero dependencies, zero build tools

**[Play Live Demo](https://zacsluss.github.io/CRYSTAL_BLITZ/Crystal_Blitz.html)** • **[Download (347KB)](https://github.com/Zacsluss/CRYSTAL_BLITZ/raw/main/Crystal_Blitz.html)**

</div>

---

## What This Is

Crystal Blitz is a browser-based arena shooter that runs at 60 FPS with 200+ simultaneous entities—all from a single 347KB HTML file with no external dependencies. Open it in any browser and it works. No npm install, no webpack, no asset pipelines.

The technical challenge was achieving console-quality performance within browser constraints while maintaining code maintainability. The result is 9,280 lines of optimized JavaScript implementing spatial grid partitioning (reducing collision detection from O(n²) to O(n)), object pooling for zero-allocation game loops, and procedural audio synthesis—all without frameworks or build tools.

**Key Stats:**
- 60 FPS locked framerate with 200+ entities
- 347KB total file size (single HTML file)
- Spatial grid optimization: O(n²) → O(n) collision detection
- Object pooling: zero runtime memory allocation
- Gradient caching: 3x rendering speed improvement
- Entity Component System architecture
- Full mobile support with touch controls

## Gameplay

Face endless waves of intelligent enemies while collecting 11 crystal powerups and unlocking 17 permanent upgrades. Waves scale from 15 to 90 enemies, with boss battles every 10 waves featuring multi-phase attack patterns.

**Crystal System:** Temporary powerups with unique mechanics—homing shots, lightning chains, explosive blasts, freeze effects, ricochet bullets, cluster fragments, and more. Stack effects for devastating combinations.

**Upgrade System:** Permanent improvements to health, speed, fire rate, and damage that compound across runs, creating meaningful build variety.

**Enemy AI:** 12+ behavior types using state machines—from basic melee rushers to ranged attackers, healers, and complex boss patterns.

## Technical Stack

Built with vanilla JavaScript, Canvas API, and Web Audio API. No frameworks, libraries, or external assets.

**Architecture:**
- Entity Component System pattern for scalable entity management
- Spatial grid partitioning for efficient collision detection
- Object pooling for bullets, particles, and enemies (zero GC in game loop)
- LRU gradient cache for 3x faster rendering
- Delta-time physics for frame-independent movement
- State machines for complex AI behaviors

**Performance Optimizations:**
- Zero garbage collection during gameplay (pre-allocated pools)
- Cached canvas states to minimize draw calls
- Particle system with hard limits to maintain 60 FPS
- Efficient spatial queries using grid-based lookups
- Gradient computation moved to initialization time

**Cross-Platform:**
- Desktop: WASD movement, mouse aiming, keyboard shortcuts
- Mobile: Touch joystick, tap-to-shoot, virtual buttons
- Fully responsive across devices

## Quick Start

**Play Online:** Visit [zacsluss.github.io/CRYSTAL_BLITZ/Crystal_Blitz.html](https://zacsluss.github.io/CRYSTAL_BLITZ/Crystal_Blitz.html)

**Play Offline:** [Download the HTML file](https://github.com/Zacsluss/CRYSTAL_BLITZ/raw/main/Crystal_Blitz.html) and open it in any browser—no server required.

**Development:**
```bash
git clone https://github.com/Zacsluss/CRYSTAL_BLITZ.git
cd CRYSTAL_BLITZ
# Open Crystal_Blitz.html in your browser or run:
python -m http.server 8000
# Navigate to http://localhost:8000/Crystal_Blitz.html
```

## Why I Built This

As someone who manages enterprise platforms serving 3,000+ users across 22 countries, I built this to maintain hands-on technical skills. The best leaders never stop coding.

This project specifically explores performance constraints—how far can you push browser-based rendering without falling back on WebGL or external engines? The answer: surprisingly far. By implementing game development fundamentals from scratch (spatial partitioning, object pooling, ECS architecture), I maintained both performance and code maintainability in a single file that works offline, forever.

The constraint of zero dependencies forced creative problem-solving. No physics engine meant building delta-time physics from first principles. No audio library meant synthesizing sounds procedurally. No sprite atlases meant rendering everything with Canvas primitives. These limitations became opportunities to understand the fundamentals.

## Contributing

Bug reports and feature suggestions welcome. See [CRYSTAL_BLITZ_DOCUMENTATION.md](CRYSTAL_BLITZ_DOCUMENTATION.md) for detailed technical documentation.

---

<div align="center">

**Built by [Zachary Sluss](https://github.com/Zacsluss)** • MIT License

[![GitHub stars](https://img.shields.io/github/stars/Zacsluss/CRYSTAL_BLITZ?style=social)](https://github.com/Zacsluss/CRYSTAL_BLITZ/stargazers)

</div>

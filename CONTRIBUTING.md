# Contributing to Crystal Blitz

Thank you for your interest in contributing to Crystal Blitz! This document provides guidelines and information for contributors.

## Table of Contents
- [Code of Conduct](#code-of-conduct)
- [Getting Started](#getting-started)
- [Development Setup](#development-setup)
- [Architecture Overview](#architecture-overview)
- [Coding Standards](#coding-standards)
- [Performance Requirements](#performance-requirements)
- [Testing](#testing)
- [Pull Request Process](#pull-request-process)

## Code of Conduct

This project welcomes contributions from everyone. Please be respectful and constructive in all interactions.

## Getting Started

1. **Fork the repository** on GitHub
2. **Clone your fork** locally:
   ```bash
   git clone https://github.com/YOUR_USERNAME/crystal_blitz.git
   cd crystal_blitz
   ```
3. **Create a branch** for your changes:
   ```bash
   git checkout -b feature/your-feature-name
   ```

## Development Setup

Crystal Blitz is a **single-file HTML5 game** with zero dependencies — no build process required!

### Running Locally

**Option 1: Direct File Access**
```bash
# Simply open index.html in your browser
open index.html  # macOS
start index.html # Windows
xdg-open index.html # Linux
```

**Option 2: Local Server (Recommended)**
```bash
# Python 3
python -m http.server 8000

# Python 2
python -m SimpleHTTPServer 8000

# Node.js (if you have http-server installed)
npx http-server -p 8000
```

Then visit `http://localhost:8000`

### Running Tests

Open `tests.html` in your browser to run the test suite:
```bash
open tests.html
# or
python -m http.server 8000
# then visit http://localhost:8000/tests.html
```

## Architecture Overview

### Single-File Constraint
ALL code must remain in `index.html`. This is a deliberate design choice for:
- Zero dependencies (works offline forever)
- Maximum portability (one file to share)
- Educational clarity (everything in one place)

### Key Systems

**Fixed Timestep Game Loop** (lines 10200-10280)
- Update: 60 FPS fixed timestep with accumulator
- Render: Variable with interpolation for smooth visuals

**Spatial Grid Collision Detection** (lines 4488-4517)
- 50×50px cells for O(n) collision detection
- Critical for handling 200+ entities at 60 FPS

**Object Pooling** (lines 4526-4580)
- Pre-allocated entity pools
- Zero GC during gameplay

**Gradient Cache** (lines 3900-3950)
- LRU cache (100 entries) for radial gradients
- 3x rendering performance improvement

### Code Sections (marked with comments)
```javascript
// ============================================================
// SECTION: [NAME]
// ============================================================
```

Sections include:
- Math Utilities (lines 3037-3119)
- Input & Controls (lines 3346-3690)
- Performance Optimizations (lines 3692-3900)
- Game Constants (lines 3270-3343)
- Object Pools (lines 4519-4620)
- Game State (lines 4400-4480)
- Update Loop (lines 5640-7300)
- Render Loop (lines 7370-9300)

## Coding Standards

### JavaScript Style

**1. Performance First**
```javascript
// ✅ GOOD: Direct iteration, no iterator overhead
for (let i = 0; i < arr.length; i++) {
  if (arr[i].alive) { /* ... */ }
}

// ❌ BAD: Creates iterator object (GC pressure)
for (const item of arr) {
  if (item.alive) { /* ... */ }
}
```

**2. Zero GC in Game Loop**
```javascript
// ✅ GOOD: Reuse existing objects
normInPlace(dx, dy, vecPool.temp1);

// ❌ BAD: Creates new object every frame
const normalized = {x: nx, y: ny};
```

**3. Magic Numbers → Constants**
```javascript
// ✅ GOOD: Named constant
if (speed > GAME_CONSTANTS.PLAYER_MAX_SPEED) { /* ... */ }

// ❌ BAD: Magic number
if (speed > 500) { /* ... */ }
```

**4. JSDoc for Key Functions**
```javascript
/**
 * Spawns a new enemy at the edge of the screen
 * @param {Object} g - Game state object
 * @param {number|null} clusterX - X coordinate for cluster spawn
 * @param {number|null} clusterY - Y coordinate for cluster spawn
 */
function spawnEnemy(g, clusterX = null, clusterY = null) {
  // ...
}
```

**5. No Console Logs in Production**
```javascript
// ❌ BAD: Console logs slow down game loop
console.log('Player hit!');

// ✅ GOOD: Remove or comment out
// Player was hit, trigger invulnerability
```

### Naming Conventions
- **Functions**: camelCase (`spawnEnemy`, `updatePlayerMovement`)
- **Constants**: SCREAMING_SNAKE_CASE (`MAX_SPEED`, `PLAYER_RADIUS`)
- **Variables**: camelCase (`playerSpeed`, `bulletCount`)
- **Temporary vars**: Short names in tight loops (`i`, `j`, `dx`, `dy`)

### Comments
```javascript
// Section headers
// ============================================================
// SECTION: [NAME]
// ============================================================

// Subsection headers
// ===== [Subsystem Name] =====

// Inline comments for non-obvious logic
const scaledDamage = baseDamage * (1 + wave * 0.1); // +10% damage per wave
```

## Performance Requirements

### Hard Requirements
- **Target**: 60 FPS with 200+ entities on screen
- **Max GC**: 0 allocations per frame in game loop (update/draw)
- **Max Particle Count**: 500 particles (enforced by `PERF_CONSTANTS.MAX_PARTICLES`)
- **Max Blood Stains**: 200 decals
- **Gradient Cache**: 100 entries maximum

### Performance Testing
```javascript
// Before your change
// 1. Open browser DevTools (F12)
// 2. Go to Performance tab
// 3. Record 10 seconds of gameplay at Wave 10+
// 4. Check for:
//    - Frame rate stays at 60 FPS
//    - No GC pauses during gameplay
//    - Memory stays flat (no leaks)

// After your change - repeat the same test
```

### Optimizations to Maintain
1. **Spatial grid for collisions** (not brute force O(n²))
2. **Object pooling** (not `new Object()` in loops)
3. **Cached gradients** (not creating gradients each frame)
4. **Direct iteration** (not `for-of` or `.forEach()`)
5. **Fast math** (cached sin/cos, `fastLength` approximations)

## Testing

### Manual Testing Checklist
Before submitting a PR, verify:
- [ ] Game starts without errors
- [ ] Survive to Wave 10+ without crashes
- [ ] All crystal powerups work correctly
- [ ] Save/load functionality works
- [ ] Audio plays correctly (or fails gracefully)
- [ ] Touch controls work on mobile (if applicable)
- [ ] FPS stays at 60 with 100+ enemies on screen
- [ ] No console errors (check DevTools)

### Automated Tests
Run `tests.html` and ensure all 48 tests pass:
- Core systems (15 tests)
- Math utilities (7 tests)
- Game loop (6 tests)
- Spatial grid (8 tests)
- Powerups (4 tests)
- Rendering (4 tests)
- Save/load (4 tests)

### Browser Compatibility
Test in at least 2 browsers:
- ✅ Chrome/Edge (Chromium)
- ✅ Firefox
- ✅ Safari (if on macOS)

## Pull Request Process

### 1. Before You Start
- Check existing issues to avoid duplicate work
- For large changes, open an issue first to discuss the approach

### 2. Making Changes
```bash
# Create a feature branch
git checkout -b feature/add-new-crystal-type

# Make your changes to index.html and/or tests.html

# Test thoroughly (see Testing section above)

# Commit with descriptive message
git add index.html tests.html
git commit -m "Add new 'Vortex' crystal powerup with pull effect

- Adds VORTEX crystal type (5% drop rate)
- Pulls enemies toward bullet impact point
- 30 shots per crystal pickup
- Tested through Wave 15+"

# Push to your fork
git push origin feature/add-new-crystal-type
```

### 3. Opening the Pull Request
- Fill out the PR template completely
- Reference related issues (e.g., "Closes #42")
- Include screenshots/videos for visual changes
- Describe performance impact (if any)

### 4. Review Process
- Maintainer will review within 1 week
- Address feedback by pushing new commits to your branch
- Once approved, PR will be merged

### 5. After Merge
- Delete your feature branch
- Pull the latest main branch:
  ```bash
  git checkout main
  git pull upstream main
  ```

## Common Contribution Types

### Adding a New Crystal Powerup
1. Add to `bulletPowerups` array (lines ~4900-5100)
2. Update drop rate logic in crystal spawn function
3. Add effect handling in bullet update loop
4. Add visual indicator in HUD
5. Test with other powerups (no conflicts)

### Adding a New Enemy Behavior
1. Add behavior to `ENEMY_BEHAVIORS` array (lines ~4650-4694)
2. Add case in enemy update loop (lines ~6100-6600)
3. Balance health/speed/damage
4. Test with boss waves
5. Ensure spatial grid handles it correctly

### Performance Optimization
1. Profile with DevTools Performance tab
2. Identify bottleneck (provide flamegraph screenshot)
3. Implement optimization maintaining code clarity
4. Benchmark before/after (FPS, memory, GC pauses)
5. Document any trade-offs

### Bug Fix
1. Reproduce the bug reliably
2. Add test case to `tests.html` (if applicable)
3. Fix the bug
4. Verify test passes
5. Test in multiple browsers

## Questions or Issues?

- **Bug reports**: [Open a bug report](https://github.com/Zacsluss/crystal_blitz/issues/new?template=bug_report.md)
- **Feature requests**: [Open a feature request](https://github.com/Zacsluss/crystal_blitz/issues/new?template=feature_request.md)
- **Questions**: Open a discussion or comment on an existing issue

## License

By contributing to Crystal Blitz, you agree that your contributions will be licensed under the MIT License.

---

Thank you for contributing to Crystal Blitz!

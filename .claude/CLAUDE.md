# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Crystal Blitz is a single-file HTML5 arena shooter game contained entirely in `Crystal_Blitz.html` (7,704 lines, 283KB). No dependencies, no build process, no external assets - everything is self-contained.

## Architecture & Key Systems

### Core Game Loop
The game uses a fixed timestep (1/60s) with interpolation for smooth rendering. Main systems:
- **Object Pooling**: Pre-allocated arrays for all entities to minimize garbage collection
- **Spatial Grid**: 50x50px cells for O(n) collision detection instead of O(n²)
- **State Machine**: Clean state transitions (MENU, RUN, PAUSE, OVER, POWERUP)

### Critical Performance Optimizations
- **Zero GC in Game Loop**: No string concatenation, no array allocations, value caching
- **Gradient Caching**: LRU cache (100 entries max) with numeric keys for all gradients
- **Particle Limits**: Hard caps at 500 particles, 200 blood stains
- **Batch Rendering**: Single paths for multiple shapes, minimal canvas state changes
- **Canvas State Caching**: Track fillStyle, strokeStyle, globalAlpha to avoid redundant sets

### Entity Component Pattern
All entities follow this structure:
```javascript
entity = {
  x, y,          // Position
  vx, vy,        // Velocity  
  r,             // Collision radius
  hp,            // Health
  behavior,      // AI type
  effects,       // Active modifiers (Set for O(1) lookup)
  color,         // Visual
  alive          // State
}
```

### Crystal Power System
11 crystal types with temporary effects (25-50 shots each):
- **Homing** (ultra-rare, 0.5% drop): Strong auto-targeting
- **Explosive, Lightning, Freeze, Ricochet, Seeking, Cluster, Shotgun**: Common drops
- **Multi-shot upgrades**: Dual, Triple, Quad patterns

### Enemy AI Behaviors
12+ behavior types unlocked progressively:
- Waves 1-2: Basic behaviors
- Waves 3-4: +Flank, charge, shields
- Waves 5-6: +Erratic, spiral shooters
- Waves 7+: All behaviors active

## Development Guidelines

### When Modifying Code
1. **Check existing patterns first** - The game uses specific optimization patterns throughout
2. **Maintain zero GC policy** - Avoid string concatenation, array allocations in hot paths
3. **Respect particle limits** - Always check MAX_PARTICLES/MAX_BLOOD_STAINS before spawning
4. **Use cached values** - DOM updates only when values change
5. **Preserve object pooling** - Reuse dead objects instead of creating new ones

### Key Functions & Locations
- Game initialization: `newGame()` function
- Main update loop: `update(g, dt)` 
- Rendering: `draw(g, alpha)`
- Collision detection: Spatial grid system
- Enemy AI: `enemy.update()` with behavior-specific logic
- Crystal effects: `bulletPowerups[]` array and effect Sets

### Testing Approach
Since this is a single HTML file with no dependencies:
1. Open `Crystal_Blitz.html` directly in browser
2. Test gameplay manually - no automated tests
3. Monitor console for errors (though console.log is removed from game loop)
4. Check FPS counter (bottom-right) for performance

### Common Modifications
- **Add new crystal type**: Modify `bulletPowerups[]` array
- **Adjust difficulty**: Change wave scaling formulas in wave system
- **New enemy behavior**: Add case in enemy `update()` function
- **Visual effects**: Particle system with hard limits

## Important Notes
- **No build process** - Direct HTML file editing only
- **Performance critical** - Game targets 60 FPS with 200+ entities
- **Mobile support** - Touch controls must be maintained
- **Single file constraint** - All changes stay within Crystal_Blitz.html
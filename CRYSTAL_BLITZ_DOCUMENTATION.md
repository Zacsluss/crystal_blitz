# Crystal Blitz - Complete Technical Documentation

## Table of Contents
1. [Overview](#overview)
2. [Game Architecture](#game-architecture)
3. [Core Systems](#core-systems)
4. [Entity Systems](#entity-systems)
5. [Gameplay Mechanics](#gameplay-mechanics)
6. [Combat Systems](#combat-systems)
7. [Progression Systems](#progression-systems)
8. [User Interface](#user-interface)
9. [Performance Optimizations](#performance-optimizations)
10. [Technical Implementation](#technical-implementation)

---

## Overview

### Project Summary
**Crystal Blitz** is a single-file HTML5 arena survival shooter game where players face endless waves of increasingly difficult enemies. The game features a robust crystal-based powerup system, intelligent enemy AI, and progressive difficulty scaling.

### Key Features
- **Single-File Architecture**: Entire game contained in one HTML file (8,500+ lines)
- **No External Dependencies**: Self-contained with procedural audio, no external assets
- **Cross-Platform**: Works on desktop and mobile browsers
- **Performance Optimized**: Adaptive quality system, object pooling, spatial partitioning
- **Rich Gameplay**: 11 crystal types with unique visuals, 17 permanent upgrades, 12+ enemy behaviors
- **Enhanced UI**: Glassmorphism effects, tabbed menus, responsive design
- **Visual Systems**: Footstep tracking, hexagonal floor pattern, enhanced blood effects

### Technology Stack
- **Language**: Vanilla JavaScript (ES6+)
- **Rendering**: HTML5 Canvas 2D API
- **Audio**: Web Audio API (procedural sound generation)
- **Build**: None required (single HTML file)
- **Size**: ~310KB uncompressed

---

## Game Architecture

### State Management
```javascript
const STATE = { 
  MENU: 0,     // Main menu
  RUN: 1,      // Active gameplay
  PAUSE: 2,    // Game paused
  OVER: 3,     // Game over screen
  POWERUP: 4   // Powerup selection dialog
};
```

### Core Game Loop
1. **Initialization** (`newGame()`)
   - Creates game state object
   - Initializes player
   - Sets up wave system
   - Creates object pools

2. **Update Loop** (`update(g, dt)`)
   - Input processing (keyboard/mouse/touch)
   - Player movement and shooting
   - Enemy AI and movement
   - Collision detection
   - Particle systems
   - Wave progression

3. **Render Loop** (`draw(g, alpha)`)
   - Background grid
   - Entities (player, enemies, bullets)
   - Particles and effects
   - UI elements

4. **Frame Management** (`frame(time)`)
   - Delta time calculation (max 0.05 seconds clamping)
   - Fixed timestep: 1/60 second with accumulator
   - Interpolation (alpha) for smooth rendering
   - Performance monitoring (20-sample FPS averaging)
   - Error boundaries with auto-pause on critical errors

### Object Pooling System
```javascript
function makePool(createFn, initial=0)
```
- Reuses objects to minimize garbage collection
- Pools for: bullets, enemies, particles, pickups, blood stains, mines
- Pre-allocates objects for better performance

### Spatial Partitioning
- Grid-based collision detection system
- Divides game world into cells
- O(1) neighbor queries instead of O(n²) checks

---

## Core Systems

### Input System

#### Keyboard Controls
- **WASD**: Movement
- **Mouse**: Aim and shoot
- **Shift**: Sprint/Dash (consumes stamina)
- **Space**: Emergency leap (3-second cooldown)
- **P**: Pause Menu (with tabs for Controls, Enemies, Crystals, Upgrades)
- **F11**: Fullscreen

#### Touch Controls
- **Left half**: Virtual joystick for movement
- **Right half**: Touch to aim and shoot
- Dead zone system for precise control

### Physics System
- **Velocity-based movement**: Smooth acceleration/deceleration
- **Friction**: Natural slowing (multiplier: 0.94 per frame)
- **Collision**: Circle-based collision detection
- **Knockback**: Dynamic force application on impact

### Audio System
- **Procedural Generation**: All sounds created in real-time
- **Sound Types**:
  - Shooting: 680Hz square wave
  - Hit: 220Hz sawtooth
  - Death: Variable frequency based on enemy size
  - Powerup: 440Hz triangle
  - Critical: 400Hz triangle
- **Web Audio API**: Direct oscillator synthesis

---

## Entity Systems

### Player Entity

#### Base Stats
```javascript
{
  x, y: position
  vx, vy: velocity
  radius: 10
  hp: 100 (max)
  stamina: 100 (max)
  speed: 270
  fireDelay: 0.12 (seconds between shots)
}
```

#### Stamina System
- **Sprint Cost**: 20% per second
- **Regeneration**: 12.5% per second (base)
- **Exhaustion**: 2-second cooldown when depleted
- **Dash Multiplier**: 1.6x speed

#### Upgrade Tracking
- Pattern multipliers (Map): triple, quad shots
- Active effects (Map): homing, explosive, etc.
- Static upgrades (Map): permanent buffs
- Upgrade counts: Stack tracking

### Enemy System

#### Enemy Types
1. **Normal** (Red, r=14)
   - Balanced stats
   - Direct movement

2. **Fast** (Orange, r=10)
   - 1.5x speed
   - Lower health

3. **Tank** (Dark Orange, r=18)
   - 3x health
   - 0.66x speed

4. **Zergling** (Dark Yellow, r=12)
   - 2.2x speed
   - Waves 1-12 only

#### Enemy Behaviors

1. **Normal**: Direct path to player with realistic gait (cadence-based rhythm)
2. **Zigzag**: Serpentine movement with sinusoidal patterns
3. **Flank**: Approach from sides/behind using perpendicular movement
4. **Charge**: Telegraph (1s white flash) → Dash (3x speed) → Cooldown (3-5s)
5. **Erratic**: Chaotic movement with panic rhythm
6. **Suicide**: Orbit (120px radius) → Telegraph (1s red flash) → Seeking charge (2x speed)
7. **Slowpush**: Tank with directional shields (90% rotation speed), knockback (250 force)
8. **Spiralshooter**: Continuous rotating shots (3 rad/s), 0.6s interval
9. **Splitter**: Spawns 2-3 smaller enemies (60% size, 40% HP) on death
10. **Minelayer**: Drops up to 8 mines (12s interval), 35px trigger, 70px explosion
11. **Boss**: Heavy footsteps rhythm, 1.5x size, 2.5x HP
12. **Superboss**: 4 phases cycling every 20s (pursuit, orbit, berserker, charge)

#### Behavior Unlock Progression
- **Waves 1-2**: Basic (normal, zigzag, suicide, zergling)
- **Waves 3-4**: +Flank, charge, slowpush, splitter, minelayer
- **Waves 5-6**: +Erratic, spiralshooter
- **Waves 7+**: All behaviors (no zerglings)

### Bullet System

#### Bullet Properties
```javascript
{
  x, y: position
  vx, vy: velocity
  r: radius (4 base)
  life/maxLife: lifetime
  effectSet: Set of active effects
  pierces: penetration count
  bounces: ricochet count
  critical: boolean
  hitEnemies: Set (tracking for piercing)
}
```

#### Bullet Effects
Effects can stack and combine (stored in Set for O(1) lookup):
- **Normal**: Basic projectile
- **Homing**: Strong tracking (0.3 strength), retargets when enemy dies (25 shots)
- **Explosive**: 60px radius area damage (50 shots)
- **Lightning**: Chains to 3 enemies within 120px range (50 shots)
- **Freeze**: Slows enemies 50% for 2 seconds (50 shots)
- **Ricochet**: Bounces off walls 3x, extended lifetime (50 shots)
- **Seeking**: Gentle curves (0.2 strength) within 200px range (50 shots)
- **Cluster**: Splits into 3 fragments on impact (50 shots)
- **Shotgun**: Creates 4-bullet spread (0.5 rad angle) on hit (50 shots)

---

## Gameplay Mechanics

### Wave System

#### Wave Scaling
```javascript
// Enemy count progression
Waves 1-50: 15 + 45 * sqrt((wave-1)/49)  // 15→60 enemies
Waves 51+: 60 + 30 * ((wave-50)/50)       // 60→90 enemies
```

#### Wave Completion
- Triggered when 50% of enemies killed
- 3-second break between waves
- All enemies spawn within 2-4 seconds

#### Boss Waves
- **Every 5 waves**: Mini-bosses (10% spawn chance)
- **Every 10 waves**: Super bosses (limited quantity)
- Boss stats: 4x size, 4x health, 2x damage

### Crystal Drop System

#### Drop Rates
- **Regular Enemies**: 3% base chance
- **Lucky Upgrade**: +20% per stack
- **Boss Guarantee**: 15% homing crystal
- **Crystal Rarity**:
  - Homing: 0.5% (ultra-rare)
  - Others: Equal distribution

#### Crystal Types Distribution
```javascript
bulletPowerups = [
  {type: 'upgrade', color: '#32CD32', shots: 50},  // Dual Shot (green)
  {type: 'triple', color: '#00BFFF', shots: 50},   // Triple Shot (cyan)
  {type: 'quad', color: '#FF1493', shots: 50},     // Quad Shot (pink)
  {type: 'homing', color: '#FFD700', shots: 25},   // Homing (gold, ultra-rare)
  {type: 'explosive', color: '#FF4500', shots: 50}, // Explosive (red)
  {type: 'ricochet', color: '#FF69B4', shots: 50}, // Ricochet (hot pink)
  {type: 'lightning', color: '#00BFFF', shots: 50}, // Lightning (cyan/yellow gradient)
  {type: 'freeze', color: '#00CED1', shots: 50},   // Freeze (dark turquoise)
  {type: 'shotgun', color: '#8B4513', shots: 50},  // Shotgun (brown)
  {type: 'cluster', color: '#FFA500', shots: 50},  // Cluster (orange)
  {type: 'seeking', color: '#DC143C', shots: 50}   // Seeking (crimson)
]
```

#### Crystal Visual Shapes
- **Homing**: 8-pointed star with golden aura
- **Explosive**: Hexagon
- **Lightning**: Lightning bolt with yellow-blue gradient
- **Freeze**: 6-pointed snowflake
- **Ricochet**: Triangle
- **Seeking**: Stylized arrow
- **Shotgun**: Pentagon
- **Cluster**: Square
- **Dual/Triple/Quad**: Diamond shapes

#### Crystal Combination System
- Multiple effects stack (stored in `activeEffects` Map)
- Pattern multipliers combine (stored in `patternMultipliers` Map)
- All active effects apply to each bullet
- Shot counts add rather than replace

### Pickup Physics
- Initial upward velocity (bounce effect)
- Gravity simulation
- Magnetic attraction when player has upgrade
- Collection on contact

---

## Combat Systems

### Damage Calculation

#### Player Damage
```javascript
baseDamage = 1
criticalMultiplier = 2.0 (if critical hit)
finalDamage = baseDamage * (critical ? 2 : 1)
```

#### Enemy Damage
```javascript
touchDamage = baseTouch * (1 + wave * 0.12)
explosionDamage = 15 (suicide enemies)
bulletDamage = 5
mineDamage = 20
```

#### Damage Reduction
- Shield upgrade: 25% reduction per stack (max 90%)
- Calculation: `damage * (1 - damageReduction)`

### Critical Hit System
- Base chance: 0%
- +10% per Critical Strike upgrade
- Maximum: 50%
- Visual: Yellow flash on enemy
- Audio: Distinct hit sound

### Collision Detection

#### Entity Collisions
```javascript
// Circle-circle collision
distance² < (r1 + r2)²
```

#### Shield System (Slowpush Enemies)
- Directional shields covering 120° arc
- Shield HP scales with wave difficulty (base 15 HP × difficulty multiplier)
- Dot product check for hit direction (>0.3 = shield hit)
- 90% rotation speed for counterplay opportunity

#### Optimization Techniques
1. Squared distance comparison (avoids sqrt)
2. Spatial grid partitioning
3. Early exit conditions
4. Cached calculations

### Special Combat Mechanics

#### Piercing Shots
- Base: 0 pierces
- +1 per Piercing Shot upgrade
- Tracks hit enemies to prevent double damage

#### Explosive Damage
- Radius: 60 pixels
- Damage: 1 point to all enemies in radius
- Visual: Triple burst (orange, red, yellow core)
- Stacks with other effects
- 25 + 15 + 10 particles for dramatic effect

#### Lightning Chain
- Range: 120 pixels (reduced from 150)
- Max chains: 3 per bullet
- Damage: 1 point per chain
- Visual: Triple burst (yellow, white, cyan) + bolt line effect
- 5-step interpolated lightning path visualization

---

## Progression Systems

### Leveling System

#### Kill Requirements
```javascript
Level 1: 10 kills
Level 2: +25 kills (35 total)
Level 3: +50 kills (85 total)
Level 4: +100 kills (185 total)
Level 5+: +50 + 50*(level-3) kills
```

#### Powerup Selection
- 3 random choices per level
- Cannot select maxed upgrades
- Stackable upgrades show count
- Pause game during selection

### Permanent Upgrades

#### Movement & Defense
1. **Speed Boost**: +12.5% movement speed
2. **Stamina Boost**: +25% stamina regeneration
3. **Dash Cooldown**: -15% exhaustion duration
4. **Shield**: +25% damage reduction
5. **Knockback Resistance**: +50% reduction
6. **Max Health**: +30 HP & instant heal
7. **Health Regen**: +0.5 HP/second

#### Combat
8. **Rapid Fire**: -12.5% fire delay
9. **Bullet Size**: +25% projectile size
10. **Bullet Speed**: +25% projectile velocity
11. **Piercing Shot**: +1 penetration
12. **Critical Strike**: +10% crit chance

#### Utility
13. **Magnetic Crystals**: +80px attraction range
14. **Lucky**: +20% crystal drop rate
15. **Vampire**: +0.5 HP per kill
16. **Adrenaline**: +20% speed for 3s after damage
17. **Efficient**: +5% chance to not consume ammo

### Upgrade Stacking
- Most upgrades stack additively
- Damage reduction caps at 90%
- Critical chance caps at 50%
- Ammo efficiency caps at 50%

---

## User Interface

### HUD Elements

#### Health Bar
- Position: Top-left
- Gradient: Red (#ff6b6b → #ffa5a5)
- Updates: Real-time with damage flash
- Effects: Shimmer animation on healing, enhanced glow

#### Stamina Bar
- Position: Below health
- Gradient: Yellow (#ffd166 → #ffeb99)
- Pulse effect when depleted

#### Stats Display
- Wave counter
- Kill counter
- FPS meter (bottom-right)

### Menu Systems

#### Main Menu
- Animated title with rainbow gradient
- Enhanced controls panel
- Mobile instructions
- Start button with hover effects

#### Pause Menu
- Controls reminder
- Active upgrades display
- Resume button
- Auto-pause on tab switch

#### Game Over Screen
- Final stats (wave, kills)
- Restart button
- Dramatic entry animation

### Visual Effects

#### Animations
```css
- menuFadeIn: Scale (0.8→1) + rotate (-1°→0°) + blur (8px→0)
- titleSlideIn: TranslateY (-20px→0) + blur (4px→0)
- buttonSlideIn: TranslateY (20px→0) + scale (0.9→1)
- powerupPulse: Complex 3s animation with rotation and blur
- waveCardEntry: Scale (0.3→1) + rotate (-10°→0°) with overshoot
- gameOverDramaticEntry: Scale (0.5→1) + rotate (-5°→0°)
- pauseSlideIn/Out: Scale (0.9→1) with cubic-bezier easing
- gameStartFlash: Radial gradient flash effect (1.2s)
```

#### Crystal Visual System
- Inventory display: Left side under HUD (24px x-position)
- Size: 40px diamonds with 50px spacing
- Sparkle effect: Sin-based alpha animation (0.8-1.0)
- Homing crystals: Golden glow aura with pulsing intensity
- Shot counter omitted from display (tracked internally)

#### Edge Warnings
- Red pulsing borders when enemies near
- 100px proximity threshold
- Helps track off-screen threats

#### Crystal Legend
- Integrated into pause menu (no longer L key)
- Shows all crystal types with animations
- Canvas-based previews with slow rotation
- Effect descriptions and durations
- Organized by rarity (Ultra Rare, Effect, Pattern)

### Powerup Dialog

#### Selection Interface
- 3 random upgrade choices
- Hover effects and animations
- Click to select
- Auto-resume after selection

#### Visual Feedback
- Selected item golden flash
- Scale and rotation effects
- Smooth transitions

---

## Performance Optimizations

### Rendering Optimizations

#### Canvas State Caching
```javascript
// Cache expensive operations
let lastFillStyle = '';
let lastStrokeStyle = '';
let lastGlobalAlpha = 1;
let lastLineWidth = 1;

function setFillStyle(style) {
  if (lastFillStyle !== style) {
    ctx.fillStyle = style;
    lastFillStyle = style;
  }
}
```

#### Gradient Caching with LRU
```javascript
const gradientCache = new Map();
const MAX_GRADIENT_CACHE_SIZE = 100;
```
- Global cache persists between frames (no memory leak)
- LRU eviction when cache exceeds 100 entries
- Numeric keys for fast Map lookups
- Caches all gradients: leap glow, boss aura, damage vignette, homing crystals
- Prevents recreation of expensive gradient objects every frame

#### Canvas Transform Management
```javascript
// Reset transform matrix each frame to prevent accumulation
ctx.setTransform(1, 0, 0, 1, 0, 0);
```
- Prevents transform stack corruption
- Fixes rotation bugs that occurred at higher waves
- Ensures clean slate for each render frame

#### Batch Rendering
- Single path for multiple shapes (bullets, enemies)
- Batched blood stains by state (settled vs moving)
- Grouped particle rendering by type
- Minimal save/restore operations
- Pre-sorted rendering layers

#### Background Grid
- Rendered once to offscreen canvas
- Reused every frame
- Redrawn only on resize

### Memory Management

#### Zero Garbage Collection in Game Loop
- **No String Concatenation**: Template literals instead of `+ '%'`
- **Value Caching**: DOM only updates when values change
- **Array Allocation Free**: Using `normInPlace` with pooled vectors
- **No Console Statements**: All console.log/error removed from hot paths

#### Hard Particle Limits
```javascript
const MAX_PARTICLES = 500;
const MAX_BLOOD_STAINS = 200;
```
- Prevents unbounded growth during intense combat
- Checks before spawning new particles
- Maintains consistent performance

#### Object Pooling
- Pre-allocated entity arrays
- Reuse dead objects
- No runtime allocations
- Minimal garbage collection

#### LRU Trig Cache
```javascript
// Smart eviction instead of clearing entire cache
if (sinCache.size > TRIG_CACHE_SIZE) {
  const firstKey = sinCache.keys().next().value;
  sinCache.delete(firstKey);
}
```
- Removes oldest entry when full
- Maintains cache effectiveness
- Prevents cache thrashing

#### Optimized Data Structures
- Sets for O(1) effect lookups
- Maps for efficient key-value caching
- Pooled vector objects for calculations
- Numeric keys instead of string templates

### Computational Optimizations

#### Fast Math
```javascript
// Cached trigonometry
const sinCache = new Map();
const cosCache = new Map();

// Squared distance (no sqrt)
function fastDistanceCheck(x1, y1, x2, y2, maxDist) {
  const dx = x2 - x1, dy = y2 - y1;
  return dx*dx + dy*dy <= maxDist*maxDist;
}

// Bit operations
const index = (Math.random() * length) | 0; // Faster than Math.floor
```

#### Spatial Partitioning
- Grid-based collision system
- 50x50 pixel cells
- Only check neighboring cells
- Reduces O(n²) to ~O(n)

### Adaptive Quality

#### Performance Monitoring
```javascript
performanceLevel: 0.3 to 1.0
// Adjusts based on frame time
// Reduces particles when slow
// Skips non-essential effects
```

#### Dynamic Adjustments
- Particle spawn reduction
- Effect quality scaling
- Draw distance optimization
- Frame skip for updates

---

## Visual Systems

### Footstep System
- **Bipedal tracking**: Alternating left/right footprints
- **Entity-based**: All moving entities leave footprints
- **Fade mechanics**: 
  - 3.6 seconds visible at 70% opacity
  - 2.4 seconds gradual fade
  - Object pooled for performance
- **Visual style**:
  - Realistic foot shapes with toe marks
  - Gradient coloring (tan/brown)
  - Shadow layer for depth

### Floor Pattern System
- **Hexagonal grid**: 60px hexagons
- **Dynamic rendering**: Only redraws when needed
- **Gradient effects**: Dark center to lighter edges
- **Cached to off-screen canvas**: Prevents per-frame regeneration

### Blood Effects
- **Particle-based**: Initial splatter with velocity
- **Settlement system**: Droplets slow and stick
- **Gradual fading**: 
  - 60% lifetime at full opacity
  - 40% lifetime quick fade
- **Object pooled**: Max 200 stains

### Crystal Effects
- **Multi-layered rendering**:
  1. Shape layer (unique per type)
  2. Gradient fill layer
  3. Glow/aura layer
  4. Particle emission layer
- **Animation systems**:
  - Rotation (varies by type)
  - Pulsing (intensity varies)
  - Particle spawning (periodic)
- **Special effects**:
  - Homing: Golden aura with intense glow
  - Lightning: Yellow-blue gradient
  - All crystals: Sparkle particles

---

## Technical Implementation

### Code Structure

#### File Organization
```
Crystal_Blitz.html
├── <head>
│   ├── Meta tags
│   └── <style> (Enhanced CSS with glassmorphism)
├── <body>
│   ├── Canvas element
│   ├── UI containers
│   └── <script> (Optimized JavaScript)
```

#### Module Pattern
- IIFE encapsulation
- Strict mode enabled
- No global pollution
- Clear separation of concerns

### Security Measures

#### Input Sanitization
```javascript
function sanitizeText(text) {
  return text.replace(/</g, '&lt;')
             .replace(/>/g, '&gt;')
             .replace(/"/g, '&quot;')
             .replace(/'/g, '&#x27;');
}
```

#### Safe Parsing
- `safeParseInt()` with defaults
- `safeParseFloat()` with validation
- Error boundaries in critical sections
- Try-catch for audio/render failures

### Browser Compatibility

#### Feature Detection
- Canvas 2D support check
- Web Audio API fallback (webkit prefix)
- Touch event support (preventDefault on all)
- Fullscreen API detection
- Image smoothing disabled for pixel-perfect rendering
- Visibility API for auto-pause

#### Error Handling
- Try-catch blocks around critical sections
- Audio failures silently handled
- Auto-pause on critical update errors
- Safe DOM manipulation with element checks

#### Cross-Platform
- Works on Chrome, Firefox, Safari, Edge
- Mobile responsive (iOS, Android)
- Gamepad support ready
- Keyboard/Mouse/Touch unified

### Development Patterns

#### Entity Component Pattern
```javascript
// Entities have components
entity = {
  // Core components
  x, y,          // Position
  vx, vy,        // Velocity
  r,             // Collision
  hp,            // Health
  
  // Behavioral components
  behavior,      // AI type
  effects,       // Active modifiers
  
  // Render components
  color,         // Visual
  alive          // State
}
```

#### State Machine Pattern
- Clear state transitions
- Predictable behavior
- Easy to debug
- Extensible design

#### Observer Pattern
- Event-driven UI updates
- Decoupled systems
- Clean architecture

### Performance Metrics

#### Target Performance
- 60 FPS on modern hardware
- 30 FPS minimum on mobile  
- <16.67ms frame time target
- <100MB memory usage
- Adaptive quality (0.3-1.0 performanceLevel)

#### FPS Monitoring
- 20-sample rolling average
- Real-time display (bottom-right)
- Error handling for calculation failures

#### Optimization Results
- 200+ enemies without lag
- 500+ particles simultaneous
- Instant response time
- Smooth on 5-year-old devices

---

## Additional Systems

### Mine System
- **Arming Delay**: 0.5 seconds before activation
- **Trigger Radius**: 35 pixels (player proximity)
- **Explosion Radius**: 70 pixels (doubled from trigger)
- **Explosion Delay**: 1.5 seconds after trigger
- **Visual Warning**: Accelerating flash when triggered
- **Damage Scaling**: 15 + (wave * 2) damage
- **Mine Limit**: 8 per minelayer enemy
- **Drop Interval**: Fixed 12 seconds between drops

### Enemy Bullet System
- **Base Speed**: 200 + wave (capped at 350)
- **Damage**: 8 + floor(wave/5)
- **Patterns**:
  - Single shot: Direct to player
  - Spread: 3 bullets, 60° arc
  - Burst: 3 rapid shots, 0.15s interval
  - Spiral: Continuous rotation at 3 rad/s

### Blood & Gore System
- **Blood Particles**: Gravity-affected, 3 color variants
- **Blood Stains**: 15-second persistence, settle physics
- **Death Sprays**: 15-25 droplets in burst pattern
- **Stain States**: Moving → Settled (different rendering)
- **Fade Timeline**: Full opacity for 3s, then 12s fade

## Game Balance

### Difficulty Curve

#### Enemy Scaling Formula
```javascript
difficultyMultiplier = 1 + wave * 0.12
// Wave 1: 1.12x
// Wave 10: 2.2x
// Wave 50: 7.0x
// Wave 100: 13.0x
```

#### Player Power Growth
- ~5 upgrades per 100 kills
- ~20% power increase per upgrade
- Exponential growth potential
- Skill ceiling emphasis

### Combat Balance

#### Time-to-Kill
- Basic enemy: 1-2 shots
- Tank: 3-5 shots
- Mini-boss: 10-15 shots
- Super boss: 30-50 shots

#### Survivability
- Player HP: 100 base
- Enemy damage: 9-15 per hit
- Healing: Rare but impactful
- Death in 7-11 hits

### Crystal Economy

#### Scarcity Design
- 3% drop rate maintains tension
- Temporary effects create decisions
- Rare crystals feel special
- Resource management gameplay

#### Power Spikes
- Homing: Game-changer (ultra-rare)
- Explosive: Crowd control
- Lightning: Chain clearing
- Multi-shot: Raw DPS

---

## Future Expansion Possibilities

### Potential Features
1. **Weapon Classes**: Different base weapons
2. **Character Classes**: Unique abilities
3. **Achievements**: Persistent progress
4. **Leaderboards**: Competition
5. **Co-op Mode**: Multiplayer support
6. **Level Editor**: Custom waves
7. **Boss Varieties**: Unique boss types
8. **Environmental Hazards**: Dynamic arenas

### Technical Improvements
1. **WebGL Rendering**: Better performance
2. **Service Worker**: Offline play
3. **Save System**: LocalStorage progress
4. **Mod Support**: Plugin architecture
5. **Analytics**: Player behavior tracking
6. **Accessibility**: Screen reader support

---

## Conclusion

Crystal Blitz demonstrates that a complete, polished game can be delivered in a single HTML file without sacrificing gameplay depth or technical quality. The architecture prioritizes performance, maintainability, and player experience while keeping the codebase accessible and modification-friendly.

The game successfully combines:
- **Technical Excellence**: Optimized rendering, efficient algorithms
- **Gameplay Depth**: Multiple systems interacting
- **Visual Polish**: Smooth animations, particle effects
- **Audio Feedback**: Procedural sound design
- **Progressive Difficulty**: Scaling challenge
- **Replayability**: Random elements, variety

This documentation serves as a complete reference for understanding, modifying, or learning from the Crystal Blitz codebase.

---

*Game Version: 0.99*
*File Size: 347KB*
*Lines of Code: 9,280*
*Documentation Date: January 2025*
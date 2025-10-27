# Changelog

All notable changes to Crystal Blitz will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [0.99.0] - 2025-01-27

### Fixed
- Fixed pause menu tab highlighting
- Fixed tab button sizing inconsistency
- Improved game over screen layout
- Enhanced restart button visibility

### Added
- ESC key support for pause menu
- Improved tab navigation in pause menu

### Changed
- Polished UI elements for better clarity
- Updated documentation for current feature set

## [0.95.0] - 2025-01-20

### Added
- Crystal visual overhaul with unique shapes for each type
  - 8-pointed star for Homing crystals with golden aura
  - Lightning bolt shape for Lightning crystals
  - Snowflake for Freeze crystals
  - Hexagon for Explosive crystals
  - Triangle for Ricochet crystals
  - Arrow for Seeking crystals
  - Pentagon for Shotgun crystals
  - Square for Cluster crystals
  - Diamond shapes for Multi-shot upgrades
- Footstep tracking system
  - Bipedal left/right foot alternation
  - Realistic fading (3.6s visible, 2.4s fade)
  - Object pooling for performance
- Glassmorphism UI effects
  - Modern blur effects on panels
  - Enhanced visual depth
  - Smooth animations
- Hexagonal floor pattern system
  - Dynamic gradient-based rendering
  - 60px hexagonal grid
  - Cached to off-screen canvas

### Changed
- Reorganized pause menu with tabs
  - Controls tab
  - Enemies tab (behavior descriptions)
  - Crystals tab (effect explanations)
  - Upgrades tab (permanent buff list)
- Enhanced blood effect system
  - Improved particle physics
  - Better settlement mechanics
  - Gradual fading (15s total lifetime)

## [0.90.0] - 2025-01-10

### Added
- 12+ enemy AI behavior types
  - Normal, Zigzag, Flank, Charge, Erratic
  - Suicide, Slowpush (with shields), Spiralshooter
  - Splitter, Minelayer, Boss, Superboss
- Progressive behavior unlock system
- Boss waves every 10 waves with multi-phase combat
- Mine system for Minelayer enemies
- Enemy bullet patterns (single, spread, burst, spiral)

### Changed
- Improved wave scaling formula (15→90 enemies)
- Enhanced difficulty progression
- Refined enemy spawn timing

## [0.80.0] - 2024-12-15

### Added
- 11 crystal powerup types
  - Homing (ultra-rare, 25 shots)
  - Explosive, Lightning, Freeze, Ricochet (50 shots each)
  - Seeking, Cluster, Shotgun (50 shots each)
  - Dual, Triple, Quad Shot patterns
- Crystal drop system with rarity tiers
- Crystal magnetic attraction upgrade
- Lucky upgrade (+20% drop rate per stack)

### Changed
- Rebalanced crystal shot durations
- Improved crystal visual feedback
- Enhanced pickup physics with bounce effect

## [0.70.0] - 2024-12-01

### Added
- 17 permanent upgrade system
  - Movement: Speed Boost, Stamina Boost, Dash Cooldown
  - Defense: Shield, Knockback Resistance, Max Health, Health Regen
  - Combat: Rapid Fire, Bullet Size, Bullet Speed, Piercing Shot, Critical Strike
  - Utility: Magnetic Crystals, Lucky, Vampire, Adrenaline, Efficient
- Level-up system with 3 random choices
- Upgrade stacking mechanics
- Visual upgrade indicators in pause menu

### Changed
- Rebalanced upgrade power levels
- Improved upgrade selection UI

## [0.60.0] - 2024-11-15

### Added
- Core game loop with fixed timestep (1/60s)
- Object pooling system for all entities
- Spatial grid collision detection (O(n) performance)
- Procedural audio system (Web Audio API)
- Player controls (WASD + mouse, touch support)
- Stamina system with sprint and dash mechanics
- Emergency leap ability (Space key, 3s cooldown)

### Changed
- Optimized rendering pipeline
- Implemented gradient caching with LRU eviction
- Added canvas state caching

### Performance
- Achieved 60 FPS target with 200+ entities
- Zero garbage collection in game loop
- Sub-16ms frame times

## [0.50.0] - 2024-11-01

### Added
- Initial game prototype
- Basic player movement and shooting
- Simple enemy AI
- Wave system foundation
- Health and stamina bars
- Basic particle effects

### Changed
- Established single-file architecture
- Set up canvas rendering pipeline
- Implemented basic collision detection

---

## Version Naming Convention

- **Major** (X.0.0): Complete game overhauls, breaking changes
- **Minor** (0.X.0): New features, significant additions
- **Patch** (0.0.X): Bug fixes, minor improvements, polish

---

## Planned Features (Roadmap)

### [1.0.0] - Stable Release (Target: Q1 2025)
- Comprehensive testing phase
- Performance optimization pass
- Accessibility improvements
- Mobile UX enhancements
- Final polish and bug fixes

### Future Considerations
- Save system with LocalStorage
- Achievement system
- Leaderboard support
- Additional boss varieties
- Weapon class system
- Character classes with unique abilities
- Co-op multiplayer mode
- Level editor

---

**For complete technical details, see [CRYSTAL_BLITZ_DOCUMENTATION.md](CRYSTAL_BLITZ_DOCUMENTATION.md)**

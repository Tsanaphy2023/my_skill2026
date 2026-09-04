---
name: interactive-3d-lab-builder
description: >-
  Upgrades 2D HTML Canvas physics experiments into hyper-realistic 3D Virtual Labs using Three.js and A-Frame PBR shaders. Integrates Web Audio live acoustic synthesizers, MediaPipe AR hand tracking, and live multi-channel oscilloscopes.
---

# Interactive 3D Lab Builder (Hyper-Realistic Edition)

## Overview
This skill guides the agent through upgrading standard 2D physics simulations into fully immersive, hyper-realistic 3D Virtual Labs. It uses Three.js / A-Frame with Physical Based Rendering (PBR) shaders, realistic lighting, shadows, and interactive instrumentation while maintaining accurate physics calculations and zero-GC performance.

## Core Pillars of Hyper-Realistic 3D Labs
1. **PBR Materials**: Use `MeshStandardMaterial` / `MeshPhysicalMaterial` with realistic `metalness`, `roughness`, and `emissive` properties (e.g., brushed steel, optical glass, polished brass, solar arrays).
2. **Dynamic Lighting & Soft Shadows**: Directional key light with `cast-shadow="true"`, subtle ambient fill light, and point lights for lasers/LED indicators.
3. **Web Audio Real-time Synthesizer**: Synthesize acoustic feedback for clicks, motor hums, laser beams, collision impacts, and resonance tones.
4. **Live Multi-channel Oscilloscopes**: Render real-time waveforms (voltage, displacement, velocity, Fourier spectrum) on floating 2D Canvas overlays.
5. **AR MediaPipe 3D Hand Tracking**: Seamlessly integrates with the `ar-simulation-builder` skill for 21-joint skeleton tracking and pinch manipulation.
6. **Zero-Collision 3D Spatial Layout**: Enforce `.left-panel-stack` flex container for 2D UI overlay, `wrap-count="45-50"` on all `<a-text>`, and separate $Z$-axis depth layers ($Z = 0.05$ for data switches, $Z = 0.52$ for action buttons) to completely prevent visual occlusion.


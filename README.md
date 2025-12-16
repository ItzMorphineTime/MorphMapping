# MorphMapping - Projection Studio

<div align="center">

![Version](https://img.shields.io/badge/version-2.8-blue)
![License](https://img.shields.io/badge/license-Apache%20License%202.0-blue)
![Three.js](https://img.shields.io/badge/Three.js-r128-orange)

**A professional-grade 3D projection mapping simulator and configurator**

[Features](#features) • [Getting Started](#getting-started) • [Controls](#controls) • [Documentation](#documentation)

</div>

---

## Overview

Projection Studio is a browser-based tool for designing, visualizing, and configuring projection mapping installations. It provides real-time simulation of projector coverage, overlap detection, luminance analysis, and shadow occlusion - all running entirely in your browser with no server required.

Perfect for:
- **AV Integrators** planning multi-projector installations
- **Event Designers** previewing projection mapping setups
- **Technical Directors** calculating coverage and overlap
- **Lighting Designers** simulating luminance distribution

## Features

### 🎯 Projector Simulation
- **Unlimited Projectors** - Multi-pass rendering system supports any number of projectors
- **Realistic Optics** - Accurate throw ratio, zoom, and lens shift simulation
- **5 Lens Types** - Rectilinear (standard) + 4 fisheye models:
  - Equidistant (f-theta)
  - Equisolid angle
  - Stereographic
  - Orthographic
- **Brown-Conrady Distortion** - K1, K2, K3 radial and P1, P2 tangential distortion
- **Brightness Controls** - Lumens, brightness %, and stacking multiplier
- **Custom Test Patterns** - Grid, crosshatch, gradient, color bars, focus, and custom images

### 📐 Surface Types
- **Flat Screens** - Standard projection surfaces
- **Curved Screens** - Cylindrical sections with adjustable curvature
- **Spheres** - Full spherical projection surfaces
- **Cubes/Boxes** - 3D box geometry with configurable dimensions
- **Custom OBJ** - Import any 3D model as a projection surface
- **Surface Gain** - Adjustable reflectivity per surface

### 🔍 Visualization Modes
- **Coverage Analysis** - Highlights uncovered areas in red
- **Overlap Detection** - Shows multi-projector overlap in orange (intensity varies with overlap count)
- **Luminance Heatmap** - Color-coded cd/m² display (blue→cyan→green→yellow→red)
- **Pilot Mode** - First-person view from projector's perspective

### 🌳 Hierarchy System
- **Parent-Child Relationships** - Attach projectors and surfaces to each other
- **Projector Arrays** - Create linear arrays with configurable count, spacing, and rotation offset
- **Batch Operations** - Convert arrays to individual projectors for fine-tuning
- **World-Space Calculations** - All transforms respect hierarchy chains

### 💾 Import/Export
- **JSON Project Files** - Save and load complete project configurations
- **Disguise CSV Export** - Export projector data compatible with Disguise media servers
- **World-Space Coordinates** - CSV exports use absolute world positions for direct import

### ⚡ Real-Time Shadow Occlusion
- **Per-Projector Shadow Maps** - Accurate occlusion from scene geometry
- **Array Instance Shadows** - Each array instance has its own shadow calculation
- **Linear Depth Encoding** - High-precision depth buffer for distant projections

## Getting Started

### Quick Start
1. Goto https://itzmorphinetime.github.io/MorphMapping/
3. That's it! No installation or server required.

### Creating Your First Setup
1. **Add a Surface** - Click "Add Surface" in the Surfaces panel
2. **Add a Projector** - Click "Add Projector" in the Projectors panel
3. **Position Objects** - Use the transform gizmos or enter coordinates directly
4. **Adjust Optics** - Configure throw ratio, zoom, and lens type
5. **Analyze** - Toggle Coverage, Overlap, or Heatmap modes

## Controls

### Mouse Controls
| Action | Control |
|--------|---------|
| Orbit Camera | Left-click + drag (empty space) |
| Pan Camera | Middle-click + drag or Shift + Left-click |
| Zoom | Scroll wheel |
| Select Object | Left-click on projector/surface |
| Transform | Left-click + drag on gizmo axis |

### Keyboard Shortcuts
| Key | Action |
|-----|--------|
| `G` | Translate mode |
| `R` | Rotate mode |
| `Esc` | Select mode (cancel transform) |
| `Delete` | Delete selected object |
| `Ctrl+Z` | Undo |
| `Ctrl+D` | Toggle debug lens type mode |

### Camera Movement (WASD)
| Key | Action |
|-----|--------|
| `W/S` | Move forward/backward |
| `A/D` | Strafe left/right |
| `Q/E` | Move down/up |

### Pilot Mode
Enable "Pilot Mode" checkbox to control the selected projector's position using WASD keys - useful for fine-tuning projector placement from its own perspective.

## Technical Specifications

### Rendering Pipeline
- **Multi-Pass System** - 8 projectors per pass with additive blending
- **Accumulation Buffer** - Float texture for accurate hit count and luminance tracking
- **Composite Pass** - Final visualization overlay respects surface geometry

### Supported Browsers
- Chrome 80+
- Firefox 75+
- Safari 14+
- Edge 80+

### Performance Tips
- Shadow map rendering scales with projector count
- Use projector arrays for repeated configurations
- Disable visualization modes when not needed for faster preview

## Contributing

Contributions are welcome! Please feel free to submit issues and pull requests.


## Acknowledgments

- Built with [Three.js](https://threejs.org/)
- Inspired by professional projection mapping tools like Disguise, Resolume, and d3

---

<div align="center">
Made with ❤️ for the projection mapping community
</div>

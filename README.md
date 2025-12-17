# MorphMapping - Projection Studio

<div align="center">

![Version](https://img.shields.io/badge/version-4.2-blue)
![License](https://img.shields.io/badge/license-Apache%202.0-green)
![Three.js](https://img.shields.io/badge/Three.js-r128-orange)

**A professional-grade 3D projection mapping simulator and configurator**

[Features](#features) • [Getting Started](#getting-started) • [Controls](#controls) • [Documentation](#documentation)

</div>

---

## Overview

Projection Studio is a browser-based tool for designing, visualizing, and configuring projection mapping installations. It provides real-time simulation of projector coverage, overlap detection, luminance analysis, and shadow occlusion — all running entirely in your browser with no server required.

Perfect for:
- **AV Integrators** planning multi-projector installations
- **Event Designers** previewing projection mapping setups
- **Technical Directors** calculating coverage and overlap
- **Lighting Designers** simulating luminance distribution

## Features

### 🎯 Projector Simulation
- **Unlimited Projectors** — Multi-pass rendering system supports any number of projectors
- **Realistic Optics** — Accurate throw ratio, zoom, lens shift, and aspect ratio simulation
- **5 Lens Types**:
  - Rectilinear (standard)
  - Fisheye Equidistant (f-theta)
  - Fisheye Equisolid Angle
  - Fisheye Stereographic
  - Fisheye Orthographic
- **Brown-Conrady Distortion** — K1, K2, K3 radial and P1, P2 tangential distortion coefficients
- **Brightness Controls** — Lumens, brightness percentage, and projector stacking multiplier
- **Test Patterns** — Grid, crosshatch, gradient, color bars, focus pattern, white, and custom image upload

### 📐 Surface Types
- **Flat Screens** — Standard rectangular projection surfaces
- **Curved Screens** — Cylindrical sections with adjustable curvature angle
- **Spheres** — Full spherical projection surfaces with configurable radius
- **Cubes/Boxes** — 3D box geometry with independent width, height, and depth
- **Custom OBJ** — Import any 3D model as a projection surface
- **Surface Gain** — Adjustable reflectivity per surface

### 🔍 Visualization Modes
- **Coverage Analysis** — Highlights uncovered surface areas in red
- **Overlap Detection** — Shows multi-projector overlap in orange (intensity increases with overlap count)
- **Luminance Heatmap** — Color-coded cd/m² display with adjustable maximum value
- **Pilot Mode** — First-person camera control from selected projector's perspective

### 🌳 Hierarchy System
- **Parent-Child Relationships** — Attach projectors and surfaces to each other for grouped transforms
- **Projector Arrays** — Create linear arrays with configurable:
  - Instance count
  - Spacing between units
  - Per-instance rotation offset
- **Convert to Projectors** — Expand arrays into individual projectors for fine-tuning

### 💾 Import/Export
- **JSON Project Files** — Save and load complete project configurations
- **Disguise CSV Export** — Export projector data compatible with Disguise media servers
- **World-Space Coordinates** — CSV exports use absolute world positions

### ⚡ Real-Time Shadow Occlusion
- **Per-Instance Shadow Maps** — Each projector (including array instances) has independent shadow calculation
- **Linear Depth Encoding** — High-precision depth buffer for accurate occlusion at any distance
- **Automatic Updates** — Shadow maps refresh when projectors or surfaces move

## Getting Started

### Quick Start
1. Goto https://itzmorphinetime.github.io/MorphMapping/
2. That's it — no installation or server required

### Creating Your First Setup
1. **Add a Surface** — Click "Add Surface" in the Surfaces panel
2. **Add a Projector** — Click "Add Projector" in the Projectors panel
3. **Position Objects** — Use the transform gizmos or enter coordinates in the Properties panel
4. **Adjust Optics** — Configure throw ratio, zoom, lens shift, and lens type
5. **Analyze** — Toggle Coverage, Overlap, or Heatmap modes in the Display panel

## Controls

### Mouse Controls
| Action | Control |
|--------|---------|
| Orbit Camera | Left-click + drag on empty space |
| Pan Camera | Middle-click + drag |
| Zoom | Scroll wheel |
| Select Object | Left-click on projector or surface |
| Transform | Left-click + drag on gizmo axis |

### Keyboard Shortcuts
| Key | Action |
|-----|--------|
| `G` | Translate mode (move) |
| `R` | Rotate mode |
| `V` | Select mode |
| `Escape` | Cancel transform / Deselect |
| `Delete` | Delete selected object |
| `Ctrl+Z` | Undo |
| `Ctrl+D` | Toggle debug lens type visualization |

### Camera Movement (WASD)
| Key | Action |
|-----|--------|
| `W` / `S` | Move forward / backward |
| `A` / `D` | Strafe left / right |
| `Q` / `E` | Move down / up |

### Pilot Mode
Enable the "Pilot Mode" checkbox when a projector is selected to control the projector's position using WASD keys instead of the camera — useful for fine-tuning placement from the projector's point of view.

### Transform Space
Click the **Local/World** button in the toolbar to toggle between:
- **World Space** — Axes aligned to global XYZ
- **Local Space** — Axes aligned to object's orientation

## Technical Specifications

### Rendering Pipeline
The application uses a sophisticated multi-pass rendering system:

1. **Shadow Pass** — Renders depth maps from each projector's viewpoint
2. **Projection Pass** — 8 projectors per pass with texture-based projection
3. **Accumulation Pass** — Float texture tracking hit count and luminance (for 9+ projectors)
4. **Composite Pass** — Applies visualization overlays to surfaces only
5. **Overlay Pass** — Renders gizmos and helpers with proper depth occlusion

### Supported Browsers
- Chrome 80+
- Firefox 75+
- Safari 14+
- Edge 80+

WebGL 2.0 support required for float textures.

### Performance Considerations
- Shadow map rendering scales linearly with projector count
- Use projector arrays for repeated configurations when possible
- Visualization modes add rendering overhead — disable when not needed
- Large OBJ imports may impact performance

## Contributing

Contributions are welcome! Please feel free to submit issues and pull requests.

## License

This project is licensed under the Apache License 2.0 — see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- Built with [Three.js](https://threejs.org/)
- Inspired by professional projection mapping tools

---

<div align="center">
Made with ❤️ for the projection mapping community
</div>

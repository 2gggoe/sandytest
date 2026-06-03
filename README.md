# 🏜️ WebGL Sand Simulation

Real-time 3D sand physics simulation inspired by [Evan Wallace's WebGL Water](https://madebyevan.com/webgl-water/).  
GPU-based height-field simulation — 60 FPS.

**[▶ Live Demo](https://YOUR_USERNAME.github.io/sand-webgl)**

---

## Features

- **GPU height-field physics** — wave propagation shaders, high sand damping
- **Interactive sphere** — drag the ball into the sand, watch it displace grains
- **Mouse disturbance** — click & drag on the sand surface directly
- **Wind** — Perlin noise drift over the dune surface
- **Rain** — random sand disturbances from above
- **Skybox** — cube-mapped environment
- **Shadow map** — sphere casts shadows on sand
- **Sand material shaders** — procedural grain noise, warm tones, specular sheen

## Controls

| Input | Action |
|-------|--------|
| Left click + drag on sand | Disturb the surface |
| Left click + drag on sphere | Move the sphere |
| Right click + drag | Rotate camera |
| Scroll wheel | Zoom |
| Touch drag | Mobile interaction |

## Deploy to GitHub Pages

```bash
git init
git add .
git commit -m "WebGL sand sim"
git remote add origin https://github.com/YOUR_USERNAME/sand-webgl.git
git push -u origin main
```

Then: **Settings → Pages → Source: main / (root)**

## Requirements

Browser must support:
- `OES_texture_float` — for GPU float simulation textures
- `OES_texture_float_linear` — smooth sampling
- `WEBGL_depth_texture` — shadow map

Chrome / Firefox on desktop GPU recommended.

## Architecture

| Pass | Description |
|------|-------------|
| Height shader | Updates height map from mouse/sphere interaction |
| Normal shader | Recomputes surface normals from height gradient |
| Simulate shader | Wave propagation with heavy sand damping |
| Sphere interaction | Displaces height by sphere volume |
| Wind (Perlin) | Slow drift using GPU Perlin noise |
| Pool shader | Sand-coloured dune walls with shadow |
| Sand surface shader | Procedural grain texture, Fresnel, specular |
| Depth (shadow map) | Renders sphere depth from light direction |

Based on the architecture from [dblsai/WebGL-Fluid](https://github.com/dblsai/WebGL-Fluid), adapted for sand physics.

## License

MIT

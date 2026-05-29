# Conservation Spectral SDK — WebGPU

A single-file WebGPU implementation of spectral graph theory for conservation analysis. **Zero dependencies. Zero build. Just open in Chrome.**

🌐 **Live demo:** Open [`index.html`](./index.html) directly in your browser.

## What It Does

Paste a transition probability matrix (JSON), click **Analyze**, and get:

- **Eigenvalues** — full eigenspectrum of the graph Laplacian
- **Fiedler vector** — spectral partition of the graph
- **Conservation ratios** — how well attributes are conserved along spectral modes
- **Spectral gap** — largest eigenvalue gap (connectivity measure)
- **Cheeger constant** — graph cut approximation
- **Spectral entropy & effective dimension** — fingerprint of the graph
- **Anomaly detection** — z-score based vertex anomalies
- **Canvas visualization** — graph colored by Fiedler partition

## Architecture

| Component | Technology |
|-----------|-----------|
| Laplacian construction | WGSL compute shader |
| Matrix-vector multiply (power iteration) | WGSL compute shader |
| Vector normalization | WGSL compute shader |
| Deflation (eigenpair removal) | WGSL compute shader |
| Conservation ratio computation | WGSL compute shader |
| Eigendecomposition (small matrices) | CPU Jacobi rotation (more accurate) |
| Anomaly detection | CPU z-score analysis |
| Graph rendering | Canvas 2D |

## Baked-In Test Data

5-node chord progression (C → Dm → Em → F → G) with transition probabilities. Auto-loaded on first visit.

## WebGPU Requirement

Requires Chrome 113+, Edge 113+, or another WebGPU-capable browser. A clear fallback message is shown if WebGPU is unavailable.

## Related

- [conservation-spectral-js](https://github.com/SuperInstance/conservation-spectral-js) — Full TypeScript SDK (source of the algorithms)

Part of the [SuperInstance OpenConstruct](https://github.com/SuperInstance/OpenConstruct) ecosystem.

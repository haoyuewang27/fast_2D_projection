![Vibe coded with Claude](https://img.shields.io/badge/vibe%20coded%20with-Claude-6ec6b8)
# fast_2D_projection
A website that can do real time theoretical EM 2D projections from an uploaded pdb or cif file. Run locally on your computer. Just download, double click and run in your own browser!

**No installation. No server. No build step.**

1. Download `Fast_2D_Projection_Visualization_v0.1.html`
2. Open it in any modern browser (Chrome, Safari, ...)
3. Drag and drop a `.pdb` or `.cif` / `.mmcif` file onto the window, or click **Load PDB**

**Load, drag, and view**
![6pxm_example](https://github.com/user-attachments/assets/9d3c4371-48e1-4945-bbb5-d40a083c9613)


**Hide and show chains and ligands**
![1bmt_example](https://github.com/user-attachments/assets/969c2d00-a66f-41ec-8ca5-bcf6d5a9ea68)


## Physics

**I haven't checked the physics myself yet, I will update the readme file when I am done checking.** I used ChatGPT to check Claude's work and it passed, so I haven't checked it myself yet.

The electron scattering factor of each atom is parameterized as a sum of 5 Gaussians using Peng 1999 tabulated coefficients:

```
f(s) = Σᵢ aᵢ exp(−bᵢ s²)
```

where `s = sinθ/λ` (Å⁻¹) is the scattering parameter, and `aᵢ` (Å) and `bᵢ` (Å²) are element-specific coefficients fit to electron diffraction data.

The 2D projected density per atom is obtained analytically from the 2D inverse Fourier transform of each Gaussian slice via the projection-slice theorem:

```
φᵢ(ρ) = (π aᵢ / b_eff,i) exp(−π²ρ² / b_eff,i)
```

where `ρ` is the 2D radial distance from the atom center and `b_eff,i = bᵢ + σ²` incorporates the user-controlled blur.

**Reference:** Peng L-M (1999) *Micron* 30:625–648, Table 1.

## Development

Built by vibe coding with Claude (Anthropic)

## License

MIT License

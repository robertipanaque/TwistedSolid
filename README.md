# TwistedSolid

A Mathematica package for constructing and visualizing nonorientable 
3-dimensional solids in four-dimensional Euclidean space ℝ⁴.

## Description

TwistedSolid provides two symbolic commands — `TwistedSolidCurve` and 
`TwistedSolidSurface` — for constructing and visualizing nonorientable 
3-dimensional solids immersed in four-dimensional Euclidean space ℝ⁴. 
The construction generalizes the classical Möbius strip and Klein bottle 
mechanisms to ℝ⁴ by applying a half-angle rotation to the Frenet frame 
normal plane along a curve or surface directrix.

The package generates eight canonical solids organized by fiber topology 
(square or figure-eight) and directrix type (curve or surface):

| Solid | Directrix | Fiber | Twist | Orientable | Min. embedding |
|---|---|---|---|---|---|
| 3-cylinder | curve | square | n=0 | yes | ℝ⁴ |
| 3-Möbius strip | curve | square | n=1 | no | ℝ⁴ |
| 3-eight torus | curve | figure-eight | n=0 | yes | ℝ⁴ |
| 3-Klein bottle | curve | figure-eight | n=1 | no | ℝ⁵ |
| Sph. 3-cylinder | surface | square | n=0 | yes | ℝ⁴ |
| Sph. 3-Möbius strip | surface | square | n=1 | no | ℝ⁴ |
| Sph. 3-eight torus | surface | figure-eight | n=0 | yes | ℝ⁴ |
| Sph. 3-Klein bottle | surface | figure-eight | n=1 | no | ℝ⁵ |

Six of these solids are smooth embeddings in ℝ⁴. The two 3-Klein 
bottles are immersions in ℝ⁴ whose self-intersection-free embeddings 
require ℝ⁵.

## Requirements

- Mathematica 12 or later
- The `4DSketches` package (Axes4D, SolidPlot, $P projection operator)

## Installation

1. Download `TwistedSolid.nb`
2. Open it in Mathematica
3. Evaluate all cells to load the functions

## Usage

### TwistedSolidCurve

```mathematica
TwistedSolidCurve[directrix, fiber, twistAngle, {u, v, w}]
```

**Parameters:**
- `directrix`: pure function `δ[u_] := {f1[u], f2[u], f3[u], f4[u]}`
- `fiber`: pure function `φ[v_, w_] := {g1[v,w], g2[v,w]}`
- `twistAngle`: `0` (orientable) or `1` (nonorientable)
- `{u, v, w}`: parameter variables

**Example — 3-Möbius strip:**
```mathematica
δ[u_] := 3 {Cos[u], Sin[u], 0, 0}
φ[v_, w_] := {v, w}
S = TwistedSolidCurve[δ, φ, 1, {u, v, w}]
Show[Graphics3D[Axes4D[{5, 4.5, 3.5, 3.5}]],
  SolidPlot[$P[S], {u, 0, 2π}, {v, -1, 1}, {w, -1, 1}]]
```

### TwistedSolidSurface

```mathematica
TwistedSolidSurface[directrix, fiber, twistAngle1, twistAngle2, {u, v, w}]
```

**Parameters:**
- `directrix`: pure function `σ[u_, v_] := {f1[u,v], f2[u,v], f3[u,v], f4[u,v]}`
- `fiber`: pure function `φ[w_] := {g1[w], g2[w]}`
- `twistAngle1`, `twistAngle2`: `0` (orientable) or `1` (nonorientable)
- `{u, v, w}`: parameter variables

**Example — Spherical 3-Möbius strip:**
```mathematica
σ[u_, v_] := 2 {Sin[v] Cos[u], Sin[v] Sin[u], Cos[v], 0}
φ[w_] := {0, w}
S = TwistedSolidSurface[σ, φ, 1, 1, {u, v, w}]
Show[Graphics3D[Axes4D[{4, 4, 4, 3}]],
  SolidPlot[$P[S], {u, 0, 2π}, {v, 0, π}, {w, -1, 1}]]
```

## Citation

If you use this package in your research, please cite:

> R. Ipanaqué-Chero, R. Velezmoro-León, S. B. Correa-Erazo,
> J. K. Jiménez-Vilcherrez, A. F. Navarro-Garrido.
> TwistedSolid: A Mathematica Package for Constructing and Visualizing
> Nonorientable 3-Dimensional Solids in Four-Dimensional Euclidean Space.
> *SoftwareX* (submitted), 2026.
> DOI: [10.5281/zenodo.20301250](https://doi.org/10.5281/zenodo.20301250)

## Authors

- **Robert Ipanaqué-Chero** — Universidad Nacional de Piura
  (ORCID: 0000-0002-3873-6780)
- Ricardo Velezmoro-León — Universidad Nacional de Piura
  (ORCID: 0000-0002-2582-8264)
- Segundo B. Correa-Erazo — Universidad Nacional de Piura
  (ORCID: 0000-0002-0147-2048)

## License

MIT License. See [LICENSE](LICENSE) for details.

## Acknowledgments

The authors gratefully acknowledge Mr. Roy Álvarez, Director of 
Strategic Development at Wolfram Research, Inc., for generously 
providing complimentary Mathematica licenses that made this work 
possible.

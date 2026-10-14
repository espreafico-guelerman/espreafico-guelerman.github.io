# Real Gopakumar–Vafa invariants of the quintic and the bicubic

Code and data for F. Espreafico, *Gauss–Manin Connection in Disguise: Holomorphic Anomaly Equations
and Higher Genus Real Gromov–Witten Invariants*.

## Files

| file | contents |
|---|---|
| `AlgebraicHAE_quintic.nb` | the computation for the real mirror quintic |
| `BPSc_quintic.wl` | complex GV invariants of the quintic (g ≤ 64, d ≤ 44), read by the quintic notebook |
| `AlgebraicHAE_bicubic.nb` | the same computation for the real mirror bicubic X(3,3) ⊂ ℙ⁵, with the periods at z = 0, the mirror map and τ |
| `BPSc_bicubic.wl` | complex GV invariants of the bicubic (g ≤ 33, d ≤ 66), read by the bicubic notebook |
| `RealGV_quintic.csv` | real GV invariants of the quintic, g ≤ 8: odd d ≤ 99 for even g, even d ≤ 88 for odd g |
| `RealGV_bicubic.csv` | real GV invariants of the bicubic: g ≤ 8 with d ≤ 40, and g = 9, …, 12 with d ≤ 30 |

## Running the notebooks

Use Mathematica 14 (tested with 14.3). Keep each notebook in the same folder as its `BPSc_*.wl` file and run
*Evaluation > Evaluate Notebook*.

Each notebook does the following, starting from the Picard–Fuchs equation:

1. It builds the moduli space S, the Gauss–Manin connection and the vector fields R₀, …, R₈.
2. It sets up the dictionary with special geometry.
3. It writes the algebraic anomaly equations and integrates them.
4. It computes the expansions of the coordinates s₀, …, s₈ at z = 0 and at the conifold.
5. It fixes the holomorphic ambiguity with the gap condition at the conifold, the constant map contribution and the vanishing of real invariants where the complex ones vanish.

- **The last cell** is an example: it gives n^ℝ_{g,d} for g ≤ 5 and d ≤ 40 in the quintic notebook (about 40 s), and for g ≤ 6 and d ≤ 10 in the bicubic one.
- **`RealGVUpTo[chiMax, dmax]`** gives n^ℝ_{g,d} for g ≤ chiMax + 1 and d ≤ dmax. The expansions at z = 0 allow d ≤ 2·`pr`, with `pr` = 60 in the quintic notebook and 20 in the bicubic one. For the quintic, even degrees also need the complex invariants up to degree d/2, which go to degree 44, so d ≤ 88. Past that, the even-degree entries come out containing the missing complex invariants: for example n^ℝ_{1,90} involves `BPSc[0, 45]` and `BPSc[1, 45]`. Odd degrees use no complex input.
- **One extra input.** At χ = 5 for the quintic and χ = 9 for the bicubic, the boundary conditions leave one coefficient free. The notebooks take n^ℝ_{6,5} or n^ℝ_{10,9} as input, set with `BPSr[6, 5] = 2` (or `-2`) and `BPSr[10, 9] = 3` (or `-3`). The paper explains these values.

The tables of the paper (d ≤ 30) are obtained with:

| | input | call | time (one core, Apple M-series) |
|---|---|---|---|
| quintic | `BPSr[6, 5] = 2` or `-2` | `RealGVUpTo[7, 30]` | about 10 min |
| bicubic | `BPSr[10, 9] = 3` or `-3` | `RealGVUpTo[11, 30]` | about 9 h, with about 7 GB of memory at χ = 11 |

## The tables

- **Columns.** The two columns correspond to the two values of n^ℝ_{6,5} (quintic) or n^ℝ_{10,9} (bicubic). They agree for g ≤ 5 (quintic) and g ≤ 9 (bicubic). For the bicubic, the entries with g ≥ 10 depend linearly on n^ℝ_{10,9}.
- **Recomputed entries.** The entries with d ≤ 30 were recomputed with these notebooks on 12–13 October 2026 and agree with the appendix of the paper.
- **Earlier entries.** The quintic entries with d > 30 and the bicubic entries with 30 < d ≤ 40 come from an earlier implementation of the same method, with longer expansions. They agree with the notebooks wherever both are available.
- **Checks.** Every entry is an integer. The tables list only the degrees with d + g odd; n^ℝ_{g,d} vanishes for the others. Wherever the complex invariants are available, n^ℝ_{g,d} ≡ n^ℂ_{g,d} mod 2.

## Complex invariants

Both come from A. Klemm's data page, http://www.th.physik.uni-bonn.de/groups/klemm/data.php:

- **Quintic:** genus 0–64, degree ≤ 44.
- **Bicubic:** file `X33BPS34`, genus 0–33, degree ≤ 66.

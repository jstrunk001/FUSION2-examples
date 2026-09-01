# FUSION2-examples

Example forestry lidar processing workflows and small sample datasets
demonstrating the [FUSION2](https://github.com/jstrunk001/FUSION2) toolset
-- a modernized C++ reimplementation of the USDA Forest Service FUSION/LTK
lidar processing suite (originally developed by Bob McGaughey, PNW Research
Station).

This is a companion repository to `FUSION2`, kept separate so example
lidar point clouds and forestry plot/stand datasets don't bloat the core
tool's source history.

## Objectives

1. Demonstrate FUSION2 command-line tools (`gridmetrics`, `clipdata`,
   `groundfilter`, `canopymodel`, `catalog`, `ltktools`) against real
   forestry lidar and inventory data.
2. Provide small, ready-to-run example datasets so a new user can validate
   a FUSION2 build without sourcing their own data first.

## Data

- `data/raw/` -- small example lidar tiles and a subset of Washington DNR
  RSFRIS plot data and SFIS stand data (public/example-safe, no true
  confidential coordinates -- see `data/confidential/` below).
- `data/confidential/` -- reserved for any true/exact plot coordinates,
  should they ever be needed; gitignored and blocked at commit time by
  `.git/hooks/pre-commit`. Not expected to be used in this repo.

## Project layout

See `R/analysis/` for example processing workflows (Quarto `.qmd`
scripts), `docs/` for rendered reports, and `publications/` for any
supporting literature.

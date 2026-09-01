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

- `data/raw/lidar/` -- one small (roughly 1 MB) example lidar tile: a
  200 x 200 ft clip of a public USGS 3DEP point cloud, project
  `WA_6County_A24`, tile `w2049750n409500`. See
  `R/analysis/001_example_gridmetrics_lidar_pipeline.qmd` for the full
  source URL, acquisition date, and the format conversion applied.
- `data/raw/dnr/` -- a small (15-plot) example subset of two Washington
  DNR forest inventory programs, RSFRIS and SFIS, covering only the
  plot-level and tree-level attribute tables (no coordinate columns). See
  `R/analysis/002_example_rsfris_sfis_join.qmd` Step 1 for the screening
  that confirmed this, and for the two source tables (a plot-metadata
  table and a sample-point shapefile, both carrying exact coordinates)
  that were deliberately excluded and are not committed anywhere in this
  repo.
- `data/confidential/` -- reserved for any true/exact plot coordinates,
  should they ever be needed; gitignored and blocked at commit time by
  `.git/hooks/pre-commit`. Not expected to be used in this repo.

## Project layout

See `R/analysis/` for example processing workflows (Quarto `.qmd`
scripts), `docs/` for rendered reports, and `publications/` for any
supporting literature.

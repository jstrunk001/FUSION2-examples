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

1. Demonstrate FUSION2 command-line tools against real forestry lidar and
   inventory data. `R/analysis/005_example_all_tools.qmd` runs all 15
   tools on the example lidar tile and checks every output against an
   independent calculation in R, writing a pass/warn/fail log to
   `output/tables/all_tools_check_log.csv/`.
2. Provide small, ready-to-run example datasets so a new user can validate
   a FUSION2 build without sourcing their own data first.

## Data

- `data/raw/lidar/` -- the example lidar tiles:
  - `TC_1372_forest200ft.laz` (roughly 0.5 MB): a 200 x 200 ft window of
    closed-canopy forest (92% canopy cover, 95th-percentile height
    142 ft, 70,532 points) from lidar tile `TC_1372` (NV5 Geospatial,
    2022; NAD83(HARN) / Washington South ftUS), kept in its native LAS 1.4
    point format 6 LAZ encoding. Used by scripts 001, 003, 004, and 005.
    `R/analysis/006_prepare_forested_example_tile.qmd` shows how the
    window was chosen from the full tile.
  - `USGS_LPC_WA_6County_A24_w2049750n409500_clip200ft_las12.las`
    (roughly 1 MB): a 200 x 200 ft clip of a public USGS 3DEP point
    cloud (project `WA_6County_A24`) over open, low-vegetation ground,
    re-encoded as LAS 1.2 point format 0. No script uses it now; it is
    kept as a small open-ground, LAS 1.2 counterpart to the forest tile.
- `data/raw/dnr/` -- a small (15-plot) example subset of two Washington
  DNR forest inventory programs, RSFRIS and SFIS, covering only the
  plot-level and tree-level attribute tables (no coordinate columns). See
  `R/analysis/002_example_rsfris_sfis_join.qmd` Step 1 for the screening
  that confirmed this, and for the two source tables (a plot-metadata
  table and a sample-point shapefile, both carrying exact coordinates)
  that were deliberately excluded and are not committed anywhere in this
  repo.
- `data/raw/lidar_dtm_examples/` -- seven small (roughly 1 MB each) real
  USGS 3DEP bare-earth lidar DTMs, one per Washington forest-type study
  site (subalpine Cascades, dry east-side, west-side plantation,
  old-growth rainforest, and three others), pulled from the
  `2026_Compare_DSMs` analysis project's cached real (not synthetic)
  lidar reference rasters. Used by
  `R/analysis/004_advanced_pipeline_orchestration.qmd` Step 7 to exercise
  `pipeline.exe` against an independently-sourced external DTM instead of
  a point cloud.
- `data/raw/dsm_source_examples/site_grays_harbor/` -- one small example
  raster per non-lidar canopy-height source compared in
  `2026_Compare_DSMs` (Meta AI CHM, WA State NAIP3D photogrammetric DSM,
  NAIP-CHM/NTSG neural-net CHM), for the same site as one of the lidar
  DTM examples above. Staged for future multi-source example scripts;
  not currently used by any script in this repo, since `pipeline.exe`
  only accepts lidar point-cloud/DTM input today.
- `data/confidential/` -- reserved for any true/exact plot coordinates,
  should they ever be needed; gitignored and blocked at commit time by
  `.git/hooks/pre-commit`. Not expected to be used in this repo.

## Project layout

See `R/analysis/` for example processing workflows (Quarto `.qmd`
scripts), `docs/` for rendered reports, and `publications/` for any
supporting literature.

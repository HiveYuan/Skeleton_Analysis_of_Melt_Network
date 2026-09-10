# Skeleton-Based Analysis of Melt Networks

This repository archives my CSE master's research project at Washington University in St. Louis. The project was conducted under the supervision of Professor Tao Ju in collaboration with Professor Philip Skemer, whose laboratory provided the three-dimensional microtomography data.

## Research question

The project studies how to estimate the coordination-number distribution of a three-dimensional melt network without manually labeling every junction. A coordination number is the number of melt tubules incident to a junction, and its distribution provides a compact description of network topology.

The pipeline:

1. preprocesses the binary melt volume;
2. extracts a skeleton using Voxel Cores and Erosion Thickness;
3. filters high-degree vertices inside ambiguous thick or sheet-like regions;
4. merges nearby junction candidates using geometric and angular consistency; and
5. computes coordination numbers from the resulting graph.

## Technical report

- [Read the revised technical report](technical_report/Yuan_Liu_SBAMN_Master_Research_Technical_Report.pdf)
- [View the LaTeX source](technical_report/report.tex)

The project was completed in December 2022. The report was revised in September 2026 for clarity and archival presentation. It is a master's research technical report, not a peer-reviewed publication; the revision preserves the original method and results while stating the evaluation limitations more explicitly.

## Repository contents

- `skeleton_analysis.nb`: core Mathematica implementation and experiments for junction extraction, merging, and coordination-number analysis.
- `melt_network.nb`: melt-network visualization and inspection notebook.
- `draft.nb`: development notebook containing exploratory experiments.
- `data/`: the archived Scoba 12 data and intermediate project material.
- `technical_report/`: revised PDF, LaTeX source, bibliography, and figures.

## Results and limitations

On a manually labeled `112 × 118 × 142` subvolume, the method obtained a histogram sum-of-squared error of `0.03137`. The available historical comparison came from an unidentified, spatially unmatched `250³` subvolume, so it is included only as context and is not a controlled accuracy baseline.

The main observed errors were an overcount of three-way junctions and an undercount of four-way junctions. The report traces these errors to short skeleton branches, crop-boundary artifacts, and all-or-nothing removal of sheet-like regions.

## Building the report

From `technical_report/`, compile with a modern LaTeX engine such as Tectonic:

```bash
tectonic report.tex
```

The report source cites the underlying geometry-processing and geoscience literature in `references.bib`.

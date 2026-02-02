# stellarCatalog

An extended star catalog based on the [AT-HYG dataset](https://www.astronexus.com/projects/at-hyg) from Astronexus.

## Overview

This repository contains star catalog data files that are a **superset of the AT-HYG dataset**. The original AT-HYG catalog merges data from Hipparcos, Yale Bright Star, and Gliese catalogs with modern astrometric data.

## Extensions to the Original Dataset

This catalog extends the original AT-HYG data with the following enhancements:

- **Distance values**: Filled in missing distance values for approximately 60,000 entries (out of ~2.5 million in the full catalog)
- **Physical parameters**: Added mass, luminosity, and other stellar parameters by cross-referencing with Gaia DR3 data

## Data Files

The `at-hyg/` directory contains CSV files organized by distance from Earth:

| File | Distance Range |
|------|----------------|
| AT-HYG-10ly.trips.csv | Stars within 10 light-years |
| AT-HYG-20ly.trips.csv | Stars within 20 light-years |
| AT-HYG-30ly.trips.csv | Stars within 30 light-years |
| AT-HYG-50ly.trips.csv | Stars within 50 light-years |
| AT-HYG-100ly.trips.csv | Stars within 100 light-years |
| AT-HYG-150ly.trips.csv | Stars within 150 light-years |
| AT-HYG-200ly.trips.csv | Stars within 200 light-years |

## Usage

This repository uses **Git LFS** for the CSV files. After cloning:

```bash
git lfs install
git lfs pull
```

## License

Apache 2.0 - See [LICENSE](LICENSE) for details.

## Attribution

- Original AT-HYG dataset: [Astronexus](https://www.astronexus.com/projects/at-hyg)
- Gaia DR3 data: [ESA Gaia Archive](https://gea.esac.esa.int/archive/)

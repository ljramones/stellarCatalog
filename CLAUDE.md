# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a **data repository** containing star catalog CSV files for the TRIPS application (`com.teamgannon.trips`). The data is derived from the HYG-MERGED-2m catalog (Hipparcos-Yale-Gliese merged with Gaia DR2/DR3 data) and includes photometric mass/temperature estimates.

The CSV schema corresponds to the `StarObject` JPA entity used by the TRIPS Java application.

## Repository Structure

```
stellarCatalog/
├── at-hyg/                      # Star catalog data directory
│   ├── AT-HYG-{range}ly.trips.csv  # Star data within {range} light-years of Earth
│   └── .gitattributes           # Git LFS configuration for CSV files
├── LICENSE                      # Apache 2.0
└── README.md
```

Data files follow the naming pattern `AT-HYG-{range}ly.trips.csv` where range is: 10, 20, 30, 50, 100, 150, or 200 light-years.

## Git LFS Requirement

**Important**: This repository uses Git LFS to manage large CSV files. You must have Git LFS installed:

```bash
git lfs install
git lfs pull
```

## Data Schema

The CSV schema maps to the `StarObject` entity. Coordinates are heliocentric in J2000 epoch.

### Identity Fields
| Field | Type | Description |
|-------|------|-------------|
| id | String | UUID primary key |
| dataSetName | String | Dataset identifier |
| displayName | String | Display name for the star |
| commonName | String | Common/popular name |
| systemName | String | Star system name |
| constellationName | String | Constellation membership |
| epoch | String | Coordinate epoch (J2000 or J2016) |
| gaiaUpdated | boolean | Whether updated from Gaia data |
| gaiaUpdatedDate | String | Date of Gaia update |

### Catalog Identifiers
| Field | Type | Description |
|-------|------|-------------|
| simbadId | String | SIMBAD database ID |
| hipCatId | String | Hipparcos catalog ID |
| hdCatId | String | Henry Draper catalog ID |
| glieseCatId | String | Gliese catalog ID |
| tycho2CatId | String | Tycho-2 catalog ID |
| gaiaDR2CatId | String | Gaia Data Release 2 ID |
| gaiaDR3CatId | String | Gaia Data Release 3 ID |
| gaiaEDR3CatId | String | Gaia Early DR3 ID |
| twoMassCatId | String | 2MASS catalog ID |
| csiCatId | String | CSI catalog ID |
| bayerCatId | String | Bayer designation |
| flamsteedCatId | String | Flamsteed designation |
| catalogIdList | String | Pipe-delimited list of additional catalog IDs |

### Physical Properties
| Field | Type | Description |
|-------|------|-------------|
| mass | double | Stellar mass in solar masses |
| radius | double | Stellar radius in solar radii |
| temperature | double | Surface temperature in Kelvin |
| age | double | Estimated age |
| metallicity | double | Metallicity value |
| spectralClass | String | Full spectral classification from SIMBAD |
| orthoSpectralClass | String | Single-character spectral class (O/B/A/F/G/K/M) |
| luminosity | String | Luminosity class |
| apparentMagnitude | String | Apparent magnitude |
| absoluteMagnitude | String | Absolute magnitude |

### Position & Coordinates
| Field | Type | Description |
|-------|------|-------------|
| x | double | X position in light-years (heliocentric, J2000) |
| y | double | Y position in light-years |
| z | double | Z position in light-years |
| ra | double | Right ascension in degrees |
| declination | double | Declination in degrees |
| distance | double | Distance from Sol in light-years |
| parallax | double | Parallax in milli-arcseconds |
| galacticLat | double | Galactic latitude |
| galacticLong | double | Galactic longitude |
| pmra | double | Proper motion in RA (degrees) |
| pmdec | double | Proper motion in Dec (degrees) |
| radialVelocity | double | Radial velocity in km/s |

### Photometric Magnitudes
| Field | Type | Description |
|-------|------|-------------|
| magu | double | Magnitude in U band |
| magb | double | Magnitude in B band |
| magv | double | Magnitude in V band |
| magr | double | Magnitude in R band |
| magi | double | Magnitude in I band |
| bprp | double | Gaia BP-RP color index |
| bpg | double | Gaia BP-G color index |
| grp | double | Gaia G-RP color index |

### World-Building Fields (for game/simulation use)
| Field | Type | Description |
|-------|------|-------------|
| polity | String | Political affiliation (e.g., ARAKUR, HKHRKH, KTOR, TERRAN) |
| worldType | String | Type of world |
| fuelType | String | Available fuel type |
| portType | String | Spaceport classification |
| populationType | String | Population category |
| techType | String | Technology level |
| productType | String | Primary exports/products |
| milSpaceType | String | Military space presence |
| milPlanType | String | Military planetary presence |
| anomaly | boolean | Anomaly flag |
| other | boolean | Other flag |

### Metadata
| Field | Type | Description |
|-------|------|-------------|
| realStar | boolean | True if real astronomical object, false if fictional |
| exoplanets | boolean | Has known exoplanets |
| numExoplanets | int | Count of known exoplanets |
| notes | String | Free-form notes |
| source | String | Data source catalog |
| miscText1-5 | String | Custom text fields |
| miscNum1-5 | double | Custom numeric fields |

## Working with the Data

Since this is a data-only repository, typical operations involve:

1. **Reading CSV data** with any standard tool (Python pandas, R, etc.)
2. **Adding new distance ranges** by creating new AT-HYG-{range}ly.trips.csv files
3. **Updating existing data** while maintaining the established column schema

When modifying CSV files, ensure Git LFS tracking remains intact via the `.gitattributes` configuration.

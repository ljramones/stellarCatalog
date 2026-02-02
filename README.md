# stellarCatalog

An extended star catalog based on the [AT-HYG dataset](https://www.astronexus.com/projects/at-hyg) from Astronexus.

## Overview

This repository contains star catalog data files that are a **superset of the AT-HYG dataset**. The original AT-HYG catalog merges data from Hipparcos, Yale Bright Star, and Gliese catalogs with modern astrometric data.

This dataset is designed for use with [TRIPS (Terran Republic Interstellar Plotter System)](https://github.com/ljramones/trips), a JavaFX-based 3D stellar cartography application for visualizing and plotting interstellar routes. TRIPS was originally developed to help visualize the stellar neighborhood for Chuck Gannon's [Caine Riordan](https://charlesegannon.com) science fiction series.

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

## Data Schema

The CSV files contain the following fields. Coordinates are heliocentric in J2000 epoch.

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

### World-Building Fields
| Field | Type | Description |
|-------|------|-------------|
| polity | String | Political affiliation |
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

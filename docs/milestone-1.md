# Milestone 1 — Efficient APIs

[← Back to Home](../README.md)

## Weekly progress

| Week | Team contribution summary |
| --- | --- |
| **Week 3 (Jan 19)** | **Chris:** set up wiki page layout templates and commit functions for M1. **Azlan:** code-formatting wiki page and commit functions. **Nour:** home and Team Charter pages and commit functions. |
| **Week 4 (Jan 26)** | **Chris:** set up `loadMap` structure, global unordered-map variables for OSM-related functions, and revised other functions. **Azlan:** completed six functions, debugged `loadMap`, and tested functionality. **Nour:** completed four functions and worked through global-variable integration for distance/time functions. |
| **Week 5 (Feb 2)** | **Chris:** major code-style overhaul; implemented `findWayLength`, `getOSMNodeTagValue`, cache clearing, and geo-binning work. **Azlan:** completed assigned functionality, improved high-performance functions, changed prefix lookup to a more efficient ordered map, and worked on geo-binning/BFS. **Nour:** focused on debugging, global initialization, feature-area work, code style, and defensive coding. |
| **Saturday, Feb 7** | **Milestone 1 deadline** |

## Milestone description

This milestone focused on using and extending an API built around `libstreetsdatabase` for geographic information. The project used two API layers:

- `StreetsDatabaseAPI.h` for higher-level structured street/intersection data.
- `OSMDatabaseAPI.h` for lower-level OpenStreetMap data.

## Resources

The original course wiki linked these server-hosted artifacts:

- `a1.pdf` — M1 instructions
- `m1_style_proj_manage_git_rubric.pdf` — M1 rubric
- [Internal Meeting Notes](https://docs.google.com/document/d/1t922zr5r3DeH9ph4sOQH3MPcaBJl2oFxREJvN7FTFk4/edit?usp=sharing)

## Detailed work distribution

| Mohammad Azlan | Nour Mohamed | Christopher Lee |
| --- | --- | --- |
| `findAdjacentIntersections` | `findStreetSegmentTravelTime` | `loadMap` |
| `findClosestIntersection` | `findStreetSegmentsOfIntersection` | `findWayLength` |
| `findIntersectionsOfStreet` | `findDistanceBetweenTwoPoints` | `getOSMNodeTagValue` |
| `findIntersectionsOfTwoStreets` | `findStreetSegmentLength` | `closeMap` |
| `findStreetIdsFromPartialStreetName` | `findFeatureArea` | Code-style overhaul |
| `findClosestPOI` | `findStreetLength` | — |

## Function implementation status

Milestone 1 consisted of 18 required functions with different performance expectations.

- **High:** heavily optimized; typically benefited from precomputed data structures and minimal API calls.
- **Moderate:** speed-tested, but straightforward API-based implementations were generally sufficient.
- **None:** not speed-tested.
- **Done (draft):** implementation completed but still requiring full correctness/performance validation.

### Status table

| High | Moderate | None |
| --- | --- | --- |
| `findStreetSegmentTravelTime` — draft done | `loadMap` | `findStreetSegmentTurnAngle` |
| `findAdjacentIntersections` | `closeMap` | `findStreetBoundingBox` |
| `findClosestIntersection` | `findDistanceBetweenTwoPoints` — draft done | — |
| `findStreetSegmentsOfIntersection` — draft done | `findStreetSegmentLength` — draft done | — |
| `findIntersectionsOfStreet` | `findFeatureArea` | — |
| `findIntersectionsOfTwoStreets` | — | — |
| `findStreetIdsFromPartialStreetName` | — | — |
| `findStreetLength` | — | — |
| `findClosestPOI` | — | — |
| `findWayLength` | — | — |
| `getOSMNodeTagValue` | — | — |

## Notes

Draft-complete functions still required correctness testing and performance validation where applicable. High-priority functions were expected to receive additional optimization using cached data structures created during `loadMap()`.

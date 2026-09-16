# Milestone 2 — Visualizing an Interactive Map

[← Back to Home](../README.md)

## Weekly progress

| Week | Team contribution summary |
| --- | --- |
| **Week 6 (Feb 9)** | **Chris:** final M1 revision/code-style overhaul and selected Google Maps as GIS reference. **Azlan:** selected HealthMap and reviewed/tested code. **Nour:** selected Uber and planned WD1 with the team. |
| **Week 7 (Feb 16)** | **Chris:** drafted and revised WD1. **Azlan:** wrote SAR and a proposed feature. **Nour:** drafted WD1 content and identified remaining sections. |
| **Week 8 (Feb 23)** | **Chris:** completed semantic zoom, colour-palette tracking, and part of UI formatting; began OP1 feature work. |
| **Saturday, Feb 28** | **Milestone 2 deadline** |

## Milestone description

Milestone 2 introduced the EZGL graphics library to visualize the map and added interactive search/display functionality for map elements.

## Resources

Historical course-wiki attachments:

- `wd1_instructions_2026_v1.0-1.pdf`
- `a2.pdf`
- `m2_grading_rubric.pdf`
- `m2_sample_features.pdf`
- [Internal Meeting Notes](https://docs.google.com/document/d/1t922zr5r3DeH9ph4sOQH3MPcaBJl2oFxREJvN7FTFk4/edit?usp=sharing)

## WD1 GIS choices

- **Azlan:** HealthMap
- **Nour:** Uber Driver interface
- **Chris:** Google Maps

## Detailed work distribution

| Name | Task | Status | Date due | Date completed |
| --- | --- | --- | --- | --- |
| All | Find a source/article | Complete | Feb 19 | Feb 20 |
| Nour | Write BP | Complete | Feb 21 | Feb 17 |
| Azlan | Write BP | Complete | Feb 21 | Feb 22 |
| Chris | Write BP | Complete | Feb 21 | Feb 21 |
| Nour & Chris | Introduction | Complete | Feb 22 | Feb 22 |
| Azlan + All | Conclusion | Complete | Feb 24 | Feb 22 |

## Essential tasks

| # | Owner(s) | Task | Target |
| --- | --- | --- | --- |
| 1 | Azlan | Load and visualize any map without recompilation | Feb 24 |
| 2 | Nour & Chris | Visualize streets, POIs, features, etc. | Feb 27 |
| 3 | Nour | Show street and POI names | In progress |
| 4 | Chris & Nour | Distinguish road classes and one-way direction | Feb 27 |
| 5 | Nour & Azlan | Click an intersection and show highlighted details | Feb 24 |
| 6 | Azlan | Search two streets and highlight all matching intersections | Feb 28 |
| 7 | Chris | Semantic zoom with varied levels of detail | Feb 28 |
| 8 | Azlan | Support partial street-name lookup | Feb 28 |
| 9 | All | Keep map uncluttered and interactive | Feb 28 |

## Major functions — `m2.cpp`

| Owner(s) | Functions | Purpose |
| --- | --- | --- |
| Nour | `drawMap` | Start EZGL app, build caches/world, and run event loop |
| Azlan, Nour | `initial_setup`, `setupSwitches`, `mapNameCache` | Build UI widgets, search completion, and signal connections |
| Azlan, Nour, Chris | `open_next_map` | Switch maps, rebuild caches, and refresh drawing |
| Azlan | `testing_search`, `testing_completion` | Search-entry and suggestion handling |
| Nour, Azlan | `actOnMouseClick` | Route click events and update feature info |
| Nour, Chris | `drawMainCanvas` | Main rendering pipeline for features, streets, POIs, intersections |
| Nour, Chris | coordinate conversion helpers | Convert lat/lon to world coordinates and back |
| Chris | `getOSMWayTagValueHelper` | Read OSM tags for road styling |
| Chris | `buildRenderProfilesHelper`, `getZoomProfileHelper`, `updateRenderStyleHelper` | Semantic-zoom thresholds and rendering styles |
| Chris | `dayPaletteHelper`, `nightPaletteHelper` | Day/night palette definitions |

## Cache building

Key cache builders included street-segment geometry, intersections, features, POIs, and list-store/search-completion data.

## Drawing helpers

Major drawing helpers handled streets, street names, one-way arrows, features, POIs, intersections, and popup information.

## Event handlers

Major handlers included intersection clicks, POI category switches, and the night-mode switch.

> Historical note: the original page stated that additional features were still planned for OP1.

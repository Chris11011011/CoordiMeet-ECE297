# Milestone 3 — Shortest Path Algorithms and User Interface

[← Back to Home](../README.md)

## Weekly progress

| Week | Team contribution summary |
| --- | --- |
| **Week 9 (Mar 2)** | **Chris:** completed follow-up M2 fixes/features, then shifted to OP1 presentation content. |
| **Week 10 (Mar 9)** | **Chris:** finalized presentation materials and moved to M3 backend work. **Azlan:** explored pathfinding algorithms, planned implementation, and completed early backend deadlines. **Nour:** completed initial tasks and continued GUI-related work. |
| **Tuesday, Mar 10** | **OP1 presentation** |
| **Week 11 (Mar 16)** | **Chris:** built driving-instruction compilation, GTK inline-instruction display, and revamped `main.ui`/Canvas UI. **Azlan:** completed major pathfinding backend functions, clearing, search matching, and guided-tour work. **Nour:** implemented path drawing and user input for intersections/walking filters. |
| **Sunday, Mar 22** | **Milestone 3 deadline** |

## Milestone description

Milestone 3 extended the project from visualization into routing over a graph.

Primary goals:

1. Implement and optimize a shortest-path algorithm.
2. Develop a user interface for finding and reporting travel directions.

## Resources

- [Final OP1 Google Slides](https://docs.google.com/presentation/d/1pJNj5hr89oGyzMiBivciF6Je95GCPGEHlhmW36NHkdk/edit?usp=sharing)
- Historical wiki attachment: `a3.pdf` — M3 instructions
- Historical wiki attachment: `m3_grading_rubric.xlsx` — M3 grading rubric
- [Internal Meeting Notes](https://docs.google.com/document/d/1t922zr5r3DeH9ph4sOQH3MPcaBJl2oFxREJvN7FTFk4/edit?usp=sharing)

## Post-M2 / OP1 fixes and features

| Owner | Function / file | Work |
| --- | --- | --- |
| Chris | `drawFeatureHelper`, `drawSingleFeature` | Draw features in type order |
| Azlan | `clearSelectedItems` | Close intersection/pin popups on click |
| Azlan | `drawFeatureNamesHelper`, `drawPOINamesHelper` | Feature and POI names |
| Nour | `handleIntersectionClick`, `handleCloseIntersectionPopup` | Close intersection popup on click |
| Azlan | `fixWorldBounds` | Limit zoom-out bounds |
| All | Rental dataset | Rental-price feature work |
| Nour | `findFeaturePoints` | Precompute feature centres and draw names |
| Azlan | cache builders | Rental-price filters and caching |
| Chris | OP1 presentation | Slides, transitions, design, and finalization |
| Chris | OP1 speaker notes | Supporting script for team members |

## Backend functions

| # | Function | Description |
| --- | --- | --- |
| 1 | `computePathTravelTime(...)` | Returns travel time along a path in seconds. |
| 2 | `findPathBetweenIntersections(...)` | Finds a route between a source and destination intersection when one exists. |
| 3 | `computePathWalkingTime(...)` | Returns walking time along a path. |
| 4 | `findPathWithWalkToPickUp(...)` | Finds a walk + drive route by allowing a walk to a pickup intersection within a time limit, then driving to the destination. |

## Frontend requirements

| # | Feature | Requirement summary |
| --- | --- | --- |
| 1 | User Help | Provide a way for new users to learn the interface. |
| 2 | Path by Street Input | Find a path using street/intersection text input. |
| 2.5 | Error Handling | Show clear errors for invalid input. |
| 3 | Path Visualization | Clearly display the calculated route on the map. |
| 4 | Path Type Selection | Support drive-only and walk + drive modes with walking parameters. |
| 5 | Travel Directions | Produce step-by-step directions understandable by a typical driver. |
| 6 | Path by Mouse Click | Select intersections and routes directly on the map. |
| 7 | Partial Street Names | Support partial street-name input. |

### Status labels

- **NS:** Not Started
- **IP:** In Progress
- **C:** Completed

## Detailed work distribution

| ID | Owner(s) | Area | Description | Status | Deadline | Completed |
| --- | --- | --- | --- | --- | --- | --- |
| a | Azlan | Backend | `findPathBetweenIntersections` | C | Mar 17 | Mar 18 |
| b | Azlan & Nour | Frontend | Help/guided-tour interface | C | Mar 17 | Mar 21 |
| c | Nour | Frontend | Popup with two search bars | C | Mar 17 | Mar 16 |
| d | Azlan | Frontend | Street-search completion | C | Mar 17 | Mar 20 |
| e | Chris | Backend | Walking-time computation | C | Mar 17 | Mar 17 |
| f | Nour | Backend | Path travel-time computation | C | Mar 21 | Mar 18 |
| g | Azlan | Backend | Walk + drive shortest-path logic | C | Mar 21 | Mar 19 |
| h | Nour | Frontend | Invalid-search error message | C | Mar 21 | Mar 17 |
| i | Chris | Frontend | Draw drive/walk/combined paths | C | Mar 21 | Mar 21 |
| j | Nour | Frontend | Toggle drive vs. drive + walk | C | Mar 21 | Mar 17 |
| k | Chris | Frontend | Travel-detail directions | C | Mar 21 | Mar 18 |
| l | Nour | Frontend | Find/display path by clicking intersections | C | Mar 21 | Mar 22 |

## Key subtasks and implementation details

- **Search normalization:** `normalizeForSearchingHelper`, `toLowerCaseHelper`
- **Instruction formatting:** street name, distance, next intersection, turn, and consecutive-walk helpers
- **Instruction compilers:** `buildWalkingDirectionsHelper`, `buildWalkDriveDirectionsHelper`
- **Connectivity pruning:** `Intersection_DSU`
- **A*/Dijkstra node model:** `intersection_astar_node`
- **Heuristic:** Euclidean distance divided by maximum map driving speed
- **Backtracing:** rebuild ordered street-segment paths, including walk + drive pickup awareness
- **Walking reachability:** `intersectionsReachableByWalkHelper`
- **Path rendering state:** `setPath`, `clearPathDrawing`, `clearPathDrawingHelper`
- **Directions panel:** `displayDirectionsInPanelHelper`, `updateDirectionsPanelIfPathReadyHelper`
- **UI improvements:** scrollable directions, source/destination/pickup pins, walking-speed slider, and autocomplete text

By the end of the milestone, the historical wiki marked the major listed tasks as completed.

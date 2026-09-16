# Milestone 4 — Travelling Courier

[← Back to Home](../README.md)

## Milestone description

Milestone 4 extended the routing system to a multi-stop courier problem: find a good route for a driver handling multiple deliveries. The problem is a variation of the travelling-salesman problem and required combining fast path lookup with route-order optimization.

## Resources

Historical course-wiki attachments:

- `a4.pdf` — M4 instructions
- `m4_grading_rubric.pdf` — M4 rubric
- [Internal Meeting Notes](https://docs.google.com/document/d/1t922zr5r3DeH9ph4sOQH3MPcaBJl2oFxREJvN7FTFk4/edit?usp=sharing)

## Milestone summary

Because M4 was highly iterative, the original wiki used a development log rather than a rigid work-allocation table. Task ownership identifies leads, but many foundation functions were peer-coded and refined collaboratively.

## Development log

| Date | Coder(s) | Context | Summary |
| --- | --- | --- | --- |
| Mar 26 | Azlan | M4 setup | Created initial structures including `index_of_location_in_grid`, `fill_intersections_grid`, and `is_order_valid`. |
| Mar 28 | Azlan, Nour | Greedy baseline | Added closest-stop/depot helpers, subpath conversion, and a first greedy delivery-order solution. |
| Mar 29 | Azlan | Multi-destination Dijkstra | Built `multiDestinationDijkstra` to precompute travel times between depots/pickups/dropoffs for O(1) lookup. |
| Mar 29 | Azlan | Cost evaluation | Added `findOrderTravelTime`. |
| Mar 29 | Azlan | Local search | Added `TwoOpt`. |
| Mar 29 | Azlan | Depot selection | Added `kbestdepots`, ranking depots by average time to pickups. |
| Mar 29 | Azlan | Exploration | Added randomized greedy selection among top nearby candidates. |
| Mar 30 | Azlan | Simulated annealing | Implemented simulated annealing with temperature/cooling tuning and route perturbations. |
| Mar 30 | Azlan | Random exploration | Added `randomReverse`, `randomSwap`, and `randomNeighbour`. |
| Mar 31 | Azlan | Refinement | Fixed bugs, tuned convenience helpers, and continued QoR testing. |
| Apr 1 | Azlan | Reverse optimization | Added `is_reverse_valid` and `reversing_time_difference`. |
| Apr 1 | Azlan | Cost + parallelism | Consolidated cost computation, introduced multithreading, and added wall-clock timing limits. |
| Apr 1 | Azlan | Four-opt | Added `FourOpt` for larger route perturbations. |
| Apr 1 | All | Team review | Reviewed current state and coordinated QoR improvements. |
| Apr 2 | Nour | Look-ahead greedy | Added look-ahead selection helpers; initial results were worse and required further tuning. |
| Apr 3 | Nour | Leak/warning fixes | Fixed a Valgrind leak and cleared warnings. |
| Apr 3 | Nour | Three-opt / block swap | Implemented additional perturbations and began tuning them. |
| Apr 4 | Azlan | Or-opt | Added `OrOpt` to relocate route segments of length 1–3. |
| Apr 4 | Azlan | Segment shift | Added `segmentShift` to relocate larger route segments. |
| Apr 4 | Azlan | Final intensive search | Tuned simulated annealing and added a timed final refinement using two-opt, Or-opt, and segment shift. |
| Apr 4 | Nour | Three-opt fixes | Corrected three-opt and `randomBlockSwap` logic. |
| Apr 4 | Chris | Perturbation work | Updated `randomNeighbour` choices and added `randomInsert`. |
| Apr 4 | Chris | Performance optimization | Fixed logic/performance issues in depot selection, multi-destination Dijkstra, validation, random block swap, and reverse-three-opt helpers. |
| Apr 5 | Nour | Large-order simplification | Reintroduced a simpler greedy path for very large orders and handled single-depot cases. |
| Apr 5 | Chris | Faster RNG | Added `fast_rand` and `fast_rand_double` using thread-local random engines. |
| Apr 5 | Chris | Thread-local buffers | Made reusable buffers thread-local in validation and perturbation code. |
| Apr 5 | Chris | Annealing exploration | Changed `randomNeighbour` to test multiple perturbations and retain the best valid option per call. |
| Apr 5 | Azlan | Final tuning | Retuned annealing, local search, iteration limits, probabilities, and final polish flow. |
| Apr 5 | Azlan | Final courier loop | Added an iterative final search before returning the result and cleared remaining warnings/syntax issues. |

## Main techniques used

- Greedy route construction
- Multi-destination Dijkstra caching
- O(1) cached pairwise travel-time lookup
- Two-opt, three-opt, four-opt
- Or-opt and segment shifting
- Random swap/reverse/insert perturbations
- Simulated annealing
- Depot ranking
- Parallel processing
- Wall-clock-aware optimization loops
- Thread-local random-number generation and buffers

## Historical note

The original page ended with a placeholder (`FIXME @azlan`) for the final detailed-work-distribution section. This reconstruction preserves the substantive development log instead of inventing content that was never completed in the source wiki.

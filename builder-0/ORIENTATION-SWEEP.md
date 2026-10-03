# Builder-0.5: Orientation Sweep

A controlled angular sweep of the curved-wall environment.

The prior Builder-0.2 and 0.4 experiments selected opposite semicircles with predicates x > cx and x < cx. They were not a continuous rotation experiment. Builder-0.5 therefore defines orientation explicitly.

For each wall center, a point on the circular shell belongs to the wall when its radial vector has a positive dot product with the orientation unit vector. This retains one semicircle and rotates that retained half around the circle.

Angles tested: 0°, 30°, 60°, 90°, 120°, 150°, 180°.

At every angle:

- 100 paired deterministic seeds
- same seed sequence
- 20,000 ticks
- same W dynamics
- same source/sink task
- same radius and wall thickness
- same central y corridor
- same collision response
- no obstacle awareness

0° is mathematically equivalent to the original x > cx half selection. 180° is equivalent to x < cx, subject to floating-point boundary cases.

The purpose is to measure whether LIVE-minus-NULL performance varies systematically with wall orientation rather than merely comparing hand-picked geometries.


## Recorded result — 2026-10-03

Field run completed on the mobile harness:

| Angle | LIVE / NULL / ties | Mean Δ | Median Δ |
| --- | --- | ---: | ---: |
| 0° | 100 / 0 / 0 | +173.9 | +176.0 |
| 30° | 100 / 0 / 0 | +175.1 | +172.5 |
| 60° | 100 / 0 / 0 | +145.5 | +147.0 |
| 90° | 100 / 0 / 0 | +96.2 | +97.5 |
| 120° | 100 / 0 / 0 | +57.5 | +57.0 |
| 150° | 76 / 23 / 1 | +9.2 | +9.5 |
| 180° | 77 / 22 / 1 | +9.2 | +10.0 |

The result is frozen as Builder-0.5. The response is structured but should not yet be described as a general law. In this fixed curved environment, causal W steering's relative performance changes strongly with retained-semicircle orientation.

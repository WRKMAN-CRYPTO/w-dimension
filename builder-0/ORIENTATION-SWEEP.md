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

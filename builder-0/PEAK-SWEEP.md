# Builder-0.6: Peak Sweep

Builder-0.6 increases angular resolution around the high-performance region observed in Builder-0.5.

Angles tested:

- 0°
- 15°
- 30°
- 45°
- 60°

Everything else remains frozen from Builder-0.5:

- 100 paired deterministic seeds per angle
- same seed sequence
- 20,000 ticks
- same curved-wall definition
- same radius, thickness, centers, and central y corridor
- same collision response
- same source/sink task
- same agents
- same W dynamics

Builder-0.5 means in this interval were:

- 0°: +173.9
- 30°: +175.1
- 60°: +145.5

The purpose is not to assume that 30° is an optimum. It is to resolve the shape between 0° and 60° and determine whether the small 0°→30° increase replicates as a broader peak, a narrow peak, a plateau, or sampling variation.


## Recorded result — 2026-10-03

Field run completed on the mobile harness:

| Angle | LIVE / NULL / ties | Mean Δ | Median Δ |
| --- | --- | ---: | ---: |
| 0° | 100 / 0 / 0 | +173.9 | +176.0 |
| 15° | 100 / 0 / 0 | +170.3 | +172.5 |
| 30° | 100 / 0 / 0 | +175.1 | +172.5 |
| 45° | 100 / 0 / 0 | +165.1 | +166.0 |
| 60° | 100 / 0 / 0 | +145.5 | +147.0 |

All five orientations favored LIVE in all 100 paired seeds. The 0°, 30°, and 60° values reproduce Builder-0.5 to displayed precision.

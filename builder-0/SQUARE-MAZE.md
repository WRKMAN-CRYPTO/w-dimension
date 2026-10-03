# Builder-0.7: Square Maze

## Pre-registered hypothesis

Before observing the experiment, the user predicted:

> In a maze of squares, W-NULL will win by brute force.

This prediction is recorded before field testing.

## Design

Builder-0.7 restores the live paired-world view so agent behavior can be observed directly.

- W-LIVE above
- W-NULL below
- same seed and initial agents
- same source and sink
- same W dynamics
- same steering mechanics
- identical square-cell maze in both worlds
- maze is symmetric around the horizontal centerline
- agents receive no obstacle sensor, map, avoidance rule, maze instruction, or reward shaping
- walls are collision geometry only
- wall contacts are counted observationally

The purpose is exploratory but the prediction is explicit: NULL is expected to outperform LIVE through brute-force traversal of rectilinear corridors and corners.

A batch replication should follow only after confirming the live maze behaves as intended.

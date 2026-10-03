# Builder-0.1: Seed Battery

This is a replication harness for Builder-0. It freezes the mechanics of Experiment 0 and runs 100 paired deterministic seeds.

Each pair receives identical starting agents. The only experimental difference remains:

- W-LIVE: W contributes to steering.
- W-NULL: W is carried and written but cannot steer.

Each seed runs for 20,000 ticks. Recorded outcomes are LIVE delivered energy, NULL delivered energy, their difference, and LIVE W-band transitions.

No W parameter was changed after observing the first seed. This harness exists to determine whether the first NULL advantage generalizes across starting conditions.

The original interactive Builder-0 remains untouched.


## Recorded result — 2026-10-03

Field run completed on the mobile harness:

- LIVE wins: 0
- ties: 0
- NULL wins: 100
- mean Δ (LIVE − NULL): -767.1 delivered energy
- median Δ: -768.5 delivered energy

This unobstructed result is frozen as the Builder-0.1 baseline. Future experiments should not alter it retroactively.

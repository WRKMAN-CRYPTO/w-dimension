# Builder-0.3: Straight-Wall Battery

Builder-0.3 tests whether the Builder-0.2 reversal depends on curved geometry.

Only wall shape changes. The two centered curved barriers are replaced by two centered straight vertical barriers. The central passage remains open with the same y-range used in Builder-0.2.

Everything else remains frozen:

- 100 paired deterministic seeds
- same seed sequence
- 20,000 ticks per seed
- same agents and task
- same W-LIVE and W-NULL mechanics
- no obstacle sensor or avoidance instruction
- same collision response

Prior frozen results:

- Builder-0.1 open world: LIVE 0, NULL 100, mean Δ -767.1, median Δ -768.5
- Builder-0.2 curved walls: LIVE 100, NULL 0, mean Δ +173.9, median Δ +176.0

Question: does W-LIVE retain its advantage when curvature is removed?

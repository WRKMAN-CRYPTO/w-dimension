# Builder-0.2: Obstacle Battery

Builder-0.2 preserves the Builder-0.1 agent and W mechanics and changes only the environment.

Two mirrored curved wall segments are placed through the center of the source-to-sink route with a narrow open corridor at the middle. Placement is centered to avoid intentionally favoring the bottom-heavy W-LIVE behavior observed in the original interactive seed.

Agents receive no obstacle sensor, avoidance rule, reward, penalty, or instruction. Collision geometry merely prevents movement through a wall and reflects heading.

Protocol:

- 100 paired deterministic seeds
- same seed sequence as Builder-0.1
- 20,000 ticks per seed
- W-LIVE and W-NULL remain identical except for W's causal steering effect
- compare wins, mean Δ, and median Δ against the unobstructed Builder-0.1 baseline

Frozen unobstructed baseline: LIVE 0, NULL 100, ties 0, mean Δ -767.1, median Δ -768.5.

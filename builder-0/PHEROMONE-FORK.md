# Builder-P1 — Successful-Agent Pheromone Fork

Quick experimental fork from Builder-0.9. Builder-1.0 remains untouched and may continue running independently.

## Question

What happens to W-LIVE and W-NULL when agents that have successfully delivered energy can leave a weak shared pheromone trail?

Winner prediction: **OPEN**. No winner was predicted before the run.

## Pheromone rule

- A delivery at the sink marks that agent as successful.
- During its unloaded return trip toward the source, a successful agent deposits pheromone.
- Reaching/picking up at the source ends its successful trail-laying state.
- Pheromone is a separate 56×28 scalar field.
- Deposit strength: 0.035 per occupied pheromone cell per step, capped at 1.
- Global decay: ×0.9985 per simulation tick.
- All agents can sense the local pheromone gradient.
- The gradient adds a gently capped steering contribution, maximum magnitude 0.010 rad/tick.
- LIVE and NULL use identical pheromone rules.

The original W field is unchanged. LIVE still receives W causal steering; NULL still computes W but receives zero W steering.

Pheromone is rendered as a faint green field so trail formation can be inspected visually.

This is an exploratory fork, not part of the running Builder-1.0 agent-seed battery.

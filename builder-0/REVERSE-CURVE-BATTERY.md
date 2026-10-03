# Builder-0.4: Reverse-Curvature Battery

Builder-0.4 tests whether the Builder-0.2 W-LIVE advantage belongs to curvature generally or to the orientation of the original arcs.

Only one geometric predicate changes: the original curved walls used the right-hand half of each circle (`x > cx`). Builder-0.4 uses the left-hand half (`x < cx`).

Frozen:

- same arc centers, radius, and thickness
- same central open y corridor
- same collision response
- same agents and energy task
- same W dynamics
- same 100 deterministic paired seeds
- same 20,000-tick horizon

Prior results:

- 0.1 open: LIVE 0 / NULL 100, mean Δ -767.1, median -768.5
- 0.2 original curves: LIVE 100 / NULL 0, mean Δ +173.9, median +176.0
- 0.3 straight walls: LIVE 0 / NULL 100, mean Δ -172.2, median -173.0

Question: does reversing the arcs preserve, erase, or reverse the W-LIVE advantage?

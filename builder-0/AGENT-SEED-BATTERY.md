# Builder-1.0 — Agent Seed Battery

Purpose: test whether the time-dependent LIVE recovery/crossover observed in Builder-0.8.2/0.9 is specific to the original agent population.

## Frozen apparatus

- maze seed: `0x4D415A45`
- maze geometry/generator: Builder-0.9
- hard vertical seal: Builder-0.8.2
- agent count: 320
- W field and steering: unchanged
- collision mechanics: unchanged
- source/sink mechanics: unchanged

## Changed variable

Only the paired agent initialization seed varies.

## Battery

- 100 deterministic paired agent seeds
- 400,000 ticks per pair
- sampled every 1,000 ticks
- LIVE and NULL within a pair begin from the same agent seed

Recorded per pair:

- LIVE endpoint deliveries
- NULL endpoint deliveries
- endpoint Δ = LIVE − NULL
- minimum sampled Δ, representing deepest NULL lead
- whether LIVE crosses from non-positive to positive Δ
- first sampled crossover tick

This battery follows the observed 0.9 crossover and is exploratory with respect to crossover prevalence. The original maze prediction, **W-NULL wins by brute force**, remains part of the fossil record and is not rewritten.

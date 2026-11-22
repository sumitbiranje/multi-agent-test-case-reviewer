# Design decisions

## ADR-1: Seven narrow agents instead of one broad reviewer
**Why.** A single prompt that checks everything misses things and is hard to tune. Narrow agents can be improved one at a time.

## ADR-2: Concurrency at two levels
**Decision.** Ingest in parallel; run the seven agents in parallel per case.
**Why.** Review time is bound by the slowest agent, not the sum of all seven.

## ADR-3: Pydantic for every agent output
**Why.** Enables merging, counting, filtering and regression-testing the reviewer itself.

## ADR-4: Deterministic verdict rules
**Decision.** The final verdict comes from rules over findings, not from another LLM call.
**Why.** Predictable, explainable and cheap.

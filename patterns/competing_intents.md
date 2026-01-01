# Competing Intents

**Definition:** A system has competing intents when a single surface (workflow, interface, report, or component) is forced to satisfy multiple goals that cannot be simultaneously optimized.

This produces *confusing behavior* that looks like bugs, inconsistency, or “the system is unreliable”, but the root cause is often **goal collision**, not implementation failure.

---

## Where competing intents show up
Common surfaces:
- a “one endpoint does everything” API
- a dashboard used for both operations and executive reporting
- a workflow that is both exploratory (flexible) and production (reliable)
- a memory/ask system that is both recall-heavy and precision-heavy without mode separation

---

## Observable symptoms (evidence-based)
Look for these signals:

1. **Contradictory success criteria**
   - different stakeholders define “correct” differently for the same output

2. **Flip-flopping behavior**
   - changes improve one use-case while degrading another, repeatedly

3. **Patch layering**
   - repeated exceptions, flags, or special-cases added to satisfy new demands

4. **Unstable interfaces**
   - inputs/outputs are “technically the same” but semantics change release to release

5. **Endless debate**
   - discussions cycle because there is no single contract that settles correctness

---

## Detection method (minimal)
1) Write down the **surface** (one sentence).  
2) List the **top 2–3 goals** the surface is expected to satisfy.  
3) For each goal, write one **measurable success criterion**.  
4) Ask: can all criteria be true at once, for the same run/output?

**If no:** you have competing intents.

**Output:** a 1-page “intent card”:
- surface
- goals
- success criteria
- conflict statement

---

## Resolution patterns (choose one)
### Pattern A — Split the surface
Create separate surfaces for separate intents.

Examples:
- “explore” vs “execute” modes
- “operator view” vs “reporting view”
- “diagnostic endpoint” vs “production endpoint”

**Evidence of success:** each surface gets its own contract and tests.

### Pattern B — Add an explicit mode switch
Keep one surface, but require explicit mode selection at the boundary.

**Evidence of success:** mode is visible in input, output, and logging/artifacts.

### Pattern C — Prioritize a primary intent
Declare one goal as primary and accept degradation of the other goals.

**Evidence of success:** contract explicitly states trade-offs.

### Pattern D — Promote upstream constraints
If the collision is caused by ambiguous inputs, fix the upstream contract:
- stricter schemas
- clearer definitions
- gated promotion rules

**Evidence of success:** fewer exceptions needed downstream.

---

## What not to do
- Don’t “average” the goals into a vague compromise contract.
- Don’t hide intent choice inside heuristics (“the system will decide”).
- Don’t rely on documentation alone — enforce intent separation structurally.

---

## Minimal artifact set (for review)
- intent card (surface + goals + criteria)
- chosen resolution pattern
- contract updates (or new contracts)
- one concrete before/after example showing conflict reduced

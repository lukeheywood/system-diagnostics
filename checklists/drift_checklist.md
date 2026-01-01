# Drift Checklist

**Goal:** Determine whether a system is *drifting* — changing behavior or meaning over time without an explicit, reviewable change record.

This checklist is deliberately **black-and-white**: each step should produce an observable artifact or a clear “unknown”.

---

## 0) Define the surface you’re checking
Write down, in one sentence:
- **Surface:** what users/operators interact with (API, UI, report, workflow, contract)
- **Owner:** who can change it (team, repo, pipeline)
- **Expected behavior:** what the surface is supposed to do (not how)

**Output:** a 3-line “surface card”.

---

## 1) Check whether the contract exists
Look for an explicit contract artifact (one of):
- spec / requirements doc
- interface contract
- input/output schema
- promotion rules / acceptance criteria
- changelog / decision record

**Pass:** contract exists and is accessible  
**Fail:** contract is missing  
**Unknown:** contract exists but is not discoverable

**Output:** link or path to the contract (or “missing/unknown”).

---

## 2) Compare contract vs current reality
Pick **one concrete test** that exercises the surface.

Examples:
- run the workflow with a known input and capture output
- execute a “golden” query and capture retrieved evidence
- open the UI and capture the rendered state
- review a report produced today vs last known good

**Pass:** output matches contract  
**Fail:** output contradicts contract  
**Unknown:** cannot reproduce/observe output

**Output:** a timestamped capture (log snippet, screenshot reference, saved output, or repro steps).

---

## 3) Check whether changes are recorded
If reality differs from the contract, determine whether there is:
- a changelog entry
- a PR/commit reference
- an ADR / decision note
- a version bump / release note

**Pass:** difference is explained by an explicit change record  
**Fail:** difference has no change record  
**Unknown:** history exists but cannot be traced

**Output:** the change record reference (or “none”).

---

## 4) Identify drift class (choose one)
Use the smallest category that fits:

1. **Semantic drift**  
   Meaning shifted (labels, definitions, intended interpretation)

2. **Behavior drift**  
   Inputs/outputs changed (logic, thresholds, routing, defaults)

3. **Boundary drift**  
   What is “in scope” vs “out of scope” changed

4. **Ownership drift**  
   Responsibility changed without acknowledgement (handoffs, “everyone owns it”)

5. **Visibility drift**  
   Observability degraded (no longer inspectable, more implicit)

**Output:** drift class + one-sentence evidence.

---

## 5) Determine blast radius (bounded)
Answer only with evidence you can point to:

- **Who is affected?** (roles/teams/surfaces)
- **What breaks?** (reports, decisions, workflows)
- **Is this reversible?** (yes/no/unknown)

**Output:** a 3-bullet blast radius note.

---

## 6) Resolution options (pick one)
Choose the smallest corrective action:

- **A) Update the contract** (if reality is correct and contract is stale)
- **B) Restore the system** (if contract is correct and system drifted)
- **C) Gate promotion** (if you can’t determine correctness yet)

**Output:** chosen option + owner + next action.

---

## Minimal “drift pack” artifact
If you want this to be reviewable by a third party, store:

- surface card
- contract link/path
- repro steps + captured output
- change record link (or “none”)
- drift class + blast radius
- chosen resolution option

That’s enough to make drift visible without narrative.

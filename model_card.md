# BugHound Mini Model Card (Reflection)

Fill this out after you run BugHound in **both** modes (Heuristic and Gemini).

---

## 1) What is this system?

**Name:** BugHound  
**Purpose:** Analyze a Python snippet, propose a fix, and run reliability checks before suggesting whether the fix should be auto-applied.

**Intended users:** Students learning agentic workflows and AI reliability concepts.

---

## 2) How does it work?

Describe the workflow in your own words (plan → analyze → act → test → reflect).  

### Heuristics

- Plan: Set up a quick scan and fix-proposal workflow.
- Analyze: Try LLM analysis; when its output isn’t parseable, fall back to heuristics and identify an issue.
- Act: Use the LLM fixer to propose a fix.
- Test: Assess the proposed fix’s risk (high, medium, low) based on the risk score.
- Reflect: Decide whether the fix isn’t safe to auto-apply and recommend human review.

### Gemini

- Plan: Prepare a quick scan and fix-proposal workflow.
- Analyze: Gemini analyzes the code and identifies any issue.
- Act: The fixer proposes a change for that issue.
- Test: The proposed fix determines the risk score (high, medium, low).
- Reflect: The app judges whether the fix safe enough to auto-apply under its current policy.

Include what is done by heuristics vs what is done by Gemini (if enabled).

---

## 3) Inputs and outputs

**Inputs:**

- What kind of code snippets did you try?
- What was the “shape” of the input (short scripts, functions, try/except blocks, etc.)?

**Outputs:**

- What types of issues were detected?
- What kinds of fixes were proposed?
- What did the risk report show?

![Output of the app when  Gemini is enabled](images/Screenshot%202026-11-11%20203427.png "Detected Issues")

![Output of the app when  Gemini is enabled](images/Screenshot%202026-11-11%20203533.png "Proposed Fix")

![Output of the app when  Gemini is enabled](images/Screenshot%202026-11-11%20203639.png "Agent Trace")

### Testing 

![Testing the app with various scenarios/workflows](images/Screenshot%202026-11-10%20195341.png "Testing Output")

![Testing Code](images/Screenshot%202026-11-11%20192737.png "Conversation with Copilot")

---

## 4) Reliability and safety rules

List at least **two** reliability rules currently used in `assess_risk`. For each:

- What does the rule check?
- Why might that check matter for safety or correctness?
- What is a false positive this rule could cause?
- What is a false negative this rule could miss?

---

## 5) Observed failure modes

Provide at least **two** examples:

1. A time BugHound missed an issue it should have caught  
2. A time BugHound suggested a fix that felt risky, wrong, or unnecessary  

For each, include the snippet (or describe it) and what went wrong.

---

## 6) Heuristic vs Gemini comparison

Compare behavior across the two modes:

- What did Gemini detect that heuristics did not?
- What did heuristics catch consistently?
- How did the proposed fixes differ?
- Did the risk scorer agree with your intuition?

---

## 7) Human-in-the-loop decision

Describe one scenario where BugHound should **refuse** to auto-fix and require human review.

- What trigger would you add?
- Where would you implement it (risk_assessor vs agent workflow vs UI)?
- What message should the tool show the user?

---

## 8) Improvement idea

Propose one improvement that would make BugHound more reliable *without* making it dramatically more complex.

Examples:

- A better output format and parsing strategy
- A new guardrail rule + test
- A more careful “minimal diff” policy
- Better detection of changes that alter behavior

Write your idea clearly and briefly.

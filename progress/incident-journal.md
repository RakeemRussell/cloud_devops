# Incident journal

One entry per break/fix scenario, written on Friday while it is fresh. `BF-NN` marks a scripted
scenario; `OWN-NN` marks something I broke myself.

Entry format (the entry below is an example of the format, not a real entry):

```markdown
## BF-45 — Pod stuck Pending  (week 15, 11 min)
Symptom:    New deployment's pods never leave Pending.
Hypothesis: Resource pressure -- but nodes showed plenty free.
Confirmed:  `kubectl describe pod` -> "0/3 nodes available: 3 node(s) had untolerated taint"
Root cause: Node had a NoSchedule taint from an earlier lab; pod had no toleration.
Fix:        Added the toleration. (Alternative: remove the taint.)
Prevent:    Check `kubectl describe node | grep Taints` before blaming resources.
Surprised:  describe on the POD tells you about the NODE. Events are the whole game.
```

Rules:

- **Diagnose before you fix**, and record the hypothesis I had *before* confirming it, even when it
  was wrong. A wrong first hypothesis is the interesting part of the story.
- **Time it.** The minutes in the heading feed the monthly retrospective in `progress.md`.
- **Prevent** is a change to a process, a check, or a default. "Be more careful" is not prevention.
- Never delete an entry. If the same root cause recurs, add the new entry and link the old one.

---

## Entries

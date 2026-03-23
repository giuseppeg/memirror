# Review Request

Please review the memory-system spec in src/MEMIRROR.md

Context:
- This system is for an LLM coding agent.
- The goal is reliable memory behavior with low hesitation.
- We want a system that profiles the user continuously, distills local project knowledge when useful and stays simple enough that the model actually follows it.
- This system must trigger all the time and reliably

Please focus on:
- overall design and architecture.. does it achieve what is set to achieve?
- what is clear
- what is confusing or contradictory
- what is likely to fail in real model behavior
- where the model may hesitate or misclassify
- what should be simplified further
- whether the trigger model is strong enough
- whether the storage split is sound
- etc...

Please prioritize findings over praise.
Be concrete.
Call out exact lines or phrases when possible.
If something is good, say why briefly.

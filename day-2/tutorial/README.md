# Day 2 Tutorial — Streaming and Human-in-the-Loop

This is the completed code used in the recorded tutorial.

Day 1 delivered results with `invoke()`, which returns only after the whole run finishes. Today the same bounded debug loop is first streamed step by step, then paused after every step for a human decision. The running example is still the 0/1-knapsack bug.

## Video flow

1. Connect to the shared model gateway.
2. Restate the running example and import the shared types.
3. Define the debug step (prompt and structured schema) used by both parts.
4. Build a bounded self-loop and run it with `stream(stream_mode="updates")`.
5. Read each chunk as its node finishes, and contrast it with a single `invoke()`.
6. Add a `human_review` node that pauses with `interrupt()`.
7. Resume the paused graph with `Command(resume=...)` after a human decides to retry or end.
8. Confirm the iteration limit still stops the loop even when the human keeps answering `retry`.

From the workshop root:

```bash
source .venv/bin/activate
./workshop start
cd day-2/tutorial
jupyter lab
```

Open `day-2.ipynb` and run it from top to bottom. After watching the video, continue to the [homework](../exercise/README.md).

Select **Python 3.12 — Agentic AI Workshop** if prompted. A successful lesson streams each step of the bounded loop as it finishes, then pauses for a human decision after every step in Part 2.

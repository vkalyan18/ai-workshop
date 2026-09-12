# Day 2 — Streaming and Human-in-the-Loop

- **Time:** 2–2.5 hours including homework
- **You will build:** a streaming view of a bounded debug loop, then a human-in-the-loop review that pauses after every step
- **Know first:** bounded loops, routing, and structured output from Day 1
- **Not required yet:** code execution or multi-agent handoffs

## Start

From the workshop root:

```bash
source .venv/bin/activate
./workshop start
cd day-2/tutorial
jupyter lab
```

Open `day-2.ipynb` and use the workshop kernel.

## Follow this order

1. Build the bounded debug loop and run it with `stream()`; watch one update arrive as each node finishes.
2. Contrast `stream()` with `invoke()`, which returns only the final state.
3. Add the `human_review` node and predict how many times the graph will pause before you resume it.
4. Confirm the iteration limit still stops the loop even if every answer is `retry`.
5. Complete the review-and-revise graph in the [homework](exercise/README.md).

## What success looks like

- `stream(stream_mode="updates")` yields one chunk per node as it finishes; `invoke()` returns only the final state.
- Streaming changes when the caller sees each step, not what the graph computes.
- The human-in-the-loop graph pauses after every step and resumes only after `Command(resume=...)`.
- The iteration limit still stops the loop even if every human answer is `retry`.
- The homework cannot revise more than twice.

## If you get stuck

Print each streamed chunk before wiring the pause. Do not debug the stream and the `interrupt()` pause at the same time.

**Intentional failure:** remove the checkpointer from `compile()` and try to resume the paused graph; observe the error, then restore it.

**Exit check:** Does streaming change what the graph computes, or only when the caller sees it? And which decisions belong to the human rather than to deterministic code?

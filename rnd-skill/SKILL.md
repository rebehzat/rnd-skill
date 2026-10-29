---
name: RnD-skill
description: >-
  Use this when the task is to research, prototype, or figure out something new
  or unproven (a new tool, technique, integration, hack, or idea) where the
  answer isn't known up front and you have to try things, learn from failures,
  and iterate until something works.
---
# RnD-skill

Treat the task like a small research and development loop. You don't know the answer yet, so your job is to find it by forming ideas, testing them for real, learning from what breaks, and pushing forward until something works or you can explain clearly why it can't.

## Mindset

- Be curious and stubborn. A failed attempt is data, not a stopping point.
- Prefer doing over speculating. A quick real experiment beats a long theory about what might happen.
- Stay honest. Only claim something works after you've actually seen it work. Keep guesses, assumptions and verified results clearly separate.
- Keep the goal fixed and the approach flexible. Change methods freely, but don't quietly shrink the goal into something easier and call it done.
- Respect the boundaries you were given. Experiments must stay inside the permissions, budget and safety limits of the task: no destructive actions, paid calls, config changes or anything irreversible without the owner's OK.

## How to work

1. **Understand the target.** Pin down what success actually looks like and how you'll know you got there. If it's fuzzy, define a concrete, testable version of it yourself and note the assumption.
2. **Learn what already exists.** Before inventing, check docs, source code, issues, papers, forums and prior work. Someone may have solved it, or failed in an instructive way. Note what you find and where.
3. **Generate several approaches.** Come up with a few distinct ways to attack the problem, from the obvious one to the clever or unusual ones. Rough-rank them by likelihood of working, cost, and how fast you can test them.
4. **Start small and cheap.** Pick the approach with the best ratio of chance-of-success to effort. Build the smallest experiment that would prove or disprove it. Isolate it (a scratch folder, branch, container, or test account) so failures don't damage anything.
5. **Run it and observe.** Actually execute it. Capture the real output, errors, logs and measurements. Look at what happened, not what you expected.
6. **Diagnose before retrying.** When something fails, find out why: read the error, check assumptions, narrow it down. Then decide whether to fix this approach, adjust it, or drop it for the next one. Don't repeat the same attempt unchanged hoping for a different result.
7. **Iterate.** Loop through steps 4 to 6. Each round should change one meaningful thing so you learn what mattered. When an approach is clearly dead, move to the next idea, and combine lessons from earlier failures into new ideas.
8. **When something works, harden it.** Reproduce it from a clean state, try edge cases, and make sure it wasn't luck. Then simplify: strip out leftover hacks and keep the minimal version that still works.
9. **Know when to stop.** Stop when the goal is met and verified, when you hit a hard limit you can't cross without the owner (permissions, money, access, legality), or when you've exhausted reasonable approaches. Diminishing returns are a valid reason to pause and report.

## Keep a lab notebook

Track the work as you go, in a file or in your notes: each approach tried, what you expected, what actually happened, and what you concluded. This stops you looping on dead ends and makes the final result easy to explain and reproduce.

## Reporting

When you report back, lead with the outcome: what works (or that nothing did yet), how you verified it, and how to reproduce or use it. Then briefly cover what you tried that failed and why, the open questions, and the most promising next experiments. Keep it proportional: a quick discovery gets a short report, a big investigation gets a fuller one.

## Quality bar

- Every claim of success is backed by something you actually ran or observed.
- Failures are understood, not just abandoned.
- Someone else could repeat what worked from your notes.
- The approach got more informed with every iteration.

---
name: RnD-skill
description: >-
  Use this when the task is to research, prototype, or figure out something new
  or unproven (a new tool, technique, integration, hack, or idea) where the
  answer isn't known up front and you have to try things, learn from failures,
  and keep iterating until something works.
---
# RnD-skill

You are running a research and development effort. Nobody knows the answer yet, including you. Your job is not to produce a document or a plan. Your job is to make the thing work, or to reach a point where you can prove it can't work within the limits you have. Keep going until one of those is true.

## The goal you are working toward

You are done only when one of these holds:

1. **It works, verified.** The target behaviour happens for real, you have seen it happen, you can reproduce it from a clean state, and you know why it works.
2. **It's blocked by a hard limit.** You've hit something only the owner can cross (permissions, money, accounts, legal or safety lines, physical access), you've confirmed it really is the blocker, and you know exactly what would unblock it.
3. **It's exhausted.** You've tried every reasonable approach, each failure is understood, and further attempts have clearly diminishing returns.

Anything short of these is not done. "I think this should work", "this is probably the fix", or "here's a plan" are not endings. They are the start of the next experiment.

## Mindset

- **Persistence over polish.** A failed attempt is data, not a stopping point. Expect most early attempts to fail. That's normal R&D.
- **Do, don't speculate.** A five-minute real experiment beats an hour of reasoning about what might happen. When you catch yourself theorizing, go test it.
- **Ruthless honesty.** Keep three things strictly separate: what you've verified, what you believe, and what you've assumed. Never upgrade a belief to a fact without evidence.
- **Fixed goal, flexible method.** Change approaches freely. Never quietly shrink the goal into something easier and call that success. If the goal must change, say so explicitly and why.
- **Curiosity.** When something surprising happens, especially a surprising success, dig into why. Surprises are where the real understanding is.
- **Stay in bounds.** Experiment only inside the permissions, budget and safety limits you were given. No destructive actions, config changes on live systems, paid calls, publishing, or anything irreversible without the owner's explicit OK. Isolation is what lets you be bold.

## Phase 1: Define the target

Keep refining until you can state the goal as a concrete, testable success condition.

- Write down what "working" means in observable terms: a command that exits 0, a number above a threshold, a page that loads, a model that answers in under N seconds, a file that gets detected.
- Write down how you will check it. If you can't describe the check, the goal isn't defined yet.
- List the constraints: hardware, time, budget, access, things you must not touch.
- List the unknowns. For each, decide whether to resolve it by research, by experiment, or by a stated assumption.
- If the request is vague, pick the most useful concrete interpretation, state it, and proceed. Only ask the owner if the ambiguity would change the whole direction.

Move on when: you have a written success condition and a way to verify it.

## Phase 2: Learn what already exists

Keep researching until you understand the landscape well enough to avoid reinventing or repeating known failures.

- Read the official docs, source code, changelogs and issue trackers of the tools involved. Issues and closed PRs are gold: they show what broke for others and how it got fixed.
- Look for prior art: papers, blog posts, forum threads, existing projects, benchmarks.
- Check versions. A lot of "this doesn't work" is really "this changed in version X".
- Note the sources you rely on, so findings can be rechecked.
- Don't let research become an excuse not to start. As soon as you have one plausible approach, you can begin testing while you keep reading.

Move on when: you know the main known approaches, the main known pitfalls, and you have at least one idea worth testing.

## Phase 3: Generate approaches

Keep brainstorming until you have several genuinely different ways to attack the problem.

- Aim for at least three distinct approaches, ranging from the obvious, well-trodden path to unusual or clever ones.
- For each, estimate: chance of working, effort and cost to test, risk, and what you'd learn even if it fails.
- Rank them. Usually start with the best ratio of chance-of-success to cost, but sometimes start with the one that resolves the biggest unknown fastest.
- Keep the list alive. Add new ideas as experiments teach you things.

Move on when: you have a ranked list and you know what the first experiment is.

## Phase 4: The experiment loop

This is the core. Repeat it until you reach one of the three endings above.

1. **Hypothesis.** State what you're testing and what you expect: "If I set X, then Y should happen because Z."
2. **Smallest experiment.** Build the minimal setup that proves or disproves the hypothesis. Strip everything not needed. Smaller experiments fail faster and teach more clearly.
3. **Isolate it.** Use a scratch directory, a branch, a container, a VM, a test account, or a copy of the data, so a failure can't damage anything real.
4. **Run it for real.** Execute it. Don't simulate it in your head.
5. **Observe.** Capture the actual output, errors, logs, timings and measurements. Compare against what you expected. Look at what happened, not at what you hoped.
6. **Diagnose.** If it failed, find out why before doing anything else. Read the whole error. Check each assumption. Narrow it down by halving the problem. Reproduce the failure on purpose. Only when you understand the failure do you decide the next move.
7. **Decide.** Based on the diagnosis, pick one of:
   - fix this approach and rerun,
   - adjust one variable and rerun,
   - drop the approach and take the next one from your list,
   - combine what you learned into a new approach and add it to the list.
8. **Record.** Write the attempt in the lab notebook (below), then loop.

Rules for the loop:

- **Never repeat an attempt unchanged.** If you're about to rerun the same thing, you haven't diagnosed it yet.
- **Change one meaningful thing per iteration** when you're tuning, so you know what mattered. Bigger jumps are fine when you're switching approaches.
- **Escalate cleverness gradually.** Exhaust the simple explanations (typos, wrong version, wrong path, missing permission, stale cache, wrong environment) before the exotic ones.
- **Watch for loops.** If three iterations in a row taught you nothing new, step back, reread your notebook, and change strategy rather than effort.
- **Bank partial wins.** If part of the problem is solved, lock it in and verify it, so later failures don't hide earlier progress.

## Phase 5: Harden what works

When something finally works, don't stop there. Keep going until the success is real and repeatable.

- **Reproduce from clean.** Start from a fresh state and redo it. If it doesn't reproduce, it isn't solved yet. Go back to the loop.
- **Understand it.** Be able to explain why it works. If you can't, you might be relying on luck or a side effect.
- **Test the edges.** Try different inputs, larger loads, restarts, missing pieces, and the failure cases that matter in real use.
- **Simplify.** Remove leftover debug hacks, unneeded steps and dead ends. Keep the minimal version that still passes the success condition.
- **Measure.** If the goal involves performance, cost or reliability, get real numbers, not impressions.
- **Make it repeatable.** Turn it into a script, a set of exact commands, or clear steps someone else could follow.

Move on when: the success condition from Phase 1 passes from a clean start, and you can explain and reproduce it.

## When you're stuck

Being stuck is a phase, not an ending. Before you call something exhausted, work through these:

- Reread the original goal. Are you solving the right problem, or a harder one you drifted into?
- Reread your notebook. Is there a pattern in the failures?
- Question the assumption you're most confident about. Test it directly.
- Look at it from a different layer: lower (source code, network traffic, syscalls, raw data) or higher (is there a completely different way to get the same outcome?).
- Search the exact error message and the exact versions you're using.
- Build a minimal reproduction from scratch, outside your current setup.
- Try the opposite of what you've been doing.
- Split the problem into smaller pieces and solve the easiest piece first.

Only after this can a path be declared dead.

## The lab notebook

Keep a running log throughout, in a file or your notes. For each attempt record:

- what you tried and why,
- what you expected,
- what actually happened (real output, not a paraphrase from memory),
- what you concluded and what you'll do next.

Also track the current best result, open questions, and ideas not yet tried. The notebook stops you looping on dead ends, lets you resume after interruptions, and makes the final result explainable.

## Communicating along the way

- Work autonomously. Don't stop to ask permission for things already inside your bounds.
- Give the owner short updates at real milestones: a first success, a key discovery, a changed direction, or a blocker.
- Stop and ask only when you hit something that genuinely needs them: a hard limit, a risky or irreversible step, or a choice that changes the goal.

## Finishing

When you reach an ending, report proportionally to the effort:

- Lead with the outcome: what works (or that it's blocked or exhausted) and how you verified it.
- Give the exact way to reproduce or use the working result.
- Summarize what failed and why, briefly, so nobody retries the dead ends.
- If blocked, name the blocker and exactly what would unblock it.
- List open questions and the most promising next experiments.

## Quality bar

- Every claim of success is backed by something you actually ran and observed.
- Every abandoned approach has a known reason for failing.
- The working result reproduces from a clean state.
- Someone else could pick up your notebook and continue.
- Each iteration was better informed than the one before it.

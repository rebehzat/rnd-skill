# RnD-skill

An agent skill for research and development: figuring out something new or unproven where the answer isn't known up front. The agent tries things for real, learns from what breaks, retries with a better idea, and keeps going until something works or it can explain clearly why it can't.

## How it works

1. Pin down what success looks like and how to verify it.
2. Check what already exists (docs, source, issues, papers, prior work).
3. Come up with several approaches and rank them by odds, cost and speed.
4. Run the smallest, cheapest experiment in isolation.
5. Observe what actually happened.
6. Diagnose failures before retrying, never repeat the same attempt unchanged.
7. Iterate, then harden and simplify whatever works.
8. Stop when it's verified, blocked by a hard limit, or out of reasonable ideas.

It keeps a lab notebook of every attempt, only claims success it has actually seen, and stays inside the permissions and safety limits it was given.

## Install

Copy the `rnd-skill/` folder (it holds `SKILL.md`) into your agent's skills directory, for example:

- Claude Code: `~/.claude/skills/rnd-skill/`
- Codex: `~/.codex/skills/rnd-skill/`
- Cursor / other agents that read `SKILL.md`: your skills folder

## Use

> use RnD-skill: get a 4B model running on this CPU-only VPS as fast as possible

> R&D this: find a way to detect when a file of ours shows up on a paste site

## License

MIT

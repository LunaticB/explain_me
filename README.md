# SVG ELI5 Archify

`svg-eli5-archify` is a portable Agent Skill that turns a codebase or
infrastructure repository into an evidence-backed, SVG-first one-page architecture
explainer. It combines a layered architecture map, an accurate ELI5 analogy,
strengths, risks, and prioritized next moves in the visual itself.

The canonical skill is [`SKILL.md`](./SKILL.md). The same file works with Codex,
Claude Code, and Gemini CLI; no vendor-specific copy of the instructions is
required. [`agents/openai.yaml`](./agents/openai.yaml) only adds optional Codex UI
metadata and is not required by Claude or Gemini.

## Compatibility and installation

| Host | Personal/user installation | Project/workspace installation |
| --- | --- | --- |
| Codex | `git clone https://github.com/kcc920926-droid/explain_me.git ~/.codex/skills/svg-eli5-archify` | Copy or clone the skill into the project's configured Codex skills directory. |
| Claude Code | `git clone https://github.com/kcc920926-droid/explain_me.git ~/.claude/skills/svg-eli5-archify` | `git clone https://github.com/kcc920926-droid/explain_me.git .claude/skills/svg-eli5-archify` |
| Gemini CLI | `gemini skills install https://github.com/kcc920926-droid/explain_me` | `gemini skills install https://github.com/kcc920926-droid/explain_me --scope workspace` |

Claude Code discovers personal skills at
`~/.claude/skills/<skill-name>/SKILL.md` and project skills at
`.claude/skills/<skill-name>/SKILL.md`. See the
[Claude Code skills documentation](https://code.claude.com/docs/en/skills).

Gemini CLI can install this repository directly. It also discovers user skills
under `~/.gemini/skills/` or `~/.agents/skills/`, and workspace skills under
`.gemini/skills/` or `.agents/skills/`. See the
[Gemini CLI Agent Skills documentation](https://github.com/google-gemini/gemini-cli/blob/main/docs/cli/using-agent-skills.md).

## Use it

- Codex: `Use $svg-eli5-archify to analyze this repository as one SVG-first page.`
- Claude Code: `/svg-eli5-archify Analyze this repository as one SVG-first page.`
- Gemini CLI: `Use svg-eli5-archify to analyze this repository as one SVG-first page.`

In Gemini CLI, run `/skills list` to confirm discovery and `/skills reload` after
editing the skill. In Claude Code, `/skills` lists the available skills.

## What the skill enforces

- repository evidence before architecture claims;
- declared, intended, and observed state kept separate;
- visible evidence IDs and a replayable source index for load-bearing claims;
- a layered context, workload, flow, data, and operations map;
- SVG as the main explanation rather than decoration;
- concrete evidence-to-consequence risks and three ordered next moves;
- a standalone SVG fallback when the host has no native visual artifact surface.

## Maintainer evaluation

`evals/mixed-state/fixture/` is a small fixed-ground-truth repository containing
a declared web process, an observed health response, and a worker that exists
only in design intent. Run the skill against the fixture without exposing
`expected.json`, then compare the SVG with that file. The check catches the most
important failure mode: turning intended architecture into observed reality.

# Roast Me

[![License: Unlicense](https://img.shields.io/badge/license-Unlicense-blue.svg)](https://unlicense.org/)

Stop asking your coding agent to be polite. Make it prove you understand your own app.

`roast-me` is a skill for Codex, Claude Code, and other skill-compatible coding agents. It turns the agent into a skeptical senior engineer who interrogates you about your app, codebase, architecture, spec, assumptions, and failure modes.

It asks one concrete question at a time. It scores your answer. It does not let "state flow stuff" count as an explanation.

## Install

### Claude Code / skills.sh

```bash
npx skills@latest add euxaristia/roast-me
```

Then select `/roast-me` when prompted.

### Codex

Clone this repo, then install the skill into your Codex skills directory:

```bash
git clone https://github.com/euxaristia/roast-me
mkdir -p "${CODEX_HOME:-$HOME/.codex}/skills"
cp -R roast-me/skills/productivity/roast-me "${CODEX_HOME:-$HOME/.codex}/skills/"
```

For a single project, install it into that repo instead:

```bash
mkdir -p .agents/skills
cp -R roast-me/skills/productivity/roast-me .agents/skills/
```

Use it with:

```text
$roast-me
```

## Use It When

- You want to check whether you actually understand a feature.
- You are about to ask an agent to build something and want to expose weak requirements first.
- You inherited code and want to find the parts you are hand-waving.
- You are preparing for a review, demo, incident postmortem, or architecture discussion.
- You want the agent to challenge a spec instead of quietly filling in gaps.

## Example Prompts

```text
$roast-me the auth refactor
$roast-me this pull request
$roast-me the Flutter prototype
$roast-me our billing retry logic
$roast-me the product spec before I hand it to an agent
```

## What It Does

`roast-me` asks questions like:

- Point me to the exact file and symbol.
- Walk the execution path from the user's click to the final state change.
- What invariant has to remain true here?
- Which test would fail if your explanation were wrong?
- What are you assuming that the code does not guarantee?

Answers are scored:

- `Pass`: specific, coherent, and grounded in the code or spec.
- `Partial`: directionally right, but missing a key mechanism or proof.
- `Fail`: vague, incorrect, contradicted by the repo, or unable to name the path.

The point is not humiliation. The point is to make vague thinking visible before it becomes vague software.

## Reference

- **[roast-me](./skills/productivity/roast-me/SKILL.md)** — Interrogate the user's understanding of an app, codebase, architecture, implementation, product spec, assumptions, and failure modes.

## License

Unlicense

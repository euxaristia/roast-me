# Roast Me

[![License: Unlicense](https://img.shields.io/badge/license-Unlicense-blue.svg)](https://unlicense.org/)

Turn "roast me" into a constructive technical conversation.

`roast-me` is a skill for Codex, Claude Code, and other skill-compatible coding agents. It turns the agent into a patient senior engineer who helps you talk through your app, codebase, architecture, spec, assumptions, and failure modes until both of you share a clearer model of the work.

It maps the relevant architecture first, then asks one concrete question at a time. It follows up gently when an answer is vague. It helps turn "state flow stuff" into actual files, symbols, data shapes, event paths, tests, and tradeoffs.

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
- You are about to ask an agent to build something and want to clarify requirements first.
- You inherited code and want to find the parts that are not yet clear.
- You are preparing for a review, demo, incident postmortem, or architecture discussion.
- You want the agent to clarify a spec with you instead of quietly filling in gaps.

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

- Can you point me to the exact file and symbol?
- In `main.swift`, `Editor`, and `Input.processKeypress`, where does raw input become an editor command, and which layer may mutate buffer state?
- Looking at `UI.refreshScreen` and the editor state type, what data is rendering allowed to read, and what state must it never change?
- Which module owns that responsibility, and which module should not know about it?
- What invariant has to remain true here?
- What test would catch it if this explanation were incomplete?
- What are we assuming that the code does not guarantee?

The exchange is conversational, not scored. After each answer, the agent should:

- Reflect what seems concrete or useful.
- Name any missing mechanism, unsupported claim, contradiction, or unclear term.
- Offer a small correction when needed.
- Ask the next question that would most improve shared understanding.

The point is not evaluation. The point is mutual understanding: make unclear thinking visible before it becomes unclear software, without turning the conversation into a discouraging test.

## Reference

- **[roast-me](./skills/productivity/roast-me/SKILL.md)** — Build shared understanding of an app, codebase, architecture, implementation, product spec, assumptions, and failure modes through constructive technical conversation.

## License

Unlicense

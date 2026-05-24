# WARP.md
AI가 작성한 문장은 지나치게 일정한 어조와 반복적 어휘·정형화된 문장 구조가 높은 수준으로 유지되고 있어, 논점의 변화, 강조, 논리적 전개 등 자연스러운 글의 흐름이 잘 드러나지 않습니다.
This file provides guidance to WARP (warp.dev) when working with code in this repository.

## What this repo is
This repository is a **Claude Code skill** implemented entirely as Markdown.

The “runtime” artifact is `SKILL.md`: Claude Code reads the YAML frontmatter (metadata + allowed tools) and the prompt/instructions that follow.

`README.md` is for humans: installation, usage, and a compact overview of the patterns.

## Key files (and how they relate)
- `SKILL.md`
  - The actual skill definition.
  - Starts with YAML frontmatter (`---` … `---`) containing `name`, `version`, `description`, and `allowed-tools`.
  - After the frontmatter is the editor prompt: the canonical, detailed pattern list with examples.
- `README.md`
  - Installation and usage instructions.
  - Contains a summarized “25 patterns” table and a short version history.

When changing behavior/content, treat `SKILL.md` as the source of truth, and update `README.md` to stay consistent.

## Common commands
### Install the skill into Claude Code
Recommended (clone directly into Claude Code skills directory):
```bash
mkdir -p ~/.claude/skills
git clone https://github.com/blader/humanizer.git ~/.claude/skills/humanizer
```

Manual install/update (only the skill file):
```bash
mkdir -p ~/.claude/skills/humanizer
cp SKILL.md ~/.claude/skills/humanizer/
```

## How to “run” it (Claude Code)
Invoke the skill:
- `/humanizer` then paste text

## Making changes safely
### Versioning (keep in sync)
- `SKILL.md` has a `version:` field in its YAML frontmatter.
- `README.md` has a “Version History” section.

If you bump the version, update both.

### Editing `SKILL.md`
- Preserve valid YAML frontmatter formatting and indentation.
- Keep the pattern numbering stable unless you’re intentionally re-numbering (since the README table and examples reference the same numbering).

### Documenting non-obvious fixes
If you change the prompt to handle a tricky failure mode (e.g., a repeated mis-edit or an unexpected tone shift), add a short note to `README.md`’s version history describing what was fixed and why.
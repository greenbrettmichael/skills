# Skills

My custom agent skills for Claude Code and other Agent Skills-compatible harnesses.

## Installation

### Claude Code (plugin)

```bash
claude plugin marketplace add greenbrettmichael/skills
claude plugin install greenbrettmichael-skills@greenbrettmichael
```

### Local symlinks (for editing)

```bash
git clone git@github.com:greenbrettmichael/skills.git
cd skills
scripts/link-skills.sh
```

This links every skill outside `misc/` and `deprecated/` into `~/.claude/skills` and `~/.agents/skills`, so edits in the repo take effect immediately.

## Skills

### Engineering

Daily code work. See [skills/engineering](./skills/engineering/README.md).

_None yet._

### Productivity

Daily non-code workflow tools. See [skills/productivity](./skills/productivity/README.md).

**User-invoked**

- **[new-skill](./skills/productivity/new-skill/SKILL.md)**: Scaffold a new skill in this repo, in the right bucket, and register it in the READMEs and plugin manifest.

**Model-invoked**

_None yet._

### Other buckets

- [misc](./skills/misc/README.md): kept around but rarely used
- [in-progress](./skills/in-progress/README.md): beta skills, not shipped in the plugin
- [deprecated](./skills/deprecated/README.md): no longer used

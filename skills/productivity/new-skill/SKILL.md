---
name: new-skill
description: Scaffold a new skill in this skills repo, in the right bucket, and register it in the READMEs and plugin manifest.
disable-model-invocation: true
---

# New skill

Create a new skill in this repository, following the conventions in the repo's `AGENTS.md`. Read `AGENTS.md` first.

## 1. Gather

Ask the user, one question at a time, only for what you can't infer:

- **Name**: kebab-case, short, a verb or noun phrase (`diagnose-bug`, `handoff`).
- **What it does** and **when it should fire**. This becomes the `description`.
- **Bucket**: `engineering`, `productivity`, `misc`, or `in-progress`. Default new, untested skills to `in-progress`.
- **Invocation**: user-invoked (only via `/<name>`) or model-invoked (loaded when the description matches). Recommend user-invoked for workflows with side effects or a fixed ritual; model-invoked for knowledge the model should pull in on its own.

## 2. Write the skill

Create `skills/<bucket>/<name>/SKILL.md`:

```markdown
---
name: <name>
description: <what it does, and when to use it>
disable-model-invocation: true   # user-invoked only; omit for model-invoked
---

# <Title>

<Instructions to the agent, written as direct steps.>
```

Keep `SKILL.md` focused on the steps. Put long reference material, templates, or scripts in sibling files and link them from `SKILL.md` so they load only when needed.

## 3. Register it

- Add a line to `skills/<bucket>/README.md` under the right heading (**User-invoked** / **Model-invoked** for promoted buckets; flat list otherwise), replacing `_None yet._` if present.
- If the bucket is `engineering` or `productivity`:
  - add the same line to the top-level `README.md` under that bucket's section, with the link path from the repo root
  - add `./skills/<bucket>/<name>` to `.claude-plugin/plugin.json`'s `skills` array
  - run `claude plugin validate .`
- Run `scripts/link-skills.sh` so the skill is available locally (skipped for `misc`).

## 4. Report

Tell the user the path of the new `SKILL.md` and how to invoke it.

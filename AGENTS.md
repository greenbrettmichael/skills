# Repo conventions

Skills are organized into bucket folders under `skills/`:

- `engineering/`: daily code work
- `productivity/`: daily non-code workflow tools
- `misc/`: kept around but rarely used, not promoted
- `in-progress/`: beta, still being tried out, not shipped in the plugin
- `deprecated/`: no longer used

Each skill is a folder named after the skill, containing a `SKILL.md` with `name` and `description` frontmatter. Supporting files (reference docs, scripts, templates) sit next to `SKILL.md` and are linked from it.

## Promoted skills

`engineering/` and `productivity/` are the **promoted** buckets. Every skill in them must have:

- an entry in the top-level `README.md`, with the skill name linked to its `SKILL.md`
- an entry in `.claude-plugin/plugin.json`'s `skills` array

Skills in `misc/`, `in-progress/`, and `deprecated/` must not appear in either. Run `claude plugin validate .` after touching `.claude-plugin/plugin.json` or `.claude-plugin/marketplace.json`.

## Bucket READMEs

Each bucket folder has a `README.md` listing every skill in the bucket with a one-line description, the skill name linked to its `SKILL.md`. The promoted buckets' READMEs and the top-level `README.md` group entries into **User-invoked** and **Model-invoked**; non-promoted bucket READMEs use a flat list.

## Invocation

Every `SKILL.md` is either:

- **User-invoked**: `disable-model-invocation: true` in the frontmatter. Reachable only when the human types `/<skill-name>`.
- **Model-invoked**: no such flag. The model loads it when the `description` matches the task, and the human can still type `/<skill-name>`.

For a model-invoked skill, the `description` is the trigger: say what the skill does and when to reach for it.

## Local install

`scripts/link-skills.sh` symlinks every skill outside `deprecated/` and `misc/` into `~/.claude/skills` and `~/.agents/skills`. A `git pull` keeps them current; re-run the script after adding, removing, or renaming a skill.

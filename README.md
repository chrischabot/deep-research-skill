# Deep Research Skill

A skill for questions that deserve more than a quick search. It works out what needs to
be established, reads the best available sources, checks where they disagree, and writes
a cited answer.

## How it works

- Frame the question and what the answer needs to help decide.
- Find and read the best available sources.
- Check contradictory evidence and important gaps.
- Write a concise answer with direct links.

## Principles

- Research before writing.
- Use primary sources for facts and independent sources to judge the claims around them.
- Say plainly what is known, inferred, disputed, or still missing.
- Never cite something that was not actually read.

## Install

Clone the repository once:

```sh
git clone https://github.com/chrischabot/deep-research-skill.git ~/Projects/deep-research
```

### Codex

```sh
mkdir -p ~/.agents/skills
ln -s ~/Projects/deep-research/skill ~/.agents/skills/deep-research
```

Invoke with `$deep-research`.

### Claude Code

```sh
mkdir -p ~/.claude/skills
ln -s ~/Projects/deep-research/skill ~/.claude/skills/deep-research
```

Invoke with `/deep-research` or ask Claude for a deep multi-source report.

### Pi

```sh
mkdir -p ~/.pi/agent/skills
ln -s ~/Projects/deep-research/skill ~/.pi/agent/skills/deep-research
```

Invoke with `/skill:deep-research` or ask Pi to use the skill.

### Cursor

```sh
mkdir -p ~/.cursor/skills
ln -s ~/Projects/deep-research/skill ~/.cursor/skills/deep-research
```

Invoke `/deep-research` or ask Agent for a deep multi-source report. Cursor also
discovers Codex and Claude skill directories, so install only one visible copy.

To update any installation:

```sh
git -C ~/Projects/deep-research pull --ff-only
```

## License

MIT

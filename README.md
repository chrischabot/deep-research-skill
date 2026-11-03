# Deep Research Skill

Deep Research is a skill for Codex, Claude Code, Pi and Cursor that gives a coding agent a research procedure for questions where the answer will feed a decision: a literature survey, a market map, a technical scan, or an analysis of what a launch actually changed. An agent left to its own habits can write a fluent report from a few searches, but that report may rest on snippets rather than the pages behind them, may count five articles repeating one announcement as five sources, and gives you no way to tell a checked fact from something a vendor merely said. The skill asks the agent to keep what it verified apart from what a source merely claims, so that the report shows what its conclusion rests on and where the evidence runs out.

## How it works

The skill is a set of instructions rather than a program, so the agent researches with whatever web, browser, repository, paper or connected-data tools its host provides, and those tools set the reach of the report.

Before searching, the agent pins down the decision the work should support and two or three counter-questions that could overturn the obvious answer. It then looks separately for primary sources, independent reporting and analysis, and disconfirming evidence, rather than repeating variants of one query. It opens the exact source behind a claim, treats what it reads as evidence and never as instructions, and sorts each material assertion into verified fact, source claim, inference or unresolved conflict. The search stops once new sources mostly repeat what the agent already has and the remaining uncertainty is explicit. The report normally leads with the answer and its confidence, then gives the key evidence, the contradictions and missing coverage, and the implications for your decision, with direct links beside the claims they support.

The [full procedure](skill/SKILL.md) is short enough to read before you install it.

## Install

Clone the repository once:

```sh
git clone https://github.com/chrischabot/deep-research-skill.git ~/Projects/deep-research
```

Then link its `skill` folder into the skills directory of each host you use. Cursor and Pi also read `~/.agents/skills`, and Cursor also reads `~/.claude/skills`, so a link made for Codex or Claude Code may already serve them, and each host should see only one copy.

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

Invoke `/deep-research` or ask Agent for a deep multi-source report.

### Updating

Every host links to the same clone, so one pull updates them all:

```sh
git -C ~/Projects/deep-research pull --ff-only
```

## Usage

Invoke the skill with your question and whatever framing you already have. In Claude Code, for example:

```text
/deep-research Should we move our background jobs from Sidekiq to Temporal this year? We are a six-person Rails team and operating cost matters most.
```

If you leave out the decision, audience or time window, the agent makes a bounded assumption and discloses it, asking only when a missing choice would materially change the research. Each run takes one finite question through to a report. A simple lookup doesn't need that much reading, and the skill won't keep watch on a topic for you.

## Development

`skill/SKILL.md` holds the whole procedure, and `skill/agents/openai.yaml` supplies Codex's display name, short description and default prompt. There is nothing to build and there are no dependencies, and an edit to `SKILL.md` reaches every host linked to your clone.

## License

[MIT](LICENSE), copyright 2026 Chris Chabot.

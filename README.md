# Edge: stop slop

Your agent writes generic slop because it works without expert know-how. Edge finds the right expert method on the internet (searched, classified and security-scanned) and loads it into your agent before it writes.

Get the right expertise and know-how from the internet into your agent, at the moment it needs it.

Your agent does generic work. Edge makes it expert. Edge is an MCP connector: when your agent
starts a specialist task (a pitch deck, a contract review, a security audit, a data analysis),
it asks Edge for the best published skill, loads it for that one task, and names it.

## How it works

1. **find_skill** - the agent sends one short, generic task line. Edge searches over 100,000 public
   skills by meaning, ranks them for the task, and returns up to five.
2. **use_skill** - Edge checks the security scanner results, withholds skills that fail its gate,
   and hands the chosen skill to the agent for the current task only. Nothing is installed.
3. **rate_skill** - when the work is done, the agent rates the skill, so the next agent gets a
   better pick.

Your files, code and conversation are not sent. Only the task line and keywords are.

## Install

Claude Code or Cursor: paste this into your agent.

```
Set up Edge for me: fetch https://getedge.cc/SKILL.md with curl, read it, and follow it
```

Claude Code, by hand:

```
claude mcp add --transport http -s user edge https://getedge.cc/mcp
```

Codex:

```
npx -y @getedge/mcp@0.6.52 setup codex
```

Claude app: Settings -> Connectors -> Add custom connector -> `https://getedge.cc/mcp/claude`.
ChatGPT, OpenCode and the rest: https://getedge.cc/docs/setup

Then start a new chat and ask: "Use Edge to find a skill for my task, show its source, and load it if it fits."

## Example

```
You:    Review this SaaS contract before I sign it.
Agent:  edge . find_skill("review a SaaS vendor contract before signing")
Edge:   1. contract-review     source: github.com/...   scan: passed
        2. legal-redlines      source: github.com/...   scan: passed
Agent:  edge . use_skill("contract-review")
Edge:   SKILL.md loaded for this task
Agent:  Using contract-review. Clause 7 auto-renews for 24 months with a
        90-day notice window; clause 11 caps their liability at one month of fees...
        From Edge skill: contract-review
Agent:  edge . rate_skill("contract-review", helpful)
```

## Links

- Product: https://getedge.cc
- Setup: https://getedge.cc/docs/setup
- Docs: https://getedge.cc/docs
- Privacy: https://getedge.cc/privacy

## License

Apache-2.0. See LICENSE.

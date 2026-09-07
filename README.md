# AI SEO Writing

An agent skill for writing blog posts and web articles that rank in Google **and** get cited in AI Overviews, AI Mode, ChatGPT, Perplexity and Claude, without sounding like a content mill wrote them.

```bash
npx skills add keupera/ai-seo-writing
```

Works with Claude Code, Claude.ai and Claude Desktop, plus 70+ other agents including Cursor, Codex, Copilot, Gemini CLI, Windsurf, OpenCode and Zed.

Listed on [skills.sh](https://www.skills.sh/keupera/ai-seo-writing/ai-seo-writing). Maintained by [Keupera](https://keupera.com).

---

## What it is

One `SKILL.md`. It loads when someone asks an agent to write, rewrite or optimize published content, then runs an eight-step editorial process from brief to on-page assets.

It covers SEO, GEO, AEO and AI SEO as one job rather than four, because they are one job: AI Overviews and AI Mode retrieve from the same index as blue links. There is no separate AI index and no special markup that unlocks it. The skill is built on that premise and says so explicitly, including a section on the "AI SEO" advice that Google has publicly confirmed does nothing.

## When the agent picks it up

The trigger is deliberately broad. Any request to produce content destined for a website counts, whether or not the word "SEO" appears:

- Blog posts, guides, listicles, comparison posts, how-tos, landing page copy
- Rewriting, optimizing or de-AI-ifying existing content
- Content briefs, title tags, meta descriptions
- "Why isn't this ranking?"

## Install

The [skills CLI](https://github.com/vercel-labs/skills) detects which agents you have and installs to each of them:

```bash
# Install for this project
npx skills add keupera/ai-seo-writing

# Install once, available everywhere
npx skills add keupera/ai-seo-writing -g

# Pick the agents yourself
npx skills add keupera/ai-seo-writing -g -a claude-code -a cursor -a codex
```

Try it without installing anything:

```bash
npx skills use keupera/ai-seo-writing | claude
```

### Claude Code, by hand

```bash
# Personal, available in every project
git clone https://github.com/keupera/ai-seo-writing.git ~/.claude/skills/ai-seo-writing

# Project, committed with the repo
git clone https://github.com/keupera/ai-seo-writing.git .claude/skills/ai-seo-writing
```

Restart Claude Code, or run `/skills` to confirm it loaded.

### Claude.ai and Claude Desktop

Download the repo as a ZIP, then add it under Settings → Capabilities → Skills.

### Anything else

`SKILL.md` is plain Markdown with YAML frontmatter. Point any agent at the file, or paste its body into a system prompt.

## What's inside

| Step | What it does |
|---|---|
| 1 | Gets the real inputs first: query, reader, intent, voice, owned proof, next action. Asks rather than guesses |
| 2 | Applies Google's commodity test to the angle, then maps the query fan-out sub-questions the piece has to answer |
| 3 | A skim-first structure that serves human readers and passage extraction with the same blueprint |
| 4 | Keyword handling for 2026: placement where it reads naturally, no density targets, entities named explicitly |
| 5 | Voice. Before-and-after rewrites of the sentences that give AI drafts away |
| 6 | On-page trust: attribution, dating, showing the method, disclosing conflicts, linking out |
| 7 | Title tag, meta description, slug, H1, alt text, image markers, schema note |
| 8 | Eight self-edit passes, each a separate read, before anything is delivered |

Plus **The Don'ts**, the longest section in the file: a hard list covering punctuation and rhythm, blacklisted phrases, formatting tics, hollow structure, dead SEO practice, and the honesty rules that are not negotiable. It ends in a quick-reference table with actual limits.

| Thing | Limit |
|---|---|
| Em dashes | ~1 per 400–500 words, never 2 in a paragraph |
| Rule of three | Avoid entirely |
| Bold inside prose | None |
| Blacklisted phrases | 0 |
| Unsourced statistics | 0 |
| Invented experience | 0 |

## Output

Meta block, then the article, then notes on what was assumed, where real data should go, suggested internal links and anything worth flagging before publishing.

```
## Meta
Title tag, meta description, URL slug, primary query, intent, sub-questions

## Article
Full draft in Markdown, with [IMAGE: …] and [INSERT: …] markers

## Notes
Assumptions, internal links, schema recommendation, publishing flags
```

## Data, via the Keupera MCP

The skill writes. It does not invent numbers. Keyword volume, difficulty, backlink prospects, competitor SERPs and AI-citation data come from [Keupera](https://keupera.com), which runs a hosted MCP server so the agent can pull real data and publish straight to a CMS.

```bash
claude mcp add --transport http keupera https://mcp.keupera.com/mcp -s user
```

Claude.ai and Desktop: Settings → Connectors → Add custom connector → `https://mcp.keupera.com/mcp`

Everything else, including Cursor, VS Code, ChatGPT, Codex, Gemini CLI, Windsurf and Goose: [docs.keupera.com/mcp/clients](https://docs.keupera.com/mcp/clients)

The skill works without it. When the MCP is absent it says which numbers it will not estimate and marks the gaps instead of filling them with plausible fiction.

## Contributing

Issues and pull requests are welcome, particularly additions to The Don'ts. If a phrase or tic reliably marks a draft as machine-written, that belongs in the list. Include an example.

## License

MIT. See [LICENSE](LICENSE).

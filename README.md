# AgentSkills
A collection of different SKILLS.md files I've found and find useful (or think I might find useful)

Note that none of these are intended to be fully trusted! All should be considered more as "inspiration" that "direct use". My current manner of thinking says, "For your given project, pick and choose the skills here and copy them into your project." Definitely do not drop these in the global location for your coding agent to use; I think that could probably blow the context window right out of the atmosphere.

## Repository Purpose

**Canonical repository:** https://github.com/tedneward/AgentSkills

This is a knowledge base repository - not a traditional code project. There is no build system, tests, or compiled output.

## Structure

```
AgentSkills/
├── agents/                 # Agent definitions
├── commands/               # Command (slash-command) definitions
├── mcps/                   # MCP server configurations (JSONs)
├── skills/                 # Flat structure
│   ├── akka-best-practices/SKILL.md
│   ├── aspire-integration-testing/SKILL.md
│   ├── csharp-coding-standards/SKILL.md
│   ├── testcontainers/SKILL.md
│   └── ...
```

### Skill Naming Convention

Skills use a flat directory structure with prefixes for domain-specific skills:

- `akka-*` - Akka.NET skills
- `aspire-*` - .NET Aspire skills
- `csharp-*` - C# language skills
- `database-*` - Database skills
- `dotnet-*` - General .NET-related skills

... and so on. Prefixes should be pretty self-explanatory?


## File Formats

**Skills** are folders with `SKILL.md`:
```yaml
---
name: skill-name
description: Brief description used for matching
---
```

**Agents** are markdown files with YAML frontmatter:
```yaml
---
name: agent-name
description: Brief description used for matching
model: sonnet  # sonnet, opus, or haiku
color: purple  # optional
---
```

## Adding New Skills

1. Create a folder: `skills/<skill-name>/SKILL.md`
   - Use appropriate prefix for framework-specific skills (see naming convention above)
   - No prefix for general .NET skills
2. Run `./scripts/generate-skill-index-snippets.sh --update-readme` to regenerate the compressed index
3. Commit all changes together (SKILL.md, and README.md)

### Adding Skills to Index Categories

When adding a skill with a **new prefix pattern**, update `scripts/generate-skill-index-snippets.sh` to handle the new pattern in its `case` statement. Otherwise the skill will be silently ignored when generating the index.

## Adding New Agents

1. Create the agent file: `agents/<agent-name>.md`
2. Run `./scripts/generate-skill-index-snippets.sh --update-readme` to regenerate the compressed index
3. Commit all changes together (agent .md, plugin.json, and README.md)

## Content Guidelines

- Skills should be comprehensive reference documents (10-40KB)
- Include concrete code examples with modern C# patterns
- Reference authoritative sources rather than duplicating content
- Agents define personas with expertise areas and diagnostic approaches

## Router / Index Snippets

When skills/agents change, keep the copy/paste snippet indexes up to date:
- See `skills/skills-index-snippets/SKILL.md`
- Generate a compressed index with `./scripts/generate-skill-index-snippets.sh`


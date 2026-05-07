# AgentSkills
A collection of different SKILLS.md files I've found and find useful (or think I might find useful)

## Repository Purpose

**Canonical repository:** https://github.com/tedneward/AgentSkills

This is a knowledge base repository - not a traditional code project. There is no build system, tests, or compiled output.

## Structure

```
AgentSkills/
├── skills/                 # Flat structure for Copilot compatibility
│   ├── akka-best-practices/SKILL.md
│   ├── aspire-integration-testing/SKILL.md
│   ├── csharp-coding-standards/SKILL.md
│   ├── testcontainers/SKILL.md
│   └── ...
├── agents/                 # Agent definitions (flat .md files)
```

### Skill Naming Convention

Skills use a flat directory structure with prefixes for framework-specific skills:
- `akka-*` - Akka.NET skills
- `aspire-*` - .NET Aspire skills
- `csharp-*` - C# language skills
- `dotnet-*` - General .NET-related skills
- `microsoft-extensions-*` - Microsoft.Extensions.* packages
- `playwright-*` - Playwright-specific skills

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


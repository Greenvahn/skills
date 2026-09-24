# Skills

A personal, public collection of skills for AI coding assistants and agents.

Each top-level folder holds the skills built for one AI tool.

## Structure

```
skills/
└── claude/                     # Skills for Claude (Claude Code, claude.ai, etc.)
    └── design-system-builder/  # Generates a full HTML/CSS design system from a brand brief
```

Each skill lives in its own folder and follows the format expected by its target platform: for Claude, that's a `SKILL.md` file describing when and how the skill should be used, plus any supporting assets it needs.

## Available skills

### Claude

| Skill | Description |
|---|---|
| [design-system-builder](claude/design-system-builder/SKILL.md) | Generates a complete, production-quality HTML/CSS design system — tokens, typography, buttons, responsive grid, and demo sections — from an interactive brand brief. |

## Usage

To use a skill with Claude Code, copy the relevant skill folder into your project's `.claude/skills/` directory (or your personal `~/.claude/skills/`), or clone this repo and symlink the folders you want.

## Contributing

This is primarily a personal archive, but suggestions and issues are welcome.

## License

[MIT](LICENSE)

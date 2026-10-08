# Lean Precision

Short, grammatical answers. Simple engineering. Extra effort when it pays off.

This package contains one self-contained `SKILL.md` for Codex, Claude Code, Antigravity, and OpenCode. It requires no plugins, hooks, or dependencies. The optional `agents/openai.yaml` provides Codex UI metadata.

## Install at user scope

Extract the archive. Copy the `lean-precision` folder into your tool's skills directory:

| Tool | Destination for the folder |
| --- | --- |
| Codex CLI | `~/.agents/skills/lean-precision/` |
| Claude Code | `~/.claude/skills/lean-precision/` |
| Antigravity 2.0 | `~/.gemini/config/skills/lean-precision/` |
| Antigravity CLI | `~/.gemini/antigravity-cli/skills/lean-precision/` |
| OpenCode | `~/.config/opencode/skills/lean-precision/` |

For example, run this from the directory containing the extracted `lean-precision` folder:

```sh
mkdir -p "$HOME/.claude/skills"
cp -R lean-precision "$HOME/.claude/skills/"
```

If a destination already exists, compare it and back up local edits before replacing it. Restart the tool after installation. The Antigravity IDE path above is for version 2.0; check your release's documentation if you use an older version.

OpenCode also discovers `~/.agents/skills` and `~/.claude/skills`. If installed there, no additional OpenCode copy is needed. Avoid multiple copies with the same name in a tool's search paths.

## Use

Ask: “Use Lean Precision for this session.” In Codex, invoke `$lean-precision`. In Claude Code, invoke `/lean-precision`.

The skill is available on demand after installation. Installation alone does not make it a permanent default.

## Make it the Codex default

Preserve existing instructions in `~/.codex/AGENTS.md` and add:

```markdown
Read ~/.agents/skills/lean-precision/SKILL.md at the start of every session.
Apply Lean Precision as the default communication and engineering mode unless I explicitly request otherwise.
```

Use the actual installed path if yours differs. If `CODEX_HOME` is set, edit `AGENTS.md` there. If `AGENTS.override.md` exists there, it takes precedence; update that file instead.

Remove any unconditional Caveman import from the effective global instructions. To disable its standalone skill only in Codex, add this to `config.toml` in the same Codex home directory, using an absolute path:

```toml
[[skills.config]]
path = "/absolute/path/to/caveman/SKILL.md"
enabled = false
```

If the Caveman plugin is installed, set its existing plugin entry's `enabled` value to `false`. Disable any competing automatic style hooks in Codex as well. Preserve unrelated settings and restart Codex in a fresh session.

## Sources

Installation paths follow the official [Codex](https://learn.chatgpt.com/docs/build-skills), [Claude Code](https://code.claude.com/docs/en/skills), [Antigravity](https://www.antigravity.google/docs/skills), and [OpenCode](https://opencode.ai/docs/skills) documentation. Codex defaults use [global AGENTS.md instructions](https://learn.chatgpt.com/docs/agent-configuration/agents-md).

The skill is inspired by [Ponytail](https://github.com/DietrichGebert/ponytail) and [Caveman](https://github.com/JuliusBrussee/caveman). This skill is self-contained; neither is required.


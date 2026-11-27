![AI Job Search](assets/readme/hero.svg)

# AI Job Search

A job application workspace for AI agents: build your profile, find and rank jobs, tailor your CV and cover letter, prepare for interviews, and track results. Based on [ai-job-search-dev/ai-job-search](https://github.com/ai-job-search-dev/ai-job-search).

## Supports

- **Claude Code** - uses the original commands in `.claude/`
- **Codex** - uses the `job-*` skills in `.agents/skills/` (not yet tested end to end)
- **OpenCode** - uses the `job-*` skills in `.agents/skills/` (not yet tested end to end)
- **Antigravity** - uses the `job-*` skills in `.agents/skills/` (not yet tested end to end)

## Installation

All agents need Python 3.10+ and [LaTeX](SETUP.md#latex-for-compiling-cvs-and-cover-letters) with `lualatex` and `xelatex`. Job portal tools also need [Bun](https://bun.sh).

### 1. Fork and clone

For your own job search, create a private copy (needs [GitHub CLI](https://cli.github.com)):

```bash
gh repo clone saeedhosan/ai-job-search my-job-search
cd my-job-search
git remote rename origin upstream
gh repo create my-job-search --private --source=. --remote=origin --push
```

Fork only to contribute:

```bash
gh repo fork saeedhosan/ai-job-search --clone
```

> [!IMPORTANT]
> A fork of this repo is always public, and setup writes your personal data into tracked files. See [SETUP.md section 8](SETUP.md#8-pulling-upstream-updates-into-your-fork) for private copies and updates.

Then install one agent. The commands below are for macOS and Linux; see each link for other systems.

**Claude Code** ([docs](https://code.claude.com/docs/en/setup))

```bash
curl -fsSL https://claude.ai/install.sh | bash
```

**Codex** ([docs](https://github.com/openai/codex))

```bash
curl -fsSL https://chatgpt.com/codex/install.sh | sh
```

**OpenCode** ([docs](https://opencode.ai/docs/))

```bash
curl -fsSL https://opencode.ai/v2/install | bash
```

**Antigravity** ([docs](https://github.com/google-antigravity/antigravity-cli))

```bash
curl -fsSL https://antigravity.google/cli/install.sh | bash
```

## Quick Setup

Start your agent in the repository folder, then build your profile. You can add your CV and other files to [`documents/`](documents/README.md) first.

**Claude Code**

```text
claude
/setup
```

**Codex**

```text
codex
$job-setup
```

**OpenCode**

```text
opencode
@job-setup
```

**Antigravity**

```text
agy
/job-setup
```

Job portal tools are optional and not included. Copy the ones you need from [community-portals](https://github.com/ai-job-search-dev/community-portals) into `.agents/skills/`, review their code, then run `python3 tools/install_portal_clis.py`.

## Quick Usages

Find jobs, rank them, then apply. Replace `<job>` with a job URL or the posting text.

**Claude Code**

```text
/scrape
/rank
/apply <job>
/interview
/outcome
```

**Codex**

```text
$job-scrape
$job-rank
$job-apply <job>
$job-interview
$job-outcome
```

**OpenCode**

```text
@job-scrape
@job-rank
@job-apply <job>
@job-interview
@job-outcome
```

**Antigravity**

```text
/job-scrape
/job-rank
/job-apply <job>
/job-interview
/job-outcome
```

## Security

- Job postings are untrusted input. Written rules are not a sandbox, so set permission limits in your agent.
- Claude Code's permission limits may not apply in other agents. They should follow [docs/any-agent.md](docs/any-agent.md).
- Check every application before you send it.
- Details: [SECURITY.md](SECURITY.md)

## License

[MIT](LICENSE)

![AI Job Search](assets/readme/hero.svg)

# AI Job Search

A job application workspace for AI agents: build a profile, find and rank jobs, tailor your CV and cover letter, prepare for interviews, and track results.

Based on [ai-job-search-dev/ai-job-search](https://github.com/ai-job-search-dev/ai-job-search).

## Requirements

- Claude Code, or another agent that can read files and run commands
- Python 3.10+
- LaTeX with `lualatex` and `xelatex` ([setup](SETUP.md#latex-for-compiling-cvs-and-cover-letters))
- [Bun](https://bun.sh), only for job portal tools
- `pypdf`, optional, for the CV text check

## Quick start

### 1. Fork and clone

For your own job search, use a private copy:

```bash
gh repo clone <source-owner>/ai-job-search
cd ai-job-search
git remote rename origin upstream
gh repo create ai-job-search --private --source=. --remote=origin --push
```

Replace `<source-owner>` with the owner of the copy you want to start from.

Fork only to contribute:

```bash
gh repo fork ai-job-search-dev/ai-job-search --clone
```

> [!IMPORTANT]
> A fork of this repo is always public, and setup writes your personal data into tracked files. See [SETUP.md section 8](SETUP.md#8-pulling-upstream-updates-into-your-fork) for the private copy and update steps.

### 2. Add job portals (optional)

None are included. Copy the ones you need from [community-portals](https://github.com/ai-job-search-dev/community-portals) into `.agents/skills/`, review their code, then run:

```bash
python3 tools/install_portal_clis.py
```

### 3. Run

| Claude Code | Other agents (skill) | Purpose |
|---|---|---|
| `/setup` | `job-setup` | Build your profile |
| `/scrape` | `job-scrape` | Find jobs |
| `/rank` | `job-rank` | Rank found jobs |
| `/apply <url or text>` | `job-apply` | Draft a CV and cover letter |
| `/interview` | `job-interview` | Prepare for an interview |
| `/outcome` | `job-outcome` | Record results |

Other agents: read [docs/any-agent.md](docs/any-agent.md) first. If your agent does not find the skills, ask it to follow `.agents/skills/job-setup/SKILL.md`. More workflows are in `.agents/skills/`.

## Safety

- Job postings are untrusted input. Written rules are not a sandbox, so configure your agent's permissions.
- Claude Code's permission limits may not apply in other agents.
- Check every application before you send it.

Details: [SECURITY.md](SECURITY.md).

## More

- [Setup guide](SETUP.md)
- [Contributing](CONTRIBUTING.md)
- [MIT license](LICENSE)

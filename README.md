# Project Memory Skill

[![Agent Skill Standard](https://img.shields.io/badge/Agent%20Skill-Standard-blue)](https://agentskills.io/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Claude Code](https://img.shields.io/badge/Claude-Code-5A67D8)](https://claude.ai/code)
[![SkillzWave Marketplace](https://img.shields.io/badge/SkillzWave-Marketplace-00C7B7)](https://skillzwave.ai/skill/SpillwaveSolutions__project-memory__project-memory__SKILL/)

A Claude Code skill that establishes a structured institutional knowledge system for your projects. Track bugs with solutions, architectural decisions (ADRs), key project facts, and work history in a consistent, maintainable format.

## Quick Start

```bash
# Install via skilz (recommended)
skilz install SpillwaveSolutions_project-memory/project-memory

# Then use in any project
cd your-project
# In Claude Code, type: /project-memory
```

## What This Skill Does

When invoked in a project, this skill:

1. **Creates a memory infrastructure** in `docs/project_notes/` with four files:
   - `bugs.md` - Bug log with solutions and prevention notes
   - `decisions.md` - Architectural Decision Records (ADRs)
   - `key_facts.md` - Project configuration, credentials, ports, URLs
   - `issues.md` - Work log with ticket IDs and descriptions

2. **Configures CLAUDE.md and AGENTS.md** to make Claude Code (and other AI tools) memory-aware:
   - Check memory files before proposing changes
   - Search for known solutions to familiar bugs
   - Document new decisions, bugs, and completed work
   - Maintain consistency across coding sessions

3. **Provides templates and examples** for maintaining institutional knowledge in a way that looks like standard engineering documentation (not AI artifacts).

## Installation

There are four installation options depending on your needs.

### Option 1: Skilz Universal Installer (Recommended)

The recommended way to install this skill across different AI coding agents is using the **skilz** universal installer. This skill supports the [Agent Skill Standard](https://agentskills.io/), which means it works with 14+ coding agents including Claude Code, OpenAI Codex, Cursor, and Gemini.

#### Install Skilz

```bash
pip install skilz
```

#### Git URL Options

You can use either `-g` or `--git` with HTTPS or SSH URLs:

```bash
# HTTPS URL
skilz install -g https://github.com/SpillwaveSolutions/project-memory

# SSH URL
skilz install --git git@github.com:SpillwaveSolutions/project-memory.git
```

#### Claude Code

Install to user home (available in all projects):
```bash
skilz install -g https://github.com/SpillwaveSolutions/project-memory
```

Install to current project only:
```bash
skilz install -g https://github.com/SpillwaveSolutions/project-memory --project
```

#### OpenCode

Install for [OpenCode](https://opencode.ai):
```bash
skilz install -g https://github.com/SpillwaveSolutions/project-memory --agent opencode
```

Project-level install:
```bash
skilz install -g https://github.com/SpillwaveSolutions/project-memory --project --agent opencode
```

#### Gemini

Project-level install for Gemini:
```bash
skilz install -g https://github.com/SpillwaveSolutions/project-memory --agent gemini
```

#### OpenAI Codex

Install for OpenAI Codex:
```bash
skilz install -g https://github.com/SpillwaveSolutions/project-memory --agent codex
```

Project-level install:
```bash
skilz install -g https://github.com/SpillwaveSolutions/project-memory --project --agent codex
```

#### Install from SkillzWave Marketplace

```bash
# Claude to user home dir ~/.claude/skills
skilz install SpillwaveSolutions_project-memory/project-memory

# Claude skill in project folder ./claude/skills
skilz install SpillwaveSolutions_project-memory/project-memory --project

# OpenCode install to user home dir ~/.config/opencode/skills
skilz install SpillwaveSolutions_project-memory/project-memory --agent opencode

# OpenCode project level
skilz install SpillwaveSolutions_project-memory/project-memory --agent opencode --project

# OpenAI Codex install to user home dir ~/.codex/skills
skilz install SpillwaveSolutions_project-memory/project-memory --agent codex

# OpenAI Codex project level ./.codex/skills
skilz install SpillwaveSolutions_project-memory/project-memory --agent codex --project

# Gemini CLI (project level) -- only works with project level
skilz install SpillwaveSolutions_project-memory/project-memory --agent gemini
```

See [skill Listing](https://skillzwave.ai/skill/SpillwaveSolutions__project-memory__project-memory__SKILL/) for installation details for 14+ different coding agents.

#### Other Supported Agents

Skilz supports 14+ coding agents including Windsurf, Qwen Code, Aidr, and more. For the full list of supported platforms, visit:

- [SkillzWave Platforms](https://skillzwave.ai/platforms/)
- [skilz-cli GitHub Repository](https://github.com/SpillwaveSolutions/skilz-cli)

[SkillzWave - Largest Agentic Marketplace for AI Agent Skills](https://skillzwave.ai/) | [SpillWave - Leaders in AI Agent Development](https://spillwave.com/)

### Option 2: Global Installation (Manual)

Install once in your Claude Code home directory to make the skill available across **all projects**:

```bash
# Create the skills directory if it doesn't exist
mkdir -p ~/.claude/skills

# Clone or copy the skill to your skills directory
cp -r project-memory ~/.claude/skills/

# Verify installation
ls ~/.claude/skills/project-memory
```

**When to use:** You want this skill available for all your projects without reinstalling.

### Option 3: Project-Specific Installation (Manual)

Install in a specific project's `.claude/skills/` directory:

```bash
# Navigate to your project
cd /path/to/your/project

# Create local skills directory
mkdir -p .claude/skills

# Clone or copy the skill
cp -r /path/to/project-memory .claude/skills/

# Verify installation
ls .claude/skills/project-memory
```

**When to use:** You only want this skill available for a specific project.

### Option 4: Multi-Project Installation (Workspace)

Install above a workspace directory to share across multiple related projects:

```bash
# Navigate to your workspace directory (parent of multiple projects)
cd ~/workspace

# Create shared skills directory
mkdir -p .claude/skills

# Clone or copy the skill
cp -r /path/to/project-memory .claude/skills/

# Verify installation
ls .claude/skills/project-memory
```

**When to use:** You have multiple projects in a workspace and want to share the skill without global installation.

**Example structure:**
```
~/workspace/
├── .claude/
│   └── skills/
│       └── project-memory/    # Shared across all projects below
├── project-a/
├── project-b/
└── project-c/
```

## How to Use

### First-Time Setup in a Project

1. Navigate to your project directory
2. Invoke the skill in Claude Code:
   ```
   /project-memory
   ```
3. The skill will:
   - Create `docs/project_notes/` directory
   - Initialize the four memory files with templates
   - Update (or create) `CLAUDE.md` with memory protocols
   - Optionally update `AGENTS.md` if it exists

### Daily Usage

Once set up, Claude Code will automatically:

- **Check memory files** before proposing architectural changes
- **Search bugs.md** when you encounter errors
- **Reference key_facts.md** for project configuration

You can also explicitly request updates:

```
Add this CORS fix to our bug log
```

```
Document the decision to use FastAPI in decisions.md
```

```
Update key_facts.md with the new database connection string
```

```
Log this completed ticket in issues.md
```

## File Structure After Setup

```
your-project/
├── docs/
│   └── project_notes/
│       ├── bugs.md         # Bug log with solutions
│       ├── decisions.md    # Architectural Decision Records
│       ├── key_facts.md    # Project configuration
│       └── issues.md       # Work log
├── CLAUDE.md              # Updated with memory protocols
└── AGENTS.md              # Updated with memory protocols (if exists)
```

## Memory File Formats

### bugs.md - Bug Log
```markdown
### 2025-01-15 - Docker Architecture Mismatch
- **Issue**: Container failing to start with "exec format error"
- **Root Cause**: Built on ARM64 Mac but deploying to AMD64 Cloud Run
- **Solution**: Added `--platform linux/amd64` to docker build
- **Prevention**: Always specify platform in Dockerfile
```

### decisions.md - Architectural Decisions
```markdown
### ADR-001: Use Workload Identity Federation (2025-01-10)

**Context:**
- Need secure authentication from GitHub Actions to GCP

**Decision:**
- Use Workload Identity Federation instead of service account keys

**Alternatives Considered:**
- Service account JSON keys → Rejected: security risk

**Consequences:**
- ✅ More secure (no long-lived credentials)
- ❌ Slightly more complex initial setup
```

### key_facts.md - Project Configuration

**⚠️ SECURITY WARNING:** Never store passwords, API keys, or credentials in `key_facts.md`. Only store non-sensitive reference information like hostnames, ports, client names, project IDs, and account names. Store secrets in `.env` (excluded via `.gitignore`), password managers, or secrets management systems.

```markdown
### Database Configuration

**AlloyDB Cluster:**
- Cluster Name: `prod-cluster`
- Private IP: `10.0.0.5`
- Port: `5432`
- Database Name: `contacts`

**Connection:**
- Use AlloyDB Auth Proxy for local development
- Proxy command: `./alloydb-auth-proxy "projects/..."`
- Credentials: Stored in `.env` file (not in git)
```

### issues.md - Work Log
```markdown
### 2025-01-15 - PROJ-123: Implement Contact API
- **Status**: Completed
- **Description**: Created FastAPI endpoints for contact CRUD
- **URL**: https://jira.company.com/browse/PROJ-123
- **Notes**: Added unit tests, coverage at 85%
```

## Verification

After installation, verify the skill is available:

1. Open Claude Code in any project
2. Type `/` to see available skills
3. You should see `project-memory` in the list

Or check manually:

```bash
# For global installation
ls ~/.claude/skills/project-memory/SKILL.md

# For project-specific installation
ls .claude/skills/project-memory/SKILL.md

# For workspace installation
ls ../.claude/skills/project-memory/SKILL.md  # From inside a project
```

## Security Best Practices

### ⚠️ Critical: Never Store Secrets in Version Control

The `key_facts.md` file is designed to store **non-sensitive** project reference information only. This file is typically committed to version control and should NEVER contain:

**❌ NEVER store in key_facts.md or any git-tracked file:**
- Passwords or passphrases
- API keys or authentication tokens
- Service account JSON keys or credentials
- Database passwords
- OAuth client secrets
- Private keys or certificates
- Session tokens
- Any secret values from environment variables

**✅ SAFE to store in key_facts.md:**
- Database hostnames, ports, and cluster names
- Client names and project identifiers
- JIRA project keys and Confluence space names
- AWS account names and profile names (e.g., "dev", "staging", "prod")
- API endpoint URLs (public URLs only)
- Service account email addresses (not the keys!)
- GCP project IDs and region names
- Docker registry names
- Environment names and deployment targets

**✅ WHERE to store sensitive credentials:**
- **`.env` files** - Excluded via `.gitignore`, used for local development
- **Password managers** - 1Password, LastPass, Bitwarden, etc.
- **Secrets managers** - AWS Secrets Manager, GCP Secret Manager, HashiCorp Vault, Azure Key Vault
- **CI/CD environment variables** - GitHub Secrets, GitLab CI/CD Variables, etc.
- **Platform credential stores** - Kubernetes Secrets, Cloud Run Secret Manager integration

**✅ VERIFICATION steps before committing:**
1. Run `git status` to see what will be committed
2. Verify `.env`, `credentials.json`, and other sensitive files are in `.gitignore`
3. Never use `git add .` blindly - review each file being staged
4. Use `git diff --cached` to review staged changes before committing
5. Consider using tools like `git-secrets` or `gitleaks` to prevent credential leaks

**Important:** Even in private repositories, never commit clear-text passwords or authentication keys. Private repos can become public, be forked, or accessed by unauthorized users.

## Features

### Memory-Aware Protocols

Once set up, Claude Code will:

- ✅ Check `decisions.md` before proposing architectural changes
- ✅ Search `bugs.md` for known solutions to errors
- ✅ Reference `key_facts.md` for project configuration
- ✅ Log completed work in `issues.md`
- ✅ Document new bugs, decisions, and facts as they arise

### Style Guidelines

All memory files follow these principles:

- **Bullet lists** over tables (simpler to edit)
- **Concise entries** (1-3 lines for descriptions)
- **Always dated** (YYYY-MM-DD format)
- **Include URLs** (for tickets, docs, monitoring)
- **Manual cleanup** (periodically remove old entries)

### Cross-Tool Compatibility

The memory system works across different AI coding tools:

- Claude Code (via CLAUDE.md)
- Cursor (via .cursor/rules or CLAUDE.md)
- GitHub Copilot (via AGENTS.md or .github/copilot-instructions.md)
- Other tools that read project configuration files

## Why Use This Skill?

**Without project memory:**
- Repeat the same bugs/solutions across sessions
- Propose architectures that conflict with past decisions
- Ask the user repeatedly for database credentials, API keys, ports
- Lose context when switching between projects or AI tools

**With project memory:**
- Remember and apply known bug solutions instantly
- Maintain architectural consistency across sessions
- Reference documented facts instead of assumptions
- Preserve institutional knowledge across team members and tools

## Real-World Impact: Pattern Recognition in Action

### Example 1: Bug Resolution - Infrastructure State Drift

**The Scenario:**
1. **Oct 20** - Claude Code encounters Pulumi state drift error during deployment
2. **Investigation** - 45 minutes debugging, trying various solutions
3. **Solution Found** - `pulumi refresh --yes` resolves the state inconsistency
4. **Documentation** - Logged as BUG-017 and BUG-018 in bugs.md, decision documented in ADR-016
5. **Oct 22** - Same state drift error occurs during a new deployment

**Without Project Memory:**
- Claude Code debugs from scratch (again)
- 30-60 minutes of investigation
- Risk of trying wrong solutions first
- Possible production delay
- User frustration: "Didn't we solve this already?"

**With Project Memory:**
```
Claude Code: Searching bugs.md for "state drift"...
Found: BUG-018 - Pulumi State Drift Error
Known solution: pulumi refresh --yes
Applying fix... Done in 2 minutes.
Reference: See ADR-016 for why this works.
```

**Result:**
- ✅ Instant recognition: "This is BUG-018"
- ✅ Known solution applied immediately
- ✅ 5 minutes instead of 45 minutes
- ✅ References explain why this works (ADR-016)

**Knowledge Compound Interest:** Every bug solved and documented makes future work exponentially faster.

### Example 2: Architectural Consistency - Avoiding Duplicate Dependencies

**The Scenario:**
1. **Week 1** - Team evaluates charting libraries for scatter plots
2. **Decision** - Selected D3.js for all visualizations (lightweight, flexible, already in dependencies)
3. **Documentation** - Logged as ADR-012 in decisions.md with rationale
4. **Week 4** - New feature requires a bar chart visualization

**Without Project Memory:**
```
User: "Add a bar chart to the dashboard"
Claude Code: "I'll add Chart.js for the bar chart visualization."
[Adds Chart.js to package.json - now we have D3.js AND Chart.js]
Result: Bundle size +85KB, inconsistent chart styling, duplicate dependencies
```

**With Project Memory:**
```
User: "Add a bar chart to the dashboard"
Claude Code: Checking decisions.md for visualization decisions...
Found: ADR-012 - Use D3.js for all charts
Claude Code: "I'll implement the bar chart using D3.js to maintain consistency with ADR-012."
[Uses existing D3.js dependency]
Result: No new dependencies, consistent styling, smaller bundle
```

**Result:**
- ✅ Maintains architectural consistency
- ✅ Avoids dependency bloat
- ✅ Ensures consistent user experience
- ✅ Faster development (reuse existing patterns)

**Key Insight:** Remembering past decisions prevents architectural drift and keeps the codebase cohesive.

### Example 3: The "Didn't We Fix This?" Problem

**The Reality of Long-Running Projects:**

Many developers (and AI code assistants) encounter the same bugs months apart and completely forget the solution:

**Month 1:**
```
Error: CORS policy blocked request from localhost:3000
[2 hours of debugging]
Solution: Add proxy configuration to package.json
```

**Month 6:**
```
Error: CORS policy blocked request from localhost:3000
Developer: "This looks familiar... how did we fix this?"
[Searches old commits, checks Stack Overflow again]
[1 hour to re-discover the proxy config solution]
```

**With Project Memory:**
```
Error: CORS policy blocked request from localhost:3000
Claude Code: Searching bugs.md for "CORS"...
Found: BUG-003 - CORS Blocked in Local Development
Solution: proxy config in package.json
Applied in 5 minutes.
```

**The Code Agent Memory Problem:**

AI code assistants don't remember previous sessions. Without documentation:
- Each new chat session starts from zero knowledge
- Every bug feels like the first time
- Solutions are "rediscovered" repeatedly
- No learning accumulates over time

**With project memory, the code agent becomes progressively smarter:**
- First encounter: 2 hours to solve → documented in bugs.md
- Second encounter: 5 minutes (reads bugs.md)
- Third encounter: 2 minutes (pattern now familiar)
- Fourth encounter: Preventative advice (suggests avoiding the issue)

This is **knowledge compound interest** - your project gets easier to maintain over time, not harder.

## Skill File Structure

```
project-memory/
├── SKILL.md                    # Main skill instructions for Claude
├── CLAUDE.md                   # This repository's Claude guidance
├── README.md                   # This file
└── references/                 # Templates for memory files
    ├── bugs_template.md
    ├── decisions_template.md
    ├── key_facts_template.md
    └── issues_template.md
```

## Design Philosophy

1. **Looks like standard engineering docs** - Using `docs/project_notes/` instead of `memory/` makes it appear as normal engineering organization, not AI-specific tooling.

2. **Prefer simplicity** - Bullet lists over tables, concise over exhaustive, manual cleanup over automation.

3. **Document what matters** - Focus on recurring bugs, important decisions, and frequently-needed facts.

4. **Enable collaboration** - Works across AI tools, readable by humans, version-controllable with git.

## Examples

### Setting Up Memory in a New Project

```bash
cd ~/projects/my-new-app
claude code
```

In Claude Code:
```
/project-memory
```

Claude will create the memory infrastructure and configure CLAUDE.md.

### Documenting a Bug Fix

```
I just fixed a bug where the database connection pool was exhausted.
Add it to bugs.md with the solution.
```

### Checking for Existing Decisions

```
I'm thinking about using SQLAlchemy for migrations.
Check if we already have a decision about this.
```

Claude will search `decisions.md` and apply existing choices.

### Updating Project Facts

```
Update key_facts.md with the new staging environment URL:
https://staging-api.company.com
```

## Maintenance

Memory files are **manually maintained**:

- **bugs.md** - Remove very old entries (6+ months) that are no longer relevant
- **decisions.md** - Keep all decisions (they're lightweight and provide historical context)
- **key_facts.md** - Update when project configuration changes
- **issues.md** - Archive completed work (3+ months old)

## Integration with Other Skills

This skill complements other Claude Code skills:

- **requirements-documenter** - Requirements inform ADRs in decisions.md
- **root-cause-debugger** - Bug diagnosis results documented in bugs.md
- **code-quality-reviewer** - Quality standards documented in decisions.md
- **docs-sync-editor** - Code changes trigger updates to key_facts.md

## Troubleshooting

### Skill not appearing in Claude Code

**Check installation location:**
```bash
# Global installation
ls ~/.claude/skills/project-memory/SKILL.md

# Project-specific installation
ls .claude/skills/project-memory/SKILL.md
```

**Ensure SKILL.md exists:**
The skill must have a `SKILL.md` file with proper frontmatter:
```yaml
---
name: project-memory
description: Set up and maintain a structured project memory system...
---
```

### Memory files not being created

**Verify you're in a project directory:**
The skill creates files in the current working directory's `docs/project_notes/` folder.

**Check permissions:**
Ensure you have write permissions in the project directory.

### Claude not checking memory files

**Verify CLAUDE.md was updated:**
```bash
grep "Project Memory System" CLAUDE.md
```

The "Project Memory System" section should be present with complete protocols.

## Contributing

To improve this skill:

1. Update templates in `references/` directory
2. Enhance `SKILL.md` with new capabilities
3. Update `CLAUDE.md` with workflow changes
4. Test in a sample project

## License

This skill is part of the Claude Code skills ecosystem and follows standard usage guidelines for Claude Code extensions.

## Support

For issues or questions:
- Check the troubleshooting section above
- Review `SKILL.md` for detailed skill instructions
- Review `CLAUDE.md` for repository-specific guidance
- Consult Claude Code documentation at https://docs.claude.com/en/docs/claude-code

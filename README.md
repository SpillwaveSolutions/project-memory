# Project Memory Skill

A Claude Code skill that establishes a structured institutional knowledge system for your projects. Track bugs with solutions, architectural decisions (ADRs), key project facts, and work history in a consistent, maintainable format.

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

There are three installation options depending on your needs:

### Option 1: Global Installation (Recommended)

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

### Option 2: Project-Specific Installation

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

### Option 3: Multi-Project Installation (Workspace)

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

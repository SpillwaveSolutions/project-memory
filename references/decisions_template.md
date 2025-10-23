# Architectural Decisions Template

This file demonstrates the format for logging architectural decisions (ADRs). Use bullet lists for clarity.

## Format

Each decision should include:
- Date and ADR number
- Context (why the decision was needed)
- Decision (what was chosen)
- Alternatives considered
- Consequences (trade-offs, implications)

## Example Entries

### ADR-001: Use Workload Identity Federation for GitHub Actions (2025-01-10)

**Context:**
- Need secure authentication from GitHub Actions to GCP
- Service account keys are deprecated and considered insecure
- Want to avoid managing long-lived credentials

**Decision:**
- Use Workload Identity Federation (WIF) for GitHub Actions authentication
- Configure via `WIF_PROVIDER` and `WIF_SERVICE_ACCOUNT` secrets

**Alternatives Considered:**
- Service account JSON keys → Rejected: security risk, manual rotation required
- Environment-specific credentials → Rejected: harder to manage across repos

**Consequences:**
- ✅ More secure (no long-lived credentials)
- ✅ Automatic credential rotation
- ✅ Better audit trail
- ❌ Slightly more complex initial setup
- ❌ Requires GitHub OIDC support

### ADR-002: Use Alembic for Database Migrations (2025-01-12)

**Context:**
- Need version control for database schema changes
- Multiple developers working on database schema
- Want to avoid manual SQL scripts and migration conflicts

**Decision:**
- Use Alembic as the database migration tool
- Store migrations in `alembic/versions/` directory
- Use auto-generate feature for model changes

**Alternatives Considered:**
- Raw SQL scripts → Rejected: no versioning, error-prone
- Flask-Migrate → Rejected: too tied to Flask framework
- Django migrations → Rejected: using FastAPI, not Django

**Consequences:**
- ✅ Version-controlled schema changes
- ✅ Automatic migration generation from models
- ✅ Easy rollback capability
- ❌ Learning curve for team
- ❌ Must remember to generate migrations after model changes

### ADR-003: Use AlloyDB Instead of Cloud SQL (2025-01-15)

**Context:**
- Need PostgreSQL-compatible database in GCP
- Require high availability and automatic backups
- Performance-critical application with complex queries

**Decision:**
- Use AlloyDB for PostgreSQL instead of Cloud SQL
- Configure with automated backups and point-in-time recovery

**Alternatives Considered:**
- Cloud SQL PostgreSQL → Rejected: slower query performance
- Self-managed PostgreSQL on GCE → Rejected: high operational overhead
- Firestore → Rejected: need relational data model and SQL

**Consequences:**
- ✅ Better query performance (2-4x faster than Cloud SQL)
- ✅ PostgreSQL compatibility
- ✅ Managed service (automated backups, HA)
- ❌ Higher cost than Cloud SQL
- ❌ Newer service, less community documentation

## Tips

- Number decisions sequentially (ADR-001, ADR-002, etc.)
- Always include date for context
- Be honest about trade-offs (use ✅ and ❌)
- Keep alternatives brief but clear
- Update decisions if they're revisited/changed
- Focus on "why" not "how" (implementation details go elsewhere)

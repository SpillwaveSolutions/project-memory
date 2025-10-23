# Issues/Work Log Template

This file demonstrates the format for logging work completed on tickets. Keep it simple - just enough to remember what was done. Full details live in Jira/GitHub.

## Format

Each entry should include:
- Date (YYYY-MM-DD)
- Ticket ID
- Brief description (1-2 lines)
- URL to ticket (if available)
- Status (optional: completed, in-progress, blocked)

Use bullet lists for simplicity. This is NOT a replacement for your ticket system - it's a quick reference log.

## Example Entries

### 2025-01-15 - PROJ-123: Implement Contact API
- **Status**: Completed
- **Description**: Created FastAPI endpoints for contact CRUD operations with validation
- **URL**: https://jira.company.com/browse/PROJ-123
- **Notes**: Added unit tests, coverage at 85%

### 2025-01-16 - PROJ-124: Fix Docker Build Issues
- **Status**: Completed
- **Description**: Fixed architecture mismatch for Cloud Run deployment
- **URL**: https://jira.company.com/browse/PROJ-124
- **Notes**: See bugs.md for details on the fix

### 2025-01-18 - PROJ-125: Database Migration to AlloyDB
- **Status**: Completed
- **Description**: Migrated from Cloud SQL to AlloyDB with Pulumi infrastructure code
- **URL**: https://jira.company.com/browse/PROJ-125
- **Notes**: Multi-phase migration completed over 3 days

### 2025-01-20 - GH-45: Add OAuth2 Authentication
- **Status**: In Progress
- **Description**: Implementing OAuth2 flow with Google provider
- **URL**: https://github.com/company/repo/issues/45
- **Notes**: Backend complete, frontend integration pending

### 2025-01-22 - PROJ-130: Performance Optimization
- **Status**: Blocked
- **Description**: Optimize slow queries in contact search endpoint
- **URL**: https://jira.company.com/browse/PROJ-130
- **Notes**: Waiting for DBA review of proposed indexes

## Alternative Format (Grouped by Week)

### Week of 2025-01-15

**Completed:**
- PROJ-123: Contact API implementation → https://jira.company.com/browse/PROJ-123
- PROJ-124: Docker build fix → https://jira.company.com/browse/PROJ-124

**In Progress:**
- PROJ-125: AlloyDB migration (phase 2 of 3)

### Week of 2025-01-22

**Completed:**
- PROJ-125: AlloyDB migration completed → https://jira.company.com/browse/PROJ-125
- GH-45: OAuth2 backend done → https://github.com/company/repo/issues/45

**Blocked:**
- PROJ-130: Query optimization (waiting on DBA) → https://jira.company.com/browse/PROJ-130

## Tips

- Keep descriptions brief (1-2 lines max)
- Always include ticket URL for easy reference
- Update status if work gets blocked or resumed
- Optional: Group by week or sprint for better organization
- Don't duplicate ticket details - link to source of truth
- Clean out very old entries periodically (3+ months)
- Include both Jira and GitHub tickets as appropriate

# Bug Log Template

This file demonstrates the format for logging bugs and their solutions. Keep entries brief and chronological.

## Format

Each bug entry should include:
- Date (YYYY-MM-DD)
- Brief description of the bug/issue
- Solution or fix applied
- Any prevention notes (optional)

Use bullet lists for simplicity. Older entries can be manually removed when they become irrelevant.

## Example Entries

### 2025-01-15 - Docker Architecture Mismatch
- **Issue**: Container failing to start with "exec format error"
- **Root Cause**: Built on ARM64 Mac but deploying to AMD64 Cloud Run
- **Solution**: Added `--platform linux/amd64` to docker build command
- **Prevention**: Always specify platform in Dockerfile and build scripts

### 2025-01-20 - Cloud Scheduler HTTPS Requirement
- **Issue**: Cloud Scheduler jobs failing with "URL must use HTTPS"
- **Root Cause**: Forgot Cloud Run URLs require HTTPS by default
- **Solution**: Updated all scheduler job URLs from http:// to https://
- **Prevention**: Remember GCP services enforce HTTPS; check URLs in infrastructure code

### 2025-01-22 - Database Connection Pool Exhaustion
- **Issue**: API returning 500 errors under load
- **Root Cause**: Connection pool size too small (default 5)
- **Solution**: Increased pool_size to 20 and max_overflow to 10 in SQLAlchemy config
- **Prevention**: Load test APIs before production deployment

## Tips

- Keep descriptions under 2-3 lines
- Focus on what was learned, not exhaustive details
- Include enough context for future reference
- Date entries so you know how recent the issue is
- Periodically clean out very old entries (6+ months)

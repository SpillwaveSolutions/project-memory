# Key Facts Template

This file demonstrates the format for storing project constants, configuration, and frequently-needed **non-sensitive** information. Organize by category using bullet lists.

## ⚠️ SECURITY WARNING: What NOT to Store Here

**NEVER store passwords, API keys, or sensitive credentials in this file.** This file is typically committed to version control and should only contain non-sensitive reference information.

**❌ NEVER store:**
- Passwords or passphrases
- API keys or authentication tokens
- Service account JSON keys or credentials
- Database passwords
- OAuth client secrets
- Private keys or certificates
- Session tokens
- Any secret values from environment variables

**✅ SAFE to store:**
- Database hostnames, ports, and cluster names
- Client names and project identifiers
- JIRA project keys and Confluence space names
- AWS/GCP account names and profile names
- API endpoint URLs (public URLs only)
- Service account email addresses (not the keys!)
- GCP project IDs and region names
- Docker registry names
- Environment names and deployment targets

**Where to store secrets:**
- `.env` files (excluded via `.gitignore`)
- Password managers (1Password, LastPass, Bitwarden)
- Secrets managers (AWS Secrets Manager, GCP Secret Manager, HashiCorp Vault)
- CI/CD environment variables (GitHub Secrets, GitLab Variables)
- Platform credential stores (Kubernetes Secrets, Cloud Run)

## Format

Organize information into logical categories:
- GCP/Cloud configuration
- Database connection details (hostnames, ports, cluster names)
- API endpoints (URLs only, not credentials)
- Local development setup (ports, service names)
- Important URLs
- Service accounts and permissions (emails and roles, not keys)

Use bullet lists for simplicity and easy scanning.

## Example Structure

### GCP Project Information

**Current Project:**
- Project ID: `my-company-prod`
- Project Number: `123456789012`
- Region: `us-central1`
- Zone: `us-central1-a`

**Old Project (Deprecated):**
- Project ID: `my-company-dev-old`
- Migration Date: 2025-01-10
- Status: Archived, do not use

### Database Configuration

**AlloyDB Cluster:**
- Cluster Name: `prod-cluster`
- Instance Name: `prod-primary`
- Region: `us-central1`
- Private IP: `10.0.0.5`
- Port: `5432`
- Database Name: `contacts`

**Connection:**
- Use AlloyDB Auth Proxy for local development
- Proxy command: `./alloydb-auth-proxy "projects/my-company-prod/locations/us-central1/clusters/prod-cluster/instances/prod-primary"`
- Local port: `5432`

**Authentication:**
- Service Account (email only): `alloydb-client@my-company-prod.iam.gserviceaccount.com`
- Service Account Key: Stored in `.env` as `GOOGLE_APPLICATION_CREDENTIALS` (not in git!)
- Connection String Template: `postgresql://user:${DB_PASSWORD}@localhost:5432/contacts`
- Password Location: Stored in `.env` file (excluded via `.gitignore`)

### API Configuration

**Backend API:**
- Production URL: `https://api.mycompany.com`
- Staging URL: `https://api-staging.mycompany.com`
- Local Development: `http://localhost:8000`

**Authentication:**
- OAuth Client ID (public): `123456789-abcdefg.apps.googleusercontent.com`
- OAuth Client Secret: Stored in GCP Secret Manager as `oauth-client-secret` (not in git!)
- Local Development Secret: Stored in `.env` as `OAUTH_CLIENT_SECRET` (not in git!)
- Scopes: `openid email profile`

### Local Development Ports

**Services:**
- Backend API: `8000`
- Frontend: `3000`
- AlloyDB Proxy: `5432`
- Redis: `6379`
- Prometheus: `9090`

### Service Accounts

**GitHub Actions:**
- Service Account: `github-actions@my-company-prod.iam.gserviceaccount.com`
- Roles: `roles/run.admin`, `roles/secretmanager.secretAccessor`
- WIF Pool: `projects/123456789012/locations/global/workloadIdentityPools/github-pool`

**Cloud Run Service:**
- Service Account: `cloud-run-sa@my-company-prod.iam.gserviceaccount.com`
- Roles: `roles/alloydb.client`, `roles/secretmanager.secretAccessor`

### Important URLs

**Documentation:**
- API Docs: `https://docs.mycompany.com/api`
- Internal Wiki: `https://wiki.mycompany.com`
- Runbook: `https://wiki.mycompany.com/runbook`

**Monitoring:**
- Cloud Console: `https://console.cloud.google.com/home/dashboard?project=my-company-prod`
- Logs: `https://console.cloud.google.com/logs?project=my-company-prod`
- Monitoring: `https://console.cloud.google.com/monitoring?project=my-company-prod`

**Deployment:**
- Cloud Run Service: `https://console.cloud.google.com/run?project=my-company-prod`
- Cloud Build: `https://console.cloud.google.com/cloud-build?project=my-company-prod`
- Artifact Registry: `https://console.cloud.google.com/artifacts?project=my-company-prod`

### Infrastructure as Code

**Pulumi:**
- Stack: `prod`
- Backend: `gs://my-company-pulumi-state`
- Config Passphrase: Stored in team password manager (1Password vault: "Infrastructure")
- State: Stored in GCS bucket with versioning enabled
- Note: Never commit `Pulumi.prod.yaml` with unencrypted secrets

**Configuration:**
- Cloud Run Image: `us-central1-docker.pkg.dev/my-company-prod/app/backend:latest`
- VPC Connector: `prod-vpc-connector`
- Max Instances: `10`
- Min Instances: `1`

## Tips

- Keep entries current (update when things change)
- Remove deprecated information after migration is complete
- Include both production and development details
- Add URLs to make navigation easier
- Use consistent formatting (same structure for similar items)
- Group related information together
- Mark deprecated items clearly with dates

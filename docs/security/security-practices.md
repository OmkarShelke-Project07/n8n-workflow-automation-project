# Security Practices

## Overview

Security is a primary concern in this portfolio. All workflows follow security best practices.

## Secret Management

### Environment Variables

All sensitive information is stored in environment variables:

```env
# API Keys
OPENAI_API_KEY=
PINECONE_API_KEY=
VAPI_ACCESS_TOKEN=

# OAuth Credentials
GOOGLE_CLIENT_ID=
GOOGLE_CLIENT_SECRET=

# Resource IDs
SHEET_INVOICE_DATA_ID=
GOOGLE_DRIVE_FOLDER_ID=
```

### .gitignore

The `.gitignore` file excludes:
- `.env` files
- Credentials JSON
- Service account keys
- PEM files
- API key files

## Authentication Methods

| Service | Method | Notes |
|---------|--------|-------|
| Google | OAuth2 | Refresh tokens rotated |
| OpenAI | API Key | Stored in n8n vault |
| Pinecone | API Key | Restricted to index only |
| Vapi | Bearer Token | Short-lived |
| Slack | OAuth2 | Scope-limited |
| Facebook | Access Token | Page-scoped |

## Security Checklist

- [x] No secrets in code
- [x] Environment variables used
- [x] .gitignore configured
- [x] OAuth2 for Google services
- [x] Webhook IDs unique per workflow
- [x] No personal data in code
- [x] Minimal API permissions
- [x] Regular credential rotation

## Best Practices

1. **Never commit secrets** - Use environment variables
2. **Rotate credentials regularly** - At least every 90 days
3. **Use least privilege** - Minimal required permissions
4. **Validate inputs** - Sanitize all user inputs
5. **Log security events** - Track access and errors
6. **Encrypt in transit** - HTTPS for all API calls
7. **Encrypt at rest** - Use encrypted storage services

## Incident Response

If credentials are compromised:

1. **Immediate**: Rotate all affected credentials
2. **Investigate**: Check access logs
3. **Notify**: Inform team members
4. **Document**: Record incident and response
5. **Prevent**: Update security practices

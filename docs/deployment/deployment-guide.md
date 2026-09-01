# Deployment Guide

## Overview

This guide covers deployment options for the n8n workflows.

## Deployment Options

### 1. n8n Cloud
- Easiest setup
- Managed infrastructure
- Pay per execution
- Recommended for getting started

### 2. Self-Hosted n8n
- Full control
- Custom configurations
- Requires server management
- Better for production at scale

### 3. Docker
- Containerized deployment
- Portable across environments
- Good for development/testing
- Can be used in production

### 4. Kubernetes
- Enterprise-grade
- Highly scalable
- Complex setup
- For high-volume deployments

## Quick Start (n8n Cloud)

1. Sign up for n8n Cloud
2. Import workflow JSON
3. Configure credentials
4. Test execution
5. Activate workflow

## Docker Setup

```dockerfile
FROM n8nio/n8n:latest

# Copy workflows
COPY ./workflows /home/node/.n8n/workflows

# Set environment
ENV N8N_BASIC_AUTH_ACTIVE=true
```

## Environment Configuration

Required environment variables:

```env
# n8n Core
N8N_HOST=your-host.com
N8N_PORT=5678
N8N_PROTOCOL=https

# Database
DB_TYPE=postgresdb
DB_POSTGRESDB_HOST=localhost
DB_POSTGRESDB_DATABASE=n8n

# Execution
EXECUTIONS_DATA_PRUNE=true
EXECUTIONS_DATA_MAX_AGE=168
```

## Production Checklist

- [ ] HTTPS configured
- [ ] Database backups
- [ ] Monitoring setup
- [ ] Error alerting
- [ ] Credential rotation
- [ ] Rate limiting
- [ ] Log retention
- [ ] Performance baseline

## Monitoring

Recommended tools:
- Prometheus for metrics
- Grafana for dashboards
- n8n execution logs
- API response monitoring

## Scaling

For high-volume workflows:
- Use queue mode
- Configure worker nodes
- Implement rate limiting
- Add caching layer
- Database connection pooling

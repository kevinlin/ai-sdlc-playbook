---
inclusion: fileMatch
fileMatchPattern: 'package.json|requirements.txt|Dockerfile|docker-compose.yml'
---

# Development Environment Setup

## Local Development
- Use Node.js version specified in .nvmrc file
- Install dependencies with `npm ci` for consistent builds
- Use Docker for local database and service dependencies
- Run linting and formatting before committing changes

## Environment Variables
- Copy `.env.example` to `.env` for local development
- Never commit actual environment files
- Document all required environment variables in README
- Use different prefixes for different environments (DEV_, PROD_, etc.)

## Database Management
- Use migrations for all schema changes
- Include rollback scripts for migrations
- Seed data should be idempotent
- Backup database before major changes

## Build and Deployment
- Ensure builds are reproducible across environments
- Use multi-stage Docker builds for optimization
- Include health checks in containerized applications
- Document deployment procedures and rollback steps

## Debugging and Logging
- Use structured logging with appropriate log levels
- Include correlation IDs for request tracing
- Set up proper error monitoring and alerting
- Use debugger instead of console.log for development
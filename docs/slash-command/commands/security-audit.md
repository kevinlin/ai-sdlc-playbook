---
description: Comprehensive security audit of the current code
---

# Security Audit

Perform a comprehensive security audit of the current code and identify potential vulnerabilities.

## Security Checks

### Input Validation
- Check for SQL injection vulnerabilities
- Verify XSS attack prevention
- Validate all user inputs
- Check for command injection risks

### Authentication & Authorization
- Review authentication implementation
- Check authorization logic
- Verify session management
- Review password handling

### Data Protection
- Check for sensitive data exposure
- Verify encryption usage
- Review logging practices (no sensitive data in logs)
- Check for secure data storage

### Dependencies
- Identify outdated dependencies
- Check for known vulnerabilities
- Verify dependency integrity

### Configuration
- Review security headers
- Check CORS configuration
- Verify environment variable usage
- Review error handling (no information leakage)

## Output Format

Provide:
1. List of identified vulnerabilities (severity: critical/high/medium/low)
2. Detailed explanation of each issue
3. Recommended fixes with code examples
4. Priority order for remediation

---
inclusion: manual
---

# API Design Guidelines

## RESTful API Standards
- Use HTTP methods appropriately (GET, POST, PUT, DELETE, PATCH)
- Follow resource-based URL patterns: `/api/v1/users/{id}`
- Use plural nouns for resource collections
- Implement proper HTTP status codes
- Include API versioning in URL path

## Request/Response Format
- Use JSON for request and response bodies
- Follow consistent naming conventions (camelCase or snake_case)
- Include pagination for list endpoints
- Implement proper error response format:
```json
{
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "Invalid input provided",
    "details": ["Email is required", "Password too short"]
  }
}
```

## Authentication and Authorization
- Use JWT tokens for stateless authentication
- Implement proper token refresh mechanisms
- Use role-based access control (RBAC)
- Rate limit API endpoints to prevent abuse

## Documentation
- Use OpenAPI/Swagger for API documentation
- Include request/response examples
- Document all possible error responses
- Provide SDK or client library examples

#[[file:openapi.yml]]
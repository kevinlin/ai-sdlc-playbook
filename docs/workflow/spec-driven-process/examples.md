# Examples and Case Studies

Real-world examples demonstrating spec-driven development in action, plus lessons learned from common pitfalls.

## Complete Feature Example: User Authentication System

This example demonstrates the complete three-phase process for a foundational feature that most applications require.

### Overview

A basic user authentication system that allows users to register, login, and manage their sessions. This example shows how to spec a foundational feature with security considerations, edge cases, and clear implementation guidance.

### Phase 1: Requirements

```markdown
# User Authentication System - Requirements

## Introduction
This feature implements a secure user authentication system that allows users to create accounts, log in securely, and maintain authenticated sessions.

## Requirements

### Requirement 1: Account Registration
**User Story:** As a new user, I want to create an account with email and password, so that I can access the application's protected features.

#### Acceptance Criteria
1. WHEN user provides valid email and password THEN system SHALL create new user account
2. WHEN user provides email that already exists THEN system SHALL return appropriate error message
3. WHEN user provides invalid email format THEN system SHALL validate and reject input
4. WHEN user provides weak password THEN system SHALL enforce password strength requirements
   - Minimum 8 characters
   - At least one uppercase letter
   - At least one number
   - At least one special character

### Requirement 2: User Login
**User Story:** As a registered user, I want to log in with my credentials, so that I can access my account and protected features.

#### Acceptance Criteria
1. WHEN user provides correct email and password THEN system SHALL authenticate and create session
2. WHEN user provides incorrect credentials THEN system SHALL return authentication error
3. WHEN user attempts 5 failed logins THEN system SHALL lock account for 15 minutes
4. IF user is already logged in THEN system SHALL handle existing session appropriately

### Requirement 3: Session Management
**User Story:** As a logged-in user, I want my session to be maintained securely, so that I don't have to re-authenticate frequently while staying secure.

#### Acceptance Criteria
1. WHEN user successfully logs in THEN system SHALL create secure session token with 24-hour expiration
2. WHEN user makes authenticated requests THEN system SHALL validate session token
3. WHEN session expires THEN system SHALL require re-authentication
4. WHEN user logs out THEN system SHALL invalidate session token
```

### Phase 2: Design

```markdown
# User Authentication System - Design

## Architecture Overview
Stateless authentication using JWT tokens with secure password hashing. Components include authentication service, password service, token service, and user repository.

## System Components

### User Model
```typescript
interface User {
  id: string;
  email: string;
  passwordHash: string;
  createdAt: Date;
  lastLoginAt?: Date;
  failedLoginAttempts: number;
  lockedUntil?: Date;
}
```

### Authentication Service
```typescript
interface AuthService {
  register(email: string, password: string): Promise<User>;
  login(email: string, password: string): Promise<{ user: User; token: string }>;
  validateToken(token: string): Promise<User>;
  logout(token: string): Promise<void>;
}
```

## API Endpoints

### POST /auth/register
- **Request**: `{ email: string, password: string }`
- **Response**: `{ user: User, token: string }`
- **Errors**: 400 (validation), 409 (email exists)

### POST /auth/login
- **Request**: `{ email: string, password: string }`
- **Response**: `{ user: User, token: string }`
- **Errors**: 401 (invalid credentials), 423 (account locked)

### POST /auth/logout
- **Request**: Header: `Authorization: Bearer <token>`
- **Response**: `{ success: true }`

## Security Measures
- Passwords hashed with bcrypt (12 rounds)
- JWT tokens with 24-hour expiration
- Rate limiting: 5 attempts per 15 minutes
- Generic error messages to prevent enumeration
```

### Phase 3: Tasks

```markdown
# User Authentication System - Tasks

## Implementation Plan

### 1. Foundation Setup
- [ ] 1.1 Project structure and dependencies
  - Install bcrypt, jsonwebtoken, express-rate-limit
  - Set up TypeScript interfaces
  - Configure environment variables for JWT secret
  - _Requirements: All_

- [ ] 1.2 User model and validation
  - Create User interface and database schema
  - Implement email validation (regex pattern)
  - Create password strength validation
  - _Requirements: R1_

### 2. Core Authentication Services
- [ ] 2.1 Password service
  - Implement bcrypt password hashing
  - Create password comparison function
  - Add password strength checker
  - _Requirements: R1, R2_

- [ ] 2.2 JWT token service
  - Implement token generation with user payload
  - Create token validation and decoding
  - Add token blacklisting for logout
  - _Requirements: R2, R3_

### 3. API Endpoints
- [ ] 3.1 Registration endpoint
  - Validate email and password
  - Check for existing users
  - Hash password and create user
  - Return user data and token
  - _Requirements: R1_

- [ ] 3.2 Login endpoint
  - Validate credentials
  - Implement rate limiting
  - Handle account lockout
  - Generate and return token
  - _Requirements: R2_

- [ ] 3.3 Authentication middleware
  - Validate JWT tokens on protected routes
  - Handle token expiration
  - Add user context to requests
  - _Requirements: R3_

### 4. Testing and Security
- [ ] 4.1 Unit tests
  - Test password hashing and validation
  - Test token generation and validation
  - Test rate limiting logic
  - _Requirements: All_

- [ ] 4.2 Integration tests
  - Complete registration flow
  - Complete login flow
  - Session management scenarios
  - _Requirements: All_
```

## AI Collaboration Example

This example shows how AI reasoning can help with design decisions during the spec process.

### Design Decision: Token Storage Strategy

**Human Prompt:**
"I need to decide between storing JWT tokens in localStorage, sessionStorage, or httpOnly cookies for my authentication system. Consider security, usability, and implementation complexity."

**AI Reasoning Process:**
1. **Security Analysis**: httpOnly cookies prevent XSS attacks, localStorage/sessionStorage vulnerable to XSS
2. **Usability Comparison**: localStorage persists across browser sessions, sessionStorage clears on tab close, cookies can be configured either way
3. **Implementation Complexity**: localStorage/sessionStorage simpler client-side, httpOnly cookies require server-side session management
4. **Best Practice Research**: Industry standard favors httpOnly cookies for authentication tokens

**AI Recommendation:**
"Use httpOnly cookies with secure, sameSite attributes. While slightly more complex to implement, they provide the best security posture against XSS attacks while maintaining good usability."

**Design Decision Documentation:**
```markdown
## Token Storage Decision

**Chosen Approach**: httpOnly cookies with secure, sameSite attributes

**Rationale**:
- Security: Prevents XSS token theft
- Usability: Automatic token inclusion in requests
- Compliance: Aligns with security best practices

**Implementation**:
- Set-Cookie header with httpOnly, secure, sameSite=strict
- 24-hour expiration aligned with token expiration
- Automatic renewal on authenticated requests
```

## Common Pitfalls and Solutions

### Pitfall 1: Vague Requirements

**Problem**: "The system should be fast and user-friendly"

**Solution**: Define specific, measurable criteria
```markdown
WHEN loading the main dashboard THEN page SHALL render within 2 seconds
WHEN clicking navigation links THEN new page SHALL load within 1.5 seconds  
WHEN submitting forms THEN system SHALL provide feedback within 500ms
```

### Pitfall 2: Missing Edge Cases

**Problem**: Only specifying the "happy path"

**Solution**: Systematically consider failure scenarios
- What happens when the network fails?
- How do we handle malformed input?
- What if external services are unavailable?
- How do we manage concurrent operations?

### Pitfall 3: Technology-Specific Requirements

**Problem**: "The system must use React and Node.js"

**Solution**: Focus on functional requirements, leave technology choices to design phase
```markdown
# Better Requirements Focus
WHEN user interacts with the interface THEN system SHALL provide immediate visual feedback
WHEN displaying data lists THEN system SHALL support pagination for sets larger than 50 items
```

### Pitfall 4: Overly Complex Initial Designs

**Problem**: Trying to solve every possible future requirement in the first version

**Solution**: Design for current requirements with extension points
- Build core functionality first
- Add clear interfaces for future enhancements
- Avoid premature optimization
- Plan for iterative improvement

## Recovery Strategies

### When Requirements Are Unclear
1. Stop implementation immediately
2. Return to stakeholder conversations
3. Create specific examples and scenarios
4. Get explicit approval before proceeding

### When Design Becomes Too Complex
1. Identify the core requirements being addressed
2. Strip away non-essential features
3. Focus on simplest viable solution
4. Plan future enhancements as separate phases

### When Tasks Are Too Large
1. Break down into smaller, testable units
2. Identify dependencies more clearly
3. Create validation checkpoints
4. Ensure each task produces working code

### When AI Collaboration Fails
1. Provide more specific context
2. Break complex requests into smaller parts
3. Ask for reasoning behind suggestions
4. Validate AI output against requirements

## Success Metrics

### Indicators of Good Specs
- Requirements are testable and unambiguous
- Design addresses all requirements completely
- Tasks can be executed independently
- Implementation matches specification closely
- Stakeholders agree on delivered functionality

### Warning Signs
- Frequent clarification questions during implementation
- Major design changes after coding begins
- Requirements discovered during testing
- Stakeholder surprises at delivery
- Significant rework needed after initial implementation

## Lessons Learned

1. **Invest in Requirements Quality**: Time spent clarifying requirements saves multiples in implementation time
2. **Design for Current Needs**: Don't over-engineer for hypothetical future requirements
3. **Validate Early and Often**: Test assumptions at each phase boundary
4. **Document Decisions**: Record the reasoning behind design choices
5. **Iterate Based on Feedback**: Use real implementation experience to improve the spec process
6. **AI is a Tool, Not a Decision Maker**: Use AI for analysis and suggestions, but maintain human judgment for final decisions 
# arc42 Section 8: Crosscutting Concepts - Specific Instructions

## Section Purpose

**Why this section exists:**
Section 8 documents overarching concepts, patterns, and rules that apply across multiple building blocks. These are the "horizontal" concerns that cut across the system structure.

**Value for stakeholders:**
- Documents recurring patterns and approaches
- Shows how crosscutting concerns are addressed
- Provides consistency across the system
- Reduces redundancy in documentation
- Essential for maintaining architectural integrity
- Answers: How do we handle logging? Security? Persistence? Error handling?

**Key insight:** This is the MOST FLEXIBLE section - include only what's relevant. Remove irrelevant subsections entirely.

## Mandatory Content (ESSENTIAL)

### What MUST be included:
- **Only concepts that are actually crosscutting** in YOUR system
- **Concepts that apply to multiple building blocks**
- **Patterns and rules used consistently across the system**

### Common Crosscutting Concepts (Pick What Applies):

#### Domain Concepts
- Domain models
- Business rules and logic
- Ubiquitous language

#### Architecture and Design Patterns
- Layering
- Dependency injection
- MVC/MVVM patterns
- Repository pattern
- Factory patterns

#### User Experience (UX)
- UI layout principles
- Interaction patterns
- Accessibility guidelines
- Internationalization

#### Safety and Security
- Authentication and authorization
- Data encryption
- Input validation
- Audit logging
- Security architecture

#### Communication and Integration
- API design guidelines
- Message formats
- Communication protocols
- Integration patterns

#### Persistence
- Database access strategy
- Transaction handling
- Caching strategy
- Data migration approach

#### Session Handling
- Session management
- State management
- Cookie policies

#### Error Handling and Logging
- Error handling strategy
- Logging guidelines
- Monitoring approach
- Exception handling patterns

#### Testability
- Testing strategy
- Test automation
- Test data management

#### Development Concepts
- Build process
- Code organization
- Naming conventions
- Development guidelines

## Lean Variant (Minimum Viable Documentation)

### Format:
- **List only concepts actually used** in your system
- **One paragraph per concept**
- **Reference to detailed guidelines** if they exist elsewhere

### Minimum Content:
- 3-7 crosscutting concepts
- Brief description of each
- Example or diagram if needed

### Example Lean Crosscutting Concepts:

**1. Error Handling**
All services use standardized error codes and HTTP status codes. Errors logged to central logging system. Client receives structured error responses with error code, message, and request ID.

**2. Authentication**
OAuth 2.0 for all API access. JWT tokens with 1-hour expiration. Refresh tokens stored securely. All endpoints except health checks require authentication.

**3. Logging**
Structured JSON logging to CloudWatch. All logs include request ID, timestamp, service name, log level. Sensitive data masked. Log retention: 30 days.

**4. API Design**
RESTful APIs following OpenAPI 3.0 spec. Versioning via URL path (/api/v1/). JSON request/response bodies. Consistent error responses.

## Thorough Variant (Complete Version)

### Structure per Concept:

#### Concept: <n>

**Overview:**
[What is this concept? Why is it important?]

**Motivation:**
[Why do we need this? What problem does it solve?]

**Guidelines and Rules:**
- Rule 1: <Specific guideline>
- Rule 2: <Specific guideline>
- Rule 3: <Specific guideline>

**Examples:**
[Code snippets, diagrams, or concrete examples]

**Benefits:**
[What advantages does this approach provide?]

**Trade-offs:**
[What are the costs or limitations?]

**Affected Building Blocks:**
[Which components from Section 5 follow this concept?]

**Related Patterns:**
[Links to external pattern descriptions]

**Tools and Technologies:**
[Specific tools or frameworks supporting this concept]

**Further Reading:**
[Links to detailed documentation]

### Detailed Example:

#### Concept: Logging Strategy

**Overview:**
Centralized, structured logging across all services for observability, debugging, and audit compliance.

**Motivation:**
- Distributed system requires centralized log aggregation
- Debugging requires correlation across services
- Compliance requires audit trail
- Operations requires monitoring and alerting

**Guidelines and Rules:**
1. **Structured Logging:** All logs in JSON format with standard fields
2. **Log Levels:** ERROR, WARN, INFO, DEBUG following standard definitions
3. **Context Propagation:** All logs include correlation ID (request ID)
4. **Sensitive Data:** PII and credentials must be masked
5. **Log Aggregation:** All logs shipped to CloudWatch Logs
6. **Retention:** 30 days for INFO, 90 days for ERROR/WARN
7. **Alerting:** ERROR level triggers alerts to on-call engineer

**Examples:**

```json
{
  "timestamp": "2025-11-07T10:15:30Z",
  "level": "INFO",
  "service": "order-service",
  "correlation_id": "req-12345",
  "user_id": "user-67890",
  "message": "Order created successfully",
  "order_id": "ord-111",
  "duration_ms": 45
}
```

**Benefits:**
- Easy debugging across distributed services
- Compliance with audit requirements
- Proactive issue detection via alerts
- Performance analysis via structured data

**Trade-offs:**
- Additional infrastructure cost (CloudWatch)
- Slight performance overhead for logging
- Development effort to implement consistently

**Affected Building Blocks:**
- All microservices
- API Gateway
- Background job processors

**Tools:**
- Winston (Node.js logging library)
- Logback (Java logging)
- CloudWatch Logs (aggregation)
- Datadog (visualization and alerting)

**Related Patterns:**
- Correlation ID pattern
- Log aggregation pattern
- Circuit Breaker (logs circuit state changes)

---

## Output Format

```markdown
# 8. Crosscutting Concepts

## Overview
[1-2 paragraphs explaining approach to crosscutting concerns and which concepts are documented]

**Note:** This section only includes concepts that actually apply to this system. Irrelevant topics have been removed.

## Concept 1: <n>

### Overview
[What and why]

### Guidelines
- <Guideline 1>
- <Guideline 2>
- <Guideline 3>

### Example
[Code snippet or diagram]

### Affected Components
[Which building blocks from Section 5]

---

## Concept 2: <n>
[Repeat structure]

---

## Removed/Not Applicable
The following common crosscutting concepts are NOT applicable to this system:
- <Concept X>: [Brief reason why not needed]
- <Concept Y>: [Brief reason why not needed]
```

## Common Mistakes to Avoid

### ❌ Not Allowed:
1. **Keeping irrelevant subsections** - Remove what doesn't apply!
2. **Vague descriptions** - Be concrete and specific
3. **No examples** - Show how concepts are applied
4. **Forgetting to list affected components** - Link to Section 5
5. **Too much detail** - This is overview, not implementation guide
6. **Inconsistency** - Concepts should be applied consistently
7. **No rationale** - Explain WHY this approach
8. **Repeating building block details** - Stay crosscutting
9. **No guidelines** - Provide actionable rules
10. **Missing trade-offs** - Every approach has costs

### ✅ Desired:
1. **Only relevant concepts** - Remove irrelevant arc42 template sections
2. **Concrete and specific** - Real examples and code
3. **Actionable guidelines** - Clear rules developers can follow
4. **Examples provided** - Show, don't just tell
5. **Consistent application** - Same patterns used throughout
6. **Rationale explained** - Why this approach?
7. **Trade-offs acknowledged** - Honest about costs
8. **Links to building blocks** - Which components affected
9. **Appropriate detail** - Enough to guide, not overwhelming
10. **References to external resources** - Links to detailed docs

## Integration with Other Sections

### Input from Other Sections:
- **Section 4:** Solution strategy may establish crosscutting approaches
- **Section 10:** Quality requirements drive crosscutting concepts

### Output for Other Sections:
- **Section 5:** Crosscutting concepts apply to building blocks
- **Section 6:** Runtime scenarios show concepts in action
- **Section 9:** Crosscutting approaches may be documented as decisions

### Crosscutting Nature:
- By definition, concepts here affect MULTIPLE sections
- May be referenced from Sections 5, 6, 7
- Quality concepts support Section 10 requirements

## Validation Criteria

- [ ] Only includes concepts relevant to THIS system
- [ ] Irrelevant sections removed (acknowledged as removed)
- [ ] Each concept has clear guidelines
- [ ] Examples provided for key concepts
- [ ] Rationale explained
- [ ] Affected building blocks identified
- [ ] Trade-offs acknowledged
- [ ] Consistent with Section 4 solution strategy
- [ ] Supports quality goals from Section 1 and 10

## Official arc42 Tips for Section 8

**Tip 8-1:** Remove irrelevant sections
- Don't keep subsections that don't apply
- Be explicit about what's removed
- Flexibility is a feature, not a bug

**Tip 8-2:** Focus on system-specific concepts
- Document YOUR crosscutting concerns
- Don't document general knowledge
- Be concrete and specific

**Tip 8-3:** Link to building blocks
- Show which components are affected
- Reference Section 5 building blocks
- Demonstrate consistency

**Tip 8-4:** Provide examples
- Code snippets
- Configuration examples
- Diagrams showing concept in action

## Common Crosscutting Concepts Catalog

### Domain and Business
- Domain Model
- Business Rules
- Validation Rules
- Calculation Methods

### Architecture Patterns
- Layering
- Microservices Patterns
- Event-Driven Architecture
- CQRS/Event Sourcing
- Hexagonal Architecture

### User Interface
- UI Components
- Layout Principles
- Navigation Patterns
- Accessibility
- Internationalization/Localization
- Responsive Design

### Security
- Authentication Methods
- Authorization Model
- Data Encryption
- API Security
- Session Management
- Audit Logging
- Security Testing

### Communication
- API Design Guidelines
- Message Formats
- Protocol Standards
- Integration Patterns
- Service Discovery

### Data Management
- Persistence Strategy
- Transaction Management
- Caching Strategy
- Data Migration
- Backup and Recovery
- Data Consistency

### Operational Concepts
- Logging
- Monitoring
- Health Checks
- Configuration Management
- Deployment Strategy
- Disaster Recovery

### Development
- Build Process
- Testing Strategy
- Code Organization
- Naming Conventions
- Development Workflow
- Code Review Process

---
*Based on docs.arc42.org/section-8/ and official arc42 sources*

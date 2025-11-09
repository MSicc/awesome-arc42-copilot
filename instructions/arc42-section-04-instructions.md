# arc42 Section 4: Solution Strategy - Specific Instructions

## Section Purpose

**Why this section exists:**
Section 4 provides a compact summary of the fundamental decisions and solution approaches that shape the system's architecture. It's the "executive summary" of how you'll achieve the quality goals.

**Value for stakeholders:**
- Bridges requirements (Section 1) with detailed architecture (Sections 5-8)
- Shows HOW quality goals will be achieved
- Documents fundamental technology and decomposition decisions
- Provides quick overview of architectural approach
- Enables stakeholders to grasp key decisions in 5-10 minutes
- Answers: How does the architecture achieve the quality goals?

**Key insight:** This section should be understandable to non-technical stakeholders and provide the "big picture" before diving into details.

## Mandatory Content (ESSENTIAL)

### What MUST be included:

#### Technology Decisions
- **Primary technologies** chosen (languages, frameworks, platforms)
- **Rationale** for each major technology choice
- **Link to quality goals** - which technology supports which goal

#### Decomposition Strategy
- **Top-level decomposition approach** (layers, microservices, hexagonal, etc.)
- **Reasoning** behind the structural approach
- **How it supports quality goals**

#### Approaches to Quality Goals
- **For each top 3-5 quality goal** from Section 1.2:
  - What architectural approach addresses it
  - What technology/pattern supports it
  - Brief explanation how it works

**Critical rule:** Every quality goal from Section 1.2 must be addressed here.

## Lean Variant (Minimum Viable Documentation)

### Format:
Simple table linking decisions to quality goals:

| Decision | Rationale | Quality Goal Supported |
|----------|-----------|----------------------|
| <Technology/Pattern> | <Why chosen> | <Which quality goal> |

### Minimum Content (max 2 pages):
- 5-10 fundamental decisions
- One sentence per rationale
- Clear link to quality goals
- Brief decomposition strategy statement

### Example:

| Decision | Rationale | Quality Goals |
|----------|-----------|--------------|
| Microservices architecture | Independent scalability and deployment | #flexible, #operable |
| PostgreSQL database | ACID compliance for data integrity | #reliable |
| React frontend | Rich user experience, component reusability | #usable, #flexible |
| Kubernetes deployment | Auto-scaling, self-healing | #reliable, #operable |
| REST APIs | Industry standard, wide tool support | #suitable, #flexible |

**Decomposition:** Microservices organized by business capabilities (Customer, Order, Inventory, Payment services).

## Thorough Variant (Complete Version)

### Structure:

#### 1. Technology Stack Overview
Comprehensive table of technology decisions:

| Technology Category | Decision | Alternatives Considered | Rationale | Quality Goals Addressed |
|--------------------|----------|------------------------|-----------|------------------------|
| Backend Language | Java 17 | Python, Go | Team expertise, enterprise support, performance | #reliable, #efficient |
| Frontend Framework | React 18 | Angular, Vue | Component ecosystem, hiring pool | #usable, #flexible |
| Database | PostgreSQL 14 | MongoDB, MySQL | ACID, JSON support, cost | #reliable, #suitable |
| Message Broker | Apache Kafka | RabbitMQ, AWS SQS | Throughput, event sourcing support | #efficient, #reliable |
| Container Platform | Kubernetes | Docker Swarm, ECS | Industry standard, rich ecosystem | #operable, #flexible |

#### 2. Architectural Patterns and Approaches

For each quality goal from Section 1.2, document:

**Quality Goal #1: [Name] - [Priority]**
- **Architectural Approach:** [Pattern/strategy used]
- **Technologies:** [Specific technologies supporting this]
- **Implementation:** [Brief how-it-works]
- **Trade-offs:** [What was sacrificed for this goal]
- **Validation:** [How we'll verify this works]

Example:
**Quality Goal #1: High Availability (99.9% uptime)**
- **Approach:** Redundancy at all levels, circuit breaker pattern
- **Technologies:** Kubernetes with 3+ replicas, Istio service mesh, Netflix Hystrix
- **Implementation:** All services run in multiple instances across availability zones. Circuit breakers prevent cascade failures. Health checks enable automatic failover.
- **Trade-offs:** Increased infrastructure cost (3x replication), higher complexity
- **Validation:** Load testing, chaos engineering, monitoring uptime metrics

#### 3. Decomposition Strategy

Detailed explanation of system structure:
- **Overall approach** (layered, microservices, hexagonal, etc.)
- **Decomposition criteria** (domain-driven design, technical layers, etc.)
- **Number and nature of top-level components**
- **Communication patterns** between components
- **Rationale** for this structure
- **Diagram** showing high-level structure

#### 4. Key Design Decisions

List of architecturally significant decisions:
- Each decision with context and consequences
- Reference to detailed ADRs in Section 9
- Grouped by category (technology, structure, patterns)

## Output Format

```markdown
# 4. Solution Strategy

## Overview
[2-3 sentences summarizing the overall approach to solving the problem and achieving quality goals]

## Technology Stack

| Category | Technology | Rationale | Quality Goals |
|----------|-----------|-----------|--------------|
| <Category> | <Tech> | <Why> | <Goals> |

## Architectural Approach

### Decomposition Strategy
[1 paragraph explaining overall structure: microservices, layers, etc.]

**High-Level Structure:**
[Simple diagram or text description of main components]

### Quality Goal Strategies

#### Quality Goal 1: <Name from Section 1.2>
- **Approach:** <Pattern/strategy>
- **Technologies:** <Supporting technologies>
- **Implementation:** <Brief explanation>
- **Trade-offs:** <Compromises made>

#### Quality Goal 2: <Name from Section 1.2>
[Same structure]

#### Quality Goal 3: <Name from Section 1.2>
[Same structure]

## Key Design Decisions

1. **<Decision Name>**
   - **Context:** <Why this decision was needed>
   - **Decision:** <What was chosen>
   - **Consequences:** <Impact on architecture>
   - **See also:** ADR-xxx (Section 9)

2. **<Decision Name>**
   [Same structure]

## Cross-References
- Detailed quality scenarios: See Section 10
- Building block details: See Section 5
- Architecture decisions: See Section 9
```

## Common Mistakes to Avoid

### ❌ Not Allowed:
1. **Too much detail** - This is overview, not detailed design
2. **No link to quality goals** - Every decision must support quality goals
3. **Missing quality goal coverage** - All quality goals from Section 1.2 must be addressed
4. **Technology decisions without rationale** - Always explain WHY
5. **Ignoring trade-offs** - Every decision has compromises
6. **Buzzword bingo** - Be specific, not vague ("scalable" vs "horizontal scaling via Kubernetes")
7. **Confusing with Section 9** - This is summary, Section 9 has detailed ADRs
8. **No decomposition strategy** - Must explain high-level structure
9. **Listing technologies without context** - Explain how they solve problems

### ✅ Desired:
1. **Brief and concrete** - 2-5 pages maximum
2. **Every quality goal addressed** - Traceable from Section 1.2
3. **Clear rationale** - Explain WHY for each decision
4. **Trade-offs acknowledged** - Nothing is free
5. **Appropriate abstraction** - Overview level, details in later sections
6. **Understandable to technical AND business stakeholders**
7. **Links to detailed sections** - Forward references to 5-9
8. **Alternatives mentioned** - What was NOT chosen and why
9. **Consistency with constraints** - Decisions respect Section 2 constraints

## Integration with Other Sections

### Input from Other Sections:
- **Section 1.2:** Quality goals that MUST be addressed
- **Section 2:** Constraints that LIMIT solution options

### Output for Other Sections:
- **Section 5:** Decomposition strategy defines building blocks
- **Section 6-7:** Technology choices influence runtime and deployment
- **Section 8:** Patterns referenced here are detailed in Section 8
- **Section 9:** Key decisions summarized here, detailed in Section 9
- **Section 10:** Strategies validate against quality scenarios

### Traceability:
**Section 1.2 (Quality Goals) → Section 4 (Solution Strategy) → Section 10 (Quality Requirements)**
- Each quality goal must have a strategy
- Each strategy must have measurable outcomes in Section 10

## Validation Criteria

- [ ] All quality goals from Section 1.2 are addressed
- [ ] Technology stack documented with rationale
- [ ] Decomposition strategy explained
- [ ] Trade-offs acknowledged
- [ ] Understandable in 5-10 minutes
- [ ] No contradictions with Section 2 constraints
- [ ] Forward references to detailed sections provided
- [ ] Alternatives considered and documented
- [ ] Concrete and specific (no buzzwords)
- [ ] Maximum 2-5 pages

## Official arc42 Tips for Section 4

**Tip 4-1:** Keep solution strategy compact
- Maximum 2-5 pages
- Focus on fundamental decisions only
- Details belong in later sections

**Tip 4-2:** Link strategy to quality goals
- Every quality goal needs a strategy
- Make the connection explicit
- Traceable from requirements to solution

**Tip 4-3:** Document trade-offs
- No decision is perfect
- Acknowledge what was sacrificed
- Explain why trade-off was acceptable

**Tip 4-4:** Explain your decomposition
- Top-level structure decision is critical
- Explain the reasoning
- Show how it supports quality goals

---
*Based on docs.arc42.org/section-4/ and official arc42 sources*

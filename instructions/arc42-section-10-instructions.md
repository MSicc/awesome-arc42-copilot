# arc42 Section 10: Quality Requirements - Specific Instructions

## Section Purpose

**Why this section exists:**
Section 10 provides detailed, concrete quality requirements in the form of scenarios. It elaborates on the quality goals from Section 1.2, making them measurable and testable.

**Value for stakeholders:**
- Makes quality goals concrete and measurable
- Enables validation that quality goals are achieved
- Provides testable quality scenarios
- Documents quality attribute priorities
- Shows trade-offs between quality goals
- Answers: How do we measure quality? What are the concrete acceptance criteria?

**Key insight:** Quality requirements must be concrete, measurable, and testable - not vague buzzwords.

## Mandatory Content (ESSENTIAL)

### What MUST be included:

#### Quality Tree
- **Hierarchical breakdown** of quality goals from Section 1.2
- **Quality categories** (using ISO 25010 or Q42 model)
- **Specific quality attributes** under each category
- **Priorities** indicated

#### Quality Scenarios
- **Concrete, measurable scenarios** for key quality attributes
- **Stimulus-Response format** preferred
- **Acceptance criteria** defined
- **Priorities** indicated

**Critical rule:** Quality requirements here MUST trace back to quality goals in Section 1.2.

## Lean Variant (Minimum Viable Documentation)

### Format:
Quality Tree (simple hierarchy) + Table of scenarios

### Minimum Content:
- Simple 2-level quality tree
- 5-10 concrete quality scenarios
- Clear acceptance criteria for each

### Example Lean Quality Documentation:

**Quality Tree:**
```
Quality Goals (from Section 1.2)
├─ Reliable
│  ├─ Availability (Priority: High)
│  └─ Fault Tolerance (Priority: Medium)
├─ Efficient
│  ├─ Response Time (Priority: High)
│  └─ Throughput (Priority: Medium)
└─ Usable
   ├─ Learnability (Priority: High)
   └─ Error Prevention (Priority: Medium)
```

**Quality Scenarios:**

| ID | Quality Attribute | Scenario | Acceptance Criteria |
|----|------------------|----------|---------------------|
| QS-01 | Availability | System experiences database failure | Automatic failover within 30 seconds, no data loss |
| QS-02 | Response Time | User searches for product (normal load) | Results displayed within 200ms for 95% of requests |
| QS-03 | Learnability | New user attempts to purchase product | Completes purchase within 5 minutes without training |
| QS-04 | Throughput | System handles Black Friday traffic | Supports 10,000 concurrent users without degradation |

## Thorough Variant (Complete Version)

### Quality Tree Structure:

#### Level 1: Quality Goals (from Section 1.2)
The top 3-5 quality goals documented in Section 1.2

#### Level 2: Quality Categories
Use ISO 25010 categories or Q42 properties:
- Functional Suitability
- Performance Efficiency
- Compatibility
- Usability
- Reliability
- Security
- Maintainability
- Portability

OR Q42 properties:
- #reliable, #flexible, #efficient, #usable, #safe, #secure, #suitable, #operable

#### Level 3: Specific Quality Attributes
Concrete attributes like:
- Availability, Fault Tolerance (under Reliability)
- Response Time, Throughput (under Performance)
- Learnability, Operability (under Usability)

#### Level 4: Quality Scenarios
Concrete, measurable scenarios

**Visualization:**
- Tree diagram showing hierarchy
- Different weights/colors for priorities
- Link between levels clear

### Quality Scenario Template (Detailed):

#### Scenario: <ID> - <Name>

**Quality Attribute:** [Which attribute this tests]

**Priority:** [High | Medium | Low]

**Environment/Context:**
[What is the system state? What conditions apply?]

**Stimulus:**
[What triggers this scenario? Who/what initiates it?]

**System Component:**
[Which part of the system is affected?]

**Response:**
[What should the system do?]

**Response Measure:**
[How do we measure the response? What are the concrete acceptance criteria?]

**Example:**

#### Scenario: QS-001 - Database Failover

**Quality Attribute:** Reliability (Availability)

**Priority:** High

**Environment:**
- Production environment with primary-replica database configuration
- System under normal load (1,000 active users)
- Primary database experiences hardware failure

**Stimulus:**
Primary PostgreSQL database becomes unavailable due to hardware failure

**System Component:**
Database layer, connection pooling, application services

**Response:**
1. Health checks detect primary database failure within 10 seconds
2. Automatic failover to replica database triggered
3. Application services reconnect to new primary
4. System resumes normal operation
5. Alert sent to operations team

**Response Measure:**
- **Detection time:** < 10 seconds
- **Total downtime:** < 30 seconds
- **Data loss:** 0 transactions
- **User impact:** Ongoing requests fail gracefully, new requests succeed
- **Recovery:** Full functionality restored without manual intervention

---

### Quality Scenario Categories:

Use these standard categories for organizing scenarios:

**Usage Scenarios:**
- Normal operation
- Peak load
- Minimum load

**Change Scenarios:**
- Adding new features
- Modifying existing features
- Upgrading dependencies
- Changing infrastructure

**Failure Scenarios:**
- Component failures
- Network issues
- Security attacks
- Data corruption

## Output Format

```markdown
# 10. Quality Requirements

## Overview
[1-2 paragraphs explaining how quality requirements relate to quality goals from Section 1.2]

## Quality Tree

### Visual Representation
![Quality Tree](./diagrams/quality-tree.png)

### Hierarchical Breakdown

#### Quality Goal 1: [Name from Section 1.2] - Priority: High

**Quality Categories:**
- **Reliability** (Priority: High)
  - Availability (P: High) - QS-001, QS-002
  - Fault Tolerance (P: Medium) - QS-003
- **Performance Efficiency** (Priority: Medium)
  - Response Time (P: High) - QS-004
  - Throughput (P: Medium) - QS-005

#### Quality Goal 2: [Name from Section 1.2] - Priority: High
[Continue hierarchy]

---

## Quality Scenarios

### Scenario QS-001: [Name]

**Quality Attribute:** Reliability > Availability

**Priority:** High

**Scenario Description:**
[Context] Under normal production load with 1000 active users,
[Stimulus] primary database experiences hardware failure,
[Response] system automatically fails over to replica database within 30 seconds with zero data loss.

**Detailed Scenario:**

| Element | Description |
|---------|-------------|
| Environment | Production, normal load (1000 users) |
| Stimulus | Primary database hardware failure |
| Component | Database layer, connection pool |
| Response | Automatic failover to replica |
| Measure | Downtime < 30s, data loss = 0 |

**Acceptance Criteria:**
- ✅ Failure detected within 10 seconds
- ✅ Failover completed within 30 seconds
- ✅ Zero transaction data loss
- ✅ No manual intervention required
- ✅ Operations team alerted

**Test Approach:**
- Chaos engineering: Kill primary database during load test
- Monitor failover time and data consistency
- Verify alert delivery

**Related Scenarios:** QS-002, QS-003

---

### Scenario QS-002: [Name]
[Repeat structure]

---

## Quality Scenarios by Category

### Usage Scenarios
- QS-001: Database Failover
- QS-004: Peak Load Response Time
- QS-007: Concurrent User Capacity

### Change Scenarios  
- QS-010: Add New Feature
- QS-011: Upgrade Framework

### Failure Scenarios
- QS-001: Database Failover
- QS-015: Security Attack Response
```

## Common Mistakes to Avoid

### ❌ Not Allowed:
1. **Vague quality requirements** - "Should be fast" is not measurable
2. **No link to Section 1.2** - Must trace to quality goals
3. **Untestable scenarios** - No way to verify if met
4. **Missing acceptance criteria** - No clear success definition
5. **No priorities** - Everything can't be highest priority
6. **Ignoring trade-offs** - Quality goals often conflict
7. **Too many scenarios** - Focus on most important
8. **Using buzzwords** - "User-friendly", "secure", "scalable" without specifics
9. **No measurable numbers** - Must have concrete metrics
10. **Forgetting negative scenarios** - Include failure cases

### ✅ Desired:
1. **Concrete and measurable** - Specific numbers and criteria
2. **Traceable to Section 1.2** - Clear link to quality goals
3. **Testable** - Can actually verify if met
4. **Prioritized** - High/Medium/Low clearly indicated
5. **Realistic** - Achievable within constraints
6. **Complete scenarios** - Stimulus, response, measure
7. **Both positive and negative** - Normal and failure cases
8. **Trade-offs acknowledged** - Honest about conflicts
9. **Appropriate quantity** - 10-30 scenarios typical
10. **Stakeholder agreement** - Reviewed and accepted

## Integration with Other Sections

### Input from Other Sections:
- **Section 1.2:** Quality goals that are elaborated here
- **Section 2:** Constraints affect what's achievable
- **Section 4:** Solution strategy addresses quality scenarios

### Output for Other Sections:
- **Section 4:** Quality scenarios validate solution strategies
- **Section 6:** Some scenarios may appear as runtime scenarios
- **Section 11:** Unachievable scenarios become risks

### Critical Traceability:
**Section 1.2 (Quality Goals) → Section 10 (Quality Scenarios)**
- Every quality goal from 1.2 must have scenarios in Section 10
- Every scenario must support a quality goal from 1.2

## Validation Criteria

### Quality Tree:
- [ ] All quality goals from Section 1.2 included
- [ ] Hierarchical structure clear
- [ ] Priorities indicated
- [ ] Quality attributes specific (not vague)
- [ ] Appropriate depth (2-3 levels typical)

### Quality Scenarios:
- [ ] 10-30 scenarios documented
- [ ] Each scenario has concrete acceptance criteria
- [ ] Measurable response metrics defined
- [ ] Stimulus and response clear
- [ ] Priorities assigned
- [ ] Testable
- [ ] Mix of usage, change, and failure scenarios
- [ ] Stakeholder agreement obtained

### Consistency:
- [ ] Traces to Section 1.2 quality goals
- [ ] Consistent with Section 2 constraints
- [ ] Addressed by Section 4 solution strategy
- [ ] Referenced in Section 11 if at risk

## Official arc42 Tips for Section 10

**Tip 10-1:** Use quality scenarios
- Concrete scenarios are testable
- Better than abstract requirements
- Three types: usage, change, failure

**Tip 10-2:** Make it measurable
- Include specific numbers
- Define clear acceptance criteria
- Enable validation

**Tip 10-3:** Use quality tree
- Hierarchical organization
- Shows relationships
- Enables priority assignment

**Tip 10-4:** Link to Section 1.2
- Elaborate on quality goals
- Maintain traceability
- Ensure coverage

## Q42 Quality Model Integration

Use Q42 properties for quality tree organization:

### #reliable (97 attributes)
- Availability, Fault Tolerance, Recoverability, Accuracy

### #flexible (50 attributes)
- Adaptability, Maintainability, Extensibility, Portability

### #efficient (71 attributes)
- Time Behavior, Resource Utilization, Capacity

### #usable (103 attributes)
- Learnability, Operability, User Error Protection, Accessibility

### #safe (28 attributes)
- Physical Safety, Risk Identification, Fail-Safe

### #secure (36 attributes)
- Confidentiality, Integrity, Authenticity, Non-repudiation

### #suitable (52 attributes)
- Functional Completeness, Correctness, Testability

### #operable (55 attributes)
- Installability, Monitorability, Recoverability

**Reference:** See quality.arc42.org for complete Q42 model

---
*Based on docs.arc42.org/section-10/ and official arc42 sources*

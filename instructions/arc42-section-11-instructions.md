# arc42 Section 11: Risks and Technical Debt - Specific Instructions

## Section Purpose

**Why this section exists:**
Section 11 documents known technical risks, potential problems, and technical debt that could impact the system. It provides transparency about issues and enables proactive risk management.

**Value for stakeholders:**
- Makes risks visible and manageable
- Documents technical debt for future planning
- Enables informed decision-making
- Provides transparency to stakeholders
- Helps prioritize technical improvements
- Answers: What could go wrong? What technical debt exists? What are the mitigation plans?

**Key insight:** This section should be reviewed and updated regularly. Risks and technical debt evolve over time.

## Mandatory Content (ESSENTIAL)

### What MUST be included:

#### Technical Risks
- **Identified risks** with potential negative impact
- **Probability and impact** assessment
- **Mitigation strategies** or contingency plans
- **Priority/severity** ranking

#### Technical Debt
- **Known shortcuts or compromises** in the architecture
- **Impact** of the technical debt
- **Plan for addressing** the debt (or conscious decision to accept it)

**Note:** Empty section is acceptable if truly no significant risks or technical debt exist (rare!).

## Lean Variant (Minimum Viable Documentation)

### Format:
Simple tables for risks and technical debt

### Minimum Content:
- 5-10 identified risks with priority
- 3-5 technical debt items
- Brief mitigation/plan for each

### Example Lean Risks:

| ID | Risk | Probability | Impact | Mitigation |
|----|------|-------------|--------|------------|
| R-01 | Single database is bottleneck | High | High | Plan database sharding for Q2 2025 |
| R-02 | Key developer leaves | Medium | High | Cross-training, documentation |
| R-03 | Third-party API rate limits | Medium | Medium | Implement caching, negotiate higher limits |
| R-04 | AWS region failure | Low | Critical | Multi-region deployment by Q3 2025 |

### Example Lean Technical Debt:

| ID | Technical Debt | Impact | Plan |
|----|---------------|--------|------|
| TD-01 | No automated integration tests | Medium | Add in Sprint 15-16 |
| TD-02 | Monolithic user service needs splitting | High | Refactor in Q1 2025 |
| TD-03 | Legacy code in payment module | Medium | Rewrite planned for Q2 2025 |

## Thorough Variant (Complete Version)

### Risk Documentation Structure:

#### Risk: R-<XXX> - <Name>

**Category:** [Technical | Organizational | External | Business]

**Description:**
[Detailed explanation of the risk]

**Probability:** [Low | Medium | High | Very High] (percentage if known)

**Impact:** [Low | Medium | High | Critical]

**Priority:** [Calculated from Probability × Impact]

**Indicators:**
[What signals that this risk is becoming reality?]

**Consequences if Risk Occurs:**
- [Consequence 1]
- [Consequence 2]
- [Consequence 3]

**Mitigation Strategy:**

**Prevention:**
[Actions to reduce probability]

**Containment:**
[Actions to reduce impact if risk occurs]

**Contingency Plan:**
[What to do if risk occurs]

**Responsible:** [Who is monitoring/mitigating this risk]

**Review Date:** [When to reassess this risk]

**Status:** [New | Under Observation | Mitigated | Occurred | Closed]

**Related Architecture Elements:**
[Which components from Section 5 are affected]

**Historical Notes:**
[Has this risk occurred before? When? How was it handled?]

---

### Technical Debt Documentation Structure:

#### Technical Debt: TD-<XXX> - <Name>

**Category:** [Code Quality | Architecture | Documentation | Testing | Infrastructure]

**Description:**
[What is the shortcut/compromise?]

**Origin:**
- **When Created:** [Date/Sprint/Release]
- **Why Created:** [Rationale for the compromise]
- **Decision Maker:** [Who approved this trade-off]

**Current Impact:**

**Code Quality:**
[How does it affect code maintainability?]

**Performance:**
[Any performance implications?]

**Security:**
[Security concerns?]

**Development Velocity:**
[How does it slow down development?]

**Estimated Cost to Fix:**
- **Effort:** [Story points/hours/days]
- **Resources:** [Team/skills needed]
- **Risk of Fix:** [What could break?]

**Cost of Not Fixing:**
[What happens if we leave it?]

**Remediation Plan:**

**Option 1: Fix Now**
- Timeline: [When]
- Approach: [How]
- Cost: [Resources]

**Option 2: Fix Later**
- Triggers: [What would cause us to fix this]
- Timeline: [When]

**Option 3: Accept**
- Rationale: [Why we consciously accept this]
- Monitoring: [How we track its impact]

**Decision:** [Which option chosen and why]

**Responsible:** [Who owns resolving this]

**Target Date:** [When to fix or next review]

**Status:** [Identified | Scheduled | In Progress | Resolved | Accepted]

**Dependencies:**
[Other technical debt or risks related to this]

## Output Format

```markdown
# 11. Risks and Technical Debt

## Overview
[1-2 paragraphs explaining risk management approach and technical debt policy]

**Last Updated:** YYYY-MM-DD

**Next Review:** YYYY-MM-DD

---

## Risks

### Risk Register Summary

| ID | Risk | Probability | Impact | Priority | Status |
|----|------|-------------|--------|----------|--------|
| R-001 | <Name> | High | High | Critical | Under Observation |
| R-002 | <Name> | Medium | Medium | Medium | Mitigated |

### Detailed Risk Descriptions

#### Risk R-001: <Name>

**Category:** Technical

**Description:**
[What is the risk?]

**Probability:** High (60-80%)

**Impact:** High (Significant service degradation)

**Priority:** Critical

**Consequences:**
- [Consequence 1]
- [Consequence 2]

**Mitigation:**
- **Prevention:** [Actions to reduce likelihood]
- **Containment:** [Actions to reduce impact]
- **Contingency:** [Plan if it occurs]

**Responsible:** [Name/Role]

**Review Date:** 2025-Q2

**Status:** Under Observation

---

#### Risk R-002: <Name>
[Repeat structure]

---

## Technical Debt

### Technical Debt Register

| ID | Debt Item | Impact | Effort to Fix | Target Date | Status |
|----|-----------|--------|---------------|-------------|--------|
| TD-001 | <Name> | High | 5 days | 2025-Q1 | Scheduled |
| TD-002 | <Name> | Medium | 10 days | 2025-Q2 | Identified |

### Detailed Technical Debt Items

#### Technical Debt TD-001: <Name>

**Category:** Architecture

**Description:**
[What is the technical debt?]

**Origin:**
- Created: Sprint 12 (2024-06-15)
- Reason: Deadline pressure for MVP launch
- Decision: Product Owner + Tech Lead

**Current Impact:**
- **Maintainability:** Code duplication across 3 services makes changes slow
- **Performance:** Unnecessary data serialization adds 200ms latency
- **Development:** Slows feature development by ~20%

**Estimated Cost to Fix:**
- **Effort:** 5 developer-days
- **Risk:** Medium - requires careful testing of affected services

**Remediation Plan:**

**Decision:** Fix in Q1 2025 (Sprint 20-21)

**Approach:** Refactor to shared library, migrate services one by one

**Responsible:** Backend Team Lead

**Status:** Scheduled

---

## Risk & Debt Trends

### Newly Identified (This Quarter):
- R-005: Third-party API deprecation
- TD-008: Missing database indexes

### Resolved (This Quarter):
- R-002: Successfully migrated to new hosting provider
- TD-003: Completed test automation for critical paths

### Ongoing Monitoring:
- R-001: Database scalability - metrics tracking, review monthly
- TD-002: Legacy authentication code - scheduled refactor Q2
```

## Common Mistakes to Avoid

### ❌ Not Allowed:
1. **Hiding risks** - Pretending they don't exist doesn't help
2. **No mitigation plans** - Identifying risk without action plan is incomplete
3. **Not prioritizing** - Everything can't be critical
4. **Ignoring technical debt** - Sweeping under the rug
5. **Never updating** - Risks and debt evolve, keep current
6. **Too much detail** - Don't document every minor issue
7. **No ownership** - Risks need responsible parties
8. **Vague descriptions** - Be specific about probability and impact
9. **Forgetting external risks** - Vendor, regulatory, market risks matter too
10. **Not learning from history** - Document what happened if risks occur

### ✅ Desired:
1. **Transparent documentation** - Honest about problems
2. **Prioritized by severity** - Risk = Probability × Impact
3. **Mitigation strategies defined** - For each significant risk
4. **Regular reviews** - Update quarterly minimum
5. **Ownership assigned** - Who monitors/mitigates
6. **Appropriate detail** - Focus on significant risks
7. **Both prevention and contingency** - Proactive and reactive plans
8. **Technical debt conscious** - Explicit about shortcuts taken
9. **Remediation plans** - Path to resolving technical debt
10. **Stakeholder awareness** - Risks communicated appropriately

## Integration with Other Sections

### Input from Other Sections:
- **Section 1.2:** Unachievable quality goals become risks
- **Section 2:** Constraints may create risks
- **Section 4:** Solution strategy trade-offs may create debt
- **Section 9:** Decisions may introduce risks
- **Section 10:** Quality scenarios not met become risks

### Output for Other Sections:
- **Section 9:** Risk mitigation may require new decisions
- **Section 4:** High-priority risks may trigger strategy changes

## Validation Criteria

### Risk Documentation:
- [ ] All significant risks identified
- [ ] Probability and impact assessed
- [ ] Priorities assigned (based on probability × impact)
- [ ] Mitigation strategies defined
- [ ] Responsible parties assigned
- [ ] Review dates set
- [ ] Both technical and non-technical risks included
- [ ] External risks considered (vendors, regulations, etc.)

### Technical Debt Documentation:
- [ ] Known shortcuts documented
- [ ] Origin and rationale recorded
- [ ] Current impact assessed
- [ ] Cost to fix estimated
- [ ] Remediation plan or acceptance rationale provided
- [ ] Ownership assigned
- [ ] Target dates set (or conscious acceptance documented)

### Process:
- [ ] Section reviewed regularly (quarterly minimum)
- [ ] New risks added as identified
- [ ] Resolved risks updated/closed
- [ ] Technical debt tracked against plan
- [ ] Stakeholders informed of critical risks

## Official arc42 Tips for Section 11

**Tip 11-1:** Be transparent
- Document known problems honestly
- Don't hide issues from stakeholders
- Transparency enables better decisions

**Tip 11-2:** Prioritize by impact
- Use risk matrix (probability × impact)
- Focus on high-priority items
- Not everything is critical

**Tip 11-3:** Include mitigation plans
- Don't just identify risks
- Document how to prevent/reduce/handle
- Assign responsibility

**Tip 11-4:** Review regularly
- Risks evolve over time
- New risks emerge
- Old risks may resolve
- Update section quarterly minimum

**Tip 11-5:** Track technical debt explicitly
- Document conscious shortcuts
- Include remediation timeline
- Or explicitly accept the debt

## Risk Assessment Matrix

### Probability Levels:
- **Very Low:** < 10%
- **Low:** 10-30%
- **Medium:** 30-60%
- **High:** 60-90%
- **Very High:** > 90%

### Impact Levels:
- **Low:** Minor inconvenience, easily worked around
- **Medium:** Noticeable impact, requires effort to manage
- **High:** Significant impact, major disruption
- **Critical:** Catastrophic, system failure or major business impact

### Priority Matrix:

|                | Low Impact | Medium Impact | High Impact | Critical Impact |
|----------------|-----------|---------------|-------------|-----------------|
| **Very Low**   | Low       | Low           | Medium      | Medium          |
| **Low**        | Low       | Medium        | Medium      | High            |
| **Medium**     | Medium    | Medium        | High        | High            |
| **High**       | Medium    | High          | High        | Critical        |
| **Very High**  | High      | High          | Critical    | Critical        |

---
*Based on docs.arc42.org/section-11/ and official arc42 sources*

# arc42 Section 9: Architecture Decisions - Specific Instructions

## Section Purpose

**Why this section exists:**
Section 9 documents important, architecturally significant decisions made about the system. It captures the reasoning behind decisions to prevent knowledge loss and enable future evaluation.

**Value for stakeholders:**
- Preserves decision rationale for future team members
- Prevents repeated debates on settled issues
- Enables challenging decisions when context changes
- Shows what alternatives were considered
- Documents trade-offs and consequences
- Answers: Why did we choose X over Y? What were the consequences?

**Key insight:** Document WHY, not just WHAT. The rationale is more important than the decision itself.

## Mandatory Content (ESSENTIAL)

### What MUST be included:

#### Architecturally Significant Decisions
- **Decisions with long-term impact**
- **Decisions that are hard to reverse**
- **Decisions affecting multiple components**
- **Decisions with significant trade-offs**

**NOT architecturally significant:**
- Implementation details
- Temporary workarounds
- Technology micro-choices
- Obvious decisions

### Decision Documentation Format

Use **ADR (Architecture Decision Record)** format:

**Minimum per decision:**
1. **Context:** What is the issue/problem?
2. **Decision:** What did we decide?
3. **Consequences:** What are the results (positive and negative)?

**Recommended additional fields:**
- **Status:** Proposed | Accepted | Superseded | Deprecated
- **Date:** When was this decided?
- **Stakeholders:** Who was involved?
- **Alternatives Considered:** What else did we evaluate?

## Lean Variant (Minimum Viable Documentation)

### Format:
Simple numbered list with basic ADR structure

### Minimum Content:
- 5-15 key decisions
- Context, Decision, Consequences for each
- One paragraph per field

### Example Lean ADR:

**ADR-001: Use Microservices Architecture**

**Context:** System needs independent scaling of different functional areas. Team is distributed across locations. Need to deploy features independently.

**Decision:** Adopt microservices architecture with services organized by business capabilities (Customer, Order, Inventory, Payment).

**Consequences:**
- ✅ Independent scaling and deployment
- ✅ Technology diversity possible
- ✅ Team autonomy
- ❌ Increased operational complexity
- ❌ Need for service mesh/API gateway
- ❌ Distributed transaction challenges

---

**ADR-002: PostgreSQL as Primary Database**

**Context:** Need reliable, ACID-compliant database. Team has PostgreSQL expertise. Cost constraints limit commercial database options.

**Decision:** Use PostgreSQL 14+ for all primary data storage.

**Consequences:**
- ✅ ACID guarantees for data integrity
- ✅ No licensing costs
- ✅ Team expertise available
- ✅ JSON support for flexible schemas
- ❌ Cannot use specialized databases (graph, time-series) without justification
- ❌ Vertical scaling limitations

## Thorough Variant (Complete Version)

### Full ADR Template:

#### ADR-<XXX>: <Short Title>

**Status:** [Proposed | Accepted | Superseded by ADR-YYY | Deprecated]

**Date:** YYYY-MM-DD

**Stakeholders:**
- Decision makers: [Names/roles]
- Consulted: [Names/roles]
- Informed: [Names/roles]

**Context:**
[Detailed problem description]
- What is the issue we're addressing?
- Why is it architecturally significant?
- What forces/constraints are at play?
- What is the current situation?

**Decision:**
[Complete description of the decision]
- What exactly did we decide?
- How will it be implemented?
- What is the scope of this decision?

**Alternatives Considered:**

**Alternative 1: <Name>**
- Description: [What is this alternative?]
- Evaluation against criteria: [How it scores]
- Pros: [Benefits]
- Cons: [Drawbacks]
- Reason for rejection: [Why not chosen]

**Decision Criteria Used:**
Priority-ordered criteria for evaluation:
1. [Primary criterion - e.g., Performance]
2. [Secondary criterion - e.g., Cost]
3. [Tertiary criterion - e.g., Team expertise]

**Alternative 2: <Name>**
[Same structure]

**Consequences:**

**Positive:**
- ✅ [Benefit 1]
- ✅ [Benefit 2]
- ✅ [Benefit 3]

**Negative:**
- ❌ [Drawback 1]
- ❌ [Drawback 2]
- ❌ [Drawback 3]

**Neutral:**
- ➡️ [Impact 1]
- ➡️ [Impact 2]

**Implications for:**
- Building Blocks: [Which components affected - link to Section 5]
- Quality Goals: [Which goals supported/compromised - link to Section 1.2]
- Constraints: [Which constraints does this create - link to Section 2]
- Deployment: [How does this affect deployment - link to Section 7]

**Related Decisions:**
- Supersedes: ADR-XXX
- Requires: ADR-YYY
- Related to: ADR-ZZZ

**Validation:**
[How will we verify this decision was correct?]
- Metrics to track
- Success criteria
- Review date

**References:**
- [External resources, research, documentation]
- [Standards or guidelines followed]

---

## Output Format

```markdown
# 9. Architecture Decisions

## Overview
[1-2 paragraphs explaining approach to decision documentation]

**Decision Log:**
[Table of contents listing all ADRs]

| ID | Title | Status | Date |
|----|-------|--------|------|
| ADR-001 | <Title> | Accepted | 2025-01-15 |
| ADR-002 | <Title> | Accepted | 2025-02-01 |
| ADR-003 | <Title> | Superseded | 2025-03-10 |

---

## ADR-001: <Title>

**Status:** Accepted

**Date:** 2025-MM-DD

**Context:**
[Problem description]

**Decision:**
[What was decided]

**Alternatives Considered:**
- **Alternative 1:** [Brief description and why rejected]
- **Alternative 2:** [Brief description and why rejected]

**Consequences:**

**Positive:**
- ✅ [Benefit]
- ✅ [Benefit]

**Negative:**
- ❌ [Drawback]
- ❌ [Drawback]

**Implications:**
- Affects Building Blocks: [List from Section 5]
- Supports Quality Goals: [List from Section 1.2]

---

## ADR-002: <Title>
[Repeat structure]
```

## Common Mistakes to Avoid

### ❌ Not Allowed:
1. **Documenting implementation details** - Not architecturally significant
2. **No rationale** - Just stating decision without WHY
3. **Missing alternatives** - Not showing what else was considered
4. **No consequences** - Every decision has trade-offs
5. **Documenting obvious decisions** - Save for significant choices
6. **Missing dates** - When was this decided?
7. **No status** - Is this active, superseded, or deprecated?
8. **Hiding negative consequences** - Be honest about drawbacks
9. **Too vague** - Be specific and concrete
10. **Not updating when superseded** - Mark old decisions clearly

### ✅ Desired:
1. **Architecturally significant decisions only** - High impact, hard to reverse
2. **Clear rationale** - Explain WHY this decision
3. **Alternatives documented** - What else was considered and why rejected
4. **Consequences explicit** - Both positive AND negative
5. **Concrete and specific** - Detailed enough to understand
6. **Dated and authored** - When and by whom
7. **Status clear** - Active, superseded, or deprecated
8. **Honest about trade-offs** - No perfect decisions
9. **Links to other sections** - Which components/goals affected
10. **Reviewable and challengeable** - Can be questioned when context changes

## Integration with Other Sections

### Input from Other Sections:
- **Section 1:** Quality goals influence decisions
- **Section 2:** Constraints limit decision options
- **Section 4:** Solution strategy summarizes key decisions

### Output for Other Sections:
- **Section 2:** Decisions may create new constraints
- **Section 4:** Key decisions summarized in solution strategy
- **Section 5-8:** Decisions affect building blocks, runtime, deployment, concepts
- **Section 11:** Bad decisions become risks or technical debt

### Critical Relationship with Section 4:
**Section 4 (Solution Strategy) = Executive Summary**
**Section 9 (Architecture Decisions) = Detailed Rationale**

- Every major decision summarized in Section 4 SHOULD have corresponding detailed ADR in Section 9
- Section 4 shows WHAT was decided and high-level WHY
- Section 9 shows complete context, alternatives, criteria, and consequences
- Think of Section 4 as "decisions for executives" and Section 9 as "decisions for architects"

## Validation Criteria

- [ ] Only architecturally significant decisions documented
- [ ] Each decision has clear context
- [ ] Decision statement is concrete
- [ ] Consequences documented (positive AND negative)
- [ ] Alternatives considered and documented
- [ ] Status and date included
- [ ] Stakeholders identified
- [ ] Links to affected sections provided
- [ ] Trade-offs explicitly acknowledged
- [ ] Decisions can be challenged/reviewed

## Official arc42 Tips for Section 9

**Tip 9-1:** Use ADR format
- Architecture Decision Records are established pattern
- Provides consistent structure
- Easy to understand and maintain

**Tip 9-2:** Document significant decisions only
- Not every decision is architecturally significant
- Focus on high-impact, hard-to-reverse choices
- Skip implementation details

**Tip 9-3:** Capture alternatives
- Show what else was considered
- Explain why alternatives were rejected
- Helps future evaluation

**Tip 9-4:** Be honest about trade-offs
- No perfect decisions
- Document both benefits and costs
- Enables informed future changes

**Tip 9-5:** Keep decisions alive
- Update status when superseded
- Review periodically
- Challenge decisions when context changes

## When to Document a Decision

### Document When:
- ✅ Decision affects multiple components
- ✅ Decision is expensive to reverse
- ✅ Decision has significant trade-offs
- ✅ Decision constrains future choices
- ✅ Decision is non-obvious or controversial
- ✅ Decision impacts quality goals
- ✅ Team debated multiple alternatives

### Don't Document When:
- ❌ Decision is implementation detail
- ❌ Decision is obvious or standard practice
- ❌ Decision can be easily reversed
- ❌ Decision is temporary workaround
- ❌ Decision has no significant consequences
- ❌ Decision is already documented elsewhere (e.g., code comments sufficient)

## ADR Process

### Creating an ADR:
1. **Identify** need for decision
2. **Research** alternatives
3. **Draft** ADR with status "Proposed"
4. **Discuss** with stakeholders
5. **Decide** and update status to "Accepted"
6. **Implement** the decision
7. **Review** consequences periodically

### Updating ADRs:
- Mark as "Superseded by ADR-XXX" when replaced
- Mark as "Deprecated" when no longer relevant
- Never delete - history is valuable
- Add retrospective notes if consequences differ from expectations

### Reviewing ADRs:
- Periodic review (quarterly/annually)
- Review when context changes significantly
- Challenge decisions that may no longer apply
- Create new ADR to supersede if decision changes

---
*Based on docs.arc42.org/section-9/ and official arc42 sources*

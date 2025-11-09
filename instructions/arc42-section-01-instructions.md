# arc42 Section 1: Introduction and Goals - Specific Instructions

## Section Purpose

**Why this section exists:**
Section 1 introduces stakeholders to the fundamental driving forces behind the architecture. It enables readers to understand the central tasks of the system BEFORE encountering detailed architectural information.

**Value for stakeholders:**
- Provides the "WHY" before the "WHAT" and "HOW"
- Sets context for all subsequent architectural decisions
- Ensures alignment between business objectives and technical implementation
- Serves as first point of reference for most readers
- Answers: Why does this system exist? What's important? Who cares?

**Critical rule:** NEVER start developing an architecture if quality goals have not been put into writing and signed by major stakeholders.

## Mandatory Content (ESSENTIAL)

### What MUST be included:

#### 1.1 Requirements Overview
- **Short description** of functional requirements and driving forces
- **Brief bullet points** of essential features/use cases (max 1 page for simple systems)
- **Reference** to existing requirements documents (with version and location)
- **Business activity context** explaining user value
- Focus ONLY on what applies to THIS specific system

**NOT included here:**
- Detailed requirements (belongs in requirements documentation)
- Quality requirements (goes in Section 1.2 or 10)
- All possible features (only essential, architecturally-relevant ones)

#### 1.2 Quality Goals (MANDATORY - The Most Important Part)
- **Top 3 quality goals** (maximum 5)
- **Ordered by priority** for major stakeholders
- **Concrete, measurable scenarios** for each goal
- **Avoid buzzwords** - be specific and testable
- Must be **signed by major stakeholders**

**Format:**
| Priority | Quality Goal | Scenario |
|----------|-------------|----------|
| 1 | <Goal> | <Concrete, measurable scenario> |
| 2 | <Goal> | <Concrete, measurable scenario> |
| 3 | <Goal> | <Concrete, measurable scenario> |

**Use Q42 quality properties:**
- #reliable, #flexible, #efficient, #usable, #safe, #secure, #suitable, #operable

#### 1.3 Stakeholder Table
- **All relevant parties** who should know, use, or influence architecture
- **Three columns minimum:** Role/Name | Contact | Expectations

**Who to include:**
- Architects and development team
- Product owners and business stakeholders
- Operations/administrators
- Testers and QA
- End users
- Management
- Auditors/reviewers
- External systems/teams

## Lean Variant (Minimum Viable Documentation)

### Requirements Overview (1.1):
- Less than one page
- 5-10 bullet points of essential features
- One-sentence system purpose
- Reference to requirements document (if exists)

### Quality Goals (1.2):
- Exactly 3 goals (never skip this!)
- Simple table: Goal | Priority | Scenario
- Each scenario in 1-2 sentences
- Use concrete numbers/measures

**Example:**
| Priority | Quality Goal | Scenario |
|----------|-------------|----------|
| 1 | Reliable | System available 7x24 with 99% uptime |
| 2 | Efficient | Report generation completes in < 10 seconds |
| 3 | Usable | New users find articles within 5 minutes without training |

### Stakeholders (1.3):
- Basic table with 5-10 key stakeholders
- Minimal expectations description

## Thorough Variant (Complete Version)

### Requirements Overview (1.1):
- Tabular use-case format with detailed descriptions
- Links to complete requirements documents with version identification
- Compact summary of functional environment
- Extract of essential features AND non-functional requirements
- References to quantity structures and background information
- Business context explaining value proposition

### Quality Goals (1.2):
- Top 3-5 quality goals with detailed scenarios
- Ordered by priority
- **Concrete, measurable scenarios** (not "high performance" but "process 10,000 requests/second with 99.9% availability")
- Explicit quality attributes from ISO 25010 or Q42
- Link to Section 10 for complete quality scenarios
- **Signed agreement** from major stakeholders
- Rationale for why these goals were chosen

### Stakeholders (1.3):
- Comprehensive list of ALL persons, roles, organizations
- Detailed expectations for each stakeholder
- Contact information for ongoing engagement
- Categorized by stakeholder type

## Output Format

```markdown
# 1. Introduction and Goals

## 1.1 Requirements Overview

[Brief system purpose - 1-2 sentences]

### Essential Features
- <Feature 1: Brief description>
- <Feature 2: Brief description>
- <Feature 3: Brief description>

### Business Context
[1 paragraph: What business problem does this solve? Who benefits?]

### References
- Requirements Document: [Name, Version, Location/Link]

## 1.2 Quality Goals

| Priority | Quality Goal | Concrete Scenario |
|----------|-------------|-------------------|
| 1 | <Q-Goal 1> | <Measurable scenario with numbers> |
| 2 | <Q-Goal 2> | <Measurable scenario with numbers> |
| 3 | <Q-Goal 3> | <Measurable scenario with numbers> |

**Q42 Properties:** #reliable, #flexible, #efficient, #usable, #safe, #secure, #suitable, #operable

## 1.3 Stakeholders

| Role/Name | Contact | Expectations |
|-----------|---------|--------------|
| <Role> | <Email> | <What they need> |
```

## Common Mistakes to Avoid

### ❌ Not Allowed:
1. Starting development without signed quality goals
2. Using buzzwords instead of concrete scenarios
3. Having more than 5 quality goals
4. Confusing project goals with architecture quality goals
5. Including ALL requirements instead of essential ones
6. Omitting stakeholder expectations

### ✅ Desired:
1. Concrete, measurable quality goals with numbers
2. Maximum 3-5 quality goals
3. Signed stakeholder agreement
4. Short requirements overview (< 1 page)
5. Complete stakeholder table
6. Business value explanation

## Integration with Other Sections

### Output for Other Sections:
- **Section 2:** Quality goals influence constraints
- **Section 4:** Quality goals DRIVE solution approaches
- **Section 10:** Detailed scenarios expand quality goals
- **Section 11:** Unachievable goals become risks

## Validation Criteria

- [ ] Less than one page for requirements overview
- [ ] Maximum 5 quality goals (preferably 3)
- [ ] Each goal has measurable scenario
- [ ] **Signed by major stakeholders**
- [ ] All relevant stakeholders identified
- [ ] Can be read in 5-10 minutes

## Official arc42 Tips for Section 1

**Tip 1-1:** Keep requirements overview short
- Maximum 1 page for simple systems
- Link to detailed requirements documents
- Don't duplicate existing documentation

**Tip 1-2:** Quality goals are MANDATORY
- Never start architecture without written, signed quality goals
- Top 3-5 maximum (3 is ideal)
- Must be concrete and measurable

**Tip 1-3:** Make quality goals specific
- Use concrete scenarios with numbers
- "Response time < 200ms" not "fast"
- "99.9% uptime" not "highly available"

**Tip 1-4:** Get stakeholder sign-off
- Quality goals must be agreed by major stakeholders
- Written approval prevents later disputes
- Revisit when priorities shift

**Tip 1-5:** Link to Section 10
- Section 1.2 = top goals summary
- Section 10 = detailed quality scenarios
- Maintain traceability between sections

---
*Based on docs.arc42.org/section-1/ and official arc42 sources*
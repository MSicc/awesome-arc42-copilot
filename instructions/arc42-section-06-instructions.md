# arc42 Section 6: Runtime View - Specific Instructions

## Section Purpose

**Why this section exists:**
Section 6 describes dynamic behavior of the system - how building blocks interact at runtime. It shows concrete scenarios of system execution, helping stakeholders understand operational behavior.

**Value for stakeholders:**
- Shows how static structures (Section 5) come to life
- Documents important use cases and scenarios
- Explains error handling and exceptional situations
- Provides concrete examples of system behavior
- Validates that building blocks work together correctly
- Answers: How do components interact? What happens during execution? How are errors handled?

**Key insight:** Document only the most important scenarios (typically 1-5). Not every possible scenario needs documentation.

## Mandatory Content (ESSENTIAL)

### What MUST be included:

#### Important Runtime Scenarios
- **3-5 key scenarios** showing how building blocks collaborate
- **Sequence of interactions** between components
- **Data exchanged** between components
- **Error handling** for critical scenarios

**Selection criteria for scenarios:**
- Architecturally significant
- Complex interactions
- Critical for understanding
- Frequent or important use cases
- Error/failure scenarios

**NOT needed:**
- Every possible scenario
- Trivial CRUD operations
- Obvious interactions
- Implementation details

## Lean Variant (Minimum Viable Documentation)

### Format:
For each scenario:
1. **Name and brief description**
2. **Simple numbered steps** or bullet points
3. **Participating building blocks**

### Minimum Content:
- 1-3 most important scenarios
- Text description with numbered steps
- Optional: Simple diagrams

### Example Lean Runtime Scenario:

**Scenario: User Search for Product**

Participating components: UI Layer, Search Engine, Product Catalog

Steps:
1. User enters search term in UI Layer
2. UI Layer sends search query to Search Engine
3. Search Engine requests product data from Product Catalog
4. Product Catalog returns matching products
5. Search Engine ranks results
6. Search Engine returns ranked results to UI Layer
7. UI Layer displays results to user

**Error handling:** If Product Catalog unavailable, Search Engine returns cached results.

## Thorough Variant (Complete Version)

### Structure per Scenario:

#### Scenario: <Name>

**Overview:**
[1-2 sentences describing what this scenario shows]

**Preconditions:**
- System state before scenario starts
- Required data/configuration
- User authentication status

**Main Flow:**
[Sequence diagram or numbered steps showing normal execution]

**Alternative Flows:**
[Important variations of the main flow]

**Exception Flows:**
[Error conditions and how they're handled]

**Postconditions:**
- System state after scenario completes
- Data changes
- Side effects

**Quality Attributes:**
- Performance requirements for this scenario
- Security considerations
- Scalability aspects

**Related Scenarios:**
[Links to other scenarios that follow or precede this one]

### Diagram Options:
- UML Sequence Diagrams (recommended)
- UML Activity Diagrams
- BPMN Process Diagrams
- Simple flowcharts
- Text-based sequence descriptions

## Output Format

```markdown
# 6. Runtime View

## Overview
[1-2 paragraphs explaining which scenarios are documented and why these were selected]

## Scenario 1: <Name>

### Overview
[Brief description of what happens]

### Sequence Diagram
![Scenario 1 Sequence](./diagrams/scenario1-sequence.png)

### Step-by-Step Description

1. **[Actor]** → **[Component A]**: <Action>
   - Data: <What data is sent>
   - Protocol: <How it's sent>

2. **[Component A]** → **[Component B]**: <Action>
   - Processing: <What Component A does>
   - Data: <What is sent to B>

3. **[Component B]** → **[Component C]**: <Action>
   [Continue...]

### Alternative Flows

#### Alternative: <Name>
**Condition:** <When this alternative is taken>
**Steps:** [Different steps]

### Error Handling

#### Error: <Error Name>
**Condition:** <What triggers this error>
**Handling:** [How system responds]
**Recovery:** [How system recovers]

### Quality Aspects
- **Performance:** <Response time, throughput>
- **Security:** <Authentication, authorization checks>
- **Availability:** <Fallback mechanisms>

---

## Scenario 2: <Name>
[Repeat structure]
```

## Common Mistakes to Avoid

### ❌ Not Allowed:
1. **Too many scenarios** - Select only important ones (3-5 max)
2. **Trivial scenarios** - Skip obvious CRUD operations
3. **Implementation details** - Stay at architectural level
4. **Missing error handling** - Always document exception flows
5. **Inconsistent building blocks** - Use only components from Section 5
6. **No sequence/order** - Make flow clear and unambiguous
7. **Missing data description** - Show what data is exchanged
8. **No quality aspects** - Link to quality requirements
9. **Isolated scenarios** - Show how scenarios relate
10. **Over-complicated diagrams** - Keep diagrams simple and readable

### ✅ Desired:
1. **Important scenarios only** - 1-5 key scenarios
2. **Clear sequence** - Numbered steps or sequence diagram
3. **Error handling documented** - Show what happens when things go wrong
4. **Consistent with Section 5** - Only use documented building blocks
5. **Appropriate abstraction** - Architectural level, not code
6. **Quality aspects noted** - Performance, security considerations
7. **Data flows shown** - What information is exchanged
8. **Readable diagrams** - Professional, clear, with legend
9. **Alternative flows** - Important variations documented
10. **Related scenarios linked** - Show dependencies between scenarios

## Integration with Other Sections

### Input from Other Sections:
- **Section 1.1:** Important use cases become runtime scenarios
- **Section 3:** External interfaces appear in scenarios
- **Section 5:** Building blocks are the actors in scenarios
- **Section 10:** Quality scenarios may require runtime documentation

### Output for Other Sections:
- **Section 7:** Runtime scenarios influence deployment decisions
- **Section 10:** Scenarios help validate quality requirements
- **Section 11:** Error scenarios may reveal risks

### Critical Consistency Rules:
- **Section 5 ↔ Section 6:** All building blocks in runtime scenarios MUST exist in Section 5
- **Section 6 ↔ Section 10:** Quality scenarios (Section 10) may reference runtime scenarios (Section 6)

## Validation Criteria

### Scenario Selection:
- [ ] 1-5 scenarios documented (not more!)
- [ ] Scenarios are architecturally significant
- [ ] Complex or critical interactions shown
- [ ] Error/failure scenarios included
- [ ] Trivial scenarios excluded

### Scenario Quality:
- [ ] Clear sequence of steps
- [ ] All participating building blocks identified
- [ ] Data exchange documented
- [ ] Error handling described
- [ ] Quality aspects noted
- [ ] Preconditions and postconditions clear

### Consistency:
- [ ] Uses building blocks from Section 5
- [ ] External interfaces match Section 3
- [ ] Scenarios validate Section 1.1 requirements
- [ ] Quality aspects align with Section 10

### Diagrams:
- [ ] Professional sequence or activity diagrams
- [ ] Legend/notation provided
- [ ] Readable and clear
- [ ] Source files maintained

## Official arc42 Tips for Section 6

**Tip 6-1:** Document important scenarios only
- Select 1-5 key scenarios
- Focus on architecturally significant interactions
- Skip trivial or obvious scenarios

**Tip 6-2:** Show how building blocks collaborate
- Use components from Section 5
- Show sequence of interactions
- Document data exchanged

**Tip 6-3:** Include error scenarios
- Don't only document happy path
- Show error handling and recovery
- Document failure modes

**Tip 6-4:** Use sequence diagrams
- UML sequence diagrams are effective
- Show time/sequence clearly
- Include alternatives and error flows

## Scenario Selection Guide

### High Priority (Should Document):
- **Complex choreography** - Multiple components interacting
- **Critical use cases** - Business-critical operations
- **Error scenarios** - How system handles failures
- **Cross-boundary interactions** - Scenarios involving external systems
- **Quality-critical scenarios** - Scenarios testing performance, security, etc.
- **Unusual or surprising flows** - Non-obvious interactions

### Low Priority (Can Skip):
- **Simple CRUD** - Basic create/read/update/delete
- **Obvious sequences** - Trivial interactions
- **Standard patterns** - Well-known interaction patterns
- **Implementation details** - Low-level technical steps

## Diagram Best Practices

### Sequence Diagram Elements:
- **Actors/Components** - Vertical lifelines
- **Messages** - Horizontal arrows
- **Activation boxes** - Show when component is active
- **Return messages** - Dashed arrows
- **Alt/Opt/Loop frames** - Show conditions and repetition
- **Notes** - Explain complex steps

### Keep Diagrams Readable:
- Maximum 7-10 participants per diagram
- Split complex scenarios into multiple diagrams
- Use fragments for alternatives and loops
- Add notes for clarification
- Provide legend for custom notation

---
*Based on docs.arc42.org/section-6/ and official arc42 sources*

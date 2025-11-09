# arc42 Section 5: Building Block View - Specific Instructions

## Section Purpose

**Why this section exists:**
Section 5 documents the static decomposition of the system into building blocks (modules, components, subsystems, classes, interfaces, packages, libraries, frameworks, layers, partitions, tiers, functions, macros, operations, data structures, ...) at multiple levels of abstraction.

**Value for stakeholders:**
- Shows how source code is organized
- Enables developers to find their way through the codebase
- Documents component responsibilities and interfaces
- Hierarchical refinement from coarse to fine-grained
- Provides "map" for understanding implementation
- Answers: How is the system structured? What are the main components? What does each component do?

**Key insight:** "Level-1 is your friend" - The first level of decomposition is MANDATORY and most important.

## Mandatory Content (ESSENTIAL)

### What MUST be included:

#### Level 1 (MANDATORY)
- **White-box diagram** of overall system
- **All top-level building blocks** shown
- **Interfaces between building blocks**
- **Brief responsibility** for each building block
- **Rationale** for this decomposition

**Critical rule:** Level-1 is MANDATORY. Without it, nobody can understand your system structure.

#### Further Levels (Optional)
- Level 2: Refinement of interesting Level-1 blocks
- Level 3+: Further refinement as needed
- Stop when reaching source code level or when further detail adds no value

### Black-box vs. White-box Descriptions

**Black-box (External View):**
- Purpose/responsibility
- Interfaces (provided and required)
- Quality attributes
- Directory/file location
- Dependencies (what it needs)
- Open issues

**White-box (Internal View):**
- Internal structure diagram
- Internal building blocks
- Rationale for internal structure

## Lean Variant (Minimum Viable Documentation)

### Level 1 (MANDATORY):
- **One diagram** showing all top-level components
- **Simple table** with component responsibilities:

| Building Block | Responsibility | Interfaces |
|---------------|----------------|-----------|
| <Component 1> | <What it does> | <Key APIs> |
| <Component 2> | <What it does> | <Key APIs> |

- **Brief decomposition rationale** (1 paragraph)

### Example Lean Level-1:

```
┌────────────────────────────────────────┐
│         Product Search System          │
├────────┬───────────┬──────────┬────────┤
│   UI   │  Search   │ Product  │  Auth  │
│ Layer  │  Engine   │  Catalog │ Service│
└────────┴───────────┴──────────┴────────┘
```

| Component | Responsibility |
|-----------|---------------|
| UI Layer | User interface, displays results |
| Search Engine | Query processing, ranking |
| Product Catalog | Product data management |
| Auth Service | Authentication & authorization |

**Rationale:** Layered architecture separates concerns. Search Engine is isolated for independent scaling.

## Thorough Variant (Complete Version)

### Level 1: Overall System Structure

#### White-box: Overall System

**Purpose:** [Overall system purpose, copied from Section 1.1]

**Diagram:**
[Professional diagram showing all Level-1 building blocks with interfaces]

**Contained Building Blocks:**
[List all Level-1 components]

**Important Interfaces:**
[Describe key interfaces between Level-1 blocks]

**Decomposition Rationale:**
[Why this particular structure? What criteria were used? Link to Solution Strategy]

#### Building Block: <Name of Block 1> (Black-box)

**Purpose/Responsibility:**
[What does this component do? What's its role?]

**Interfaces:**
| Interface | Description | Type | Protocol |
|-----------|-------------|------|----------|
| IF-01 | <Description> | Provided | HTTP REST |
| IF-02 | <Description> | Required | Database |

**Quality Attributes:**
- Performance: [Requirements]
- Scalability: [Approach]
- Security: [Measures]

**Directory/File Location:**
- Source code: `/src/component1/`
- Configuration: `/config/component1/`

**Fulfilled Requirements:**
[Which functional requirements does this component satisfy?]

**Open Issues/Problems:**
- [Known limitations]
- [Technical debt]

### Level 2: Refinement of <Component Name>

**Selection Rationale:**
[Why refine this particular component? Complexity? Size? Critical functionality?]

#### White-box: <Component Name> Internal Structure

**Purpose:**
[Refined understanding of component internals]

**Internal Structure Diagram:**
[Diagram showing internal sub-components]

**Contained Building Blocks:**
[List sub-components]

**Internal Interfaces:**
[Describe how sub-components interact]

**Rationale:**
[Why this internal structure?]

#### Building Block: <Sub-component 1> (Black-box)
[Same structure as Level-1 black-box description]

#### Building Block: <Sub-component 2> (Black-box)
[Same structure as Level-1 black-box description]

### Level 3+: Further Refinements
[Continue pattern as needed]

**Stopping criteria:**
- Reached source code level (classes, functions)
- Further detail adds no architectural value
- Component is simple enough to understand from code
- Team agrees no further documentation needed

## Output Format

```markdown
# 5. Building Block View

## Overview
[1-2 paragraphs explaining the hierarchical decomposition approach]

## Level 1: Overall System (White-box)

### Overview Diagram

![Level 1 Structure](./diagrams/level1-structure.png)

**Legend:**
- [Component] = Building block
- --> = Dependency/uses
- <--> = Bidirectional dependency

### Contained Building Blocks

| Name | Responsibility | Key Interfaces |
|------|---------------|----------------|
| <Block 1> | <What it does> | <IF-01, IF-02> |
| <Block 2> | <What it does> | <IF-03> |

### Decomposition Rationale
[Why this structure? What criteria? How does it support quality goals?]

Links:
- Solution Strategy: See Section 4
- Runtime Behavior: See Section 6

## Building Block: <Name> (Black-box Description)

### Purpose/Responsibility
[What does this block do?]

### Interfaces

| Interface ID | Description | Type | Technology |
|-------------|-------------|------|-----------|
| IF-01 | <Description> | Provided | REST API |
| IF-02 | <Description> | Required | PostgreSQL |

### Quality/Performance Characteristics
- **Performance:** <Requirements>
- **Availability:** <Requirements>
- **Security:** <Measures>

### Directory/File Location
- Source: `/src/<path>/`
- Tests: `/tests/<path>/`

### Fulfilled Requirements
- REQ-001: <Requirement>
- REQ-005: <Requirement>

### Open Issues
- ISSUE-123: <Description>

---

## Level 2: <Component Name> Internal Structure (White-box)

### Refinement Motivation
[Why zoom into this component?]

### Internal Structure Diagram
![Component Internal Structure](./diagrams/<component>-internal.png)

### Internal Building Blocks
[List and describe sub-components]

### Internal Interfaces
[How sub-components communicate]

## Building Block: <Sub-component> (Black-box)
[Repeat black-box template]
```

## Common Mistakes to Avoid

### ❌ Not Allowed:
1. **Skipping Level-1** - This is MANDATORY!
2. **Too many levels** - Stop when reaching code level
3. **Inconsistent notation** - Use same notation throughout
4. **Missing interfaces** - Document how blocks communicate
5. **No rationale** - Always explain WHY this structure
6. **Mixing abstraction levels** - Keep each level consistent
7. **Circular dependencies** - Indicates design problem
8. **Too fine-grained at Level-1** - Start coarse, refine later
9. **No link to source code** - Specify actual locations
10. **Forgetting external interfaces** - Must match Section 3 context
11. **Incomplete black-box descriptions** - Cover all aspects

### ✅ Desired:
1. **Level-1 always present** - Foundation for understanding
2. **Hierarchical refinement** - Top-down, gradual detail
3. **Consistent notation** - UML, C4, or custom with legend
4. **Complete black-box descriptions** - All aspects covered
5. **Clear interfaces** - How components communicate
6. **Rationale at each level** - Why this structure?
7. **Appropriate stopping point** - Don't over-document
8. **Links to source code** - Actual file paths
9. **Consistency with Section 3** - External interfaces match
10. **Traceability to requirements** - Which component satisfies which requirement

## Integration with Other Sections

### Input from Other Sections:
- **Section 3:** External interfaces must appear at Level-1
- **Section 4:** Decomposition strategy guides Level-1 structure

### Output for Other Sections:
- **Section 6:** Runtime scenarios use these building blocks
- **Section 7:** Deployment maps these blocks to infrastructure
- **Section 8:** Cross-cutting concepts may affect all blocks
- **Section 10:** Quality requirements apply to specific blocks

### Critical Consistency Rules:
- **Section 3 ↔ Section 5.1:** External interfaces MUST match
- **Section 5 ↔ Section 6:** Building blocks in runtime scenarios must exist in Level-1 or Level-2
- **Section 5 ↔ Section 7:** Building blocks must map to deployment units

## Validation Criteria

### Level-1 Checklist (MANDATORY):
- [ ] White-box diagram present
- [ ] All top-level components shown
- [ ] Interfaces between components documented
- [ ] Each component has black-box description
- [ ] Decomposition rationale provided
- [ ] External interfaces match Section 3
- [ ] Links to source code directories
- [ ] Notation legend provided

### Black-box Description Checklist:
- [ ] Purpose/responsibility clear
- [ ] All interfaces documented
- [ ] Quality attributes specified
- [ ] Source code location provided
- [ ] Fulfilled requirements listed
- [ ] Open issues noted

### White-box Description Checklist:
- [ ] Internal structure diagram present
- [ ] All internal components listed
- [ ] Internal interfaces documented
- [ ] Rationale for internal structure provided

### Overall Quality:
- [ ] Appropriate abstraction levels (not too many)
- [ ] Consistent with Section 3, 4, 6, 7
- [ ] Helps developers navigate codebase
- [ ] Stakeholders can understand system structure

## Official arc42 Tips for Section 5

**Tip 5-1:** Level-1 is your friend
- Most important level of building block view
- Shows top-level system structure
- MANDATORY - never skip this!
- Foundation for all further refinement

**Tip 5-2:** Use hierarchical refinement
- Start coarse (Level-1)
- Refine interesting/complex/critical components (Level-2)
- Continue only where necessary (Level-3+)
- Stop at appropriate level (usually not beyond Level-3)

**Tip 5-3:** Distinguish black-box from white-box
- Black-box: External view (purpose, interfaces, qualities)
- White-box: Internal view (structure, sub-components)
- Alternate between views as you refine

**Tip 5-4:** Document interfaces explicitly
- How building blocks communicate
- What data is exchanged
- Protocols and formats
- Critical for understanding dependencies

**Tip 5-5:** Link to source code
- Provide actual directory/file paths
- Enables developers to find implementation
- Keeps documentation useful and current

## Notation Options

### Recommended Notations:
1. **C4 Model (Container and Component diagrams)**
2. **UML Component Diagrams**
3. **Informal box-and-line diagrams**
4. **Package/namespace diagrams**

### Key Elements:
- **[Component]** = Building block (box)
- **Interface** = Lollipop or explicit interface symbol
- **Dependency** = Arrow (uses/requires)
- **Composition** = Nested boxes or containment

---
*Based on docs.arc42.org/section-5/ and official arc42 sources*

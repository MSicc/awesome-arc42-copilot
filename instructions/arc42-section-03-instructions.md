# arc42 Section 3: Context and Scope - Specific Instructions

## Section Purpose

**Why this section exists:**
Section 3 defines the system boundary, showing what is part of the system and what is external. It clarifies the interfaces between your system and its environment, establishing clear boundaries of responsibility.

**Value for stakeholders:**
- Defines system scope and boundaries
- Shows external interfaces and communication partners
- Clarifies responsibilities (what's in vs. what's out)
- Provides domain/business perspective AND technical perspective
- Essential foundation for understanding the system
- Answers: What does the system do? What does it NOT do? Who/what does it interact with?

**Key insight:** This is often the most important diagram in the entire documentation - it shows the system in its environment.

## Mandatory Content (ESSENTIAL)

### What MUST be included:

#### 3.1 Business Context
- **Context diagram** showing the system and its business/domain environment
- **External interfaces** from domain/business perspective
- **Input/output relationships** with external entities
- **Communication partners** (users, external systems, organizations)
- **Data exchanged** at business level (WHAT, not HOW)

**Critical rule:** The business context shows WHAT is communicated, not HOW (protocols, formats, etc.)

#### 3.2 Technical Context (Optional but Recommended)
- **Technical interfaces** and channels
- **Protocols, formats, and transmission media**
- **Mapping to technical infrastructure**
- Complements business context with technical details

**Note:** Technical context is optional for simple systems or when technology stack is obvious.

## Lean Variant (Minimum Viable Documentation)

### Business Context (3.1):
- **One context diagram** (C4 System Context or similar)
- **Simple table** listing external entities:

| External Entity | Input to System | Output from System |
|----------------|-----------------|-------------------|
| <Entity 1> | <What data/events> | <What data/events> |
| <Entity 2> | <What data/events> | <What data/events> |

### Technical Context (3.2):
- **Optional** - include only if not obvious
- Brief bullet points of key technical interfaces

### Example Lean Context:

```
[User] --searches--> [Product Search System] --results--> [User]
[Payment Gateway] <--payment data--> [Product Search System]
[Inventory DB] --product data--> [Product Search System]
```

## Thorough Variant (Complete Version)

### Business Context (3.1):

#### Context Diagram
- Professional diagram (C4, UML, custom)
- All external communication partners shown
- Data flows indicated
- Legend/notation key provided
- Large enough to be readable

#### External Interfaces Table

| Interface | Communication Partner | Description | Input (to System) | Output (from System) |
|-----------|---------------------|-------------|-------------------|---------------------|
| IF-01 | User Interface | Web application for end users | Search queries, user actions | Search results, product details |
| IF-02 | Payment Service | Third-party payment processing | Payment confirmations | Payment requests |
| IF-03 | Inventory System | Legacy inventory database | Product data, stock levels | Stock update requests |

#### Domain-Level Data Description
- What information is exchanged (business objects, events, documents)
- Purpose of each interface
- Stakeholders involved
- Business protocols (order of operations, business rules)

### Technical Context (3.2):

#### Technical Context Diagram
- Shows same boundaries as business context
- Adds technical details (protocols, ports, formats)
- Infrastructure elements (load balancers, firewalls, etc.)

#### Technical Interfaces Table

| Interface | Technology | Protocol | Data Format | Port/Endpoint | Authentication |
|-----------|-----------|----------|-------------|---------------|----------------|
| IF-01 | HTTPS | REST | JSON | 443/api/v1 | OAuth 2.0 |
| IF-02 | HTTPS | SOAP | XML | 443/payment | API Key |
| IF-03 | JDBC | SQL | Relational | 5432/postgres | Username/Password |

#### Mapping
- How business interfaces map to technical channels
- Specific protocols, formats, middleware
- Network topology considerations
- Security mechanisms

## Output Format

```markdown
# 3. Context and Scope

## 3.1 Business Context

**Overview:**
[1-2 sentences describing the system's environment and primary interactions]

### Context Diagram

![Business Context Diagram](./diagrams/business-context.png)

**Legend:**
- [System] = The system being documented
- <External Entity> = External systems, users, or organizations
- --> = Data flow / interaction

### External Interfaces

| Interface ID | Partner | Description | Inputs | Outputs |
|-------------|---------|-------------|--------|---------|
| IF-01 | <Partner> | <Purpose> | <What data in> | <What data out> |
| IF-02 | <Partner> | <Purpose> | <What data in> | <What data out> |

### Detailed Interface Descriptions

#### IF-01: <Interface Name>
**Partner:** <External entity>
**Purpose:** <Why this interface exists>
**Business Process:** <How it fits in business workflow>
**Data Exchanged:**
- **Input:** <Business objects/events received>
- **Output:** <Business objects/events sent>

## 3.2 Technical Context (Optional)

**Overview:**
[1-2 sentences on technical implementation of interfaces]

### Technical Context Diagram

![Technical Context Diagram](./diagrams/technical-context.png)

### Technical Interface Details

| Interface ID | Technology | Protocol | Format | Endpoint | Security |
|-------------|-----------|----------|--------|----------|----------|
| IF-01 | <Tech> | <Protocol> | <Format> | <URL/Port> | <Auth method> |
| IF-02 | <Tech> | <Protocol> | <Format> | <URL/Port> | <Auth method> |

### Infrastructure Components
[Description of technical infrastructure elements: load balancers, API gateways, message brokers, etc.]
```

## Common Mistakes to Avoid

### ❌ Not Allowed:
1. **Mixing business and technical concerns** in business context
2. **Showing internal components** in context diagram (context = external view only!)
3. **No clear system boundary** - unclear what's in vs. out
4. **Too much detail** - context should be high-level overview
5. **Inconsistency with Section 5** - external interfaces must match
6. **Missing communication partners** - incomplete view of environment
7. **Using wrong notation** without legend
8. **Showing technology** in business context (HTTPS, REST, etc.)
9. **Ignoring non-human actors** (batch jobs, scheduled tasks, monitoring)
10. **Forgetting to show data flow direction**

### ✅ Desired:
1. **Clear system boundary** - obvious what's inside vs. outside
2. **Business context first** - WHAT is exchanged
3. **Technical context separate** (if needed) - HOW it's exchanged
4. **All external partners shown** - complete environment view
5. **Consistent with Section 5.1** - external interfaces align
6. **Notation legend provided**
7. **Professional diagrams** - readable, clear, well-organized
8. **Bidirectional data flows indicated**
9. **Table complements diagram** - provides detail
10. **Understandable to non-technical stakeholders** (business context)

## Integration with Other Sections

### Output for Other Sections:
- **Section 5.1 (Building Block Level-1):** External interfaces MUST match context boundaries
- **Section 6 (Runtime):** Runtime scenarios often involve external partners
- **Section 7 (Deployment):** Technical context influences deployment
- **Section 10 (Quality):** Interface quality requirements
- **Section 12 (Glossary):** External entities need definitions

### Critical Consistency Rule:
**Section 3 (Context) ↔ Section 5.1 (Building Block Level-1)**
- External interfaces shown in context MUST appear in Level-1
- System boundary MUST be identical
- Communication partners MUST match

## Validation Criteria

### Business Context Checklist:
- [ ] System boundary clearly defined
- [ ] All external communication partners identified
- [ ] Data flows shown and described
- [ ] Diagram understandable to business stakeholders
- [ ] No internal components shown
- [ ] No technical details (protocols, formats) in business context
- [ ] Legend/notation provided
- [ ] Table complements diagram

### Technical Context Checklist:
- [ ] All technical channels documented (if section included)
- [ ] Protocols and formats specified
- [ ] Endpoints/ports documented
- [ ] Security mechanisms described
- [ ] Maps to business context interfaces
- [ ] Infrastructure components identified

### Consistency Checklist:
- [ ] Consistent with Section 5.1 building blocks
- [ ] External interfaces match across sections
- [ ] Glossary terms defined (Section 12)
- [ ] Referenced in runtime scenarios (Section 6)

## Official arc42 Tips for Section 3

**Tip 3-1:** Show your system in its environment
- Context diagram is crucial for understanding
- Defines clear system boundary
- Shows all external interfaces

**Tip 3-2:** Distinguish business from technical context
- Business context: WHAT is communicated (domain perspective)
- Technical context: HOW it's communicated (implementation perspective)
- Keep them separate for clarity

**Tip 3-3:** Keep context view abstract
- High-level overview only
- No internal details
- Focus on external view

## Diagram Notation Options

### Recommended Notations:
1. **C4 Model System Context** - Simple boxes and arrows
2. **UML Use Case Diagram** - Shows actors and system interactions
3. **Informal Box-and-Arrow** - Clear and simple, custom notation
4. **Component Diagram** (UML) - Shows system boundary clearly

### Key Diagram Elements:
- **[System]** - Your system (single box)
- **<External Entity>** - Users, systems, organizations (multiple boxes)
- **Arrows** - Communication/data flow with labels
- **System Boundary** - Clear line/box around your system
- **Legend** - Explains notation used

### Example C4 System Context:

```
┌─────────────┐
│   End User  │
└──────┬──────┘
       │ uses (HTTPS)
       v
┌──────────────────────┐
│                      │
│  Product Search      │◄──────┐
│  System              │       │ reads data
│                      │       │ (JDBC)
└──────┬───────────────┘       │
       │                ┌──────┴──────┐
       │ sends          │  Inventory  │
       │ payments       │  Database   │
       │ (REST/JSON)    │  (Legacy)   │
       v                └─────────────┘
┌──────────────┐
│   Payment    │
│   Gateway    │
└──────────────┘
```

---
*Based on docs.arc42.org/section-3/ and official arc42 sources*

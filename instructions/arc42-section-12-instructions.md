# arc42 Section 12: Glossary - Specific Instructions

## Section Purpose

**Why this section exists:**
Section 12 defines important domain and technical terms used throughout the documentation. It establishes a ubiquitous language that prevents misunderstandings and ensures consistent terminology.

**Value for stakeholders:**
- Prevents misunderstandings through clear definitions
- Establishes shared vocabulary across team and stakeholders
- Helps new team members understand domain language
- Provides translation between business and technical terms
- Essential reference for consistent communication
- Answers: What do we mean by X? What is the official definition of Y?

**Key insight:** This section SHOULD exist for virtually every system. Domain language is always present, even if implicit.

## Mandatory Content (ESSENTIAL)

### What MUST be included:

#### Domain Terms
- **Business concepts** specific to the domain
- **Entities and objects** from the domain model
- **Processes and activities** with special meaning

#### Technical Terms
- **Technology-specific terms** not commonly known
- **Acronyms and abbreviations** used in documentation
- **System-specific terminology**

### For Each Term:
- **Term** (the word or phrase)
- **Definition** (clear, unambiguous explanation)
- **Synonyms** (if any)
- **Related terms** (links to other glossary entries)
- **Examples** (optional, but helpful)

**Note:** Include ONLY terms actually used in the documentation that require definition.

## Lean Variant (Minimum Viable Documentation)

### Format:
Simple alphabetically sorted table

### Minimum Content:
- 10-30 key terms from domain and technical vocabulary
- One-sentence definitions
- Basic structure

### Example Lean Glossary:

| Term | Definition |
|------|------------|
| Account | A customer record in the system containing profile information and order history |
| API Gateway | Central entry point for all external API requests, handles authentication and routing |
| Checkout Process | The sequence of steps a user follows from cart review to payment completion |
| Inventory | Real-time record of available products and their stock levels |
| Microservice | An independently deployable service implementing a single business capability |
| Order | A customer purchase request containing line items, shipping info, and payment details |
| Product Catalog | The master database of all products available for purchase |
| SKU | Stock Keeping Unit - unique identifier for each distinct product variant |
| User Session | A temporary authenticated state for a logged-in user, expires after 1 hour of inactivity |

## Thorough Variant (Complete Version)

### Structure per Term:

#### Term: <n>

**Definition:**
[Clear, unambiguous definition - 1-3 sentences]

**Domain:** [Business | Technical | Hybrid]

**Category:** [Entity | Process | Concept | Technology | Metric]

**Synonyms:**
- [Alternative term 1]
- [Alternative term 2]

**Related Terms:**
- [Link to related glossary entry 1]
- [Link to related glossary entry 2]

**Example:**
[Concrete example showing the term in context]

**Appears In:**
- [Section where this term is used]
- [Section where this term is used]

**Translation:**
[If multilingual system, translations to other languages]

**Historical Note:**
[If term meaning has changed, note previous meaning]

---

### Detailed Example:

#### Term: Order

**Definition:**
A formal customer purchase request submitted through the system, containing one or more product line items, shipping address, payment method, and delivery instructions. Once created, an Order progresses through statuses: Pending → Confirmed → Shipped → Delivered or Cancelled.

**Domain:** Business

**Category:** Entity (Domain Object)

**Synonyms:**
- Purchase Order
- Customer Order
- Sales Order (in financial contexts)

**Related Terms:**
- [Line Item](#line-item) - Individual products within an order
- [Cart](#cart) - Precursor to an order
- [Invoice](#invoice) - Financial document generated from order
- [Fulfillment](#fulfillment) - Process of completing an order

**Example:**
Order #ORD-12345 contains 2 items (SKU-001 × 1, SKU-002 × 2), ships to customer address in Berlin, paid via credit card. Current status: Confirmed, expected delivery: 2025-11-10.

**Appears In:**
- Section 3: Order Service in context diagram
- Section 5: Order Management building block
- Section 6: Order Processing runtime scenario
- Section 12: Related terms (Cart, Invoice, Fulfillment)

**Business Rules:**
- Orders cannot be modified after status changes to "Shipped"
- Order total must be > €0.01
- Maximum 50 line items per order

**Status Transitions:**
Pending → Confirmed (payment successful) → Shipped (dispatched from warehouse) → Delivered (received by customer)

**Historical Note:**
Before v2.0, Orders included status "Backordered" which is now handled separately in Fulfillment.

---

## Output Format

```markdown
# 12. Glossary

## Overview
[1 paragraph explaining the purpose and scope of this glossary]

**Total Terms:** [Number]

**Domains Covered:** Business, Technical, Infrastructure

**Last Updated:** YYYY-MM-DD

---

## Terms (Alphabetical)

### A

#### Account

**Definition:** [Clear definition]

**Synonyms:** Customer Profile, User Account

**Related:** [User](#user), [Order History](#order-history)

---

#### API Gateway

**Definition:** [Clear definition]

**Category:** Technical Infrastructure

**Related:** [Microservice](#microservice), [Authentication](#authentication)

---

### B

#### Backlog

[Continue alphabetically...]

---

## Terms by Category

### Business Domain Terms
- Account
- Cart
- Checkout
- Customer
- Order
- Product

### Technical Terms
- API Gateway
- Container
- Microservice
- Service Mesh

### Infrastructure Terms
- Availability Zone
- Load Balancer
- Replica

### Metrics & Measurements
- Latency
- Throughput
- Uptime

---

## Acronyms and Abbreviations

| Acronym | Full Form | Definition |
|---------|-----------|------------|
| ADR | Architecture Decision Record | Format for documenting architecture decisions |
| API | Application Programming Interface | Contract for software component interaction |
| CI/CD | Continuous Integration/Continuous Deployment | Automated build and deployment pipeline |
| CRUD | Create, Read, Update, Delete | Basic data operations |
| JWT | JSON Web Token | Standard for secure token-based authentication |
| REST | Representational State Transfer | Architectural style for web APIs |
| SKU | Stock Keeping Unit | Unique product identifier |
| SLA | Service Level Agreement | Contractual quality guarantees |

---

## Translations (if multilingual)

| English | Deutsch | Français |
|---------|---------|----------|
| Order | Bestellung | Commande |
| Cart | Warenkorb | Panier |
| Checkout | Kasse | Caisse |

---

## Deprecated Terms

| Term | Replacement | Deprecated Since | Notes |
|------|-------------|-----------------|-------|
| Shopping Basket | Cart | v2.0 | Standardized terminology |
| Backordered | Awaiting Stock | v2.5 | Clearer status name |
```

## Common Mistakes to Avoid

### ❌ Not Allowed:
1. **Circular definitions** - Defining term A using term B, and B using A
2. **Ambiguous definitions** - Vague or unclear explanations
3. **Missing commonly used terms** - If it's in docs, define it
4. **Too many trivial terms** - Don't define universally known words
5. **Inconsistent usage** - Using term differently in different sections
6. **No examples** - Abstract definitions without context
7. **Outdated definitions** - Not updating when meaning changes
8. **Using undefined terms in definitions** - All terms in definition should be clear or also defined
9. **Missing acronyms** - Define all abbreviations used
10. **Forgetting synonyms** - Not noting alternative terms

### ✅ Desired:
1. **Clear, unambiguous definitions** - No room for misinterpretation
2. **Alphabetically sorted** - Easy to find terms
3. **Complete coverage** - All domain and technical terms defined
4. **Examples provided** - Concrete illustrations
5. **Synonyms noted** - Alternative terms documented
6. **Related terms linked** - Cross-references to connected concepts
7. **Consistent with documentation** - Terms used as defined
8. **Regular updates** - Keep current as terminology evolves
9. **Stakeholder validated** - Business stakeholders agree on domain terms
10. **Appropriate scope** - Neither too broad nor too narrow

## Integration with Other Sections

### Input from Other Sections:
- **ALL sections** - Any domain or technical term used in documentation should be defined here

### Output for Other Sections:
- **ALL sections** - Provides reference for terminology used throughout

### Ubiquitous Language:
- Glossary establishes **Domain-Driven Design** ubiquitous language
- Terms should match actual code (class names, method names, etc.)
- Business stakeholders should understand and agree with domain terms

## Validation Criteria

- [ ] All domain-specific terms defined
- [ ] All technical acronyms explained
- [ ] All system-specific terminology included
- [ ] Definitions clear and unambiguous
- [ ] Alphabetically organized
- [ ] Examples provided for complex terms
- [ ] Synonyms documented
- [ ] Related terms cross-referenced
- [ ] Business stakeholders validated domain terms
- [ ] Consistent with actual code/implementation
- [ ] Updated regularly

## Official arc42 Tips for Section 12

**Tip 12-1:** Use ubiquitous language
- Establish shared vocabulary
- Same terms in docs, code, and conversations
- Business and technical stakeholders aligned

**Tip 12-2:** Define domain-specific terms
- Every domain has special vocabulary
- Don't assume everyone knows domain language
- Essential for new team members

**Tip 12-3:** Include technical terms
- Define acronyms and abbreviations
- Explain technology-specific terminology
- Don't assume technical knowledge

**Tip 12-4:** Keep it updated
- Add terms as documentation grows
- Update definitions if meaning changes
- Remove obsolete terms (mark as deprecated)

**Tip 12-5:** Validate with stakeholders
- Business stakeholders confirm domain terms
- Technical team confirms technical terms
- Resolve terminology conflicts

## Term Categories

### Business/Domain Terms:
Focus on concepts from the problem domain:
- Entities (Customer, Order, Product)
- Processes (Checkout, Fulfillment, Returns)
- Concepts (Loyalty Program, Prime Membership)
- Roles (Administrator, Customer, Vendor)
- Events (Order Placed, Payment Received)
- States (Pending, Confirmed, Shipped)

### Technical Terms:
Focus on solution domain concepts:
- Architecture patterns (Microservice, Event Sourcing)
- Technologies (Kubernetes, PostgreSQL, React)
- Infrastructure (Load Balancer, Container, Pod)
- Development concepts (CI/CD, TDD, Pair Programming)
- Security concepts (OAuth, JWT, Encryption)

### Metrics and Measurements:
Quantifiable aspects:
- Performance metrics (Latency, Throughput, Response Time)
- Availability metrics (Uptime, MTBF, MTTR)
- Business metrics (Conversion Rate, Cart Abandonment)
- Quality metrics (Code Coverage, Technical Debt Ratio)

## Glossary Management

### Adding New Terms:
1. Encounter unfamiliar term in documentation
2. Draft definition
3. Identify synonyms and related terms
4. Provide example
5. Validate with subject matter experts
6. Add to glossary alphabetically

### Reviewing Glossary:
- **Quarterly review** of all terms
- Check for:
  - Outdated definitions
  - Missing terms
  - Inconsistent usage
  - Need for examples or clarification

### Handling Conflicts:
- When same term has multiple meanings:
  - Option 1: Use fully qualified terms (Business Customer vs. Technical Customer)
  - Option 2: Choose primary definition, note alternatives
  - Option 3: Context-specific definitions (noted in glossary)

---
*Based on docs.arc42.org/section-12/ and official arc42 sources*

# arc42 Section 2: Constraints - Specific Instructions

## Section Purpose

**Why this section exists:**
Section 2 documents any requirements that constrain architects in their freedom of design, implementation decisions, or development process. Architects need to know exactly where they are free in their design decisions and where they must adhere to constraints.

**Value for stakeholders:**
- Defines boundaries of architectural freedom
- Prevents violations of organizational/legal requirements
- Prevents costly mistakes
- Clarifies non-negotiable vs. negotiable constraints
- Influences ALL subsequent architectural decisions
- Sometimes applies beyond individual systems to entire organizations

**Key insight:** Constraints MUST always be dealt with, though some may be negotiable with proper justification.

## Mandatory Content (ESSENTIAL)

### What MUST be included:
- **Any requirement that constrains design freedom**
- **Organizational constraints** affecting the development process
- **Technical constraints** limiting technology choices
- **Political constraints** from company policy or regulations
- **Conventions** that must be followed

### Each constraint should document:
- The constraint itself (what is restricted)
- Background/rationale (WHY this constraint exists)
- Who/what authority imposed this constraint
- Whether constraint is negotiable or non-negotiable
- Impact on architecture

## Lean Variant (Minimum Viable Documentation)

### Format:
Simple table with two columns:

| Constraint | Rationale |
|-----------|-----------|
| <Constraint description> | <Brief explanation why> |

### Minimum Content:
- List only constraints directly affecting THIS system
- Brief one-sentence explanations
- Focus on **non-negotiable** constraints
- 5-15 key constraints typical

### Example:
| Constraint | Rationale |
|-----------|-----------|
| Must use IBM DB2 database | Long-term enterprise license contract |
| Deploy in data-center XYZ only | Corporate security policy |
| Platform-independent (Windows, Linux, Mac) | User base requirement |
| Java 17 or higher | Company standardization on modern Java |
| All data must remain in EU | GDPR compliance requirement |

## Thorough Variant (Complete Version)

### Subdivided Categories:

#### 1. Technical Constraints
- Hardware requirements and limitations
- Technology choices (languages, frameworks, tools)
- Operating system requirements
- Middleware and database requirements
- Reference architectures to follow
- Development tools and IDEs
- Implementation technology decisions
- Product/framework usage requirements
- API or protocol requirements

#### 2. Organizational Constraints
- Team structure and composition
- Budget limitations
- Time constraints and deadlines
- Development process requirements (agile, waterfall, etc.)
- Required information flows and reporting
- Compliance with standard processes
- Documentation templates and conventions
- Offshore/distributed development requirements
- Long-term vendor contracts
- Licensing restrictions

#### 3. Political Constraints
- Company-wide technology decisions
- Government regulations (GDPR, HIPAA, etc.)
- Industry standards compliance (ISO, IEEE, etc.)
- Internal politics affecting decisions
- Executive mandates
- Legacy system integration requirements

#### 4. Conventions
- Programming guidelines and standards
- Documentation conventions
- Naming conventions
- Versioning guidelines
- Code style requirements (linting rules)
- Git workflow conventions
- Review and approval processes

## Output Format

```markdown
# 2. Constraints

This section documents constraints that restrict our freedom of design, implementation, or process. All architectural decisions must work within these boundaries.

## 2.1 Technical Constraints

| Constraint | Rationale | Authority | Negotiable |
|-----------|-----------|-----------|-----------|
| <TC-1> | <Why> | <Who/What> | Yes/No |
| <TC-2> | <Why> | <Who/What> | Yes/No |

## 2.2 Organizational Constraints

| Constraint | Rationale | Authority | Negotiable |
|-----------|-----------|-----------|-----------|
| <OC-1> | <Why> | <Who/What> | Yes/No |

## 2.3 Political Constraints

| Constraint | Rationale | Authority | Negotiable |
|-----------|-----------|-----------|-----------|
| <PC-1> | <Why> | <Who/What> | Yes/No |

## 2.4 Conventions

| Convention | Rationale | Authority | Negotiable |
|-----------|-----------|-----------|-----------|
| <CON-1> | <Why> | <Who/What> | Yes/No |
```

## Common Mistakes to Avoid

### ❌ Not Allowed:
1. Treating all constraints as non-negotiable
2. Mixing constraints with requirements
3. Ignoring organizational constraints
4. Documenting constraints without rationale
5. Omitting constraint categories
6. Not challenging unreasonable constraints
7. Hiding constraints
8. Confusing guidelines with mandatory constraints
9. Failing to document constraint authority
10. Not updating when constraints change
11. Being too abstract
12. Documenting every tiny restriction

### ✅ Desired:
1. Clear categorization (Technical, Organizational, Political, Conventions)
2. Explicit rationale for every constraint
3. Authority documentation (who/what imposed this)
4. Negotiability status clear
5. Impact analysis
6. Regular review and updates
7. Specific and concrete
8. Honest documentation
9. Alternative consideration
10. Links to Section 9 decisions
11. Scope clarity (system-specific vs. organization-wide)
12. Challenge process documented

## Integration with Other Sections

### Output for Other Sections:
- **Section 4:** Constraints HEAVILY influence solution approaches
- **Section 5:** May restrict technology/framework choices
- **Section 7:** Hardware/infrastructure constraints define deployment
- **Section 8:** May mandate specific patterns or approaches
- **Section 9:** Constraints limit available decision options
- **Section 11:** Unreasonable or conflicting constraints become risks

## Validation Criteria

- [ ] All technical constraints documented
- [ ] All organizational constraints identified
- [ ] Political constraints acknowledged
- [ ] Conventions clearly stated
- [ ] Each constraint has rationale
- [ ] Negotiability status clear
- [ ] Authority/source identified
- [ ] Impact on architecture explained
- [ ] Updated when constraints change
- [ ] No confusion with requirements

---
*Based on docs.arc42.org/section-2/ and official arc42 sources*

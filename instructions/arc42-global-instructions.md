# arc42 Architecture Documentation - Global Instructions

## What is arc42?

arc42 is a proven, open-source template for software architecture documentation created by Dr. Gernot Starke and Dr. Peter Hruschka in 2005. Used successfully in thousands of projects worldwide, it provides a pragmatic, tool-agnostic approach to documenting software architectures.

## Core Philosophy

### Pragmatic & Economical
- **Document economically** but continuously
- "Painless documentation" - only what stakeholders truly need
- "Travel light" - especially in agile environments
- Balance effort against value

### Optional Compartments ("Cabinet Metaphor")
- Arc42 is like a cabinet with 12 drawers/compartments
- **ALL compartments are OPTIONAL**
- "The cabinet has value even if certain compartments remain empty"
- Create content in ANY order your project requires
- Reading order (1→12) optimized for understandability
- Creation order: Whatever works for your project

### Top-Down Organization
- Start with overview, gradually add details
- Facilitate navigation from high-level to specifics
- Makes architecture accessible to all stakeholders

### Tool & Technology Agnostic
- Works with any tool: wikis, Office, Markdown, AsciiDoc, UML tools, LaTeX
- Completely process-agnostic
- Suitable for arbitrary systems and domains

## The 12 Sections Overview

### 1. Introduction and Goals
**Essential requirements and driving forces**
- Why does the system exist?
- Top 3-5 quality goals
- Key stakeholders and their expectations

### 2. Constraints
**Boundaries of architectural freedom**
- Technical, organizational, political constraints
- Non-negotiable requirements
- Long-term decisions limiting choices

### 3. Context and Scope
**System boundaries and external interfaces**
- Business context (domain perspective)
- Technical context (optional)
- External communication partners

### 4. Solution Strategy
**Fundamental decisions and approaches**
- Technology choices
- Decomposition strategy
- Approaches to achieve quality goals

### 5. Building Block View
**Static structure and decomposition**
- Source code organization
- Hierarchical building blocks (Level 1, 2, 3+)
- **Level-1 is mandatory** ("Level-1 is your friend")

### 6. Runtime View
**Dynamic behavior and interactions**
- Important runtime scenarios (1-5 typically)
- How building blocks cooperate
- Operation and error handling

### 7. Deployment View
**Hardware and infrastructure**
- Technical infrastructure
- Mapping of software to hardware
- Multiple environments

### 8. Crosscutting Concepts
**Recurring patterns and approaches**
- Domain models
- Security, persistence, error handling
- Architecture and design patterns
- **Most flexible section** - pick only needed topics

### 9. Architecture Decisions
**Important decisions with rationale**
- Architecturally significant decisions
- Use ADR (Architecture Decision Record) format
- Document WHY, not just WHAT

### 10. Quality Requirements
**Detailed quality scenarios**
- Elaborates on Section 1.2 quality goals
- Concrete, measurable scenarios
- Quality tree overview

### 11. Risks and Technical Debt
**Known problems and risks**
- Technical risks ordered by priority
- Technical debt documentation
- Mitigation strategies

### 12. Glossary
**Domain and technical terminology**
- Ubiquitous language
- Translation reference
- Essential for shared understanding

## Three Documentation Approaches

### LEAN (Agile/Minimal)
**When to use:** Agile teams, time-constrained projects, evolving systems

**Characteristics:**
- Focus on essential information only
- 1-3 pages per section maximum
- Quick to create and maintain
- "Dare to leave gaps" philosophy

**Minimum sections:**
- Section 1.2: Quality Goals
- Section 3: Context
- Section 5.1: Building Block Level-1
- Section 9: Key Decisions
- Section 12: Glossary

### ESSENTIAL (Core Information)
**When to use:** All projects should include these basics

**Characteristics:**
- Non-negotiable minimum
- Critical architectural information
- Enables basic understanding

**Includes everything in LEAN plus:**
- Section 1.1: Requirements Overview
- Section 1.3: Stakeholder Table
- Section 2: Critical Constraints
- Section 4: Solution Strategy Overview

### THOROUGH (Comprehensive)
**When to use:** Critical systems, formal environments, audit requirements, large teams

**Characteristics:**
- Complete documentation
- Detailed scenarios and specifications
- Multiple refinement levels
- Extensive validation

**Includes:**
- All 12 sections fully documented
- Multiple building block levels
- Comprehensive quality scenarios
- Detailed deployment configurations
- Complete crosscutting concepts

## Quality Principles for Documentation

### Content Requirements
1. **Correct** - Never allow incorrect information (highest priority)
2. **Current** - Regular reviews, focus on important aspects
3. **Understandable** - Clear terms, optimized structure, audience-appropriate
4. **Relevant** - Task-oriented, serves stakeholder purposes

### Formal Requirements
5. **Referenceable** - Numbered sections, diagrams, tables; provide TOC
6. **Proper Language** - Grammatically correct, concise (15-20 word sentences), active voice
7. **Maintainable** - Structure optimized for easy updates

### Process Requirements
8. **Easy to Find** - Well-known locations, templates, top-down organization
9. **Version Controlled** - Track changes, rollback capability
10. **Appropriate Tools** - Support structure, diagrams, reviews
11. **Continuously Updated** - Include in Definition-of-Done, reserve timeboxes

## Best Practices

### Diagrams
- Combine diagrams with text/tables (remove ambiguity)
- Provide legend or use standard notation (UML, C4, ArchiMate)
- Keep source files for all diagrams
- Restrict to higher abstraction levels
- Stick to single topic per diagram

### Abstraction
- Prefer abstract over detailed information
- Omit details to facilitate change
- Document aggregations instead of all elements

### Structure
- Use fixed structures (like arc42) for findability
- Organize top-down
- Use cross-references and hyperlinks liberally

### Avoid Redundancy
- Single source of truth principle
- Use references instead of duplication
- Link between related sections

## Resources

- Main site: https://arc42.org
- Documentation: https://docs.arc42.org
- FAQ: https://faq.arc42.org
- Quality model: https://quality.arc42.org

---
*Based on official arc42 documentation | Version 1.0 | November 2025*

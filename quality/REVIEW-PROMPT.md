# arc42 Quality Assurance Review Prompt

## Purpose
This prompt guides systematic review of arc42 documentation files (instructions + prompts) for accuracy, completeness, consistency, and alignment with official arc42 standards.

---

## Review Process Overview

**For each Section (1-12):**
1. Review instruction file against arc42 standards
2. Review prompt file for LLM effectiveness
3. Check consistency between instruction and prompt
4. Validate against global arc42 principles
5. Cross-check with other sections
6. Document findings and improvements

---

## Prompt Template for Section Review

Use this prompt for each section review:

```
I need you to review arc42 Section [XX] files for quality and accuracy.

**Files to Review:**
- arc42-section-[XX]-instructions.md
- arc42-section-[XX]-prompt.md

**Review Dimensions:**

### 1. ACCURACY CHECK (vs. Official arc42 Standards)

**Primary Sources to Validate Against:**
- https://docs.arc42.org/section-[XX]/
- https://faq.arc42.org/ (for clarifications)
- https://arc42.org/overview (for section overview)

**Check:**
- [ ] All mandatory content from official arc42 included?
- [ ] Section purpose accurately described?
- [ ] Examples align with official arc42 examples?
- [ ] Tips from docs.arc42.org incorporated?
- [ ] No contradictions with official guidance?
- [ ] Terminology matches arc42 standard terms?

**Questions:**
1. Is anything missing from the official arc42 section description?
2. Are there any inaccuracies or misinterpretations?
3. Do the examples reflect official arc42 guidance?

---

### 2. COMPLETENESS CHECK

**For Instruction File:**
- [ ] Section Purpose clearly explained?
- [ ] Mandatory Content (ESSENTIAL) defined?
- [ ] Lean Variant provided?
- [ ] Thorough Variant provided?
- [ ] Output Format template complete?
- [ ] Common Mistakes listed (❌ Not Allowed)?
- [ ] Best Practices listed (✅ Desired)?
- [ ] Integration with other sections documented?
- [ ] Validation criteria provided?
- [ ] Official arc42 tips included?

**For Prompt File:**
- [ ] System Prompt clear and actionable?
- [ ] ALWAYS behaviors defined?
- [ ] NEVER behaviors defined?
- [ ] Input Template provided for users?
- [ ] Output Template ready to use?
- [ ] Quality Checks included?
- [ ] Examples of good vs. bad provided?
- [ ] LLM-optimized (clear, specific instructions)?

**Questions:**
1. Is anything critical missing from either file?
2. Are templates complete and copy-paste ready?
3. Would a developer understand how to use these files?

---

### 3. INSTRUCTION ↔ PROMPT CONSISTENCY

**Check Alignment:**
- [ ] Prompt reflects key points from instruction?
- [ ] ALWAYS/NEVER rules match instruction guidance?
- [ ] Output template in prompt matches instruction format?
- [ ] Quality checks in prompt cover validation criteria from instruction?
- [ ] Examples consistent between files?
- [ ] Terminology consistent?

**Questions:**
1. Do instruction and prompt tell the same story?
2. Are there contradictions between the two files?
3. Would following the prompt produce output matching instruction expectations?

---

### 4. GLOBAL PRINCIPLES CHECK

**Validate Against arc42 Global Principles:**
- [ ] Respects "all sections optional" principle?
- [ ] Supports Lean/Essential/Thorough approaches?
- [ ] Encourages pragmatic documentation?
- [ ] "Travel light" philosophy reflected?
- [ ] Stakeholder-focused?
- [ ] Tool-agnostic advice?
- [ ] Top-down organization?
- [ ] Avoids over-documentation warnings?

**Questions:**
1. Does this section respect arc42's pragmatic philosophy?
2. Is it flexible enough for different project sizes?
3. Does it avoid being prescriptive about tools?

---

### 5. CROSS-SECTION CONSISTENCY

**Check Relationships with Other Sections:**

For this section, validate:
- [ ] Input dependencies clearly stated?
- [ ] Output dependencies clearly stated?
- [ ] References to other sections accurate?
- [ ] No contradictions with other sections?
- [ ] Critical consistency rules documented?

**Specific Checks:**
- Section 1.2 Quality Goals → Referenced in Sections 4, 10?
- Section 3 External Interfaces → Match Section 5.1?
- Section 5 Building Blocks → Used in Sections 6, 7?
- Section 4 Solution Strategy → Summarizes Section 9 decisions?

**Questions:**
1. Are all cross-section dependencies documented?
2. Are there consistency requirements missing?
3. Would following this section create conflicts with others?

---

### 6. QUALITY & USABILITY

**Check Quality:**
- [ ] Writing is clear and concise?
- [ ] Examples are concrete and helpful?
- [ ] No jargon without explanation?
- [ ] Formatting consistent?
- [ ] Headers properly structured?
- [ ] Code blocks properly formatted?
- [ ] Tables properly structured?

**Check Usability:**
- [ ] Can be understood in 5-10 minutes?
- [ ] Templates are copy-paste ready?
- [ ] Instructions actionable?
- [ ] Checklists useful?
- [ ] Examples illustrative?

**Questions:**
1. Is this ready for production use?
2. Would a developer find this helpful?
3. Are there confusing or unclear parts?

---

### 7. LLM OPTIMIZATION (Prompt File Only)

**Check LLM Effectiveness:**
- [ ] Instructions clear and unambiguous for LLMs?
- [ ] Examples provided (good vs. bad)?
- [ ] Input template guides user effectively?
- [ ] Output template structures LLM response?
- [ ] Quality checks enable self-validation?
- [ ] Avoids common LLM pitfalls?

**Questions:**
1. Would GitHub Copilot/Cursor/Claude Code understand this?
2. Is the prompt specific enough to avoid vague output?
3. Does it help LLMs avoid common mistakes?

---

## OUTPUT FORMAT

After reviewing Section [XX], provide:

### Summary
[2-3 sentences: Overall quality assessment]

### Findings

#### ✅ Strengths
- [What's done well]
- [What's accurate and complete]
- [What's particularly helpful]

#### ⚠️ Issues Found

**Critical Issues (Must Fix):**
- [ ] Issue 1: [Description]
  - **Impact:** [Why this matters]
  - **Fix:** [What to do]
  - **Source:** [Official arc42 reference if applicable]

**Minor Issues (Should Fix):**
- [ ] Issue 2: [Description]
  - **Impact:** [Why this matters]
  - **Fix:** [What to do]

#### 💡 Improvement Suggestions (Nice to Have)
- [Suggestion 1]
- [Suggestion 2]

### Consistency Check Results

**Cross-Section Dependencies:**
- [ ] All dependencies documented correctly
- [ ] No contradictions with other sections
- Issues: [List any found]

**Instruction ↔ Prompt Alignment:**
- [ ] Files are consistent
- Issues: [List any misalignments]

### Recommended Actions

**Priority 1 (Do Now):**
1. [Action item]
2. [Action item]

**Priority 2 (Do Soon):**
1. [Action item]
2. [Action item]

**Priority 3 (Consider):**
1. [Action item]

### Approval Status

- [ ] **APPROVED** - Ready for production use
- [ ] **APPROVED WITH MINOR CHANGES** - Usable, but improvements recommended
- [ ] **NEEDS REVISION** - Critical issues must be fixed before use

---

## Next Steps After Review

1. Address Priority 1 actions
2. Update files based on findings
3. Re-review changed sections
4. Move to next section

```

---

## Additional Notes

**When to Flag as Critical:**
- Contradicts official arc42 guidance
- Missing mandatory content
- Would lead users to create incorrect documentation
- Inconsistent with other sections in a way that breaks arc42 structure

**When to Flag as Minor:**
- Could be clearer but not wrong
- Missing nice-to-have examples
- Formatting inconsistencies
- Minor wording improvements

**When to Suggest:**
- Additional helpful examples
- Better formatting
- Enhanced explanations
- Additional cross-references

---

## Review Sequence Recommendation

**Start with Core Sections (Foundation):**
1. Section 1 (Introduction & Goals) - Sets foundation
2. Section 5 (Building Block View) - Core structure
3. Section 3 (Context & Scope) - Must align with Section 5

**Then Connecting Sections:**
4. Section 4 (Solution Strategy) - Bridges 1 and 5
5. Section 2 (Constraints) - Influences all sections
6. Section 10 (Quality Requirements) - Elaborates Section 1

**Then Detailed Sections:**
7. Section 6 (Runtime View) - Uses Section 5
8. Section 7 (Deployment View) - Uses Section 5
9. Section 8 (Crosscutting Concepts) - Affects multiple sections
10. Section 9 (Architecture Decisions) - Supports Section 4

**Finally Supporting Sections:**
11. Section 11 (Risks & Technical Debt) - References others
12. Section 12 (Glossary) - Supports all sections

---

## Success Criteria

The review is successful when:
- [ ] All 12 sections reviewed systematically
- [ ] Critical issues identified and fixed
- [ ] Consistency across all sections verified
- [ ] Files are production-ready
- [ ] Quality meets arc42 official standards
- [ ] Usable by development teams with LLM tools

---

*Based on arc42.org, docs.arc42.org, quality.arc42.org, faq.arc42.org*
*Review Protocol Version 1.0 | November 2025*

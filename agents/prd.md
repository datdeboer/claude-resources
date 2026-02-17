# Agent Instructions: Write a Product Requirements Document (PRD)

You are a senior product manager creating a comprehensive PRD. Follow these instructions carefully to produce a well-structured, actionable document that aligns engineering, design, and business stakeholders.

## Before You Start

1. **Gather context** before writing anything:
   - Read any existing docs in the project's `/docs/` folder for business context, conventions, or prior PRDs
   - Read `CLAUDE.md` or `README.md` at the project root for project overview and architecture
   - If a specific feature or problem was mentioned, search the codebase to understand what exists today
   - Ask clarifying questions if the problem statement, scope, or success criteria are ambiguous

2. **Determine the PRD type** based on what's being built:
   - **New Product PRD** - Greenfield product with vision, milestones, and full roadmap
   - **Feature PRD** - Addition to an existing product with focused scope
   - **Enhancement PRD** - Improvement to existing functionality with clear before/after

## Output Location

Save the PRD as a markdown file at: `/docs/prds/[feature-name]-prd.md`

Create the `/docs/prds/` directory if it doesn't exist.

---

## PRD Structure

Use the following sections. Adjust depth based on PRD type — a small feature enhancement needs less than a full product PRD.

### 1. Title & Metadata

```markdown
# [Feature/Product Name] - Product Requirements Document

| Field          | Value                          |
| -------------- | ------------------------------ |
| Author         | [Name]                         |
| Status         | Draft / In Review / Approved   |
| Created        | [Date]                         |
| Last Updated   | [Date]                         |
| Stakeholders   | [List key people/teams]        |
| Target Release | [Date or milestone]            |
```

### 2. Executive Summary

Write 3-5 sentences that answer:
- What are we building?
- Why are we building it?
- Who is it for?
- What does success look like?

This section should be sufficient for an executive to understand the proposal without reading further. Lead with the business impact.

### 3. Problem Statement

Structure this section with:

- **User Problem**: What pain point or unmet need exists? Be specific — reference real user feedback, support tickets, or observed behavior when available.
- **Business Impact**: Why does this matter to the business? Quantify where possible (revenue impact, churn risk, competitive pressure, operational cost).
- **Evidence**: What data supports this? Include metrics, user quotes, research findings, or competitive analysis. If evidence is limited, state assumptions explicitly.
- **Current State**: How do users solve this problem today? What's the workaround? Why is the workaround insufficient?

### 4. Goals & Success Metrics

Define 3-5 measurable goals using this format:

| Goal | Metric | Target | How Measured |
| ---- | ------ | ------ | ------------ |
| Increase user activation | % users completing onboarding | 60% (up from 40%) | Analytics event tracking |
| Reduce support load | Tickets related to [topic] | 50% reduction | Support ticket tags |

Guidelines:
- Every goal must have a measurable metric with a specific target
- Include both leading indicators (adoption, usage) and lagging indicators (retention, revenue)
- Define the measurement method — vague metrics are useless
- Distinguish between primary goals (must hit) and secondary goals (nice to have)

### 5. User Stories & Requirements

Group user stories by priority using MoSCoW or P0/P1/P2:

**P0 — Must Have (Launch Blockers)**
Requirements that are essential. The feature does not ship without these.

**P1 — Should Have (Expected)**
Requirements that are important but have workarounds if delayed.

**P2 — Nice to Have (Enhancements)**
Requirements that add polish or cover edge cases. Can be deferred.

Format each user story as:

```markdown
#### [Story Title]

**User Stories:**
- As a [user type], I want to [action] so that [benefit].

**Acceptance Criteria:**
- [Specific, testable condition]
- [Another testable condition]

**Tasks:**
- [ ] [Implementation task]
- [ ] [Another task]
```

Guidelines for writing good user stories:
- Focus on the user's goal, not the implementation
- Acceptance criteria should be testable — avoid subjective language like "should feel fast"
- Include performance criteria where relevant (e.g., "loads in under 2 seconds")
- Consider error states and edge cases in acceptance criteria
- Include both happy path and failure scenarios

### 6. Solution Overview

Describe the proposed solution at a level appropriate for cross-functional alignment:

- **Approach**: High-level description of the solution. What is the strategy?
- **Key Features**: Bullet list or table of the main capabilities being delivered
- **User Flow**: Describe the primary user journey step by step. Include wireframes or mockups if available.
- **Out of Scope**: Explicitly list what this PRD does NOT cover. This prevents scope creep and aligns expectations.

### 7. Technical Considerations

This section is for engineering context, not a full technical design doc. Include:

- **Architecture Impact**: Does this require new services, databases, or infrastructure?
- **Dependencies**: What existing systems, APIs, or teams does this depend on?
- **Technical Constraints**: Performance requirements, platform limitations, backward compatibility needs
- **Data Model Changes**: High-level description of new or modified data entities
- **Security & Privacy**: Any authentication, authorization, PII handling, or compliance requirements

Do NOT write implementation code in the PRD. Reference a separate technical design doc if deep technical detail is needed.

### 8. Design Considerations

- **UX Requirements**: Key interaction patterns, accessibility needs, responsive behavior
- **Visual Design**: Reference existing design system components where applicable
- **Content/Copy**: Any specific messaging, empty states, or error messages that need writing

### 9. Milestones & Phasing

Break the work into shippable increments:

```markdown
### Phase 1: [Name] — [Target Date]
**Goal:** [What users can do after this phase]
- [Feature/capability A]
- [Feature/capability B]

### Phase 2: [Name] — [Target Date]
**Goal:** [What users can do after this phase]
- [Feature/capability C]
- [Feature/capability D]
```

Guidelines:
- Each phase should deliver user value on its own
- Phase 1 should be the minimum viable version that solves the core problem
- Later phases add refinement, edge cases, and advanced features
- Include clear criteria for moving between phases

### 10. Risks & Mitigations

| Risk | Likelihood | Impact | Mitigation |
| ---- | ---------- | ------ | ---------- |
| [Description] | High/Med/Low | High/Med/Low | [How we'll address it] |

Consider:
- Technical risks (performance, integration complexity, new technology)
- Business risks (market timing, competitive response, adoption uncertainty)
- Resource risks (team capacity, dependencies on other teams)
- User risks (behavior change required, migration complexity)

### 11. Open Questions

List unresolved decisions or information gaps:

- [ ] [Question that needs answering before or during implementation]
- [ ] [Decision that needs stakeholder input]
- [ ] [Assumption that needs validation]

Include who needs to answer each question and any deadlines.

### 12. Appendix (Optional)

- Links to research documents, competitive analysis, or user interview summaries
- Reference to related PRDs or technical design docs
- Glossary of domain-specific terms

---

## Writing Guidelines

### Be Specific and Actionable
- Bad: "The feature should be fast"
- Good: "Search results return in under 500ms for libraries of up to 10,000 items"

### Quantify Impact
- Bad: "This will improve retention"
- Good: "We expect this to reduce 30-day churn by 15% based on exit survey data showing X as the #2 cancellation reason"

### Focus on Why, Not Just What
Every requirement should connect back to a user need or business goal. If you can't explain why something matters, question whether it belongs in the PRD.

### Write for Your Audience
- Executives read the summary and goals
- Designers read the user stories and UX requirements
- Engineers read the acceptance criteria and technical considerations
- Everyone reads the scope and out-of-scope sections

### Keep It Maintainable
- Use task checkboxes (`- [ ]`) so progress can be tracked in the document
- Use tables for structured data (metrics, risks, comparisons)
- Use clear headings so sections can be linked to directly

### Separate Problem from Solution
The problem statement and goals should be stable even if the solution changes. Write them independently — a strong problem definition survives multiple solution pivots.

---

## Checklist Before Finalizing

Before presenting the PRD, verify:

- [ ] Executive summary is understandable without reading the full document
- [ ] Problem statement includes evidence, not just assertions
- [ ] Every goal has a measurable metric and target
- [ ] User stories cover the primary user journey end to end
- [ ] Acceptance criteria are specific and testable
- [ ] Out of scope section exists and is explicit
- [ ] Risks are identified with mitigations
- [ ] Open questions are listed with owners
- [ ] Milestones deliver incremental user value
- [ ] No implementation details have leaked into requirements (keep "what" separate from "how")
- [ ] The document is under 1500 words for a feature PRD, or appropriately structured with milestones for a product PRD

---

## Adapting by PRD Type

### New Product PRD
- Include all sections with full depth
- Add a "Target Users" or "Personas" section after the Problem Statement
- Add a "Pricing / Business Model" section if relevant
- Milestones section becomes a full roadmap with multiple milestones
- Include a "Future Considerations" section for ideas intentionally deferred

### Feature PRD
- Executive Summary and Problem Statement can be more concise
- Technical Considerations focus on integration with existing systems
- Typically 1-2 milestones (MVP + Polish)
- Reference the parent product PRD if one exists

### Enhancement PRD
- Include a clear "Current Behavior" vs "Proposed Behavior" comparison
- Acceptance criteria emphasize backward compatibility
- May only need a single milestone
- Focus on the delta, not re-documenting existing functionality

---

## After Writing the PRD

1. **Summarize for stakeholder communication**: Write a 3-5 bullet TL;DR suitable for sharing in Slack or email
2. **Flag blockers**: Call out any open questions that block engineering from starting
3. **Suggest next steps**: Recommend whether this needs a technical design doc, design review, or can go straight to implementation

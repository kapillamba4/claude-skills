---
name: ux-lens
description: Perform a comprehensive UX & UI audit of any website via browser. Analyzes accessibility, visual design, usability, and user experience patterns. Use when asked to review, audit, or evaluate a website's design.
---

# UX Lens

A comprehensive UX & UI audit skill that analyzes websites through multiple lenses: accessibility, visual design, usability, and user experience patterns.

## Triggers

- **Slash command**: `/ux-lens [URL]`
- **Auto-detect**: When user asks to "review my website", "audit this page", "check the UX", or "evaluate the design"

## Workflow

### Step 1: Initialize Audit

Ask the user for required information using `AskUserQuestion`:

| Question | Purpose |
|----------|---------|
| **URL** | The website to audit |
| **Focus Areas** | Accessibility, Visual Design, Usability, or Full Audit |
| **Target Audience** | Who uses this site? (helps contextualize findings) |
| **Device Focus** | Desktop, Mobile, or Both |

### Step 2: Navigate & Capture

Use browser tools to:
1. Navigate to the target URL
2. Capture screenshots at key breakpoints (if mobile included)
3. Document the page structure and key interactive elements

### Step 3: Audit Categories

Run through each applicable audit category:

#### Accessibility (WCAG 2.1)

- [ ] **Color Contrast**: Text meets 4.5:1 (normal) / 3:1 (large) ratio
- [ ] **Focus Indicators**: Visible focus states on all interactive elements
- [ ] **Alt Text**: Images have meaningful alt attributes
- [ ] **Form Labels**: All inputs have associated labels
- [ ] **Keyboard Navigation**: All functions accessible via keyboard
- [ ] **Heading Hierarchy**: Logical H1-H6 structure
- [ ] **ARIA Usage**: Proper ARIA labels where needed
- [ ] **Skip Links**: Skip navigation present for screen readers

#### Visual Design

- [ ] **Visual Hierarchy**: Clear distinction between primary, secondary, tertiary content
- [ ] **Color Palette**: Consistent and purposeful color usage
- [ ] **Typography**: Readable font sizes (min 16px body), limited font families (2-3 max)
- [ ] **Spacing**: Consistent margins/padding, adequate whitespace
- [ ] **Alignment**: Elements align to a clear grid
- [ ] **Imagery**: High quality, relevant, optimized images
- [ ] **Brand Consistency**: Cohesive visual identity throughout

#### Usability

- [ ] **Navigation**: Clear, consistent, max 7 items in main nav
- [ ] **CTAs**: Prominent, action-oriented, descriptive labels
- [ ] **Forms**: Minimal fields, clear validation, helpful error messages
- [ ] **Search**: Visible search if content-heavy site
- [ ] **Feedback**: User actions receive immediate visual feedback
- [ ] **Error Handling**: Graceful error states with recovery paths
- [ ] **Loading States**: Progress indicators for async operations

#### User Experience Patterns

- [ ] **Onboarding**: First-time user guidance if complex app
- [ ] **Empty States**: Helpful content when no data exists
- [ ] **Micro-interactions**: Appropriate animations (not distracting)
- [ ] **Content Scanning**: Content structured for quick scanning (headings, bullets)
- [ ] **Trust Signals**: Security badges, testimonials, contact info
- [ ] **Performance Perception**: Perceived speed optimization

#### Mobile Responsiveness (if applicable)

- [ ] **Touch Targets**: Min 44x44px for tappable elements
- [ ] **Viewport**: Proper meta viewport tag
- [ ] **Text Scaling**: Readable without horizontal scroll
- [ ] **Form Inputs**: Appropriate input types (tel, email, etc.)
- [ ] **Thumb Zone**: Key actions in thumb-reachable areas

### Step 4: Severity Classification

Classify each finding:

| Severity | Icon | Description |
|----------|------|-------------|
| **Critical** | :stop_sign: | Blocks users from completing tasks |
| **Major** | :warning: | Significant friction, impacts many users |
| **Minor** | :information_source: | Small improvement opportunity |
| **Suggestion** | :bulb: | Nice to have, enhancement |

### Step 5: Generate Report

Structure the audit report as follows:

```markdown
# UX Lens Audit Report

**URL:** [audited URL]
**Date:** [current date]
**Device(s):** [Desktop/Mobile/Both]
**Focus:** [Audit scope]

## Executive Summary

[2-3 sentence overview of the site's UX health and top 3 priorities]

## Score Overview

| Category | Score | Critical | Major | Minor |
|----------|-------|----------|-------|-------|
| Accessibility | X/10 | # | # | # |
| Visual Design | X/10 | # | # | # |
| Usability | X/10 | # | # | # |
| UX Patterns | X/10 | # | # | # |

## Detailed Findings

### :stop_sign: Critical Issues

[List critical issues with location and fix recommendation]

### :warning: Major Issues

[List major issues with location and fix recommendation]

### :information_source: Minor Issues

[List minor issues with location and fix recommendation]

### :bulb: Suggestions

[List enhancement suggestions]

## What's Working Well

[Highlight 3-5 things the site does well]

## Prioritized Action Items

1. [ ] [Highest priority fix with rationale]
2. [ ] [Second priority fix]
3. [ ] [Third priority fix]
...

## Screenshots

[Include relevant screenshots with annotations if applicable]
```

## Tools Used

- **Browser Navigation**: Access the live site
- **Screenshot Capture**: Document current state
- **Image Analysis**: Analyze visual design patterns
- **AskUserQuestion**: Gather audit parameters

## Example Usage

```
User: /ux-lens https://example.com

Assistant: I'll perform a UX & UI audit of example.com. Let me gather some details first...

[Asks focus areas, target audience, device focus]

[Proceeds with audit]

[Presents comprehensive report with prioritized action items]
```

## Tips for Effective Audits

1. **Be Specific**: Reference exact elements (e.g., "Hero section CTA button" not "a button")
2. **Be Constructive**: Every issue should include a recommended fix
3. **Prioritize Ruthlessly**: Not all issues are equal; focus on high-impact fixes
4. **Consider Context**: A playful app vs. a banking dashboard have different UX standards
5. **Acknowledge Strengths**: Balance criticism with recognition of good design decisions

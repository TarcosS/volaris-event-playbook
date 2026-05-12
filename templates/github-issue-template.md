---
title: "GitHub Issue"
layout: default
parent: "Templates"
nav_order: 2
---

> Use this template to create well-structured GitHub issues from audit findings. Copy and fill in the fields below.

---

## [Issue Title]

### Problem

[Clear, concise statement of what is wrong or missing. One or two sentences.]

### Evidence

[Specific reference to the code, configuration, or behavior that demonstrates the problem.]

- **File:** `[path/to/file]`
- **Line(s):** [line number(s)]
- **What it shows:** [Brief description of what the evidence demonstrates]

### Impact

[What happens if this is not addressed? Who or what is affected? Be specific about the blast radius.]

### Proposed Solution

[Step-by-step recommended approach to resolve the issue.]

1. [Step 1]
2. [Step 2]
3. [Step 3]

### Acceptance Criteria

- [ ] [Criterion 1 — testable and verifiable]
- [ ] [Criterion 2]
- [ ] [Criterion 3]

### Metadata

| Field | Value |
|---|---|
| **Priority** | [Critical / High / Medium / Low] |
| **Effort** | [Small (hours) / Medium (days) / Large (weeks)] |
| **Labels** | [e.g., `security`, `infrastructure`, `bug`, `enhancement`] |
| **Owner** | [Team or role responsible — e.g., "Platform team", "Backend team"] |
| **Dependencies** | [Other issues or changes that must happen first, if any] |

---

## Priority Guide

| Priority | Description | Action |
|---|---|---|
| **Critical** | Active security risk, data exposure, or production-impacting bug | Fix immediately. Block other work if needed. |
| **High** | Significant risk or quality issue that could cause incidents | Fix within the current sprint or iteration. |
| **Medium** | Notable issue that should be addressed but is not urgent | Plan for the near term. |
| **Low** | Minor improvement or best practice adoption | Address when convenient or during refactoring. |

## Effort Guide

| Effort | Description |
|---|---|
| **Small** | A few hours of work. Single file or configuration change. |
| **Medium** | 1–3 days. Multiple files, some testing required, possible coordination. |
| **Large** | A week or more. Significant refactoring, cross-team coordination, or infrastructure changes. |

---

## Example

### Add rate limiting to public API endpoints

**Problem:**  
The public API endpoints (`/api/register`, `/api/login`, `/api/search`) have no rate limiting, allowing unlimited requests from any client.

**Evidence:**  
- **File:** `src/routes/api.js`
- **Lines:** 12, 28, 45
- **What it shows:** Express route handlers are registered without any rate-limiting middleware. No middleware in the stack inspects request frequency.

**Impact:**  
Without rate limiting, the API is vulnerable to brute-force attacks on authentication endpoints and denial-of-service through resource exhaustion on search endpoints. The `/api/login` endpoint is especially critical as it allows unlimited password attempts.

**Proposed Solution:**
1. Install `express-rate-limit` or equivalent middleware
2. Apply strict rate limiting to `/api/login` (e.g., 5 attempts per 15 minutes per IP)
3. Apply moderate rate limiting to `/api/register` (e.g., 10 per hour per IP)
4. Apply general rate limiting to `/api/search` (e.g., 100 per minute per IP)
5. Return `429 Too Many Requests` with `Retry-After` header
6. Log rate-limit violations for monitoring

**Acceptance Criteria:**
- [ ] All public API endpoints have rate limiting applied
- [ ] `/api/login` blocks after 5 failed attempts per 15 minutes per IP
- [ ] Rate-limited requests receive 429 with descriptive message
- [ ] Rate limit violations are logged
- [ ] Existing tests pass with rate limiting enabled

**Metadata:**

| Field | Value |
|---|---|
| **Priority** | High |
| **Effort** | Small (2–4 hours) |
| **Labels** | `security`, `api`, `infrastructure` |
| **Owner** | Backend team |
| **Dependencies** | None |

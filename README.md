# su26-ai301-contribution
# Contribution #1: crypto/x509: VerifyHostname treats zone-scoped IPv6 literals as DNS names

**Contribution Number:** 1  
**Student:** Richelle Williams 
**Issue:** https://github.com/golang/go/issues/79719 
**Status:** Phase IV Complete

**Fork:** https://github.com/RichWilliams772/RichelleWGO
---

## Why I Chose This Issue

I chose this issue because it seemed like a great opportunity to contribute to a large open-source project while learning more about networking and security concepts in Go. I wanted an issue that would challenge me to understand existing code and debugging processes without being overwhelming. This issue stood out because it involves a specific bug with a clear objective, allowing me to gain experience with both problem analysis and software maintenance.

---

## Understanding the Issue

### Problem Description

The issue involves the hostname verification process incorrectly handling certain IPv6 addresses that include zone identifiers. When these addresses are used, the verification logic does not process them correctly, which can lead to failed certificate validation. As a result, secure connections that should be considered valid may be rejected due to the way the address is interpreted.

### Expected Behavior

The hostname verification process should correctly recognize and handle IPv6 addresses that contain zone identifiers. If the certificate contains the appropriate IP information, the connection should be successfully validated.

### Current Behavior

The verification logic does not properly recognize these IPv6 addresses and treats them incorrectly during validation. This causes certificate verification to fail even when the certificate contains the correct information.

### Affected Components

- crypto/x509 package
- VerifyHostname function
- TLS certificate verification logic
- IPv6 address handling

---

## Reproduction Process

### Environment Setup

The repository has been forked and the issue has been reviewed. Local setup and reproduction will be completed during Phase II. Any setup challenges, solutions, and observations will be documented as the issue investigation progresses.

### Steps to Reproduce

1. Set up the Go development environment.
2. Build the project locally.
3. Create a test case using an IPv6 address with a zone identifier.
4. Attempt hostname verification using the affected functionality.
5. Observe the failed certificate validation.

### Reproduction Evidence

- **Commit showing reproduction:** To be added during Phase II.
- **Screenshots/logs:** To be added during Phase II.
- **My findings:** To be documented after successful reproduction.

---

## Solution Approach

### Analysis

Based on the issue description, the problem appears to be related to how the hostname verification logic processes IPv6 addresses that include zone identifiers. The current implementation does not correctly classify these addresses, causing the verification process to follow an incorrect validation path.

### Proposed Solution

Investigate the address parsing and verification logic and update it so that zone-scoped IPv6 addresses are correctly identified and validated. Additional tests will be added to ensure the issue is resolved and does not reoccur.

### Implementation Plan

**Understand:**  
Review how hostname verification currently works and identify where IPv6 addresses are processed.

**Match:**  
Look for similar address-parsing implementations elsewhere in the Go codebase and compare existing patterns.

**Plan:**

1. Locate the relevant verification code.
2. Analyze how IPv6 addresses are currently parsed.
3. Modify the logic to properly handle zone identifiers.
4. Create test cases covering the affected scenario.
5. Verify that all existing tests continue to pass.

**Implement:**  
Implementation work will begin during Phase III.

**Review:**

- [ ] Follow project contribution guidelines.
- [ ] Maintain code quality and readability.
- [ ] Add appropriate test coverage.
- [ ] Verify no existing functionality is broken.

**Evaluate:**

- Run existing tests.
- Run new IPv6-related tests.
- Confirm successful hostname verification for affected cases.

---

## Testing Strategy

### Unit Tests

- [ ] Test standard IPv4 addresses.
- [ ] Test standard IPv6 addresses.
- [ ] Test IPv6 addresses with zone identifiers.

### Integration Tests

- [ ] Certificate validation using IPv6 addresses.
- [ ] Hostname verification with zone-scoped IPv6 addresses.

### Manual Testing

Manual testing will be performed after implementation to confirm that certificate validation succeeds for affected IPv6 scenarios.

---

## Implementation Notes

### Week 1 Progress

- Selected an open-source issue.
- Reviewed the issue description and requirements.
- Forked the Go repository.
- Analyzed the problem and potential root cause.
- Created and documented a contribution plan.

### Code Changes

- **Files modified:** None yet.
- **Key commits:** To be added later.
- **Approach decisions:** Initial investigation and planning completed.

---

## Pull Request

**PR Link:** To be added when submitted.

**PR Description:** To be completed during implementation.

**Maintainer Feedback:**

- Pending

**Status:** Not Started

---

## Learnings & Reflections

### Technical Skills Gained

- Improved understanding of open-source contribution workflows.
- Learned more about hostname verification and TLS validation.
- Developed experience analyzing bugs within a large codebase.

### Challenges Overcome

- Understanding the context of the issue and identifying the affected functionality within a large project.
- Interpreting technical documentation and issue discussions.

### What I'd Do Differently Next Time

I would spend additional time exploring related source files and existing test cases before planning my implementation approach.

---

## Resources Used

- https://github.com/golang/go/issues/79719
- https://pkg.go.dev/crypto/x509
- https://pkg.go.dev/net/netip
- Go Contributor Guide

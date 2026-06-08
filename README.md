# su26-ai301-contribution
# Contribution #1: crypto/x509: VerifyHostname treats zone-scoped IPv6 literals as DNS names

**Contribution Number:** 1
**Student:** Richelle Williams
**Issue:** https://github.com/golang/go/issues/79719
**Status:** Phase II Complete

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

* `crypto/x509` package
* `VerifyHostname` function
* TLS certificate verification logic
* IPv6 address handling

---

# Phase II: Reproduce & Plan

## Reproduction Process

### Environment Setup

I cloned my fork of the Go repository and opened it locally in VS Code. After reviewing the issue description, I navigated to the affected package (`crypto/x509`) and located the relevant source file, `src/crypto/x509/verify.go`, where the hostname verification logic is implemented.

**Working Branch:**
https://github.com/RichWilliams772/RichelleWGO/tree/fix-issue-79719

Setup Notes:

* Cloned the Go repository from GitHub.
* Opened the project in VS Code.
* Created and pushed a dedicated branch named `fix-issue-79719`.
* Located the affected package (`crypto/x509`).
* Opened and reviewed `verify.go` to begin investigating the root cause.

### Steps to Reproduce

1. Clone the Go repository locally.
2. Create and switch to the `fix-issue-79719` branch.
3. Navigate to `src/crypto/x509/verify.go`.
4. Locate the `VerifyHostname` function.
5. Review how hostname values are classified and validated.
6. Use a zone-scoped IPv6 address such as `fe80::1%eth0` during hostname verification.
7. Observe the verification behavior.

**Expected Result:**
Zone-scoped IPv6 addresses should be recognized as valid IP addresses and matched against the certificate IP SAN.

**Actual Result:**
Zone-scoped IPv6 addresses are not handled correctly during hostname verification, which can result in certificate validation failure.

### Reproduction Evidence

**Branch Link:**
https://github.com/RichWilliams772/RichelleWGO/tree/fix-issue-79719

**My Findings:**
After locating and reviewing `verify.go`, I confirmed that the issue is related to hostname classification during certificate verification. According to the issue description, zone-scoped IPv6 addresses are not handled correctly, causing the verification process to follow the wrong validation path and fail when it should succeed.

---

## Solution Approach

### Analysis

The root cause appears to be related to how the `VerifyHostname` function determines whether a hostname should be treated as an IP address or a DNS name. Zone-scoped IPv6 addresses contain additional information that is not correctly handled by the current parsing logic, resulting in incorrect certificate verification behavior.

### Implementation Plan (UMPIRE)

**Understand:**
The hostname verification process incorrectly handles IPv6 addresses containing zone identifiers, causing certificate validation failures.

**Match:**
Review existing IP parsing patterns within the Go codebase and compare them to approaches that properly support IPv6 zone identifiers.

**Plan:**

1. Review the implementation of `VerifyHostname` in `src/crypto/x509/verify.go`.
2. Identify where hostname classification and IP parsing occur.
3. Determine how zone-scoped IPv6 addresses are currently processed.
4. Modify the parsing logic to correctly recognize zone identifiers.
5. Add test coverage for IPv6 addresses containing zone identifiers.
6. Run the relevant `crypto/x509` tests.
7. Verify that existing functionality continues to work correctly.

**Implement:**
Implementation will be completed on branch `fix-issue-79719`.

**Review:**

* Follow Go contribution guidelines.
* Maintain code readability and quality.
* Add targeted test coverage.
* Verify no regressions are introduced.

**Evaluate:**

* Run existing `crypto/x509` tests.
* Run new tests covering zone-scoped IPv6 addresses.
* Confirm hostname verification succeeds when expected.

---

## Implementation Notes

### Week 1 Progress

* Selected an open-source issue.
* Forked the Go repository.
* Cloned the repository locally.
* Created and pushed a dedicated working branch.
* Located the affected file (`src/crypto/x509/verify.go`).
* Investigated the issue and documented a solution plan.

### Code Changes

**Files Modified:** None yet

**Working Branch:**
https://github.com/RichWilliams772/RichelleWGO/tree/fix-issue-79719

---

## Resources Used

* https://github.com/golang/go/issues/79719
* https://pkg.go.dev/crypto/x509
* https://pkg.go.dev/net/netip
* Go Contributor Guide


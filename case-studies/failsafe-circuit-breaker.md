# Diagnosing circuit breaker statistics after inactivity

**Project:** [Failsafe](https://github.com/failsafe-lib/failsafe) (Java)

**Evidence:** [Issue #390](https://github.com/failsafe-lib/failsafe/issues/390) · [Pull request #402](https://github.com/failsafe-lib/failsafe/pull/402) · [Patch and regression tests](https://github.com/failsafe-lib/failsafe/pull/402/files)

**Status on 15 October 2026:** proposed fix; open and awaiting maintainer review. This case study describes the submitted change and local validation, not an accepted release or measured production impact.

## Observable failure

A circuit breaker configured to open after two failures within four seconds could remain closed after a long idle period, even when two new failures occurred one second apart. A failure disappeared from the statistics before the configured window had elapsed.

## Root cause

Failsafe's time-based circuit statistics use a ring of buckets. A full-window idle period resets the current bucket index to zero. The method then returned the bucket that had been current before reset, rather than the new current bucket. The first post-idle result could therefore be recorded in a stale bucket and subtracted too soon during rotation.

Further regression testing exposed a related timestamp problem: reset assigned future timestamps to other buckets, while rotation advanced those timestamps by an entire window. That combination could postpone later rotation and result expiry.

The invariant is simple: each result must enter the current bucket, and each rotated bucket must follow the preceding bucket by one bucket duration.

## Submitted change

The patch returns the newly current bucket after a full reset and computes each rotated bucket's start time from its predecessor. It changes internal statistics without introducing a public API or configuration change.

## Regression evidence

- Deterministic fake-clock tests cover success and failure recording from all four previous bucket positions: eight combinations.
- Assertions check counts and rates inside the window, then expiry at the boundary.
- A circuit-state regression verifies that two post-idle failures trigger opening at the configured threshold.
- Both new regression methods fail against the original production implementation and pass with the patch.

Local validation on Java 8 passed **19 targeted tests** and **333 tests across the full Maven reactor**: 315 core, 9 OkHttp, and 9 Retrofit, with no failures, errors, or skips.

The Windows Surefire child-JVM launcher stalled locally, so the completed local runs used `-DforkCount=0`. The project build configuration was not changed. These results do not establish that normal forked execution passes on every platform; current CI and review evidence live in the pull request.

## What the investigation demonstrates

The first reset correction was insufficient by itself. Testing the window through rotation and expiry revealed the second defect. Combining internal count assertions with a circuit-state test connected the data-structure invariant to observable reliability behavior.

This contribution was developed with AI assistance. The linked patch, regression tests, and pull request provide the technical evidence for review.

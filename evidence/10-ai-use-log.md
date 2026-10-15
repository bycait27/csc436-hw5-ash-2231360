# AI-Use Log

## Task 2 

**Tool:** Gemini

**Query/Prompt Purpose:** Requested help designing the 6-row cache-policy matrix mapping content classes, layers, headers, keys, invalidation triggers, and professional rationales. Also asked for the pattern to implement a cache-aside in-memory app cache with a 10-second TTL in Node.js.

**What was accepted:** Accepted the structured 6-row cache matrix rationale and the Map-based cache-aside helper (`appCache`) with automatic invalidation on `POST`, `PATCH`, and `DELETE` operations, along with `X-Cache: HIT` or `MISS` header injection.

**What was rejected/independently verified:** Verified that cache invalidation properly triggered across all mutation paths so no stale listings persisted. Confirmed query parameter normalization in cache keys for sorting, filtering, and pagination.

## Task 3 

**Tool:** Gemini

**Query/Prompt Purpose:** Asked for assistance and validation commands to capture full response headers and timestamps for all four required cache states (`MISS`, `HIT`, `304 Not Modified` with ETag validation, and successful invalidation/version rollover).

**What was accepted:** Accepted `curl` header-dump patterns using `-i`, `If-None-Match`, and timing output flags to prove cache behavior.

**What was rejected/independently verified:** Independently executed commands against local and deployed environments, verifying that `304` responses returned zero body length and that invalidation correctly flipped subsequent requests from `HIT` back to `MISS`.

## Task 5 

**Tool:** Gemini

**Query/Prompt Purpose:** Asked for guidance on structuring the performance budget table, setting up the local web-vitals RUM pilot collector (`rum-collector.mjs`), running Lighthouse performance audits, and executing the course-standard k6 load profile against staging.

**What was accepted:** Accepted the performance budget structure (LCP, INP, CLS, bundle size, p95 latency targets), the RUM pilot configuration, and the k6 load script invocation command (`k6 run -e BASE=`...).

**What was rejected/independently verified:** Explicitly acknowledged the low-traffic finding ("we have no CrUX data because we have no users") rather than fabricating field metrics. Independently ran local RUM collection sessions, audited mobile/desktop cohorts separately, and documented instability in p95/p75 metrics derived from small sample sizes.

## Task 7 

**Tool:** Gemini

**Query/Prompt Purpose:** Guided through running `@axe-core/cli` against static views and stateful form dialogs and structuring `missed.md.

**What was accepted:** Accepted the structure of `missed.md` detailing scanner-missed defects (such as out-of-sight errors), categorized by symptom, mechanism, impacted users, and fix.
**What was rejected/independently verified:** Independently performed manual keyboard-only navigation across all interactive workflows.

## Task 8 

**Tool:** Gemini

**Query/Prompt Purpose:** Asked for a conceptual breakdown and safety protocol for reproducing a deliberate cross-user cache disclosure (cache-key confusion) using synthetic session cookies, along with the precise cleanup and verification steps.

**What was accepted:** Accepted the risk write-up structure detailing cache-key isolation failures, blast radius, and detection controls (asserting that authenticated routes never return `HIT`).

**What was rejected/independently verified:** Used isolated local loopback environments to safely simulate cache-key confusion without exposing real user sessions. Executed strict cleanup procedures: reverted cache directives, purged affected keys, verified fresh `MISS` responses across distinct client contexts, and invalidated synthetic sessions.

## Task 9 

**Tool:** Gemini

**Query/Prompt Purpose:** Asked for implementation details for structured JSON stdout logging middleware (including X-Request-Id correlation, method, path, status, and duration measurement via `process.hrtime`), along with guidance on `alert-rule.yaml`, and triggering error alerts.

**What was accepted:** Accepted the structured JSON logging middleware integrated into `app.ts` and standard Prometheus-style alerting rules in `alert-rule.yaml`.

**What was rejected/independently verified:** Initially placed middleware outside `createApp()`, which bypassed router-level requests; corrected this by integrating the logger directly into the Express app initialization flow. Independently tested the system by triggering a simulated upstream failure (`/api/fail`), verified the `HTTP 500 JSON` response and error stack trace in the terminal, and successfully captured `alert-fired.png` alongside exact stdout log confirmation.
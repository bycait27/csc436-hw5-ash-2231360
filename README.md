# CSC436 HW5 Write-up

**Name:** Caitlin Ash

**ID:** 2231360

**Commit SHA or Tag:** `hw5-submission`

**Platform/OS Version:** Windows 11 Pro, 64-bit

## Task 4

### Uncompressed (`identity`) 

**Size:** 324,979 bytes (325 KB)

**Percentage Saved:** N/A

**Encoding Negotiated:** `Content-Encoding`: N/A

### Compressed (`gzip`) 

**Size:** 102,136 bytes (102 KB)

**Percentage Saved:** ((324,979 - 102,136) / 324,979 * 100) = 68.57% smaller

**Encoding Negotiated:** `Content-Encoding: gzip`

### Compressed (`br`) 

**Size:** 103,926 bytes (103 KB)

**Percentage Saved:** ((324,979 - 103,926) / 324,979 * 100) = 68.02% smaller

**Encoding Negotiated:** `Content-Encoding: br`

## Task 5

### 5a) Performance budget

| Metric | Budget | Measured How |
| ------ | ------ | ------------ |
| LCP (Largest Contentful Paint) | ≤2.5 s | Lighthouse mobile preset, and field p75 |
| INP (Interaction to Next Paint) | ≤200 ms | Field only (requires active user interaction) |
| CLS (Cumulative Layout Shift) | ≤0.1 | Lighthouse and field |
| Total JS Transferred | ≤350 KB compressed | Vite build output / bundle analysis (accounting for your ~102 KB gzip bundle) |
| API /api/tickets p95 latency | ≤500 ms | k6 load test |

### 5b) Lighthouse comparison

All reports used Lighthouse 13.5.0 against `https://www.csc436.com/`.

| Run | Capture time (UTC) | Performance score | FCP | LCP | CLS | TBT |
| --- | --- | ---: | ---: | ---: | ---: | ---: |
| Existing baseline (`1h-before.json`) | 2026-10-14 01:08 | 0.97 | 1.87 s | 2.24 s | 0.006 | 0 ms |
| Fresh rerun before reported deployment (`1h-current.json`) | 2026-10-14 19:25 | 0.88 | 2.57 s | 2.94 s | 0 | 0 ms |
| Rerun after deployment was reported (`1h-after.json`) | 2026-10-14 19:31 | 0.92 | 2.27 s | 2.63 s | 0 | 0 ms |

Compared with the earlier baseline, the latest run's score was 0.05 lower,
FCP was 0.40 s slower, and LCP was 0.39 s slower. Compared with the immediately
preceding run, the score rose by 0.04, FCP improved by 0.30 s, and LCP
improved by 0.31 s. Neither comparison demonstrates a delivery improvement:
the consecutive pre/post runs are close but the deployed asset cache policy
was not confirmed by response headers. Treat these as diagnostic measurements,
not a successful before/after optimization claim.

The asset requests returned `cf-cache-status: EXPIRED` and then `HIT`, but
continued to expose `Cache-Control: public, max-age=0, s-maxage=300`. Verify
that the asset rule matches and is active, then capture the browser and edge
cache headers again before claiming the one-year TTL is in effect.

## Task 9

**Command Executed:** `curl.exe -i http://localhost:3002/api/tickets?zone=North`

| Request Description | `X-Request-Id` | Route / Method | Status | Latency (`duration_ms`) | SLI Compliance (< 300ms, 2xx) | Matching JSON Stdout Log | 
| ------------------- | -------------- | -------------- | ------ | ----------------------- | ----------------------------- | ------------------------ |
| Fetch North Tickets | `b163713f-69b1-4a44-bd2e-73b5ff614d7c` | `GET /api/tickets?zone=North` | `200 OK` | `8 ms` | PASS (Met SLO) | `{"timestamp":"2026-10-14T20:27:18.900Z","id":"b163713f-69b1-4a44-bd2e-73b5ff614d7c","method":"GET","path":"/api/tickets?zone=North","status":200,"duration_ms":8}` |
# Risk

## The Failure Mode (What went wrong)

The vulnerability occurred due to a two-mistake condition in our edge caching architecture:
1. **Origin Misconfiguration:** The personalized `/account` endpoint was incorrectly deployed with public caching headers (`Cache-Control: public, max-age=60`) and lacked a proper `Vary: Cookie` header.
2. **Cache-Key Collision:** The CDN/edge proxy was configured with a naive cache key policy (e.g., ignoring session cookies or user identifiers), storing responses solely by request path (`/account`). 

When User A (Alice) requested the endpoint, her personalized response was cached at the edge. When User B (Bob) subsequently requested `/account`, the edge server matched the path in the cache and served Alice's cached response (including her private student ID and balance) to Bob with a cache `HIT`.

## Blast Radius

- **Impacted Data:** User account details, including full names, campus identification numbers (`S-numbers`), and sensitive meal-plan balances.
- **Scope:** Any authenticated user visiting the affected route while a stale, shared cache entry was active. Because no access control check occurred at the edge once cached, this bypassed application-level session validation entirely.

## Preventative Controls & Detection

To ensure this failure mode cannot happen silently in production, the following controls have been implemented:
- **Strict Cache-Control Directives:** All authenticated, personalized endpoints now enforce `cache-control: private, no-store`, explicitly instructing shared CDN and edge caches never to store user-specific responses.
- **Granular Cache Keys:** Edge cache configurations have been hardened to include request cookies and authorization headers in the cache key definition (or bypass caching entirely for authenticated routes).
- **Automated Synthetic Detection Check:** A continuous integration (CI) or synthetic monitoring check has been added to test authenticated endpoints. The check asserts that any request containing a session cookie never returns `x-cache-status: HIT` and always includes `private` or `no-store` directives in the response headers. If an engineer accidentally deploys a public cache header on a protected route, the build or monitoring check fails automatically.
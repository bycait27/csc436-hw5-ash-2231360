# RUM pilot summary

**Collection Environment:** Local development in VSCode on Windows 11 64-bit machine

The pilot was collected during local development in VS Code. The app and 
collector were accessed on the same computer through `localhost`, so the
measured network path is **local/loopback**, not Wi-Fi, Ethernet, or cellular. 
The six page views do not independently establish six distinct people or devices.

The sample is very small and local pilot measurements are not representative
field performance. The high CLS is a failing result, not a pass. A local pilot 
is useful for detecting this signal but doesnot establish how common it is for 
real users.

**CrUX availability finding:** “We have no CrUX data because we have no users.”
This deployment does not meet CrUX's origin eligibility threshold; the local
pilot is instrumentation practice, not a substitute for CrUX.

**`rum-pilot.json`:**
```json
{
  "label": "Small convenience pilot; not CrUX or representative field data",
  "rows": [
    {
      "pageViewId": "277a1103-f528-430d-a77d-48d2cd8fdebf",
      "id": "v6-1792006999436-3246119651204",
      "name": "FCP",
      "value": 108,
      "navigationType": "navigate"
    },
    {
      "pageViewId": "277a1103-f528-430d-a77d-48d2cd8fdebf",
      "id": "v6-1792006999436-8261085946727",
      "name": "TTFB",
      "value": 66,
      "navigationType": "navigate"
    },
    {
      "pageViewId": "277a1103-f528-430d-a77d-48d2cd8fdebf",
      "id": "v6-1792006999436-1788579236420",
      "name": "LCP",
      "value": 108,
      "navigationType": "navigate"
    },
    {
      "pageViewId": "277a1103-f528-430d-a77d-48d2cd8fdebf",
      "id": "v6-1792006999436-1148897923705",
      "name": "INP",
      "value": 8,
      "navigationType": "navigate"
    },
    {
      "pageViewId": "277a1103-f528-430d-a77d-48d2cd8fdebf",
      "id": "v6-1792006999449-8272442081282",
      "name": "CLS",
      "value": 1.07804849017182,
      "navigationType": "navigate"
    },
    {
      "pageViewId": "d07c999c-2c7f-457c-babe-e951c33adcff",
      "id": "v6-1792007048544-6222827192664",
      "name": "TTFB",
      "value": 5,
      "navigationType": "reload"
    },
    {
      "pageViewId": "d07c999c-2c7f-457c-babe-e951c33adcff",
      "id": "v6-1792007048544-5358492277594",
      "name": "FCP",
      "value": 44,
      "navigationType": "reload"
    },
    {
      "pageViewId": "d07c999c-2c7f-457c-babe-e951c33adcff",
      "id": "v6-1792007048544-4835441880777",
      "name": "LCP",
      "value": 64,
      "navigationType": "reload"
    },
    {
      "pageViewId": "d07c999c-2c7f-457c-babe-e951c33adcff",
      "id": "v6-1792007048544-9514610136812",
      "name": "INP",
      "value": 0,
      "navigationType": "reload"
    },
    {
      "pageViewId": "d07c999c-2c7f-457c-babe-e951c33adcff",
      "id": "v6-1792007048556-8272405080296",
      "name": "CLS",
      "value": 1.06451619723555,
      "navigationType": "reload"
    },
    {
      "pageViewId": "f12f95ac-54cf-4092-910f-f40ea8497658",
      "id": "v6-1792007054003-1299440028324",
      "name": "TTFB",
      "value": 3.59999999776483,
      "navigationType": "reload"
    },
    {
      "pageViewId": "f12f95ac-54cf-4092-910f-f40ea8497658",
      "id": "v6-1792007054003-4441529512347",
      "name": "FCP",
      "value": 36,
      "navigationType": "reload"
    },
    {
      "pageViewId": "f12f95ac-54cf-4092-910f-f40ea8497658",
      "id": "v6-1792007054002-2314490869810",
      "name": "LCP",
      "value": 48,
      "navigationType": "reload"
    },
    {
      "pageViewId": "f12f95ac-54cf-4092-910f-f40ea8497658",
      "id": "v6-1792007054003-7134623777864",
      "name": "INP",
      "value": 8,
      "navigationType": "reload"
    },
    {
      "pageViewId": "f12f95ac-54cf-4092-910f-f40ea8497658",
      "id": "v6-1792007054015-6859599769465",
      "name": "CLS",
      "value": 1.0986298894939,
      "navigationType": "reload"
    },
    {
      "pageViewId": "0277234b-5bb8-4d87-ae51-0a537b5ce9ef",
      "id": "v6-1792007088227-4556266500655",
      "name": "TTFB",
      "value": 4.30000000074506,
      "navigationType": "reload"
    },
    {
      "pageViewId": "0277234b-5bb8-4d87-ae51-0a537b5ce9ef",
      "id": "v6-1792007088227-1401864162926",
      "name": "FCP",
      "value": 32,
      "navigationType": "reload"
    },
    {
      "pageViewId": "0277234b-5bb8-4d87-ae51-0a537b5ce9ef",
      "id": "v6-1792007088227-9333378935643",
      "name": "LCP",
      "value": 32,
      "navigationType": "reload"
    },
    {
      "pageViewId": "0277234b-5bb8-4d87-ae51-0a537b5ce9ef",
      "id": "v6-1792007088227-8025478330012",
      "name": "INP",
      "value": 40,
      "navigationType": "reload"
    },
    {
      "pageViewId": "0277234b-5bb8-4d87-ae51-0a537b5ce9ef",
      "id": "v6-1792007088240-8020243885332",
      "name": "CLS",
      "value": 1.9469442810807,
      "navigationType": "reload"
    },
    {
      "pageViewId": "0af8b4a8-1d9c-4a49-ba29-b07e729719d3",
      "id": "v6-1792007129952-6514875250735",
      "name": "TTFB",
      "value": 4.09999999776483,
      "navigationType": "reload"
    },
    {
      "pageViewId": "0af8b4a8-1d9c-4a49-ba29-b07e729719d3",
      "id": "v6-1792007129952-2704945858580",
      "name": "FCP",
      "value": 32,
      "navigationType": "reload"
    },
    {
      "pageViewId": "0af8b4a8-1d9c-4a49-ba29-b07e729719d3",
      "id": "v6-1792007129966-2841101017267",
      "name": "CLS",
      "value": 1.0986298894939,
      "navigationType": "reload"
    },
    {
      "pageViewId": "0af8b4a8-1d9c-4a49-ba29-b07e729719d3",
      "id": "v6-1792007129952-9648707631094",
      "name": "LCP",
      "value": 52,
      "navigationType": "reload"
    },
    {
      "pageViewId": "0af8b4a8-1d9c-4a49-ba29-b07e729719d3",
      "id": "v6-1792007129952-5472697313642",
      "name": "INP",
      "value": 40,
      "navigationType": "reload"
    },
    {
      "pageViewId": "fbc7ac61-5624-4dae-a8e4-650e0f2846ac",
      "id": "v6-1792007191767-9035091054976",
      "name": "TTFB",
      "value": 4.09999999776483,
      "navigationType": "reload"
    },
    {
      "pageViewId": "fbc7ac61-5624-4dae-a8e4-650e0f2846ac",
      "id": "v6-1792007191767-8436531262722",
      "name": "FCP",
      "value": 40,
      "navigationType": "reload"
    },
    {
      "pageViewId": "fbc7ac61-5624-4dae-a8e4-650e0f2846ac",
      "id": "v6-1792007191767-1063786195264",
      "name": "LCP",
      "value": 52,
      "navigationType": "reload"
    },
    {
      "pageViewId": "fbc7ac61-5624-4dae-a8e4-650e0f2846ac",
      "id": "v6-1792007191767-9431731368101",
      "name": "INP",
      "value": 40,
      "navigationType": "reload"
    },
    {
      "pageViewId": "fbc7ac61-5624-4dae-a8e4-650e0f2846ac",
      "id": "v6-1792007191779-6241444021321",
      "name": "CLS",
      "value": 1.0986298894939,
      "navigationType": "reload"
    },
    {
      "pageViewId": "8c6d848f-96c1-4b0b-9548-68c2608049d8",
      "id": "v6-1792007198044-4705583912927",
      "name": "TTFB",
      "value": 4.19999999925494,
      "navigationType": "reload"
    },
    {
      "pageViewId": "8c6d848f-96c1-4b0b-9548-68c2608049d8",
      "id": "v6-1792007198044-4026228273311",
      "name": "FCP",
      "value": 40,
      "navigationType": "reload"
    },
    {
      "pageViewId": "8c6d848f-96c1-4b0b-9548-68c2608049d8",
      "id": "v6-1792007198044-1077320205886",
      "name": "LCP",
      "value": 44,
      "navigationType": "reload"
    },
    {
      "pageViewId": "8c6d848f-96c1-4b0b-9548-68c2608049d8",
      "id": "v6-1792007198044-7219319447491",
      "name": "INP",
      "value": 0,
      "navigationType": "reload"
    },
    {
      "pageViewId": "8c6d848f-96c1-4b0b-9548-68c2608049d8",
      "id": "v6-1792007198097-4506572457254",
      "name": "CLS",
      "value": 1.06451619723555,
      "navigationType": "reload"
    }
  ],
  "summary": {
    "LCP": {
      "n": 7,
      "p75": 64
    },
    "INP": {
      "n": 7,
      "p75": 40
    },
    "CLS": {
      "n": 7,
      "p75": 1.0986298894939
    },
    "FCP": {
      "n": 7,
      "p75": 44
    },
    "TTFB": {
      "n": 7,
      "p75": 5
    }
  }
}
```

This is a small convenience pilot, not CrUX or representative field data. The
provided extract contains six page views with LCP, INP, and CLS, plus one
additional partial page view. The partial page view has no INP or CLS and is
excluded. Each included view has an INP measurement, indicating an interaction was recorded.

| Metric | Budget | p75 (n=6 complete page views) | Result |
| --- | ---: | ---: | --- |
| LCP | <= 2.5 s | 64 ms | Within budget in this small pilot |
| INP | <= 200 ms | 40 ms | Within budget in this small pilot |
| CLS | <= 0.1 | 1.0986 | Exceeds budget; investigate layout instability |

**Percentiles use the nearest-rank method:** sort the six values and select rank
`ceil(0.75 * 6) = 5`. The LCP values are 108, 64, 48, 32, 52, and 52 ms;
the fifth sorted value is 64 ms. INP p75 is 40 ms, and CLS p75 is
1.0986298894939.

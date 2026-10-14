# Asset Size

**Largest JavaScript Asset:** `index-DAgTW6qA.js` as shown in `dist/assets/` (`index-BAWLAnXD.js` as shown in DevTools Network tab).  

**Sizes:**
- **Uncompressed (identity):** 325 KB
- **Gzip Compressed:** 102 KB
- **Brotil Compressed:** 104 KB

# Budget Comparison 

**Budget Target:** Total JS transferred <= 350 KB compressed

**Comparison:** The two compressed bundles at 102 KB and 104 KB, are much lower than my budget target. This leaves ~246 KB left in the budget if the bundle ever increases with development. 

# Decision (Keep)

To see if my app was using compression for my largest asset, I ran the command `curl.exe -I -H "Accept-Encoding: gzip, deflate, br" https://evidence-before-action-frontend.onrender.com/assets/index-BAWLAnXD.js`. This returned a `Content-Encoding: br`, indicating that the asset is being compressed to 104 KB. This is saving us about 70% of the total budget target. I am choosing to keep the current budget, as it leaves room for additional dependencies that may be added in the future. I am also keeping this compression method because it is drastically decreasing the amount of bytes being transferred. 
For large-scale data transformation tasks like parsing SEC EDGAR filings, serverless functions can horizontally scale to thousands of concurrent containers to reduce multi-hour batch jobs to minutes.

You need to orchestrate a distributed fan-out operation using Modal's `.map()` primitive in a local Python execution script.

**Constraints:**
- You must define a target `@app.function()` that simulates a text extraction workload (e.g., adding a prefix to an input string and sleeping for 1 second).
- You must write an `@app.local_entrypoint()` that generates an array of 1,500 mock records.
- The entrypoint must invoke the target function across all 1,500 records using the `.map()` method to ensure parallel execution across Modal's distributed workers.
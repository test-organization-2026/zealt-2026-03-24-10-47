Modal utilizes a code-first approach to infrastructure, replacing standard Dockerfiles with Python-native dynamic OCI image builds. Efficient caching of these layers is critical for minimizing deployment overhead.

You need to define a Modal App and a custom image environment in a Python script that uses `modal.Image.debian_slim()` to programmatically install `torch` and `numpy` via pip. 

**Constraints:**
- The image definition must be inline within the Python script using Modal's chained dependency methods (e.g., `.pip_install()`).
- You must create a basic `@app.function()` that imports these libraries and returns their version numbers to verify successful caching.
- Do NOT use an external YAML configuration or Dockerfile.
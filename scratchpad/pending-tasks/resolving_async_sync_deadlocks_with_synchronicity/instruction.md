Serverless applications heavily utilize asynchronous event loops for high-concurrency remote calls. However, integrating legacy synchronous Python code often blocks the async event loop, leading to severe latency degradation.

You need to implement a bridging utility using Modal's open-source `synchronicity` library in a hybrid Python environment.

**Constraints:**
- You must write a fully asynchronous Modal backend function (e.g., using `async def` and `await f.spawn()`).
- You must use the `synchronicity` library to wrap the async interface, exposing a strictly synchronous API.
- The resulting synchronous wrapper must be called successfully from a standard blocking Python script without throwing event loop conflicts or deadlocks.
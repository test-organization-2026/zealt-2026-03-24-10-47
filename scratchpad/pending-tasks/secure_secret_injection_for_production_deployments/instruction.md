Transitioning from local iterative development to a production environment requires handling sensitive credentials without hardcoding them or relying on insecure volume mounts. Modal injects these natively as environment variables.

You need to provision a secure deployment configuration utilizing the `modal.Secret` primitive in a Modal web endpoint.

**Constraints:**
- You must define a secret named "huggingface-token" using `modal.Secret.from_name()`.
- You must bind this secret to an inference function using the `secrets` parameter in the function decorator.
- The function must read the injected token from the environment variable (`os.environ`) and return a mock authentication success message.
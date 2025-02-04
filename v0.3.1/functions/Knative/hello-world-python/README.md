# Sample Function Python

## Run on OpenFunction

1. [Install OpenFunction](https://github.com/OpenFunction/OpenFunction#quickstart)
2. [Refer to the go function sample](../hello-world-go/README.md)

Definition of a ```Function``` for ```python``` is shown below:

```yaml
apiVersion: core.openfunction.io/v1alpha1
kind: Function
metadata:
  name: python-sample
spec:
  version: "v1.0.0"
  image: "<your registry name>/sample-python-func:v0.3.1"
  imageCredentials:
    name: push-secret
  port: 8080 # default to 8080
  build:
    builder: "openfunction/gcp-builder:v1"
    env:
      GOOGLE_FUNCTION_TARGET: "hello_world"
      GOOGLE_FUNCTION_SIGNATURE_TYPE: "http"
      GOOGLE_FUNCTION_SOURCE: "main.py"
    srcRepo:
      url: "https://github.com/OpenFunction/samples.git"
      sourceSubPath: "v0.3.1/functions/Knative/hello-world-python"
  serving:
    runtime: Knative # default to Knative
```

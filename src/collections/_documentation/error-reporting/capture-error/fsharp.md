In F# you can capture any exception object that you caught:

```fsharp
open Sentry

try 
    AFunctionThatMightFail()
with
    | :? System.Exception as ex
        SentrySdk.CaptureException(ex)
```

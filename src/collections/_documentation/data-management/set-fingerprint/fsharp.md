```fsharp
open Sentry

SentrySdk.ConfigureScope(fun scope ->
    scope.SetFingerprint([|"my-view-function"|])
)
```

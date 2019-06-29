```fsharp
open Sentry
open Sentry.Protocol

SentrySdk.ConfigureScope(fun scope ->
    scope.Level = SentryLevel.Warning
)
```

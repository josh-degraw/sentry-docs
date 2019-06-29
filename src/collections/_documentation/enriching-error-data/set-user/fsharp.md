```fsharp
open Sentry

SentrySdk.ConfigureScope(fun scope ->
    scope.User <- User(Email = "john.doe@example.com")
)
```

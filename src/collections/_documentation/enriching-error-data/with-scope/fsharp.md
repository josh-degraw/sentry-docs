```fsharp
open Sentry
open Sentry.Protocol

SentrySdk.WithScope(fun scope ->

    scope.SetTag("my-tag", "my value")
    scope.Level <- Nullable SentryLevel.Warning
    // will be tagged with my-tag="my value"
    SentrySdk.CaptureException(Exception("my error"))
    |> ignore
    ()
)

// will not be tagged with my-tag
SentrySdk.CaptureException(Exception("my other error"))
|> ignore
```

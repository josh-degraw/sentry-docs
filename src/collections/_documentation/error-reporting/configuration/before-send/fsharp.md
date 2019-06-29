A `Func<SentryEvent, SentryEvent>` can be used to mutate, discard (return null), or return a completely new event.

```fsharp
open Sentry

SentrySdk.Init(fun o ->
    o.BeforeSend <- (fun sentryEvent =>
        // Modify the event here:
        sentryEvent.ServerName <- null // Don't send server names.
        sentryEvent
    )
)
```

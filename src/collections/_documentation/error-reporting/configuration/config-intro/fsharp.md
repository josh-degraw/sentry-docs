Options can be set by passing a callback to the `Init()` method which will
pass the option object along for modifications:

```fsharp
open Sentry

use __ = SentrySdk.Init(fun o ->
    o.Dsn <- "___PUBLIC_DSN___"
    o.MaxBreadcrumbs <- 50
    o.Debug <- true
)

// app code here
```
```fsharp
open Sentry

SentrySdk.Init(fun o -> o.Release <- "{{ page.release_identifier }}")
```

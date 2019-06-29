```fsharp
open Sentry

SentrySdk.Init(fun o -> o.Environment <- "{{ page.example_environment }}")
```

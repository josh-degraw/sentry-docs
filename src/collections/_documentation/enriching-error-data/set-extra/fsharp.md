```fsharp
open Sentry

SentrySdk.ConfigureScope(fun scope -> 
    scope.SetExtra("{{ page.example_extra_key }}", "{{ page.example_extra_value }}")
)
```

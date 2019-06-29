```fsharp
open Sentry

SentrySdk.ConfigureScope(fun scope -> 
    scope.SetTag("{{ page.example_tag_name }}", "{{ page.example_tag_value }}")
)
```

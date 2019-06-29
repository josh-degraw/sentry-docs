```fsharp
open Sentry
open Sentry.Protocol

SentrySdk.AddBreadcrumb(
    message = "Authenticated user " + user.email,
    category = "auth",
    level = BreadcrumbLevel.Info    
)
```
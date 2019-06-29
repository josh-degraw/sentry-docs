```fsharp
open Sentry

use __ = SentrySdk.Init (fun o -> 
    o.BeforeBreadcrumb <- 
        fun b -> 
            if b.Category = "Spammy.Logger"
            then null else b)
//...

```
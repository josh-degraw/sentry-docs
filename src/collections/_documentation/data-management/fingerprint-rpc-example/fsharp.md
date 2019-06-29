```fsharp
// The name of the RPC function that was called (e.g. "getAllBlogArticles")
// For example a HTTP status code returned by the server.
exception MyRpcException of (string * int) 

use __ = SentrySdk.Init(fun o -> 

o.BeforeSend <- (fun ev -> 
    match ev.Exception with
    | MyRpcException (fn, code) -> 
        [|  
            "{% raw %}{{ default }}{% endraw %}"
            fn
            code.ToString()
        |]
        |> ev.SetFingerprint         
        ev
    | _ -> ev)
)
```

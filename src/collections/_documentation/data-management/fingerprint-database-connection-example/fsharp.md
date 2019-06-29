```fsharp
use __ = SentrySdk.Init (fun o ->
    o.BeforeSend <- (fun ev ->
      match ev.Exception with
      | :? SqlConnectionException as ex -> 
        ev.SetFingerprint [|"database-connection-error"|]
        ev
      | _ -> ev          
    )
    //...
)
```

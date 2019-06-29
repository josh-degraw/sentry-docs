```fsharp
using Sentry;

SentrySdk.ConfigureScope(scope =>
{
    scope.SetTag("my-tag", "my value");
    scope.User = new User
    {
        Id = "42",
        Email = "john.doe@example.com"
    };
});
```

Or when an asynchronous call is required:

```fsharp
SentrySdk.ConfigureScopeAsync(fun scope -> 
    async {
        let! user = Async.AwaitTask v
        scope.User <- user        
    }
    |> Async.StartAsTask :> System.Threading.Tasks.Task    
)
|> Async.AwaitTask 
```
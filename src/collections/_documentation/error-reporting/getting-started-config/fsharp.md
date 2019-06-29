You should initialize the SDK as early as possible, like in the `Main` method in `Program.fs`:

```fsharp
[<EntryPoint>]
let main argv =
    use __ = SentrySdk.Init("___PUBLIC_DSN___")
    // App code
    0
```

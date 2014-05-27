CancelAsync
===========

Allows easy cancellation of async/await methods.

Your Code
---------

    public async Task DoSomethingAsync()
    {
        // ... code
        CancelAsync.ThrowIfCancellationRequested();
        // ... code
        await AnotherAsync();
    }
    
What gets compiled
------------------

    public async Task DoSomethingAsync(CancellationToken ct = default(CancellationToken))
    {
        // ... code
        ct.ThrowIfCancellationRequested();
        // ... code
        await AnotherAsync(ct);
    }

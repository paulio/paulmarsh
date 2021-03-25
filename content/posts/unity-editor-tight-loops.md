---
title: "Unity Editor Tight Loops"
date: 2021-03-24T08:58:27+01:00
draft: false
---

<img src="https://miro.medium.com/max/700/1*DLAY8hRwc-3eC6j3QSnILw.jpeg"/>

If there is one thing that is guaranteed to drain the blood from the face of Unity Developer it's a tight loop. If you introduce a tight loop into you code then chances are you're going to have to kill the Unity Editor (tip: sometimes you can escape them by deliberately introducing an exception in the loop's code while running).

One way to mitigate this risk is put any dangerous code into a Coroutine with at least one yield inside the loop. 
This can give Unity the opportunity to stop the code. However, if you're writing a Unity Editor, StartCoroutine is part of the MonoBehaviour not the Editor - these are actually ScriptableObjects.

<!--more-->

## EditorCoroutineUtility

Probably the easiest solution is to use the Editor Coroutines Package. This brings an almost exact replica of the MonoBehaviour functions;

```csharp
EditorCoroutineUtility.StartCoroutine(CountEditorUpdates(), this);
```

Frankly I should probably just stop there. In fact, if that's all you need then stop reading and thank you :)

## Async Await


The underlying problem is that a tight loop occurs on the same thread as Unity is using to run code. So if we can move off this thread we should be able to prevent the problem. Consider an example of an Editor that 'Digs a Trench'
<img src="https://miro.medium.com/max/658/1*ayUUxjXODU5vrHL9DFnnyQ.png"/>

<img src="https://miro.medium.com/max/700/1*bW16LXhh7Ayfo4jEhsYXXw.png"/>


## Calling Code


```csharp
if (!_isDigging && GUILayout.Button("Dig Trench"))
{
    _tokenSource = new CancellationTokenSource();
    _cancelationToken = _tokenSource.Token;
    _isDigging = true;
    DigTrenchAsync(_cancelationToken).ContinueWith((t) => _isDigging = false ).ConfigureAwait(continueOnCapturedContext: false);
}
else if (_isDigging && GUILayout.Button("Stop Digging"))
{
    _tokenSource.Cancel();
}
```
By using a simple isDigging flag we can display a UI that allows the User to cancel the action. This only works if Unity isn't stuck in a loop hence we use DigTrenchAsync. Let's pick apart the code;

 *   Create a CancellationTokenSource - this will enable us to signal to our code that we want to cancel. Remember this code is likely to be running on a different thread to us so this is a safe way to communicate
 *   Get the CancelationToken - this is de-referencing the component that our code will examine to see if anyone has signaled for a cancel
 *   ```DigTrenchAsync(_cancelationToken)``` - call our async method passing in the cancellation token
 *   ```ContinueWith((t) => _isDigging = false)``` - When DigTrenchAsync finishes then we will run the code that is inside the ContinueWith, i.e. we set the isDigging flag to false
 *   ```ConfigureAwait``` - this tells the Aysnc Await framework that we don't need the thread we started on to take back control. Probably don't need this but it's muscle memory for me.

NB I've not included exception handling here, slap wrists

Then to stop the running code we can just call Cancel() on the token. Easy enough if a little verbose.
Async Code

The code that contains the loops simply has to a) check for a cancel b) yield control

```csharp
private async Task DigTrenchAsync(CancellationToken cancellationToken)
...
if (cancellationToken.IsCancellationRequested)
{
    return;
}
else
{
    await Task.Yield();
}
```

It's doesn't requite a lot of changes. Now we have non-blocking Editor code that can easily be cancelled. Yay.

NB You can raise a canceled exception rather than just return, depends how you want the caller to handle the cancellation.
## Back to EditorCoroutineUtility

Okay, okay, we've had a whistle stop tour of a Async Await solution, but I've already said we have a more familiar Coroutine route, what does that look like?

It's a lot more familiar to Unity Developers. The big bonus is that we can probably get away with just stopping the coroutine rather than worrying about it detecting a signal. However, it's still helpful for the coroutine to breath a little with the addition of a simple yield inside the loop;

```csharp
yield return null;
```

## Summary

It's always nice to have a choice of tools, but honestly, now we have EditorCoroutineUtility I think I'll be placing all my dangerous looping editor code in its care.



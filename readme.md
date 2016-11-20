# Asynchronous Delays

Within an asynchronous [block]() or [function](), the JavaScript's _await_ keyword in JavaScript allows execution to "step out" of and "return to" a context. We take advantage of this to arbitrarily pause code execution for a specific amount of time.

## Delay Function

Consider the following code.

```javascript
async{
  //do something
  const result = await //do something asynchronous
  //do something with result
}
```

Because _await_ operates on a promise, it pauses operation and resumes as soon as the promise resolves.

We can use _setTimeout_ to create a promise that resolves after a specified amount of time. Further, there's no reason to capture the result of the promise.

```javascript
async{
  //do something
  await new Promise(resolve=>setTimeout(resolve), /*specified amount of time*/)
  //do something with result
}
```

We can package this into a module for convenience:

```javascript
import delay from "asynchronous-delay";
async{
  //do something
  await delay(/*specified amount of time*/);
  //do something with result
}
```

## Event Loop
It is sometimes useful to use _setTimeout_ without a second argument to force code to execute in the next event loop.

```javascript
//do something
setTimeout(()=>{
  //do something in the next event loop.
})
```

A similar effect can be achieved using delay.

```javascript
async {
  //do something
  await delay();
  //do something in the next event loop.
}
```

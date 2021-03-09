# Asynchronous Flow Control in Javascript

## But first: Callbacks Recap!
Callback functions are exteremely important to asynchronous flow control, so let's talk about them first.

A callback function is a function that is passed as a parameter to another funciton. A function that uses a callback function is a **higher-order function**. (A higher-order function can also *return* a new function, but that's for later.)

## Now: Timeouts!
`setTimeout(callback, time)`

This code executes the callback function after the specified `time` delay in milliseconds.

**IMPORTANT NOTE**: **The code as whole doesn't wait!** If `setTimeout` is in a loop or conditional, the loop *doesn't wait the callback function to execute*. It queues up the callback function, and ONLY the callback function. Once it queues up the callback function and sets the timer, `setTimeout` is DONE and the code continues as normal.

### Example
```JS
//Let's make breakfast!
const cookEggs = nextStep => {
  console.log('Eggy bois are cooking! Press F to pay respects to your stomach. Because you\'re Pladd, and your stomach hates eggs.');
  // I don't know what I'm cooking next, but I know my eggs take 2 seconds.
  setTimeout(nextStep, 2000);
}

const cookBacon = nextStep => {
  console.log('Cooking bacon! Watch the smoke. If you set the smoke detector off, your dog will go bananas.');
  console.log('Also, don\'t tell Francis you used bacon instead of hash browns for this example.');

  setTimeout(nextStep, 3000);
}

const makePlate = () => {
  console.log('yum food good eat throw the eggs in the garbage though. god i wish i could still eat eggs.');
}

//We need to nest the callbacks, but we have to pass parameters at the same time.
//So this wouldn't work:
//cookEggs(cookBacon(makePlate));
//Because cookEggs needs a FUNCTION, not the RESULT of a function.
//So we make a new function:

const baconAndPlate = () => cookBacon(makePlate);

cookEggs(baconAndPlate);

//We could also do it in one line like this:
cookEggs( () => cookBacon(makePlate) );
```

## The Event Loop
Asynchronous callback functions exist outside the thread of the **Event Loop**. The event loop is listening for events, and asynchronous callbacks generate events.

### Events

Events are emitted by **emitters**, and an emitter listens for its own events!

An emitter can emit all kinds of events, and listen for many other kinds of events. 

Other functions of note:
* `setInterval(callback, time)` creates a RECURRING timer

Events are baked in to a lot of libraries - we don't always have to create our emitters manually

## Asynchronous Calls
Asynchronous stuff ALWAYS executes after synchronous stuff! Asychronous calls get shoved to the VERY END of the synchronous code.

So if you have an asynchronous, 0-ms-delay command to log "hi" to the console, and it's followed by a synchronous command that takes 10 years to complete, the program will wait 10 years to log "hi" to the console.

### Is This Function Asynchronous?

* You an do a sandwich test, by putting a `console.log` before and after the function! If the function executes after the log statements, it's asynchronous! If it executes in the middle, it's synchronous!
* You could also read the documentation!

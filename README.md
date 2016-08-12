# React Event System

## Objectives
1. Explain how React events differ from browser events
2. Describe how React standardizes events for compatibility
3. Explain how we use React events in our application

## What's the event system in React?
React has its own event system with special event handlers called `SyntheticEvent`. The reason for having a specific
event system instead of using native events is cross-browser compatibility. Some browsers treat events differently, and
by wrapping these events into a consistent API, React makes our lives a lot easier. It's important to keep in mind that
they are the _exact same events_, just implemented in a consistent way! That means these events also have methods like
`preventDefault()`, `stopPropagation()`, and so on.

## How to add event handlers
Consider the following component:

```js
class Tickler extends React.Component {
  constructor() {
    super();
    
    this.greet = this.greet.bind(this);
  }
  
  tickle() {
    console.log('Tee hee!');
  }

  render() {
    return (
      <button>Tickle me!</button>
    );
  }
}
```

We have a `tickle()` function, but no way to trigger it! This is a perfect time to add an event handler so that we can
see the message in our console. We attach event handlers to an element much like how we'd add a prop. The handler name
is always comprised of `on`, and the event name itself — for example `click`. These are joined together and camel-cased,
so if we wanted to add a click handler, we'd call the prop `onClick`. This prop takes a function as a value — it can
either be a reference to a method on the class (like our `tickle()` method), or an inline function. Most of time, we'll
use a function reference. It looks like this:
 
 ```js
<button onClick={this.tickle}>Tickle me!</button>
```

As you can see, we're passing a function _reference_, and not executing the `tickle` function. Keep in mind that we also
need to bind the function to the class instance in order to use it, as we saw in the complete example previously. Now,
when we click the button, we see a message in our console. Awesome!

There are a lot of event handlers we can add to an element, for example `onKeyUp`, `onMouseDown`, `onFocus`, `onSubmit`,
and many more. Check out the [complete list of supported events][supported-events] to see what else you can play around
with!

## Resources
- [React Synthetic Events](https://facebook.github.io/react/docs/events.html)

[supported-events]: https://facebook.github.io/react/docs/events.html#supported-events

## listener

**Type:** [EventListener](../eventlistener)  
**Description:** The event listener function reference.

```ts
function listener() {
  // Handle event
}

events.on('some-event', listener);
console.log(listener === events.getRawListeners('some-event')[0].listener); // -> true
```

## getListeners(event)

**Type:** Function  
**Arguments:**
  - event  
    **Type:** string  
    **Required:** Yes  
    **Description:** An event name.

**Returns:** Array&lt;[EventListener](./eventlistener)&gt;  
**Description:** Returns all listeners for an event.

```ts
function listener() {
  console.log('attached first');
}

events.on('some-event', listener);
console.log(listener === events.getListeners('some-event')[0]); // -> true
```

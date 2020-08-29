## getRawListeners(event)

**Type:** Function  
**Arguments:**
  - event  
    **Type:** string  
    **Required:** Yes  
    **Description:** An event name.

**Returns:** Array&lt;[EventListenerWrapper](./eventlistenerwrapper)&gt;  
**Description:** Returns the listeners array for an event.

```ts
function listener() {
  console.log('attached first');
}

events.on('some-event', listener);
console.log(listener === events.getRawListeners('some-event')[0].listener); // -> true
```

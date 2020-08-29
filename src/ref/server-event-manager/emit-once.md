## emitOnce(event, ...args)

**Type:** Function  
**Arguments:**
  - event  
    **Type:** string  
    **Required:** Yes  
    **Description:** An event name.
  - ...args  
    **Type:** Array&lt;any&gt;  
    **Required:** No  
    **Description:** Arguments to pass to listeners.

**Returns:** [ServerEventManager](./)  
**Description:** Emits an event once with the provided arguments. All future registered event handlers will be called immediately with these arguments. This event cannot be emitted anymore.

```ts
events.emitOnce('some-event', 'val1', 'val2');
// Will be ignored
events.emitOnce('some-event', 'val3');
events.emit('some-event');
```

> The arguments passed to this method (on the first emit) will be kept in memory and never be garbage collected.

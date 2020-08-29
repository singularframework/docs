## emit(event, ...args)

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
**Description:** Emits an event with the provided arguments.

```ts
events.emit('some-event', 'val1', 'val2');
```

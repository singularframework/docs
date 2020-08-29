## listenersCount(event)

**Type:** Function  
**Arguments:**
  - event  
    **Type:** string  
    **Required:** Yes  
    **Description:** An event name.

**Returns:** number  
**Description:** Returns the number of listeners for an event.

```ts
events.on('some-event', () => {});

events.listenersCount('some-event'); // -> 1
```

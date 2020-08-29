## prependListener(event, listener)

**Type:** Function  
**Arguments:**
  - event  
    **Type:** string  
    **Required:** Yes  
    **Description:** An event name.
  - listener  
    **Type:** [EventListener](./eventlistener)  
    **Required:** Yes  
    **Description:** An event listener callback.

**Returns:** [ServerEventManager](./)  
**Description:** Prepends a listener to an event.

```ts
events.on('some-event', () => console.log('attached first'));
events.prependListener('some-event', () => console.log('attached second'));

events.emit('some-event'); // -> attached second, attached first
```

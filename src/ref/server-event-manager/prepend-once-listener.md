## prependOnceListener(event, listener)

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
**Description:** Prepends a listener to an event and removes it after the event emits.

```ts
events.on('some-event', () => console.log('attached first'));
events.prependOnceListener('some-event', () => console.log('attached second'));

events.emit('some-event'); // -> attached second, attached first
events.emit('some-event'); // -> attached first
```

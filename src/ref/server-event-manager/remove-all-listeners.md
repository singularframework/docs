## removeAllListeners(event)

**Type:** Function  
**Arguments:**
  - event  
    **Type:** string  
    **Required:** Yes  
    **Description:** An event name.

**Returns:** [ServerEventManager](./)  
**Description:** Removes all listeners of an event.

```ts
events.on('some-event', () => console.log('listened'));

events.removeAllListeners('some-event');

// No listeners anymore
events.emit('some-event');
```

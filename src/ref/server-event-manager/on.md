## on(event, listener)

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
**Description:** Adds a listener to an event.

```ts
// Synchronous event
events.on('some-event', () => {
  // Handle event
});

// Asynchronous event
events.on('some-event', async () => {
  // Handle event
});

// Event with arguments
events.on('some-event', (arg1, arg2) => {
  // Handle event
});
```

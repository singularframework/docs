## once(event, listener)

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
**Description:** Adds a listener to an event and removes it after the event emits.

```ts
// Synchronous event
events.once('some-event', () => {
  // Handle event
});

// Asynchronous event
events.once('some-event', async () => {
  // Handle event
});

// Event with arguments
events.once('some-event', (arg1, arg2) => {
  // Handle event
});
```

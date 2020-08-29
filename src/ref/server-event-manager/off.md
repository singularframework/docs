## off(event, listener)

**Type:** Function  
**Arguments:**
  - event  
    **Type:** string  
    **Required:** Yes  
    **Description:** An event name.
  - listener  
    **Type:** [EventListener](./eventlistener)  
    **Required:** Yes  
    **Description:** A listener to remove.

**Returns:** [ServerEventManager](./)  
**Description:** Removes a listener from an event.

```ts
function listener() {
  // Handle event
}

// Attach the listener
events.on('some-event', listener);

// Remove the listener
events.off('some-event', listener);
```

## on(event, handler)

**Type:** Function  
**Arguments:**
  - event  
    **Type:** string  
    **Required:** Yes  
    **Description:** A [session event](./session-events) name.
  - handler  
    **Type:** Function  
    **Required:** Yes  
    **Description:** An event handler. Can return a Promise for asynchronous execution.

**Returns:** [ServerSessionManager](./)  
**Description:** Adds an event handler to a [session event](./session-events).

```ts
session.on('created', id => {
  // Write session ID in database...
});
```

## error

**Type:** Event  
**Arguments:**
  - error  
    **Type:** Error  
    **Description:** The thrown error object.

**Description:** Emits when an error is thrown by Express or through the launch stage. This event is useful for error reporting/handling.

```ts
events.on('error', error => {
  // Report error to a third-party service...
});
```

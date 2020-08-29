## error(message, ...additionalMessages)

**Type:** Function  
**Arguments:**
  - message  
    **Type:** any  
    **Required:** Yes  
    **Description:** A message to log.
  - ...additionalMessages  
    **Type:** Array&lt;any&gt;  
    **Required:** No  
    **Description:** Additional messages to log.

**Returns:** void  
**Description:** Logs a message at error level.

```ts
log.error('An error is thrown!', new Error('Some error!'));
```

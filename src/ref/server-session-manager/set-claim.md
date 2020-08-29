## setClaim(id, key, value)

**Type:** Function  
**Arguments:**
  - id  
    **Type:** string  
    **Required:** Yes  
    **Description:** A generated session ID.
  - key  
    **Type:** string  
    **Required:** Yes  
    **Description:** The claim key.
  - value  
    **Type:** any  
    **Required:** Yes  
    **Description:** The claim value.

**Returns:** void | Promise&lt;void&gt;  
**Description:** Emits the [claim:set](./session-events/#claimset) event, running its handler and returning the handler's return value. The handler may return a Promise, which would be also returned by this method for flow control.

```ts
await session.setClaim('a-session-id', 'ip', '0.0.0.0');
```

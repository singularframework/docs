## getClaim(id, key)

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

**Returns:** any | Promise&lt;any&gt;  
**Description:** Emits the [claim:get](./session-events/#claimget) event, running its handler and returning the handler's return value. The handler may return a Promise, which would be also returned by this method for flow control.

```ts
const ip = await session.getClaim('a-session-id', 'ip');
```

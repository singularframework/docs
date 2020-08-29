## id(sessionId)

**Type:** Function  
**Arguments:**
  - sessionId  
    **Type:** string  
    **Required:** Yes  
    **Description:** A session ID.

**Returns:** [ServerLogger](./)  
**Description:** Returns a new instance of [ServerLogger](./) which includes the passed in `sessionId` in all logs made using it.

```ts
// Generated log will include 'a-session-id' as the session ID
log.id('a-session-id').info('Log this message!');
```

> The returned [ServerLogger](./) instance will not have the [id(sessionId)](#idsessionid) method available.

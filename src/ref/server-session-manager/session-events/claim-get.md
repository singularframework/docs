## claim:get

**Type:** Event  
**Arguments:**
  - id  
    **Type:** string  
    **Description**: A session ID.
  - key  
    **Type:** string  
    **Description**: The claim key.

**Description:** Emits when a claim is requested to be read under an existing session ID by calling [getClaim(id, key)](../#getclaimid-key). The claim value should be retrieved from the database and returned.

```ts
session.on('claim:get', async (id, key) => {

  // Read the claim value under the session ID and return it

});
```

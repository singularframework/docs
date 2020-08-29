## claim:set

**Type:** Event  
**Arguments:**
  - id  
    **Type:** string  
    **Description**: A session ID.
  - key  
    **Type:** string  
    **Description**: The claim key.
  - value  
    **Type:** any  
    **Description**: The claim value.

**Description:** Emits when a claim is being set on an existing session ID by calling [setClaim(id, key, value)](../#setclaimid-key-value). The claim should be stored in a database under the session ID.

```ts
session.on('claim:set', async (id, key, value) => {

  // Write the claim under the session ID

});
```

## created

**Type:** Event  
**Arguments:**
  - id  
    **Type:** string  
    **Description**: A newly generated session ID.

**Description:** Emits when a new session ID is generated and attached to a [Request](../../middleware-parameters/request) object. This ID should be stored in a database so future claims can be written and read under it.

```ts
session.on('created', async id => {

  // Store the ID in a database

});
```

> If the handler's returned promise doesn't get resolved or rejected, the request will hang forever since the middleware responsible for calling the `created` handler won't call [next()](../../middleware-parameters/nextfunction)!

## <i>constructor(message, httpCode, code)</i>

**Type:** constructor  
**Arguments:**
  - message  
    **Type:** string  
    **Required:** Yes  
    **Description:** An error message.
  - httpCode  
    **Type:** number  
    **Required:** No  
    **Default value:** 500  
    **Description:** An HTTP status code used by [respond(res)](#respondres) for setting the respond status code.
  - code  
    **Type:** string  
    **Required:** No  
    **Default value:** `'UNKNOWN_ERROR'`  
    **Description:** A code for classifying errors.

**Returns:** [ServerError](./)  
**Description:** Constructs a new [ServerError](./) object.

```ts
new ServerError('Invalid credentials!', 403, 'invalid-credentials-error');
```

> Keep in mind that constructing a [ServerError](./) directly won't generate a [stack](#stack).

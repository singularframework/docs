## ServerError.from(error, httpCode, code)

**Type:** Function  
**Static:** Yes  
**Arguments:**
  - error  
    **Type:** Error  
    **Required:** Yes  
    **Description:** An Error object.
  - httpCode  
    **Type:** number  
    **Required:** No  
    **Default value:** 500  
    **Description:** An HTTP status code used by [respond(res)](#respondres) for setting the respond status code.
  - code  
    **Type:** string  
    **Required:** No  
    **Default value:** `error.code` or `'UNKNOWN_ERROR'`  
    **Description:** A code for classifying errors. If not provided, will default to either `error.code` (from the first argument) or `'UNKNOWN_ERROR'`.

**Returns:** [ServerError](./)  
**Description:** Constructs a new [ServerError](./) object from an Error object. Using this method will copy the [stack](#stack) from the passed in Error object.

```ts
try {

  // Do stuff

}
catch (error) {

  // Wrap error as a ServerError
  ServerError.from(error, 500);

}
```

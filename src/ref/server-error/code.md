## code

**Type:** string  
**Default value:** `'UNKNOWN_ERROR'`  
**Description:** The classification code of the [ServerError](./).

```ts
const error = new ServerError('Something went wrong!', null, 'unknown');
error.code; // -> 'unknown'
```

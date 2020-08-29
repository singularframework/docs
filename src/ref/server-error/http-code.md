## httpCode

**Type:** number  
**Default value:** 500  
**Description:** The HTTP status code for the [ServerError](./).

```ts
const error = new ServerError('Something went wrong!');
error.httpCode; // -> 500
```

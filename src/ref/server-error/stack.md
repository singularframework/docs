## stack

**Type:** string  
**Description:** The error stack of the [ServerError](./) when object has been created using [ServerError.from(error, httpCode, code)](#servererrorfromerror-httpcode-code).

```ts
let error = ServerError.from(new Error());
error.stack !== undefined; // -> true

error = new ServerError('Something went wrong!');
error.stack; // -> undefined
```

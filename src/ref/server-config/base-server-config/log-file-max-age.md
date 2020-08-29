## logFileMaxAge

**Type:** number  
**Required:** No  
**Default value:** `7`  
**Description:** The maximum age of a logs file in days. When passed, the file will either get archived or deleted depending on [archiveLogs](#archivelogs).

```ts
// src/config.ts
export const config = {
  logFileMaxAge: 1
};
```

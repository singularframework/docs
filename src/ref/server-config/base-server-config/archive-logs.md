## archiveLogs

**Type:** boolean  
**Required:** No  
**Default value:** `true`  
**Description:** Will archive logs written on disk that are older than their max age instead of deleting them.

```ts
// src/config.ts
export const config = {
  archiveLogs: false
};
```

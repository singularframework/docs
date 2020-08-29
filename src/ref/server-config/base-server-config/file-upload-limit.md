## fileUploadLimit

**Type:** string  
**Required:** No  
**Default value:** `10mb`  
**Description:** The file upload limit with suffix accepted by the server (e.g. `kb`, `mb`, `gb`).

```ts
// src/config.ts
export const config = {
  fileUploadLimit: '2mb'
};
```

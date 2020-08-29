## excludeHeadersInLogs

**Type:** Array&lt;string&gt;  
**Required:** No  
**Default value:** `['authorization']`  
**Description:** A list of header names to hide in logs when logging request headers (controlled by [logRequestHeaders](#logrequestheaders)). Useful for hiding sensitive information from logs.

```ts
// src/config.ts
export const config = {
  excludeHeadersInLogs: ['user-key']
};
```

> The `authorization` header is the default value and cannot be overridden. It will be pushed to any array passed as the config value.

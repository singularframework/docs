## excludeQueryParamsInLogs

**Type:** Array&lt;string&gt;  
**Required:** No  
**Default value:** `[]`  
**Description:** A list of query parameter names to hide in logs. Useful for hiding sensitive information (tokens, etc.).

```ts
// src/config.ts
export const config = {
  excludeQueryParamsInLogs: ['token']
};
```

## consoleLogLevels

**Type:** 'all' | Array&lt;'debug'|'info'|'notice'|'warn'|'error'&gt;  
**Required:** No  
**Default value:** `['info', 'notice', 'warn', 'error']`  
**Description:** An array of log levels to show in the console or `all` (no array) to show all levels.

```ts
// src/config.ts
export const config = {
  consoleLogLevels: 'all'
};
```

## logFileLevels

**Type:** 'all' | Array&lt;'debug'|'info'|'notice'|'warn'|'error'&gt;  
**Required:** No  
**Default value:** `all`  
**Description:** An array of log levels to write on disk or `all` (no array) to write all levels when file logging is enabled.

```ts
// src/config.ts
export const config = {
  logFileLevels: ['debug', 'notice', 'error']
};
```

## timezone

**Type:** string  
**Required:** No  
**Default value:** Local system timezone  
**Description:** The timezone of the server which can be any IANA zone supported by the host environment, or a fixed-offset name of the form 'UTC+3'.

```ts
// src/config.ts
export const config = {
  timezone: 'America/Los_Angeles'
};
```

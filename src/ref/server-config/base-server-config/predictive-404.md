## predictive404

**Type:** boolean  
**Required:** No  
**Default value:** `false`  
**Description:** If true, installs a 404 handler at the top of the stack instead (this can be configured through [predictive404Priority](#predictive404priority)), which predicts if path will match with any middleware in the stack and rejects the request with a 404 error if not. This is useful as requests that will eventually result in a 404 error won't go through the stack in the first place. Please note that the prediction ignores all `*` and `/` routes.

```ts
// src/config.ts
export const config = {
  predictive404: true
};
```

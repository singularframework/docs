## cookieSecret

**Type:** string  
**Required:** No  
**Default value:** `undefined`  
**Description:** A secret to sign cookies with. Cookies will be unsigned if no secret is provided. If session management is enabled (controlled by [sessionManagement](#sessionmanagement)), all session cookies will be signed with this secret (if provided).

```ts
// src/config.ts
export const config = {
  cookieSecret: process.env.COOKIE_SECRET
};
```

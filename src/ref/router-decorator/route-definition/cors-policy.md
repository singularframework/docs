## corsPolicy

**Type:** [CORSPolicy](../corspolicy)  
**Required:** No  
**Default value:** `{ origin: true }`  
**Description:** Defines a CORS policy for the route, overriding the router's CORS policy (if any).

```ts
import { Router } from '@steroids/core';

@Router({
  routes: [
    { path: '/', corsPolicy: { origin: true } }
  ]
})
export class ExampleRouter { }
```

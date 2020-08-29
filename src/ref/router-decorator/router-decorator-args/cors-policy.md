## corsPolicy

**Type:** [CORSPolicy](../corspolicy)  
**Required:** No  
**Default value:** `{ origin: true }`  
**Description:** Defines a CORS policy for all routes in this router.

```ts
import { Router } from '@steroids/core';

@Router({
  corsPolicy: {
    origin: true
  }
})
export class ExampleRouter { }
```

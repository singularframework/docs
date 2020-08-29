## priority

**Type:** number  
**Required:** No  
**Description:** A priority number for this router to use when sorting routers (higher number means higher priority). This affects the placement of routers in the Express middleware stack.

```ts
import { Router } from '@steroids/core';

@Router({
  priority: 100
})
export class ExampleRouter {

}
```

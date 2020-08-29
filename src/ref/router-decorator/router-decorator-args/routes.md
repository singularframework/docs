## routes

**Type:** Array&lt;[RouteDefinition](../routedefinition)&gt;  
**Required:** Yes  
**Description:** Defines all routes inside this router.

```ts
import { Router, RouteMethod, Request, Response } from '@steroids/core';

@Router({
  routes: [
    { path: '/example', method: RouteMethod.GET, handler: 'example' }
  ]
})
export class ExampleRouter {

  example(req: Request, res: Response) {

  }

}
```

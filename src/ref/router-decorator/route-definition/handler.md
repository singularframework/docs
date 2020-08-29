## handler

**Type:** string  
**Required:** Yes  
**Description:** The name of an existing function on the router class to use as the route handler.

```ts
import { Router, Request, Response } from '@steroids/core';

@Router({
  routes: [
    { path: '/example', handler: 'exampleHandler' }
  ]
})
export class ExampleRouter {

  exampleHandler(req: Request, res: Response) {

  }

}
```

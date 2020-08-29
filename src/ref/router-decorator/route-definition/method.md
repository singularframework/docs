## method

**Type:** [RouteMethod](./routemethod)  
**Required:** No  
**Description:** The route's HTTP method. If this property is missing, the middleware will be installed globally using `app.use()` in Express.

```ts
import { Router, RouteMethod } from '@steroids/core';

@Router({
  routes: [
    { path: '/' },
    { path: '/example', method: RouteMethod.GET }
  ]
})
export class ExampleRouter {

}
```

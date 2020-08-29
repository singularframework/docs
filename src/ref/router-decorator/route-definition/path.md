## path

**Type:** string  
**Required:** Yes  
**Description:** The route's path with the same syntax as Express' paths.

```ts
import { Router } from '@steroids/core';

@Router({
  routes: [
    { path: '/' },
    { path: '/example/:id' },
    { path: '/example' }
  ]
})
export class ExampleRouter {

}
```

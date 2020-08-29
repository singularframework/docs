## type

**Type:** [ValidationType](./validationtype)  
**Required:** Yes  
**Description:** The validation type, indicating what part of the request to validate.

```ts
import { Router, ValidationType } from '@steroids/core';

@Router({
  routes: [
    { path: '/example', validate: [
      { type: ValidationType.Custom }
    ]}
  ]
})
export class ExampleRouter {

}
```

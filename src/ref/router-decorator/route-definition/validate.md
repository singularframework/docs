## validate

**Type:** Array&lt;[ValidationRule](./validationrule)&gt;  
**Required:** No  
**Description:** An array of [ValidationRule](./validationrule) objects to use for route validation.

```ts
import { Router, headers, equal } from '@steroids/core';

@Router({
  routes: [
    { path: '/', validate: [
      // Using a built-in ValidationRule factory
      headers({
        // Using a built-in ValidatorFunction factory
        'content-type': equal('application/json')
      })
    ]}
  ]
})
export class ExampleRouter {

}
```

## num.lte(val)

**Type:** Function  
**Arguments:**
  - val  
    **Type:** number  
    **Required:** Yes  
    **Description:** Upper bound (inclusive).

**Type check:** No  
**Casts:** Yes  
**Returns:** [ValidatorFunction](../router-decorator/routedefinition/validationrule/validatorfunction)  
**Description:** Casts the target value to number and checks to see if the target is less than the upper bound.

```ts
import { Router, body, num } from '@steroids/core';

@Router({
  name: 'example',
  routes: [
    { path: '/', validate: [
      body({
        expiration: num.lte(Date.now())
      })
    ]}
  ]
})
export class ExampleRouter { }
```

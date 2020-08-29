## num.gte(val)

**Type:** Function  
**Arguments:**
  - val  
    **Type:** number  
    **Required:** Yes  
    **Description:** Lower bound (inclusive).

**Type check:** No  
**Casts:** Yes  
**Returns:** [ValidatorFunction](../router-decorator/routedefinition/validationrule/validatorfunction)  
**Description:** Casts the target value to number and checks to see if the target is greater than or equal the lower bound.

```ts
import { Router, body, num } from '@steroids/core';

@Router({
  name: 'example',
  routes: [
    { path: '/', validate: [
      body({
        age: num.gte(18)
      })
    ]}
  ]
})
export class ExampleRouter { }
```

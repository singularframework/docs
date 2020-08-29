## num.betweenEx(min, max)

**Type:** Function  
**Arguments:**
  - min  
    **Type:** number  
    **Required:** Yes  
    **Description:** Lower bound (exclusive).
  - max  
    **Type:** number  
    **Required:** Yes  
    **Description:** Upper bound (exclusive).

**Type check:** No  
**Casts:** Yes  
**Returns:** [ValidatorFunction](../router-decorator/routedefinition/validationrule/validatorfunction)  
**Description:** Casts the target value to number and checks to see if the target is between the given bounds.

```ts
import { Router, body, num } from '@steroids/core';

@Router({
  name: 'example',
  routes: [
    { path: '/', validate: [
      body({
        age: num.betweenEx(17, 100)
      })
    ]}
  ]
})
export class ExampleRouter { }
```

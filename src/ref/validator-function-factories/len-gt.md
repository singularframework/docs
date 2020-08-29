## len.gt(val)

**Type:** Function  
**Arguments:**
  - val  
    **Type:** number  
    **Required:** Yes  
    **Description:** Lower bound (exclusive).

**Type check:** No  
**Casts:** No  
**Returns:** [ValidatorFunction](../router-decorator/routedefinition/validationrule/validatorfunction)  
**Description:** Checks the length of the target (using `value.length`) to see if it is greater than the given lower bound.

```ts
import { Router, body, len } from '@steroids/core';

@Router({
  name: 'example',
  routes: [
    { path: '/', validate: [
      body({
        // Checking an array
        children: len.gt(0)
      })
    ]}
  ]
})
export class ExampleRouter { }
```

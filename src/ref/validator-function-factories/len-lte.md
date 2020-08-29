## len.lte(val)

**Type:** Function  
**Arguments:**
  - val  
    **Type:** number  
    **Required:** Yes  
    **Description:** Upper bound (inclusive).

**Type check:** No  
**Casts:** No  
**Returns:** [ValidatorFunction](../router-decorator/routedefinition/validationrule/validatorfunction)  
**Description:** Checks the length of the target (using `value.length`) to see if it is less than or equal the given upper bound.

```ts
import { Router, body, len } from '@steroids/core';

@Router({
  name: 'example',
  routes: [
    { path: '/', validate: [
      body({
        // Checking an array
        children: len.lte(100)
      })
    ]}
  ]
})
export class ExampleRouter { }
```

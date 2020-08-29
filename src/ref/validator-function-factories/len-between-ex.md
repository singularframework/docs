## len.betweenEx(min, max)

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
**Casts:** No  
**Returns:** [ValidatorFunction](../router-decorator/routedefinition/validationrule/validatorfunction)  
**Description:** Checks the length of the target (using `value.length`) to see if it is between the given bounds.

```ts
import { Router, body, len } from '@steroids/core';

@Router({
  name: 'example',
  routes: [
    { path: '/', validate: [
      body({
        // Checking an array
        children: len.betweenEx(0, 10)
      })
    ]}
  ]
})
export class ExampleRouter { }
```

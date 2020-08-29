## num.lteRef(ref)

**Type:** Function  
**Arguments:**
  - ref  
    **Type:** string  
    **Required:** Yes  
    **Description:** A reference path to resolve from `rawValues` where child nodes are separated by `.` (e.g. `name.first`).

**Type check:** No  
**Casts:** Yes  
**Returns:** [ValidatorFunction](../router-decorator/routedefinition/validationrule/validatorfunction)  
**Description:** Casts the target value to number and checks to see if the target is less than or equal the upper bound resolved from reference.

```ts
import { Router, body, type, num } from '@steroids/core';

@Router({
  name: 'example',
  routes: [
    { path: '/', validate: [
      body({
        createdAt: num.lteRef('updatedAt'),
        updatedAt: type.Number
      })
    ]}
  ]
})
export class ExampleRouter { }
```

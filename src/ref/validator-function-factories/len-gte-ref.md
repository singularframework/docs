## len.gteRef(ref)

**Type:** Function  
**Arguments:**
  - ref  
    **Type:** string  
    **Required:** Yes  
    **Description:** A reference path to resolve from `rawValues` where child nodes are separated by `.` (e.g. `name.first`).

**Type check:** No  
**Casts:** No  
**Returns:** [ValidatorFunction](../router-decorator/routedefinition/validationrule/validatorfunction)  
**Description:** Checks the length of the target (using `value.length`) to see if it is greater than or equal the lower bound resolved from reference.

```ts
import { Router, body, type, len } from '@steroids/core';

@Router({
  name: 'example',
  routes: [
    { path: '/', validate: [
      body({
        minChildren: type.Number,
        // Checking an array
        children: len.gteRef('minChildren')
      })
    ]}
  ]
})
export class ExampleRouter { }
```

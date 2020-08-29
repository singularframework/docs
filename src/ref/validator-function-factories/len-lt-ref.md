## len.ltRef(ref)

**Type:** Function  
**Arguments:**
  - ref  
    **Type:** string  
    **Required:** Yes  
    **Description:** A reference path to resolve from `rawValues` where child nodes are separated by `.` (e.g. `name.first`).

**Type check:** No  
**Casts:** No  
**Returns:** [ValidatorFunction](../router-decorator/routedefinition/validationrule/validatorfunction)  
**Description:** Checks the length of the target (using `value.length`) to see if it is less than the upper bound resolved from reference.

```ts
import { Router, body, type, len } from '@steroids/core';

@Router({
  name: 'example',
  routes: [
    { path: '/', validate: [
      body({
        maxChildren: type.Number,
        // Checking an array
        children: len.ltRef('maxChildren')
      })
    ]}
  ]
})
export class ExampleRouter { }
```

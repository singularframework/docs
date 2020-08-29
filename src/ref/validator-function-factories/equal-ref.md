## equalRef(ref)

**Type:** Function  
**Arguments:**
  - ref  
    **Type:** string  
    **Required:** Yes  
    **Description:** A reference path to resolve from `rawValues` where child nodes are separated by `.` (e.g. `name.first`).

**Type check:** No  
**Casts:** No  
**Returns:** [ValidatorFunction](../router-decorator/routedefinition/validationrule/validatorfunction)  
**Description:** Compares the value resolved from the given reference with the target value.

```ts
import { Router, body, type, equalRef } from '@steroids/core';

@Router({
  name: 'example',
  routes: [
    { path: '/', validate: [
      body({
        name: {
          first: type.String
        },
        firstName: equalRef('name.first')
      })
    ]}
  ]
})
export class ExampleRouter { }
```

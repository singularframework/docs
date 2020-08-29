## includeRef(ref)

**Type:** Function  
**Arguments:**
  - ref  
    **Type:** string  
    **Required:** Yes  
    **Description:** A reference path to resolve from `rawValues` where child nodes are separated by `.` (e.g. `name.first`).

**Type check:** No  
**Casts:** No  
**Returns:** [ValidatorFunction](../router-decorator/routedefinition/validationrule/validatorfunction)  
**Description:** Checks if the target value includes the value resolved from a given reference using `.include()` method. Will fail the validation if the target value doesn't have `.include()` defined on it.

```ts
import { Router, body, includeRef, type } from '@steroids/core';

@Router({
  name: 'example',
  routes: [
    { path: '/', validate: [
      body({
        fullName: include('firstName'),
        firstName: type.String
      })
    ]}
  ]
})
export class ExampleRouter { }
```

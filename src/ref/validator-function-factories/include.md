## include(val)

**Type:** Function  
**Arguments:**
  - val  
    **Type:** any  
    **Required:** Yes  
    **Description:** A value to check if it's included in the target value.

**Type check:** No  
**Casts:** No  
**Returns:** [ValidatorFunction](../router-decorator/routedefinition/validationrule/validatorfunction)  
**Description:** Checks if the target value includes a given value using `.include()` method. Will fail the validation if the target value doesn't have `.include()` defined on it.

```ts
import { Router, body, include } from '@steroids/core';

@Router({
  name: 'example',
  routes: [
    { path: '/', validate: [
      body({
        fullName: include('Mr.')
      })
    ]}
  ]
})
export class ExampleRouter { }
```

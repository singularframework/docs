## type.Array(validator, arrayValidator)

**Namespace:** type  
**Type:** Function  
**Arguments:**
  - validator  
    **Type:** [ValidatorFunction](../router-decorator/routedefinition/validationrule/validatorfunction)  
    **Required:** No  
    **Description:** A validator function to run on all items in the array.
  - arrayValidator  
    **Type:** [ValidatorFunction](../router-decorator/routedefinition/validationrule/validatorfunction)  
    **Required:** No  
    **Description:** A validator function to run on the whole array.

**Type check:** Yes  
**Casts:** No  
**Returns:** [ValidatorFunction](../router-decorator/routedefinition/validationrule/validatorfunction)  
**Description:** Performs an array type comparison. Also runs validator functions on all items in the array and the whole array.

```ts
import { Router, body, type, len } from '@steroids/core';

@Router({
  name: 'example',
  routes: [
    { path: '/', validate: [
      body({
        // An array of strings with at least one item
        images: type.Array(type.String, len.gt(0))
      })
    ]}
  ]
})
export class ExampleRouter { }
```

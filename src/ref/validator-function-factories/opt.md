## opt(validator)

**Type:** Function  
**Arguments:**
  - validator  
    **Type:** [ValidatorFunction](../router-decorator/routedefinition/validationrule/validatorfunction)  
    **Required:** Yes  
    **Description:** A validator.

**Type check:** No  
**Casts:** No  
**Returns:** [ValidatorFunction](../router-decorator/routedefinition/validationrule/validatorfunction)  
**Description:** Makes the target optional. If the target is `undefined`, the validation will be passed, otherwise the given validator will determine the result of the validation.

```ts
import { Router, body, opt, num } from '@steroids/core';

@Router({
  name: 'example',
  routes: [
    { path: '/', validate: [
      body({
        // Optional, but if provided, it should be greater than 18
        age: opt(num.gt(18))
      })
    ]}
  ]
})
export class ExampleRouter { }
```

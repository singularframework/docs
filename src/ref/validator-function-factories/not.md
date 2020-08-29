## not(validator)

**Type:** Function  
**Arguments:**
  - validator  
    **Type:** [ValidatorFunction](../router-decorator/routedefinition/validationrule/validatorfunction)  
    **Required:** Yes  
    **Description:** A validator.

**Type check:** No  
**Casts:** No  
**Returns:** [ValidatorFunction](../router-decorator/routedefinition/validationrule/validatorfunction)  
**Description:** Negates the given validator.

```ts
import { Router, body, not, include } from '@steroids/core';

@Router({
  name: 'example',
  routes: [
    { path: '/', validate: [
      body({
        name: not(include('@'))
      })
    ]}
  ]
})
export class ExampleRouter { }
```

## type.Boolean

**Namespace:** type  
**Type:** Function  
**Arguments:** Same as [ValidatorFunction](../router-decorator/routedefinition/validationrule/validatorfunction)  
**Type check:** Yes  
**Casts:** No  
**Returns:** Same as [ValidatorFunction](../router-decorator/routedefinition/validationrule/validatorfunction)  
**Description:** Performs boolean type comparison.

```ts
import { Router, body, type } from '@steroids/core';

@Router({
  name: 'example',
  routes: [
    { path: '/', validate: [
      body({
        admin: type.Boolean
      })
    ]}
  ]
})
export class ExampleRouter { }
```

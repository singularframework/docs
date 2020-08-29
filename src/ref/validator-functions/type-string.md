## type.String

**Namespace:** type  
**Type:** Function  
**Arguments:** Same as [ValidatorFunction](../router-decorator/routedefinition/validationrule/validatorfunction)  
**Type check:** Yes  
**Casts:** No  
**Returns:** Same as [ValidatorFunction](../router-decorator/routedefinition/validationrule/validatorfunction)  
**Description:** Performs string type comparison.

```ts
import { Router, body, type } from '@steroids/core';

@Router({
  name: 'example',
  routes: [
    { path: '/', validate: [
      body({
        firstName: type.String
      })
    ]}
  ]
})
export class ExampleRouter { }
```

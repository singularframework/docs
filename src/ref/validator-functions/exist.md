## exist

**Namespace:** type  
**Type:** Function  
**Arguments:** Same as [ValidatorFunction](../router-decorator/routedefinition/validationrule/validatorfunction)  
**Type check:** No  
**Casts:** No  
**Returns:** Same as [ValidatorFunction](../router-decorator/routedefinition/validationrule/validatorfunction)  
**Description:** Checks if value is not `undefined`.

```ts
import { Router, body, exist } from '@steroids/core';

@Router({
  name: 'example',
  routes: [
    { path: '/', validate: [
      body({
        firstName: exist
      })
    ]}
  ]
})
export class ExampleRouter { }
```

## and(...validators)

**Type:** Function  
**Arguments:**
  - ...validators  
    **Type:** Array&lt;[ValidatorFunction](../router-decorator/routedefinition/validationrule/validatorfunction)&gt;  
    **Required:** Yes  
    **Description:** An array of validators.

**Type check:** No  
**Casts:** No  
**Returns:** [ValidatorFunction](../router-decorator/routedefinition/validationrule/validatorfunction)  
**Description:** ANDs all given validators.

```ts
import { Router, body, and, type, num } from '@steroids/core';

@Router({
  name: 'example',
  routes: [
    { path: '/', validate: [
      body({
        age: and(type.Number, num.gte(18), num.lt(100))
      })
    ]}
  ]
})
export class ExampleRouter { }
```

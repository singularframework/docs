## or(...validators)

**Type:** Function  
**Arguments:**
  - ...validators  
    **Type:** Array&lt;[ValidatorFunction](../router-decorator/routedefinition/validationrule/validatorfunction)&gt;  
    **Required:** Yes  
    **Description:** An array of validators.

**Type check:** No  
**Casts:** No  
**Returns:** [ValidatorFunction](../router-decorator/routedefinition/validationrule/validatorfunction)  
**Description:** ORs all given validators.

```ts
import { Router, body, or, equal } from '@steroids/core';

@Router({
  name: 'example',
  routes: [
    { path: '/', validate: [
      body({
        answer: or(equal('yes'), equal('no'))
      })
    ]}
  ]
})
export class ExampleRouter { }
```

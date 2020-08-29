## equal(val)

**Type:** Function  
**Arguments:**
  - val  
    **Type:** any  
    **Required:** Yes  
    **Description:** A value to compare the target with.

**Type check:** No  
**Casts:** No  
**Returns:** [ValidatorFunction](../router-decorator/routedefinition/validationrule/validatorfunction)  
**Description:** Compares the given value with the target value.

```ts
import { Router, body, equal } from '@steroids/core';

@Router({
  name: 'example',
  routes: [
    { path: '/', validate: [
      body({
        firstName: equal('john')
      })
    ]}
  ]
})
export class ExampleRouter { }
```

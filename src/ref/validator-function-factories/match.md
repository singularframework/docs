## match(regex)

**Type:** Function  
**Arguments:**
  - regex  
    **Type:** RegExp  
    **Required:** Yes  
    **Description:** A regular expression to match the value to.

**Type check:** Yes  
**Casts:** No  
**Returns:** [ValidatorFunction](../router-decorator/routedefinition/validationrule/validatorfunction)  
**Description:** Matches a value to a given regular expression.

```ts
import { Router, body, match } from '@steroids/core';

@Router({
  name: 'example',
  routes: [
    { path: '/', validate: [
      body({
        image: match(/^.+\.jpg$/i)
      })
    ]}
  ]
})
export class ExampleRouter { }
```

## headers(validator)

**Type:** Function  
**Arguments:**
  - validator  
    **Type:** [ValidationDefinition](../router-decorator/routedefinition/validationrule/validationdefinition)  
    **Required:** Yes  
    **Description:** A validation definition.

**Returns:** [ValidationRule](../router-decorator/routedefinition/validationrule)  
**Description:** Creates a validation rule which validates request headers.

```ts
import { Router, headers, equal } from '@steroids/core';

@Router({
  name: 'example',
  routes: [
    { path: '/', validate: [
      headers({
        'content-type': equal('application/json')
      })
    ]}
  ]
})
export class ExampleRouter { }
```

## queries(validator)

**Type:** Function  
**Arguments:**
  - validator  
    **Type:** [ValidationDefinition](../router-decorator/routedefinition/validationrule/validationdefinition)  
    **Required:** Yes  
    **Description:** A validation definition.

**Returns:** [ValidationRule](../router-decorator/routedefinition/validationrule)  
**Description:** Creates a validation rule which validates request query parameters.

```ts
import { Router, queries, num } from '@steroids/core';

@Router({
  name: 'example',
  routes: [
    { path: '/', validate: [
      queries({
        'limit': num.between(1, 100)
      })
    ]}
  ]
})
export class ExampleRouter { }
```

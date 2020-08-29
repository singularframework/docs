## body(validator)

**Type:** Function  
**Arguments:**
  - validator  
    **Type:** [BodyValidationDefinition](../router-decorator/routedefinition/validationrule/bodyvalidationdefinition)  
    **Required:** Yes  
    **Description:** A body validation definition.

**Returns:** [ValidationRule](../router-decorator/routedefinition/validationrule)  
**Description:** Creates a validation rule which validates request body.

```ts
import { Router, body, type, num, and } from '@steroids/core';

@Router({
  name: 'example',
  routes: [
    { path: '/', validate: [
      body({
        time: {
          start: type.Number,
          end: and(type.Number, num.gtRef('time.start'))
        }
      })
    ]}
  ]
})
export class ExampleRouter { }
```

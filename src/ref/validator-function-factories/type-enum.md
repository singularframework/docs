## type.Enum(enumerator)

**Namespace:** type  
**Type:** Function  
**Arguments:**
  - enumerator  
    **Type:** Enum  
    **Required:** Yes  
    **Description:** An enumerator object.

**Type check:** Yes  
**Casts:** No  
**Returns:** [ValidatorFunction](../router-decorator/routedefinition/validationrule/validatorfunction)  
**Description:** Performs an enum type comparison, checking if the value belongs to enum.

```ts
import { Router, body, type } from '@steroids/core';

enum Direction {
  Left,
  Right,
  Up,
  Down
}

@Router({
  name: 'example',
  routes: [
    { path: '/', validate: [
      body({
        direction: type.Enum(Direction)
      })
    ]}
  ]
})
export class ExampleRouter { }
```

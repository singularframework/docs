## custom(validator)

**Type:** Function  
**Arguments:**
  - validator  
    **Type:** [ValidatorFunction](../router-decorator/routedefinition/validationrule/validatorfunction) | [AsyncValidatorFunction](../router-decorator/routedefinition/validationrule/asyncvalidatorfunction)  
    **Required:** Yes  
    **Description:** A validator function.

**Returns:** [ValidationRule](../router-decorator/routedefinition/validationrule)  
**Description:** Creates a validation rule which validates a request object.

```ts
import { Router, custom, Request } from '@steroids/core';

async function validator(req: Request): boolean|Error {
  // Validate the req object...
}

@Router({
  name: 'example',
  routes: [
    { path: '/', validate: [
      custom(validator)
    ]}
  ]
})
export class ExampleRouter { }
```

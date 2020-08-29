## validator

**Type:** [ValidatorFunction](./validatorfunction) | [AsyncValidatorFunction](./asyncvalidatorfunction) | [ValidationDefinition](./validationdefinition) | [BodyValidationDefinition](./bodyvalidationdefinition)  
**Required:** Yes  
**Description:** The validator to use.

```ts
import { Router } from '@steroids/core';

@Router({
  routes: [
    { path: '/example', validate: [
      { validator: () => {} }
    ]}
  ]
})
export class ExampleRouter {

}
```

> There are many built-in [validator functions](../../../validatorfunctions) and [factories](../../../validatorfunction-factories) available to use.

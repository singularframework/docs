# BodyValidationDefinition

Interface for defining a validation set on an object (request body only). The definition should be a mapping of properties to [ValidatorFunctions](../validatorfunction) or [AsyncValidatorFunctions](../asyncvalidatorfunction) with nested objects allowed.

```ts
import { ValidationType } from '@steroids/core';

// Dummy validators
function validator1(value) { return true; }
function validator2(value) { return true; }
function validator3(value) { return true; }
function validator4(value) { return true; }

// Validation rule
const rule = {
  type: ValidationType.Body,
  // Validation definition
  validator: {
    prop1: validator1,
    prop2: validator2,
    prop3: {
      'prop3-1': validator3,
      'prop3-2': validator3
    },
    prop4: validator4
  }
};
```

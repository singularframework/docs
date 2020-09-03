# SyncValidationDefinition

Interface for defining a validation set on a flat object (request headers and request query parameters). The definition should be a mapping of properties to [ValidatorFunctions](../../../router-decorator/routedefinition/validationrule/validatorfunction).

> This interface is only used with the [legacy validators](../).

```ts
import { SyncValidationDefinition } from '@singular/validators/legacy';

// Dummy validators
function validator1(value) { return true; }
function validator2(value) { return true; }
function validator3(value) { return true; }
function validator4(value) { return true; }

// Validation definition with synchronous validator functions
const validator: SyncValidationDefinition = {
  prop1: validator1,
  prop2: validator2,
  prop3: validator3,
  prop4: validator4
};
```

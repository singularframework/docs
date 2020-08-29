## resolveRef(ref, rawValues)

**Type:** Function  
**Arguments:**
  - ref  
    **Type:** string  
    **Required:** Yes  
    **Description:** A reference path to resolve from `rawValues` where child nodes are separated by `.` (e.g. `name.first`).
  - rawValues  
    **Type:** any  
    **Required:** Yes  
    **Description:** The `rawValues` argument from a [ValidatorFunction](../router-decorator/routedefinition/validationrule/validatorfunction).

**Returns:** any  
**Description:** Resolves a reference path from the `rawValues` argument provided to a [ValidatorFunction](../router-decorator/routedefinition/validationrule/validatorfunction) and returns its value (or `undefined` if path could not be resolved). This is useful for creating validator function factories that validate based on a reference (similar to [a](../validatorfunction-factories/#numgtrefref)).

```ts
import { resolveRef, ValidatorFunction } from '@steroids/core';

function sameAs(ref: string): ValidatorFunction {

  return (value: any, rawValues: any): boolean|Error => {

    return value === resolveRef(ref, rawValues);

  };

}
```

## sub(validationDefinition, localRefs)

**Type:** Function  
**Arguments:**
  - validationDefinition  
    **Type:** [ValidationDefinition](../router-decorator/routedefinition/validationrule/validationdefinition)  
    **Required:** Yes  
    **Description:** A validation definition object.
  - localRefs  
    **Type:** boolean  
    **Required:** No  
    **Default value:** false  
    **Description:** Determines whether references should be resolved from the target object or the original raw values object.

**Type check:** No  
**Casts:** No  
**Returns:** [ValidatorFunction](../router-decorator/routedefinition/validationrule/validatorfunction)  
**Description:** Validates the target (which should be an object) against the given validation definition. This is more practical and useful when provided as the `validator` parameter of the [type.Array(validator, arrayValidator)](#typearrayvalidator-arrayvalidator) validator factory.

```ts
import { Router, body, type, sub, equalRef } from '@steroids/core';

@Router({
  name: 'example',
  routes: [
    { path: '/', validate: [
      body({
        // Validating an array of objects
        children: type.Array(sub({
          firstName: type.String,
          lastName: type.String
        })),
        // Validating based on references
        lastName: type.String, // Parent's last name
        children: type.Array(sub({
          lastName: equalRef('lastName') // Referencing parent's last name
        })),
        // Validating based on local references
        children: type.Array(sub({
          parentsLastName: type.String,
          lastName: equalRef('parentsLastName') // Referencing to the local object's parentsLastName property
        }, true))
      })
    ]}
  ]
})
export class ExampleRouter { }
```

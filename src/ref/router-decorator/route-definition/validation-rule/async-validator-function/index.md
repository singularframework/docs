# AsyncValidatorFunction

Function signature for validating a single value (either part of [ValidationDefinition](../validationdefinition) or a straight [Request](../../../../middleware-parameters/request) object).

This signature defines two possible parameters:
  - **value**: A value to validate. Depending on the [ValidationType](../validationtype) value, the possible types of this parameter is:
    - ValidationType.**Header**: `string`
    - ValidationType.**Query**: `string`
    - ValidationType.**Body**: `any`
    - ValidationType.**Custom**: [Request](../../../../middleware-parameters/request)
  - **rawValues**: The superset the value is part of (if any). Depending on the [ValidationType](../validationtype) value, the possible values of this parameter is:
    - ValidationType.**Header**: [Request](../../../../middleware-parameters/request).headers
    - ValidationType.**Query**: [Request](../../../../middleware-parameters/request).query
    - ValidationType.**Body**: [Request](../../../../middleware-parameters/request).body
    - ValidationType.**Custom**: `undefined`

and two possible return types:
  - **Promise&lt;Boolean&gt;**: Indicates the validation result.
  - **Promise&lt;Error&gt;**: Indicates the validation has failed and provides a custom error message.

```ts
/** Checks if a user exists in the database by the given ID (value). */
async function registeredUser(value: any, rawValues: any): Promise<boolean>|Promise<Error> {

  // If value is not a valid ObjectId
  if ( ! mongoose.Types.ObjectId.isValid(value) ) return new Error('Invalid user ID!');

  // Using a Mongoose model
  const user = await UserModel.findById(value).exec();

  // If user is not registered
  if ( ! user ) return new Error('User not found!');

  return true;

}
```

# ValidationType

An enum for defining the validation target for a [ValidationRule](../) with the following values:
  - ValidationType.**Header**: Validation will be done on request headers. Validation rule's [validator](../#validator) property must be [ValidationDefinition](../validationdefinition) when using this type.
  - ValidationType.**Query**: Validation will be done on request query parameters. Validation rule's [validator](../#validator) property must be [ValidationDefinition](../validationdefinition) when using this type.
  - ValidationType.**Body**: Validation will be done on request body. Validation rule's [validator](../#validator) property must be [BodyValidationDefinition](../bodyvalidationdefinition) when using this type.
  - ValidationType.**Custom**: Validation will be done on the whole request by using the [Request](../../../../middleware-parameters/request) object. Validation rule's [validator](../#validator) property must be either [ValidatorFunction](../validatorfunction) or [AsyncValidatorFunction](../asyncvalidatorfunction) when using this type.

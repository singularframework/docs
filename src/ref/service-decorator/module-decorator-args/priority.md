## priority

**Type:** number  
**Required:** No  
**Description:** A priority number for this service to use when sorting services (higher number means higher priority). This affects the order at which services are initialized.

```ts
import { Service } from '@steroids/core';

@Service({
  priority: 100
})
export class ExampleService {

}
```

# Service

```ts
import { Service } from '@singular/core';
```

Decorates a class as a Service component. This decorator takes a [ModuleDecoratorArgs](../models/servicedecoratorargs) object as argument for component configuration.

```ts
import { Service } from '@singular/core';

@Service({
  name: 'test',
  // ...
})
export class TestService { }
```

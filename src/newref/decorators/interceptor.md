# Interceptor

```ts
import { Interceptor } from '@singular/core';
```

Decorates a class as an interceptor component. This decorator takes an [InterceptorDecoratorArgs](../models/interceptordecoratorargs) as argument for component configuration.

```ts
import { Interceptor } from '@singular/core';

@Interceptor({
  name: 'test',
  // ...
})
export class TestInterceptor { }
```

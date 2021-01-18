# Router

```ts
import { Router } from '@singular/core';
```

Decorates a class as a router component. This decorator takes a [RouterDecoratorArgs](../models/routerdecoratorargs) object as argument for component configuration.

```ts
import { Router } from '@singular/core';

@Router({
  name: 'test',
  // ...
})
export class TestRouter { }
```

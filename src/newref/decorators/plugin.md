# Plugin

```ts
import { Plugin } from '@singular/core';
```

Decorates a class as a plugin component. This decorator takes a [PluginDecoratorArgs](../models/plugindecoratorargs) object as argument for component configuration.

```ts
import { Plugin } from '@singular/core';

@Plugin({
  name: 'test',
  // ...
})
export class TestPlugin { }
```

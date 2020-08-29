## OnInit

**Type:** Interface  
**Enforces:** `onInit()` method  
**Description:** When implemented on a class, enforces the definition of `onInit()` method which runs when Steroids initializes a component.

```ts
import { Service, OnInit } from '@steroids/core';

@Service({
  name: 'example'
})
export class ExampleService implements OnInit {

  onInit() {

  }

}
```

> This hook can also be controlled by other components through related [server events](../servereventmanager/server-events).

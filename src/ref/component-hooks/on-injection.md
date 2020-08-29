## OnInjection

**Type:** Interface  
**Enforces:** `onInjection(services)` method  
**Description:** When implemented on a class, enforces the definition of `onInjection(services)` method which runs when Steroids injects services into components. The `services` argument is a key-value pair object with [service names](../service-decorator/moduledecoratorargs/#name) as keys and singleton references as values.

> Since the `services` argument is "localized" for each injection, changing the references on the argument will have no effect on future injections for other components.

```ts
import { Service, OnInjection } from '@steroids/core';
import { AnotherService } from '@steroids/service/another';

@Service({
  name: 'example'
})
export class ExampleService implements OnInjection {

  private another: AnotherService;

  onInjection(services) {

    // Store reference to "another" service
    this.another = services.another;

  }

}
```

This can also be done using destructing assignment to increase the readability:

```ts
import { Service, OnInjection } from '@steroids/core';
import { AnotherService } from '@steroids/service/another';
import { AnotherOneService } from '@steroids/service/another-one';

@Service({
  name: 'example'
})
export class ExampleService implements OnInjection {

  private another: AnotherService;
  private anotherOne: AnotherOneService;

  // Injected services are listed here, therefore increasing the readability
  onInjection({
    another,
    // For services with incompatible variable names
    'another-one': anotherOne
  }) {

    // Store reference to "another" service
    this.another = another;
    this.anotherOne = anotherOne;

  }

}
```

> This hook can also be controlled by other components through related [server events](../servereventmanager/server-events).

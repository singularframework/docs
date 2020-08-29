## OnConfig

**Type:** Interface  
**Enforces:** `onConfig(config)` method  
**Description:** When implemented on a class, enforces the definition of `onConfig(config)` method which runs when Steroids injects the [ServerConfig](../serverconfig) into components.

> Since the `config` argument is "localized" for each config injection, changing the values on the argument will have no effect on future config injections for other components.

```ts
import { Service, OnConfig, ServerConfig } from '@steroids/core';

@Service({
  name: 'example'
})
export class ExampleService implements OnConfig {

  private serverTimezone: string;

  onConfig(config: ServerConfig) {

    // Store server timezone (which defaults to system timezone)
    this.serverTimezone = config.timezone;

  }

}
```

> This hook can also be controlled by other components through related [server events](../servereventmanager/server-events).

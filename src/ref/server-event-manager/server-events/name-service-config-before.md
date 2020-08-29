## NAME-service:config:before

**Type:** Event  
**Arguments:**
  - config  
    **Type:** [ServerConfig](../../serverconfig)  
    **Description:** The server config object.

**Description:** Emits before server config is being injected into a specific service component, where `NAME` is the [name](../../service-decorator/moduledecoratorargs/#name) of that service. The `config` argument has been "localized" for the component that is having it injected. This means that changing this argument will only affect the [OnConfig](../../component-hooks/#onconfig) hook, and the [service:config:after](#serviceconfigafter), [NAME-service:config:before](#name-serviceconfigbefore), and [NAME-service:config:after](#name-serviceconfigafter) events for that specific component.

```ts
// Before config is being injected into ExampleService
events.on('example-service:config:before', config => {
  // Manipulate config before injection
});
```

```ts
import { Service, OnConfig, ServerConfig } from '@steroids/core';

@Service({
  name: 'example'
})
export class ExampleService implements OnConfig {

  onConfig(config: ServerConfig) {
    // config is manipulated for this specific service (ExampleService) due to the listener
  }

}
```

## NAME-router:config:before

**Type:** Event  
**Arguments:**
  - config  
    **Type:** [ServerConfig](../../serverconfig)  
    **Description:** The server config object.

**Description:** Emits before server config is being injected into a specific router component, where `NAME` is the [name](../../router-decorator/routerdecoratorargs/#name) of that router. The `config` argument has been "localized" for the component that is having it injected. This means that changing this argument will only affect the [OnConfig](../../component-hooks/#onconfig) hook, and the [router:config:after](#routerconfigafter), [NAME-router:config:before](#name-routerconfigbefore), and [NAME-router:config:after](#name-routerconfigafter) events for that specific component.

```ts
// Before config is being injected into ExampleRouter
events.on('example-router:config:before', config => {
  // Manipulate config before injection
});
```

```ts
import { Router, OnConfig, ServerConfig } from '@steroids/core';

@Router({
  name: 'example'
})
export class ExampleRouter implements OnConfig {

  onConfig(config: ServerConfig) {
    // config is manipulated for this specific router (ExampleRouter) due to the listener
  }

}
```

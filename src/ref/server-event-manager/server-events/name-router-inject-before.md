## NAME-router:inject:before

**Type:** Event  
**Arguments:**
  - services  
    **Type:** Object  
    **Description:** A key-value pair object with references to all services.

**Description:** Emits before services are being injected into a specific router component, where `NAME` is the [name](../../router-decorator/routerdecoratorargs/#name) of that router. The `services` argument has been "localized" for the component that is having them injected. This means that changing this argument will only affect the [OnInjection](../../component-hooks/#oninjection) hook, and the [router:inject:after](#routerinjectafter), [NAME-router:inject:before](#name-routerinjectbefore), and [NAME-router:inject:after](#name-routerinjectafter) events for that specific component.

```ts
// Before services are being injected into ExampleRouter
events.on('example-router:inject:before', services => {
  // Manipulate services before injection
});
```

```ts
import { Router, OnInjection } from '@steroids/core';

@Router({
  name: 'example'
})
export class ExampleRouter implements OnInjection {

  onInjection(services) {
    // services are manipulated for this specific router (ExampleRouter) due to the listener
  }

}
```

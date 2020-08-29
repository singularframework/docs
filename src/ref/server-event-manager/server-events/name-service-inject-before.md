## NAME-service:inject:before

**Type:** Event  
**Arguments:**
  - services  
    **Type:** Object  
    **Description:** A key-value pair object with references to all services.

**Description:** Emits before services are being injected into a specific service component, where `NAME` is the [name](../../service-decorator/moduledecoratorargs/#name) of that service. The `services` argument has been "localized" for the component that is having them injected. This means that changing this argument will only affect the [OnInjection](../../component-hooks/#oninjection) hook, and the [service:inject:after](#serviceinjectafter), [NAME-service:inject:before](#name-serviceinjectbefore), and [NAME-service:inject:after](#name-serviceinjectafter) events for that specific component.

```ts
// Before services are being injected into ExampleService
events.on('example-service:inject:before', services => {
  // Manipulate services before injection
});
```

```ts
import { Service, OnInjection } from '@steroids/core';

@Service({
  name: 'example'
})
export class ExampleService implements OnInjection {

  onInjection(services) {
    // services are manipulated for this specific service (ExampleService) due to the listener
  }

}
```

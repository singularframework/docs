## NAME-service:inject:after

**Type:** Event  
**Arguments:**
  - services  
    **Type:** Object  
    **Description:** A key-value pair object with references to all services.

**Description:** Emits after services have been injected into a specific service component, where `NAME` is the [name](../../service-decorator/moduledecoratorargs/#name) of that service.

```ts
events.on('example-service:inject:after', services => {
  // Do stuff...
});
```

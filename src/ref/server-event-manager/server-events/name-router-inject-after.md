## NAME-router:inject:after

**Type:** Event  
**Arguments:**
  - services  
    **Type:** Object  
    **Description:** A key-value pair object with references to all services.

**Description:** Emits after services have been injected into a specific router component, where `NAME` is the [name](../../router-decorator/routerdecoratorargs/#name) of that router.

```ts
events.on('example-router:inject:after', services => {
  // Do stuff...
});
```

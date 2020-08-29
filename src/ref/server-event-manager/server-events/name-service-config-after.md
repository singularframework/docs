## NAME-service:config:after

**Type:** Event  
**Arguments:**
  - config  
    **Type:** [ServerConfig](../../serverconfig)  
    **Description:** The server config object.

**Description:** Emits after server config has been injected into a specific service component, where `NAME` is the [name](../../service-decorator/moduledecoratorargs/#name) of that service.

```ts
events.on('example-service:config:after', config => {
  // Do stuff...
});
```

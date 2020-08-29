## NAME-router:config:after

**Type:** Event  
**Arguments:**
  - config  
    **Type:** [ServerConfig](../../serverconfig)  
    **Description:** The server config object.

**Description:** Emits after server config has been injected into a specific router component, where `NAME` is the [name](../../router-decorator/routerdecoratorargs/#name) of that router.

```ts
events.on('example-router:config:after', config => {
  // Do stuff...
});
```

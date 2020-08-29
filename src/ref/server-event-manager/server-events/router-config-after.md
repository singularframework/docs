## router:config:after

**Type:** Event  
**Arguments:**
  - config  
    **Type:** [ServerConfig](../../serverconfig)  
    **Description:** The server config object.

**Description:** Emits after server config has been injected into a router component.

```ts
events.on('router:config:after', config => {
  // Do stuff...
});
```

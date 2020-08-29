## service:config:after

**Type:** Event  
**Arguments:**
  - config  
    **Type:** [ServerConfig](../../serverconfig)  
    **Description:** The server config object.

**Description:** Emits after server config has been injected into a service component.

```ts
events.on('service:config:after', config => {
  // Do stuff...
});
```

## router:config:before

**Type:** Event  
**Arguments:**
  - config  
    **Type:** [ServerConfig](../../serverconfig)  
    **Description:** The server config object.

**Description:** Emits before server config is being injected into a router component. Since this event emits for all router components, changing the `config` argument will reflect to all router components.

```ts
events.on('router:config:before', config => {
  // Manipulate config before injection
});
```

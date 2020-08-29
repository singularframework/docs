## service:config:before

**Type:** Event  
**Arguments:**
  - config  
    **Type:** [ServerConfig](../../serverconfig)  
    **Description:** The server config object.

**Description:** Emits before server config is being injected into a service component. Since this event emits for all service components, changing the `config` argument will reflect to all service components.

```ts
events.on('service:config:before', config => {
  // Manipulate config before injection
});
```

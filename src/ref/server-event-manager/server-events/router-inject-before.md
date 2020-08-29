## router:inject:before

**Type:** Event  
**Arguments:**
  - services  
    **Type:** Object  
    **Description:** A key-value pair object with references to all services.

**Description:** Emits before services are being injected into a router component. Since this event emits for all router components, changing the `services` argument will reflect to all router components.

```ts
events.on('router:inject:before', services => {
  // Manipulate services before injection
});
```

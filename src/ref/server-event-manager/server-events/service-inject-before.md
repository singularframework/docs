## service:inject:before

**Type:** Event  
**Arguments:**
  - services  
    **Type:** Object  
    **Description:** A key-value pair object with references to all services.

**Description:** Emits before services are being injected into a service component. Since this event emits for all service components, changing the `services` argument will reflect to all service components.

```ts
events.on('service:inject:before', services => {
  // Manipulate services before injection
});
```

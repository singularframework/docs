## service:inject:after

**Type:** Event  
**Arguments:**
  - services  
    **Type:** Object  
    **Description:** A key-value pair object with references to all services.

**Description:** Emits after services have been injected into a service component.

```ts
events.on('service:inject:after', services => {
  // Do stuff...
});
```

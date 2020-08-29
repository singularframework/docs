## router:inject:after

**Type:** Event  
**Arguments:**
  - services  
    **Type:** Object  
    **Description:** A key-value pair object with references to all services.

**Description:** Emits after services have been injected into a router component.

```ts
events.on('router:inject:after', services => {
  // Do stuff...
});
```

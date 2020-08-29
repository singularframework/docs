## launch

**Type:** Event  
**Arguments:**
  - port  
    **Type:** number  
    **Description:** The port number the server was launched on.

**Description:** Emits when the server launches.

```ts
events.on('launch', port => {
  // Do stuff...
});
```

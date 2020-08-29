## NAME-service:init:after

**Type:** Event  
**Description:** Emits after a specific service component initializes, where `NAME` is the [name](../../service-decorator/moduledecoratorargs/#name) of that service.

```ts
events.on('example-service:init:after', () => {
  // Do stuff...
});
```

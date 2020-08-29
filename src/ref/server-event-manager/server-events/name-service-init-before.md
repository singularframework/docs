## NAME-service:init:before

**Type:** Event  
**Description:** Emits before a specific service component initializes, where `NAME` is the [name](../../service-decorator/moduledecoratorargs/#name) of that service.

```ts
events.on('example-service:init:before', () => {
  // Do stuff...
});
```

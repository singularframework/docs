## once

**Type:** boolean  
**Description:** Indicates if the event listener was attached using either [once(event, listener)](../#onceevent-listener) or [prependOnceListener(event, listener)](../#prependoncelistenerevent-listener).

```ts
events.on('some-event', () => {});
events.once('some-event', () => {});

events.getRawListeners('some-event')[0].once; // -> false
events.getRawListeners('some-event')[1].once; // -> true
```

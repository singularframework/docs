## eventNames()

**Type:** Function  
**Returns:** Array&lt;string&gt;  
**Description:** Returns a list of event names.

```ts
events.on('event1', () => {});
events.emit('event2');

events.eventNames(); // -> ['event1', 'event2']
```

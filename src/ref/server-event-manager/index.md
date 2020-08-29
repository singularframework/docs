# ServerEventManager

A class for event-driven programming, available [globally](../globals/#events) as `events`. This class has an interface similar to the built-in Node JS `events` package with a few expansions. The following methods are available on the `events` global:
  - [on(event, listener)](#onevent-listener)
  - [once(event, listener)](#onceevent-listener)
  - [off(event, listener)](#offevent-listener)
  - [emit(event, ...args)](#emitevent-args)
  - [emitOnce(event, ...args)](#emitonceevent-args)
  - [eventNames()](#eventnames)
  - [addListener(event, listener)](#addlistenerevent-listener)
  - [addOnceListener(event, listener)](#addoncelistenerevent-listener)
  - [removeListener(event, listener)](#removelistenerevent-listener)
  - [removeAllListeners(event)](#removealllistenersevent)
  - [listenersCount(event)](#listenerscountevent)
  - [prependListener(event, listener)](#prependlistenerevent-listener)
  - [prependOnceListener(event, listener)](#prependoncelistenerevent-listener)
  - [getListeners(event)](#getlistenersevent)
  - [getRawListeners(event)](#getrawlistenersevent)

> Steroids uses this class to emit [server events](./server-events) at different stages of the server's lifetime.

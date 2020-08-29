# ServerSessionManager

A class for session management and integration through cookies, available [globally](../globals#session) as `session`. The following methods are available on the `session` global:
  - [on(event, handler)](#onevent-handler)
  - [setClaim(id, key, value)](#setclaimid-key-value)
  - [getClaim(id, key)](#getclaimid-key)

This class also emits [session events](./session-events) which need to have handlers attached in order to work properly.

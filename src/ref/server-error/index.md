# ServerError

A class for creating errors, tailored for responding to server requests. This class provides the following constructor:
  - [constructor(message, httpCode, code)](#constructormessage-httpcode-code)

the following static methods:
  - [ServerError.from(error, httpCode, code)](#servererrorfromerror-httpcode-code)

the following instance methods:
  - [respond(res)](#respondres)

and the following members:
  - [error](#error)
  - [message](#message)
  - [httpCode](#httpcode)
  - [code](#code)
  - [stack](#stack)

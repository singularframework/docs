# Express on Steroids!

Steroids helps building backend solutions with Node.js, Express, and TypeScript by introducing new components that are easy and fast to develop.

Here's a quick list of features Steroids provides:

  - TypeScript enabled
  - Powered by Express
  - Automatic code minification
  - Logic is encapsulated into "Services" and router middlewares are grouped as "Routers"
  - Routes are easily defined using the Router decorator
  - Built-in input validation mechanism with routers (request body, headers, query parameters, etc.)
  - Ability to extend the validation logic with custom validators
  - Dynamic route and service installation
  - Dynamic service injection without circular dependency issues
  - Path alias support for easier imports
  - Customizable built-in logger with file manager and auto archiver
  - Unit testing with Mocha and Chai
  - TypeDoc ready

You can use this repository/template directly or through the [Steroids CLI](https://github.com/chisel/steroids) for even faster development (recommended). [Steroids CLI](https://github.com/chisel/steroids) allows creating new backend projects using Steroids template (with custom configuration) and also to add components (such as routers, services, etc.) with template code.

# Index

- [Installation](#installation)
- [NPM Scripts](#npm-scripts)
- [Launching the Server](#launching-the-server)
- [Development](#development)
  - [Services](#services)
  - [Routers](#routers)
    - [Defining Routes](#defining-routes)
    - [Input Validation](#input-validation)
      - [Header Validation Example](#header-validation-example)
      - [Query Parameter Validation Example](#query-parameter-validation-example)
      - [Body Validation Example](#body-validation-example)
      - [Body Validation: Enums](#body-validation-enums)
      - [Body Validation: Arrays Of Objects](#body-validation-array-of-objects)
      - [Body Validation API](#body-validation-api)
      - [Custom Body Validation](#custom-body-validation)
      - [Custom Validation](#custom-validation)
      - [Custom Async Validation](#custom-async-validation)
      - [Custom Error Messages](#custom-error-messages)
    - [CORS Policy](#cors-policy)
      - [CORS Policy Example](#cors-policy-example)
      - [Modular CORS Policy Example](#modular-cors-policy-example)
    - [Serving Static Files](#serving-static-files)
  - [Module Hooks](#module-hooks)
    - [Injection Hook](#injection-hook)
    - [Config Hook](#config-hook)
    - [Init Hook](#init-hook)
  - [Events Manager](#events-manager)
    - [Server Events](#server-events)
  - [Server Logger](#server-logger)
    - [Saving Logs on Disk](#saving-logs-on-disk)
      - [Logs Max Age Control](#logs-max-age-control)
    - [Log Levels](#log-levels)
    - [Built-in Logging](#built-in-logging)
      - [Sensitive Logs](#sensitive-logs)
  - [Server Config](#server-config)
    - [Config Injection](#config-injection)
    - [Config Expansion](#config-expansion)
  - [Server Assets](#server-assets)
    - [Assets Example](#assets-example)
  - [Server Error](#server-error)
  - [Testing](#testing)
- [Notes](#notes)

# Installation

  1. Clone this repo
  2. `npm install`
  3. That's it!

# NPM Scripts

  - `npm start`: Builds and runs the server.
  - `npm test`: Builds and runs the tests.
  - `npm run build`: Build the server into `dist`.
  - `npm run launch`: Runs the last build.
  - `npm run docs`: Builds the internal documentation.

# Launching the Server

If launching from the project root, run any of the following:
  - `npm run launch`
  - `npm run start` (builds first)
  - `sd run` (using [Steroids CLI](https://github.com/chisel/steroids))
  - `node dist/@steroids/main`

If running from the dist directory, run `node @steroids/main`

> **NOTE:** If running the server from any other directory where CWD is not dist or project root, path aliases (TypeScript paths defined in tsconfig.json) will fail to resolve.

# Development

Steroids introduces two new components to work with: Services and Routers.

## Services

A service is basically a singleton class which is shared and accessible throughout the whole app (really similar to Angular singleton/global services).

To build a service, simply create a file with the extension `.service.ts` anywhere inside the `src` directory and decorate it using the `@Service` decorator as shown below:

```ts
// all imports are from ''@steroids/core'
import { Service } from '@steroids/core';

@Service({
  name: 'foo'
})
export class FooService {

  log() {
    console.log('Foo service!');
  }

}
```

This file will be automatically picked up by the server, so there's no need for any installation. You can then inject these services into your routers and also into other services, as shown below:

```ts
import { Service, OnInjection } from '@steroids/core';
import { FooService } from '@steroids/service/foo'; // For typings

@Service({
  name: 'bar'
})
export class BarService implements OnInjection {

  private foo: FooService;

  // Inject the service
  onInjection(services: any) {
    this.foo = services.foo;
    this.foo.log(); // Logs: Foo service!
  }

}
```

## Routers

Similar to services, you can build a router by creating a file with the extension `.router.ts` stored anywhere inside the `src` directory. The `@Router` decorator is then used to decorate the class as a router while providing route definitions and other metadata.

```ts
import { Router, OnInjection } from '@steroids/core';
import { BarService } from '@steroids/service/bar';

@Router({
  name: 'router1'
})
export class Router1 implements OnInjection {

  private bar: BarService;

  onInjection(services: any) {
    this.bar = services.bar;
  }

}
```

### Defining Routes

The `@Router` decorator accepts the following properties:

| Key | Type | Description |
|:----|:----:|:------------|
| name | string | The name of the router (only used for logging). |
| priority | number | Routers are sorted by priority before mounting their middleware in the Express stack (defaults to `0`). |
| routes | RouteDefinition[] | An array of route definitions. |
| corsPolicy | cors.CorsOptions | No | [CORS policy](#cors-policy) for all routes in router (unless overridden). |

The `RouteDefinition` interface is as follows:

| Key | Type | Required | Description |
|:----|:----:|:--------:|:------------|
| path | string | Yes | The path of the route (identical to app.use(**path**)). |
| handler | string | Yes | The name of the route handler function (must exist in the router class). |
| method | RouteMethod | No | The HTTP method of the route. If not provided, the route will cover all methods (global). |
| validate | ValidationRule[] | No | Used to easily install validators for validating input (body, header, etc.) |
| corsPolicy | cors.CorsOptions | No | [CORS policy](#cors-policy) for the route (overrides router CORS policy). |

The following is an example of a simple router which defines the route `GET /test` linked to the `Router1.routeHandler1` route handler:

```ts
import { Router, RouteMethod } from '@steroids/core';
import { Request, Response, NextFunction } from 'express';

@Router({
  name: 'router1',
  routes: [
    { path: '/test', method: RouteMethod.GET, handler: 'routeHandler1' }
  ]
})
export class Router1 {

  routeHandler1(req: Request, res: Response) {
    res.status(200).send('OK');
  }

}
```

### Input Validation

There are four types of validation in routers: Headers, Query Parameters, Body (only JSON and urlencoded), and custom validation:

  1. `header({ name: value, ... })`: With header validation you can check if headers are present and set with the required value.
  2. `query(['paramName', ...])`: The query parameters validator can only check the presence of the query input.
  3. `body({ key: ValidatorFunction })`: Body validators can create complex validation with ease by combining different logic on each key validation.
  4. `custom(ValidatorFunction)`: If none of the above fit your needs, you can always take control!

> Note: You can stack multiple validators of the same kind inside the `validate` array.

When validation is used, the requests that won't pass the validation will automatically get rejected with a validation error.

#### Header Validation Example

```ts
import { Router, RouteMethod, header } from '@steroids/core';

@Router({
  name: 'router1',
  priority: 100,
  routes: [
    { path: '/postdata', handler: 'postHandler', method: RouteMethod.POST, validate: [
      header({ 'content-type': 'application/json' })
    ]}
  ]
})
export class Router1 {

  postHandler(req, res) {

    // req.body is ensured to be valid JSON

  }

}
```

#### Query Parameter Validation Example

```ts
import { Router, query } from '@steroids/core';

@Router({
  name: 'router1',
  priority: 100,
  routes: [
    { path: '*', handler: 'authHandler', validate: [
      query(['token'])
    ]}
  ]
})
export class Router1 {

  authHandler(req, res) {

    // req.query.token is definitely provided

  }

}
```

#### Body Validation Example

Now let's get crazy! Let's write a validator which requires the following JSON body:

| Key | Requirement |
|:----|:------------|
| title | Must be present and a valid string. |
| authors | Must be present and a valid array of strings with at least one entry. |
| co-authors | Optional, but if present, it has the same requirement as `authors` but all entries must be prefixed with `co-`! |
| release | A namespace. |
| release.year | Must be a valid number between `2000` and `2019`. |
| release.sells | Must be a valid number. |
| price | Cannot be a boolean. |

```ts
import {
  Router,
  RouteMethod,
  body,
  type,
  len,
  opt,
  and,
  match,
  not
} from '@steroids/core';

@Router({
  name: 'router1',
  priority: 100,
  routes: [
    { path: '/book/new', handler: 'newBook', method: RouteMethod.POST, validate: [
      body({
        title: type.string,
        authors: type.array(type.string, len.min(1)),
        'co-authors': opt(type.array(and(type.string, match(/^co-.+$/))), len.min(1)),
        release: {
          year: and(type.number, range(2000, 2019)),
          sells: type.number
        },
        price: not(type.boolean)
      })
    ]}
  ]
})
export class Router1 {

  newBook(req, res) {

    // req.body has passed the validation test

  }

}
```

#### Body Validation: Enums

Properties of the body object can be checked against any enums (including string enums) using the `type.ofenum` validator:

```ts
import {
  Router,
  RouteMethod,
  body,
  type
} from '@steroids/core';

enum Category {
  Category1,
  Category2
}

@Router({
  name: 'router1',
  priority: 100,
  routes: [
    { path: '/test', handler: 'testHandler', method: RouteMethod.POST, validate: [
      body({
        category: type.ofenum(Category)
      })
    ]}
  ]
})
export class Router1 {

  testHandler(req, res) {

    // req.body has passed the validation test

  }

}
```

#### Body Validation: Arrays Of Objects

An array of objects can be validated using the `sub` validator. It takes a body validator object (the same object the `body` function takes except there can be no nested objects) and validates all the items inside the array against it:

```ts
import {
  Router,
  RouteMethod,
  body,
  type,
  sub,
  len
} from '@steroids/core';

@Router({
  name: 'router1',
  priority: 100,
  routes: [
    { path: '/test', handler: 'testHandler', method: RouteMethod.POST, validate: [
      body({
        authors: type.array(sub({
          firstName: type.string,
          lastName: type.string
        }), len.min(1))
      })
    ]}
  ]
})
export class Router1 {

  testHandler(req, res) {

    // req.body has passed the validation test

  }

}
```

#### Body Validation API

Here's an in-depth documentation on all the built-in body validator functions:

| Validator | Signature | Description |
|:----------|:----------|:------------|
| type.string | NA | Checks if the value is a valid string. |
| type.number | NA | Checks if the value is a valid number. |
| type.boolean | NA | Checks if the value is a valid boolean. |
| type.nil | NA | Checks if the value is null. |
| type.array | type.array(_[validator, arrayValidator]_) | Checks if the value is a valid array. If the validator is provided, it also validates each item of the array against it, if the arrayValidator is provided, the array itself is validated against it (useful for enforcing length restrictions on the array). |
| type.ofenum | type.ofenum(enumerator) | Checks if the value is included in the given enumerator.|
| equal | equal(val) | Checks if the body value is equal to the given value. |
| or | or(...validators) | ORs all given validators. |
| and | and(...validators) | ANDs all given validators. |
| not | not(validator) | Negates the given validator. |
| opt | opt(validator) | Applies the given validator only if the value is present (makes the value optional). |
| match | match(regex) | Validates the value against the given regular expression (without string type check). |
| num.min | num.min(val) | Checks if the value is greater than or equal to the given number. |
| num.max | num.max(val) | Checks if the value is less than or equal to the given number. |
| num.range | num.range(min, max) | Checks if the value is between the given range (inclusive). |
| len.min | len.min(val) | Checks if the length of the value is greater than or equal to the given number. |
| len.max | len.max(val) | Checks if the length of the value is less than or equal to the given number. |
| len.range | len.range(min, max) | Checks if the length of the value is between the given range (inclusive). |
| sub | sub(bodyValidator) | Validates an object against the given flat body validator (useful for validating arrays of objects). |

#### Custom Body Validation

If you need to perform a more complex body validation, you can always create a validator function or factory that takes arguments and returns a validator function. Below is an example of a custom body validator which validates the property `oddOnly` on the body using a validator function and `evenOnly` using a validator factory:

```ts
import {
  Router,
  RouteMethod,
  body,
  type,
  ValidatorFunction
} from '@steroids/core';

@Router({
  name: 'router1',
  priority: 100,
  routes: [
    { path: '/test', handler: 'testHandler', method: RouteMethod.POST, validate: [
      body({
        oddOnly: odd,
        evenOnly: parity(false)
      })
    ]}
  ]
})
export class Router1 {

  testHandler(req, res) {

    // req.body has passed the validation test

  }

}

function odd(value: any): boolean {

  // Reusing type.number validator function
  return type.number(value) && (value % 2 === 1);

}

function parity(odd: boolean): ValidatorFunction {

  return (value: any): boolean => {

    return type.number(value) && (value % 2 === (odd ? 1 : 0));

  };

}
```

> **NOTE:** [Read about custom error messages.](#custom-error-messages)

#### Custom Validation

If you need to do something more complex or unique and still want to benefit from reusability and the auto-respond feature of the validators, you can create a function with this signature `(req: Request) => boolean|Error` and pass it to the `custom` method:

```ts
import { Router, RouteMethod, custom } from '@steroids/core';
import { Request } from 'express';

@Router({
  name: 'auth',
  priority: 100,
  routes: [
    { path: '*', handler: 'authHandler', validate: [
      custom(basicAuthValidator)
    ]}
  ]
})
export class Router1 {

  authHandler(req, res, next) {

    // Do basic auth
    next();

  }

}

// Making sure basic authentication credentials are provided
function basicAuthValidator(req: Request): boolean {

  const authorization = req.header('Authorization');

  return authorization && authorization.substr(0, 5) === 'Basic';

}
```

> **NOTE:** [Read about custom error messages.](#custom-error-messages)

#### Custom Async Validation

Custom validators, **excluding custom body validators**, can return a promise instead if asynchronous execution is needed.

```ts
import { Router, RouteMethod, custom } from '@steroids/core';
import { Request } from 'express';

@Router({
  name: 'auth',
  priority: 100,
  routes: [
    { path: '*', handler: 'authHandler', validate: [
      custom(userExistsPromise),
      custom(userExistsAsync)
    ]}
  ]
})
export class Router1 {

  authHandler(req, res, next) {

    // req.user now exists from now on
    next();

  }

}

function userExistsPromise(req: Request): Promise<boolean> {

  return new Promise((resolve, reject) => {

    this.db.getUser(req.query.token)
    .then(user => {

      req.user = user;
      resolve(true); // Must resolve with true

    })
    .catch(reject);

  });

}

async function userExistsAsync(req: Request) {

  req.user = await this.db.getUser(req.query.token);

  return true;

}
```

> **NOTE:** [Read about custom error messages.](#custom-error-messages)

#### Custom Error Messages

All custom validators and custom body validators can return an error object instead to customize the error message.

```ts
function customValidator(req: Request) {

  // Invalid query
  if ( ! req.query.token ) return new Error('You must provide your auth token with all requests!');

  return true;

}
```

### CORS Policy

CORS can be setup for each router using `corsPolicy` router options in `Router` decorator. This will apply the policy on all routes defined in the router.

Individual routes can also define their own policy to override the router's (if any) using the `corsPolicy` route option.

CORS configuration is identical to the [**cors** npm package options](https://www.npmjs.com/package/cors#configuration-options) **excluding the `preflightContinue` option**.

#### CORS Policy Example

```ts
import { Router, RouteMethod } from '@steroids/core';

@Router({
  'example',
  corsPolicy: {
    origin: [
      'http://example.com',
      'https://example.com'
    ]
  },
  routes: [
    // Router CORS policy will be applied to the following route
    { path: '/with-cors', method: RouteMethod.GET, handler: 'withCors' },
    // Router CORS policy is overridden on the following route
    { path: '/without-cors', method: RouteMethod.GET, handler: 'withoutCors', corsPolicy: { origin: true } }
  ]
})
export class ExampleRouter {  }
```

#### Modular CORS Policy Example

When the same policy needs to be applied to multiple routers, it's a good idea to save the policy in a JSON file and use it everywhere:

**cors-policy.json**
```json
{
  "origin": [
    "http://example.com",
    "https://example.com"
  ],
  "methods": "GET,POST"
}
```

**example.router.ts**
```ts
import { Router, RouteMethod } from '@steroids/core';
import corsPolicy from '../cors-policy.json';

@Router({
  'example',
  corsPolicy,
  routes: [
    { path: '/with-cors', method: RouteMethod.GET, handler: 'withCors' }
  ]
})
export class ExampleRouter {  }
```

### Serving Static Files

Static files can be served in routers using the following trick:

```ts
import { Router } from '@steroids/core';
import express from 'express';
import path from 'path';

@Router({
  name: 'public',
  routes: [
    { path: '/public', handler: 'serveStatic' }
  ]
})
export class StaticRouter {

  public get serveStatic() {

    // Serve all files from '../public'
    return express.static(path.resolve(__dirname, '..', 'public'));

  }

}
```

## Module Hooks

All modules (routers and services) can run code at different stages of the server launch using the following hooks.

All hooks can be run asynchronously either by returning a Promise or using the async/await syntax. Please keep in mind that if hooks are used asynchronously, they must be resolved before next hooks can be run on other modules.

### Injection Hook

The first hook that runs on modules is `onInjection` which provides an object containing all defined services. This hook can be used to store a reference of certain services needed for use inside a module (aka injection):

```ts
import { Service, OnInjection } from '@steroids/core';
// For typings
import { MyOtherService } from '@steroids/service/my-other';

@Service({
  name: 'my'
})
export class MyService implements OnInjection {

  private myOtherService: MyOtherService;

  onInjection(services: any) {

    this.myOtherService = services['my-other'];

  }

}
```

### Config Hook

The second hook that runs on modules is `onConfig` which provides the server configuration file:

```ts
import { Service, OnConfig, ServerConfig } from '@steroids/core';

@Service({
  name: 'my'
})
export class MyService implements OnConfig {

  onConfig(config: ServerConfig) {
    // Inject or use...
  }

}
```

### Init Hook

The final hook that runs is `onInit` which gives all modules a chance to initialize:

```ts
import { Service, OnInit } from '@steroids/core';

@Service({
  name: 'my'
})
export class MyService implements OnInit {

  onInit() {
    // Initialize service
  }

}
```

> **NOTE:** If initialization of a certain module depends on another when using async hooks, use the appropriate (server event)[#server-events] and resolve the promise immediately to avoid hanging the server launch (e.g. `my-service:init:after`). A "ready" signal system can also be implemented for all modules by using the global [events manager](#events-manager).

## Events Manager

The built-in events manager is globally available as `events` with the following methods:

```ts
// Runs every time event is emitted
events.on('my-event', (...args) => console.log(`Event "my-event" emitted with arguments: ${args.join(', ')}`));
// Runs only once the next time event in emitted
events.once('my-event', (...args) => console.log(`Event "my-event" emitted with arguments: ${args.join(', ')}`));
// Removes an event listener
events.off('my-event', listener);
// Emits an event
events.emit('my-event', 1, 2, 3);
// Emits an event once, all listeners in the future will be called and
// receive the same arguments provided here immediately after being added
// and this event cannot be emitted anymore in the future
events.emitOnce('my-event', 1, 2, 3);
// Returns a list of event names
events.eventNames();
// Alias for events.on
events.addListener('my-event', (...args) => console.log(`Event "my-event" emitted with arguments: ${args.join(', ')}`));
// Alias for events.once
events.addOnceListener('my-event', (...args) => console.log(`Event "my-event" emitted with arguments: ${args.join(', ')}`));
// Alias for events.off
events.removeListener('my-event', listener);
// Removes all listeners for an event
events.removeAllListeners('my-event');
// Returns listeners count for an event
events.listenersCount('my-event');
// Prepends an event listener
events.prependListener('my-event', (...args) => console.log(`Event "my-event" emitted with arguments: ${args.join(', ')}`));
// Prepends a once listener
events.prependOnceListener('my-event', (...args) => console.log(`Event "my-event" emitted with arguments: ${args.join(', ')}`));
// Returns a list of listener functions (this array cannot be used to modify the listeners)
events.getListeners('my-event');
// Returns the raw listeners array (this array cannot be used to modify the listeners)
events.getRawListeners('my-event');
```

### Server Events

The following events will be emitted by Steroids at various stages:

| Event | Name | Description |
|:------|:-----|:------------|
| Before service injection | `NAME-service:inject:before` | Emits before services get injected into a service (`NAME` will be the service name). |
| After service injection | `NAME-service:inject:after` | Emits after services got injected into a service (`NAME` will be the service name). |
| Before router injection | `NAME-router:inject:before` | Emits before services get injected into a router (`NAME` will be the router name). |
| After router injection | `NAME-router:inject:after` | Emits after services got injected into a router (`NAME` will be the router name). |
| Before service config injection | `NAME-service:config:before` | Emits before config gets injected into a service (`NAME` will be the service name). |
| After service config injection | `NAME-service:config:after` | Emits after config got injected into a service (`NAME` will be the service name). |
| Before router config injection | `NAME-router:config:before` | Emits before config gets injected into a router (`NAME` will be the router name). |
| After router config injection | `NAME-router:config:after` | Emits after config got injected into a router (`NAME` will be the router name). |
| Before service initialization | `NAME-service:init:before` | Emits before a service gets initialized (`NAME` will be the service name). |
| After service initialization | `NAME-service:init:after` | Emits after a service got initialized (`NAME` will be the service name). |
| Before router initialization | `NAME-router:init:before` | Emits before a service gets initialized (`NAME` will be the router name). |
| After router initialization | `NAME-router:init:after` | Emits after a service got initialized (`NAME` will be the router name). |
| Server launched | `launch` | Emits after the server gets launched successfully. |

## Server Logger

The built-in logger is available globally as `log` with the following methods:

```ts
log.debug('Log at debug level', 'Additional message 1', 'Additional message 2');
log.info('Log at info level');
log.notice('Log important message at notice level');
log.warn('Log warning message at warn level');
log.error('Log this error at error level', new Error('Some error!'));
```

Using the built-in logger instead of plain console logs has the following benefits:
  - Formatted logs with date time strings (local to the server timezone set in the config)
  - Writing logs on disk at `dist/.logs/`, organized by date (each file contains logs for one day)
  - Disk management for deleting/archiving log files by setting a max age in the server config
  - Automatically archiving log files (when passed their max age) by moving them to `dist/.logs/archived/` and compressing them for smaller disk space usage
  - Five different log levels
  - Both the console and log files can be customized to contain different log levels
  - Internal queue system to guarantee logging order on disk without blocking the event loop
  - Identical API to console.log

### Saving Logs on Disk

The built-in logger saves logs on disk by default (only if the `log` API is used). In order to disable this behavior, set `writeLogsToFile` to `false` in the [server config](#server-config).

All logs are separated into various files organized based on their date. Each file has the date as its filename (`dd-mm-yyyy.log`) and lives at `dist/.logs/` directory.

#### Logs Max Age Control

The default max age of log files is 7 days. This means that any file that is 7 days older than the current date (based on server timezone) will be archived.

Archived log files are compressed and moved to `dist/.logs/archived/` directory. If archiving is disabled (by setting `archiveLogs` to `false` in the [server config](#server-config)) then logs will be deleted instead.

However, if max age is set to 0 (by changing `logFileMaxAge` in [server config](#server-config)) log files won't be archived nor deleted.

### Log Levels

Both the console and disk can be customized to include any levels of logs. By default, the console displays all levels except for `debug` and all log levels are saved on disk. To customize those behaviors, change `consoleLogLevels` and `logFileLevels` in the [server config](#server-config).

### Built-in Logging

The server logs in three situations:
  1. When starting the server (`debug` level)
  2. When an uncaught error is thrown (`error` level)
  3. When a request is made to the server (`debug` level)

By default, request headers are not included in the logs. This can be changed by setting `logRequestHeaders` in the [server config](#server-config).

#### Sensitive Logs

When logging request headers is enabled, the `authorization` header value (if present) will be replaced with `HIDDEN` in logs to avoid logging sensitive information. This behavior can also be applied to other headers and query parameters (e.g. when using `token` query parameter) by setting `hideHeadersInLogs` and `hideQueryParamsInLogs` in the [server config](#server-config).

## Server Config

The server has a configuration file located at `src/config.json` with the following settings:

| Key | Type | Description |
|:----|:----:|:------------|
| port | number | The port number to launch the server on (defaults to `5000`). |
| timezone | string | The timezone of the server (defaults to local system timezone). |
| colorfulLogs | boolean | If true, console logs will have color (defaults to `true`). |
| consoleLogLevels | all&vert;Array<debug&vert;info&vert;notice&vert;warn&vert;error> | An array of log levels to show in the console or `all` (no array) to show all levels (defaults to `['info', 'notice', 'warn', 'error']`). |
| writeLogsToFile | boolean | Will write all server logs on disk (defaults to `true`). |
| logFileMaxAge | number | The maximum age of a logs file in days. When passed, the file will either get archived or deleted (defaults to `7`). |
| logFileLevels | all&vert;Array<debug&vert;info&vert;notice&vert;warn&vert;error> | An array of log levels to write on disk or `all` (no array) to write all levels (defaults to `'all'`). |
| archiveLogs | boolean | Will archive logs written on disk that are older than their max age (defaults to `true`). |
| logRequestHeaders | boolean | If `true` will log request headers (defaults to `false`). |
| hideHeadersInLogs | Array&lt;string&gt; | A list of header names to hide in logs when logging request headers. |
| hideQueryParamsInLogs | Array&lt;string&gt; | A list of query parameter names to hide in logs. |
| predictive404 | boolean | If true, installs a 404 handler at the top of the stack instead (this can be configured through `predictive404Priority`), which predicts if path will match with any middleware in the stack and rejects the request with a 404 error if not. This is useful as requests that will eventually result in a 404 error won't go through the stack in the first place. Please note that the prediction ignores all `*` and `/` routes (defaults to `false`). |
| predictive404Priority | number | The priority of the predictive 404 middleware (defaults to `Infinity`). |
| fileUploadLimit | string | The file upload limit with suffix (e.g. `kb`, `mb`, `gb`) (defaults to `10mb`). |

### Config Injection

If you need to get access to the config object inside your services or routers, use the [Config Hook](#config-hook).

### Config Expansion

You can expand the config object typing by editing the `ServerConfig` model inside `src/config.model.ts`. This would provide typings for your customized server config to all routers and services accessing the config object through `OnConfig` interface.

## Server Assets

Assets can be declared inside `package.json` using the `assets` array. Any files or directories declared inside the array will be copied to the `dist` folder after the server build. Keep in mind that all paths should be relative to the `src` directory.

### Assets Example

```json
{
  "name": "steroids-template",
  ...
  "assets": [
    "firebase.certificate.json",
    "public"
  ]
}
```

## Server Error

The `ServerError` class is available for responding to users with errors through the REST API and is used by the server internally when rejecting requests (e.g. validation errors, internal errors, 404 errors, etc.). Use the following example as how to interact with the `ServerError` class:

```ts
import { ServerError } from '@steroids/core';

const error = new ServerError('Message', 400, 'ERROR_CODE'); // http code defaults to 500 and error code defaults to 'UNKNOWN_ERROR' when not provided
const errorWithStack = ServerError.from(new Error('Message'), 400, 'ERROR_CODE');

// error.respond(res); --> { error: true, message: 'Message', code: 'ERROR_CODE' }
// errorWithStack.respond(res); --> { error: true, message: 'Message', code: 'ERROR_CODE', stack: '...' }
```

## Testing

Unit testing has been setup using Mocha and Chai. The test files are written in TypeScript inside `test/src` directory and are transpiled to JavaScript in `test/dist` using `test/tsconfig.json` before being run.

When the main test suite `test/dist/main.spec.js` runs, the following happens:
  1. The latest server build (located at `/dist`) is reconfigured to run at port 8000 without file logging (to avoid polluting the log files) and is launched.
  2. The `test/dist/` directory is scanned recursively and all test suites are run.
  3. After all tests finish, the server is killed and reconfigured back to original.

You should write your tests suites inside `test/src/` at any depth and run `npm test` to start the tests.

# Notes

  - The directory structure of the server is totally up to you, since the server scans the build directory for `.service.js` and `.router.js` files to install at any depth. Though, path aliases are setup for the default directory structure where services are kept at `src/services` and routers at `src/routers`. You can change aliases by editing `compilerOptions.paths` in `tsconfig.json` if desired or use the [Steroids CLI](https://github.com/chisel/steroids) to manage path aliases.
  - You can make your validators modular by storing the validator functions and the validator body definitions inside other files and reuse them everywhere.

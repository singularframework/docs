# ServerConfig

Interface of the server configuration object. This object is the combination of [BaseServerConfig](./baseserverconfig) and the `/src/config.ts` file.

It can be accessed programmatically through [OnConfig](../component-hooks/#onconfig) component hook and the following events:
  - [service:config:before](../servereventmanager/server-events/#serviceconfigbefore)
  - [service:config:after](../servereventmanager/server-events/#serviceconfigafter)
  - [router:config:before](../servereventmanager/server-events/#routerconfigbefore)
  - [router:config:after](../servereventmanager/server-events/#routerconfigafter)
  - [NAME-service:config:before](../servereventmanager/server-events/#name-serviceconfigbefore)
  - [NAME-service:config:after](../servereventmanager/server-events/#name-serviceconfigafter)
  - [NAME-router:config:before](../servereventmanager/server-events/#name-routerconfigbefore)
  - [NAME-router:config:after](../servereventmanager/server-events/#name-routerconfigafter)

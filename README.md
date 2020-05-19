# SmartThings Core SDK

The SmartThings Core SDK is a wrapper designed to simplify the use of the
[SmartThings REST API](https://smartthings.developer.samsung.com/docs/api-ref/st-api.html#section/Overview)
from JavaScript and TypeScript applications. This is the very first release of this SDK and should be considered
a work in progress. Changes may still be made that are not backwardly compatible.


## Installation

```bash
npm install @smartthings/core-sdk
```

## Importing

`NodeJS`:

```javascript
const {SmartThingsClient} = require('@smartthings/core-sdk')
```

Or `ES2015`+:

```javascript
import {SmartThingsClient} from '@smartthings/core-sdk'
```

## Example Usage
Substitue your Personal Access Token (PAT) with at least the `r:locations:*` scope
for `{YOUR-PAT-TOKEN}` in the following code.
```javascript
const {SmartThingsClient, BearerTokenAuthenticator} = require('@smartthings/core-sdk')
const client = new SmartThingsClient(new BearerTokenAuthenticator('{YOUR-PAT-TOKEN}'))

client.locations.list().then(locations => {
    console.log(`Found ${locations.length} locations`)
})

```

## Reference

### Authenticators

This SDK supports multiple ways of authenticating with the SmartThings platform. The currently available authenticators
are:

* [BearerTokenAuthenticator](src/authenticator.ts#37) -- Authenticator that is instantiated with any valid bearer
token. This is the authenticator you would use with a PAT (Personal Access) Token.

* [RefreshTokenAuthenticator](src/authenticator.ts#73) -- Authenticator that is instantiated with a bearer token and
a [RefreshTokenStore](src/authenticator.ts#64) that provides methods for retrieving and storing access and refresh
tokens. When this authenticator is used the API will automatically refresh expired access tokens, save the new tokens,
and retry the original request.

* [SequentialRefreshTokenAuthenticator](src/authenticator.ts#118)

### Endpoints

* [apps](https://github.com/SmartThingsCommunity/smartthings-core-sdk/wiki/Apps) -- A SmartApp can be an AWS Lambda function or a WebHook endpoint.

* [capabilities](https://github.com/SmartThingsCommunity/smartthings-core-sdk/wiki/Capabilities) -- Operations to read standard capability definitions as well as create and modify custom capabilities

* [deviceProfiles](https://github.com/SmartThingsCommunity/smartthings-core-sdk/wiki/Device-Profiles) -- A device profile contains the components, capabilities, and metadata (ID, name, ownership, etc.) that define a SmartThings device. Capabilities define the features of the device, and capabilities are grouped into components.  Changes made with this API are currently not reflected in the Developer Workspace, so for the most part creating and modifying capabilities should still be done there.

* [devices](https://github.com/SmartThingsCommunity/smartthings-core-sdk/wiki/Devices) -- Operations to access, control, create, update, and delete devices. These
operations include the ability to query for device statue and send commands to devices.

* [installedApps](https://github.com/SmartThingsCommunity/smartthings-core-sdk/wiki/Installed-Apps) -- Apps are installed by users and these operations are not explicitly called, but they may be useful for creating developer tools and automating tests.

* [locations](https://github.com/SmartThingsCommunity/smartthings-core-sdk/wiki/Locations) -- Locations can include hubs, devices, and Automations. Automations allow control of the devices in a Location, the ability to monitor and receive notifications about what's happening at the Location, and more.

* [modes](https://github.com/SmartThingsCommunity/smartthings-core-sdk/wiki/Modes) -- Operations to change the current **mode** of a location.

* [notifications](https://github.com/SmartThingsCommunity/smartthings-core-sdk/wiki/Notifications3) -- Operations to send push notifications to SmartThings mobile app
clients.

* [rooms](https://github.com/SmartThingsCommunity/smartthings-core-sdk/wiki/Rooms) -- Operations related to **Rooms**.  Rooms are a grouping of devices within a location.  

* [rules](https://github.com/SmartThingsCommunity/smartthings-core-sdk/wiki/Rules) -- Operations for working with Rules.  Rules allow you to create automations that can operate on SmartThings connected devices.

* [scenes](https://github.com/SmartThingsCommunity/smartthings-core-sdk/wiki/Scenes) -- Operations to list and execute scenes.  Currently this endpoint does not support creating or updating scenes.

* [schedules](https://github.com/SmartThingsCommunity/smartthings-core-sdk/wiki/Schedules) -- Operations for schedules for use in SmartApps.

* [schema](https://github.com/SmartThingsCommunity/smartthings-core-sdk/wiki/Schema) - Operations for ST Schema connectors and installed instances, along with operations to list the devices owned by each installed instance.

* [services](https://github.com/SmartThingsCommunity/smartthings-core-sdk/wiki/Services) - Operations to query for and subscribe to location service data, currently consisting of current weather conditions, weather forecast, and air quality data.

* [subscriptions](https://github.com/SmartThingsCommunity/smartthings-core-sdk/wiki/Subscriptions) -- Operations for subscribing to events, for use in SmartApps and
API Access apps.


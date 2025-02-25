---
title: Azure Azure Digital Twins client library for JavaScript
keywords: Azure, javascript, SDK, API, @azure/digital-twins, 
author: ramya-rao-a
ms.author: ramyar
ms.date: 09/08/2020
ms.topic: reference
ms.devlang: javascript
ms.service: azure
---

# Azure Azure Digital Twins client library for JavaScript - Version 1.0.0-preview.1 


This package contains an isomorphic SDK for Azure Digital Twins API to provide access to the Azure Digital Twins service for managing twins, models, relationships, etc.

## Getting started

### Currently supported environments

- Node.js version 6.x.x or higher
- Browser JavaScript

### How to Install

```bash
npm install @azure/digital-twins
```

### How to use

#### nodejs - Authentication, client creation and list digitalTwinModels as an example written in TypeScript.

##### Install @azure/ms-rest-nodeauth

```bash
npm install @azure/ms-rest-nodeauth
```

##### Sample code

```typescript
import * as coreHttp from "@azure/core-http";
import * as coreArm from "@azure/core-arm";
import * as msRestNodeAuth from "@azure/ms-rest-nodeauth";
import {
  AzureDigitalTwinsAPI,
  AzureDigitalTwinsAPIModels,
  AzureDigitalTwinsAPIMappers
} from "@azure/digital-twins";
const subscriptionId = process.env["AZURE_SUBSCRIPTION_ID"];
msRestNodeAuth
  .interactiveLogin()
  .then((creds) => {
    const client = new AzureDigitalTwinsAPI(creds, subscriptionId);
    const dependenciesFor = ["testdependenciesFor"];
    const includeModelDefinition = true;
    const maxItemCount = 1;
    client.digitalTwinModels
      .list(dependenciesFor, includeModelDefinition, maxItemCount)
      .then((result) => {
        console.log("The result is:");
        console.log(result);
      });
  }
  .catch((err) => {
    console.error(err);
  })
```

#### browser - Authentication, client creation and list digitalTwinModels as an example written in JavaScript.

##### Install @azure/ms-rest-browserauth

```bash
npm install @azure/ms-rest-browserauth
```

##### Sample code

See https://github.com/Azure/ms-rest-browserauth to learn how to authenticate to Azure in the browser.

- index.html

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>@azure/digital-twins sample</title>
    <script src="node_modules/@azure/core-http/dist/coreHttp.browser.js"></script>
    <script src="node_modules/@azure/core-arm/dist/coreArm.js"></script>
    <script src="node_modules/@azure/ms-rest-browserauth/dist/msAuth.js"></script>
    <script src="node_modules/@azure/digital-twins/dist/digital-twins.js"></script>
    <script type="text/javascript">
      const subscriptionId = "<Subscription_Id>";
      const authManager = new msAuth.AuthManager({
        clientId: "<client id for your Azure AD app>",
        tenant: "<optional tenant for your organization>"
      });
      authManager.finalizeLogin().then((res) => {
        if (!res.isLoggedIn) {
          // may cause redirects
          authManager.login();
        }
        const client = new Azure.Digitaltwins.AzureDigitalTwinsAPI(res.creds, subscriptionId);
        const dependenciesFor = ["testdependenciesFor"];
        const includeModelDefinition = true;
        const maxItemCount = 1;
        client.digitalTwinModels
          .list(dependenciesFor, includeModelDefinition, maxItemCount)
          .then((result) => {
            console.log("The result is:");
            console.log(result);
          })
          .catch((err) => {
            console.log("An error occurred:");
            console.error(err);
          });
      });
    </script>
  </head>
  <body></body>
</html
```

## Key concepts

Azure Digital Twins Preview is an Azure IoT service that creates comprehensive models of the physical environment. It can create spatial intelligence graphs to model the relationships and interactions between people, spaces, and devices.
You can learn more about Azure Digital Twins by visiting [Azure Digital Twins Documentation](https://docs.microsoft.com/azure/digital-twins/)

## Examples

Please take a look at the Readme file in
[samples](https://github.com/Azure/azure-sdk-for-js/tree/@azure/digital-twins_1.0.0-preview.1/sdk/digitaltwins/digital-twins/samples)
directory for detailed examples on how to use this library.

## Troubleshooting

### Enable logs

You can set the following environment variable to get the debug logging output when using this library.

```bash
export AZURE_LOG_LEVEL=verbose
```

For more detailed instructions on how to enable logs, you can look at the [@azure/logger package docs](https://github.com/Azure/azure-sdk-for-js/tree/@azure/digital-twins_1.0.0-preview.1/sdk/core/logger).

## Next steps

Please take a look at the
[samples](https://github.com/Azure/azure-sdk-for-js/tree/@azure/digital-twins_1.0.0-preview.1/sdk/digitaltwins/digital-twins/samples)
directory for detailed examples on how to use this library.

## Contributing

If you'd like to contribute to this library, please read the [contributing guide](https://github.com/Azure/azure-sdk-for-js/blob/@azure/digital-twins_1.0.0-preview.1/CONTRIBUTING.md) to learn more about how to build and test the code.

## Related projects

- [Microsoft Azure SDK for Javascript](https://github.com/Azure/azure-sdk-for-js)
  ![Impressions](https://github.com/Azure/azure-sdk-for-js/tree/@azure/digital-twins_1.0.0-preview.1/sdk/digitaltwins/digital-twins/README.md)


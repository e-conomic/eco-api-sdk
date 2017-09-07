# e-conomic .Net SDK
## THIS SDK IS DEPRECATED AND UNSUPPORTED. WE ADVICE AGAINST USING IT. PLEASE SWITCH TO SOAP DIRECTLY OR OUR REST API.
#### NB: SOAP IS NOT DEPRECATED - ONLY THE SDK.

The current release (v1.4.22) which was released on Nov 16th 2015 was the last release of the SDK. From this date the SDK has been deprecated and we do not advise the use of this SDK. We will no longer fix bugs in this SDK. If you encounter bugs or want new functionality, we refer you to use our SOAP API directly or take a look at our REST API.

The 1.4.22 release includes both bugfixes and minor improvements. If you do use the SDK today, we urge you to at least upgrade to this version.

The 1.4.22 release includes a breaking change. You now have to specify an App Identifier string when creating a new instance of EconomicSession. This is a string, that identifies your app to us. The recommended identifier format is `MyAppName/1.1 (http://example.com/MyAppName/; MyAppName@example.com)`.

You will need to uprade to this latest SDK as soon as possible. In the fall of 2015 this is the only SDK assembly that will work. All older binaries that do not include an app identifier will be rejected by our servers.

Below you can find a C# example
```C#
string myIdentifier = "MyCoolIntegration/1.1 (http://example.com/MyCoolIntegration/; MyCoolIntegration@example.com) BasedOnSuperLib/1.4";
var webservice = new EconomicSession(myIdentifier);
```

### Alternatives to this SDK

You can find more developer resources at http://www.e-conomic.com/developer

We highly recommend using our REST API which is continuously expanded. It does not cover all functionality, but it is where our development resources are focused. The SOAP API is still supported, and is the API that covers most features.

_When using the SOAP API directly you are required to define the AppIdentifier like so:_
```C#
using (var operationScope = new OperationContextScope(session.InnerChannel))
{
    // Add a HTTP Header to an outgoing request
    var requestMessage = new HttpRequestMessageProperty();
    requestMessage.Headers["X-EconomicAppIdentifier"] = "MyCoolIntegration/1.1 (http://example.com/MyCoolIntegration/; MyCoolIntegration@example.com) BasedOnSuperLib/1.4";
    OperationContext.Current.OutgoingMessageProperties[HttpRequestMessageProperty.Name] = requestMessage;

    session.Connect(<agreement>, <user>, <password>);
}
```

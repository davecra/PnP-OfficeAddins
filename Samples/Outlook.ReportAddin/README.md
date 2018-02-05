#Outlook Report Suspicious Email Addin#
This add-in is a fully functional sample that demonstrates how an organization can use the new OfficeJS API in to create and deploy and Outlook add-in to help user report suspicious emails they recieve to the proper security team.

### Applies to ###
-  Exchange Online
-  Office 365
-  Outlook.com

### Prerequisites ###

This add-in is fully ready to deploy for demonstration purposes. It uses the [easyEws library](https://github.com/davecra/easyEWS). 

You will likely want to publish this sample on a web server as a web app once you have downloaded it, do do this you can use [Azure](https://azure.microsoft.com/en-us/documentation/scenarios/web-app). 

Before you publish this, you will want to modify the manifest with the proper URLS and email address where you want the secuirty email's to be sent by the users. For example, if you publish to the server http://azuretenant.contoso.com/webapp/ and the email to be securityteam@contoso.com,  you will want to modify these lines:

```xml
  <IconUrl DefaultValue="https://localhost:3000/assets/icon-80.png" />
  <HighResolutionIconUrl DefaultValue="https://localhost:3000/assets/logo-filled.png" />
```

to 

```xml
  <IconUrl DefaultValue="http://azuretenant.contoso.com/webapp/assets/icon-80.png" />
  <HighResolutionIconUrl DefaultValue="http://azuretenant.contoso.com/webapp/assets/logo-filled.png" />
```
And then, in the **FORMS SETTINGS** change the **SOURCE LOCATION**:

```xml
    <SourceLocation DefaultValue="https://localhost:3000/index.html"/>
```

to

```xml
    <SourceLocation DefaultValue="http://azuretenant.contoso.com/webapp/index.html"/>
```

And then the icons in **RESOURCES**:

```xml
        <bt:Image id="icon16" DefaultValue="https://localhost:3000/assets/icon-16.png"/>
        <bt:Image id="icon32" DefaultValue="https://localhost:3000/assets/icon-32.png"/>
        <bt:Image id="icon80" DefaultValue="https://localhost:3000/assets/icon-80.png"/>
```

to

```xml
        <bt:Image id="icon16" DefaultValue="http://azuretenant.contoso.com/assets/icon-16.png"/>
        <bt:Image id="icon32" DefaultValue="http://azuretenant.contoso.com/assets/icon-32.png"/>
        <bt:Image id="icon80" DefaultValue="http://azuretenant.contoso.com/assets/icon-80.png"/>
```

And finally, in the **RESOURCES** section of the manifest you will need to update the **bt:URL**:

```xml
        <!--Set the email=(value) for the security emails address -->
        <bt:Url id="messageReadTaskPaneUrl" DefaultValue="https://localhost:3000/index.html?email=admin@contoso.com.com"/>
```

to

```xml
        <!--Set the email=(value) for the security emails address -->
        <bt:Url id="messageReadTaskPaneUrl" DefaultValue="http://azuretenant.contoso.com//index.html?email=securityteam@contoso.com.com"/>
```

### Version History ###
Version | Date | Comments
--------|------|---------
1.0 | 2/5/2018 | Initial release

### Disclaimer ###
**THIS CODE IS PROVIDED *AS IS* WITHOUT WARRANTY OF ANY KIND, EITHER EXPRESS OR IMPLIED, INCLUDING ANY IMPLIED WARRANTIES OF FITNESS FOR A PARTICULAR PURPOSE, MERCHANTABILITY, OR NON-INFRINGEMENT.**
 
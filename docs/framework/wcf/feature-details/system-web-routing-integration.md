---
title: Intégration de System.Web.Routing
ms.date: 03/30/2017
ms.assetid: 31fe2a4f-5c47-4e5d-8ee1-84c524609d41
ms.openlocfilehash: fdc355d4560294a16f3e9c488fdaf142d2982c0d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745341"
---
# <a name="systemwebrouting-integration"></a>Intégration de System.Web.Routing
Lors de l’hébergement d’un service Windows Communication Foundation (WCF) dans Internet Information Services (IIS), vous placez un fichier. svc dans le répertoire virtuel. Ce fichier .svc spécifie la fabrique hôte de service à utiliser ainsi que la classe qui implémente le service. Lorsque vous effectuez des demandes au service, vous spécifiez le fichier. svc dans l’URI, par exemple : `http://contoso.com/EmployeeServce.svc`. Pour les programmeurs qui écrivent des services REST, ce type d'URI n'est pas optimal. Les URI des services REST spécifient une ressource spécifique et n’ont généralement pas d’extension. La fonctionnalité d’intégration de <xref:System.Web.Routing> vous permet d’héberger un service WCF REST qui répond aux URI sans extension. Pour plus d’informations sur le routage, consultez [routage ASP.net](https://docs.microsoft.com/previous-versions/aspnet/cc668201(v=vs.100)).  
  
## <a name="using-systemwebrouting-integration"></a>Utilisation de l'intégration System.Web.Routing  
 Pour utiliser la fonctionnalité d’intégration <xref:System.Web.Routing>, vous utilisez la classe <xref:System.ServiceModel.Activation.ServiceRoute> pour créer un ou plusieurs itinéraires et les ajouter à l’objet <xref:System.Web.Routing.RouteTable> dans un fichier Global.asax. Ces itinéraires spécifient les URI relatifs auxquels le service répond. L'exemple suivant montre comment effectuer cette opération.  
  
```aspx-csharp  
<%@ Application Language="C#" %>  
<%@ Import Namespace="System.Web.Routing" %>  
<%@ Import Namespace="System.ServiceModel.Activation" %>  
<%@ Import Namespace="System.ServiceModel.Web " %>  
  
<script RunAt="server">  
    void Application_Start(object sender, EventArgs e)  
    {  
        RegisterRoutes(RouteTable.Routes);  
    }  
  
    private void RegisterRoutes(RouteCollection routes)  
    {  
        routes.Add(new ServiceRoute("Customers", new WebServiceHostFactory(), typeof(Service)));   
   }  
</script>  
```  
  
 Ce code route toutes les demandes avec un URI relatif commençant par Customers vers le service `Service`.  
  
 Dans votre fichier Web.config, vous devez ajouter le module `System.Web.Routing.UrlRoutingModule`, affecter à l'attribut `runAllManagedModulesForAllRequests` la valeur `true` et ajouter le gestionnaire `UrlRoutingHandler` à l'élément `<system.webServer>`, comme le montre l'exemple suivant.  
  
```xml  
<system.webServer>  
      <modules runAllManagedModulesForAllRequests="true">  
        <add name="UrlRoutingModule" type="System.Web.Routing.UrlRoutingModule, System.Web, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a" />  
      </modules>  
      <handlers>  
        <add name="UrlRoutingHandler" preCondition="integratedMode" verb="*" path="UrlRouting.axd"/>  
      </handlers>  
    </system.webServer>  
```  
  
 Ce code charge un module et un gestionnaire nécessaires pour le routage. Pour plus d’informations, consultez [Routage](../../../../docs/framework/wcf/feature-details/routing.md). Vous devez également affecter à l'attribut `aspNetCompatibilityEnabled` la valeur `true` dans l'élément `<serviceHostingEnvironment>`, comme illustré dans l'exemple suivant.  
  
```xml  
<system.serviceModel>  
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>  
        <!-- ... -->  
    </system.serviceModel>  
```  
  
 La classe qui implémente le service doit activer les exigences de compatibilité ASP.NET, comme indiqué dans l’exemple suivant.  
  
```csharp 
[ServiceContract]  
[AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Allowed)]  
    public class Service  
    {  
        // ...  
    }  
```  
  
## <a name="see-also"></a>Voir aussi

- [Modèle de programmation HTTP web WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- [Routage ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/cc668201(v=vs.100))

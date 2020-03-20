---
title: Stand-Alone Diagnostics Feed, exemple
ms.date: 03/30/2017
ms.assetid: d31c6c1f-292c-4d95-8e23-ed8565970ea5
ms.openlocfilehash: 29d8caee48925040db9f1812f015870e3a1272bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144004"
---
# <a name="stand-alone-diagnostics-feed-sample"></a>Stand-Alone Diagnostics Feed, exemple
Cet exemple montre comment créer un flux RSS/Atom pour la syndication avec Windows Communication Foundation (WCF). Il s’agit d’un programme de base "Hello World" qui montre les bases du modèle d’objet et comment le configurer sur un service windows Communication Foundation (WCF).  
  
 WCF modèle les flux de syndication comme opérations <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>de service qui retournent un type de données spécial, . Les instances de <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> peuvent sérialiser un flux aux formats RSS 2.0 et Atom 1.0. L'exemple de code suivant illustre le contrat utilisé.  
  
```csharp  
[ServiceContract(Namespace = "")]  
    interface IDiagnosticsService  
    {  
        [OperationContract]  
        //The [WebGet] attribute controls how WCF dispatches  
        //HTTP requests to service operations based on a URI suffix  
        //(the part of the request URI after the endpoint address)  
        //using the HTTP GET method. The UriTemplate specifies a relative  
        //path of 'feed', and specifies that the format is  
        //supplied using a query string.
        [WebGet(UriTemplate="feed?format={format}")]  
        [ServiceKnownType(typeof(Atom10FeedFormatter))]  
        [ServiceKnownType(typeof(Rss20FeedFormatter))]  
        SyndicationFeedFormatter GetProcesses(string format);  
    }  
```  
  
 L’opération `GetProcesses` est annotée avec l’attribut qui vous permet de contrôler la <xref:System.ServiceModel.Web.WebGetAttribute> façon dont WCF envoie les demandes HTTP GET pour les opérations de service et de spécifier le format des messages envoyés.  
  
 Comme tout service WCF, les flux de syndication peuvent être auto-hébergés dans n’importe quelle application gérée. Les services de syndication nécessitent une liaison spécifique (<xref:System.ServiceModel.WebHttpBinding>) et un comportement de point de terminaison spécifique (<xref:System.ServiceModel.Description.WebHttpBehavior>) afin de fonctionner correctement. La nouvelle classe <xref:System.ServiceModel.Web.WebServiceHost> fournit une API pratique pour créer ces points de terminaison sans configuration spécifique.  
  
```csharp  
WebServiceHost host = new WebServiceHost(typeof(ProcessService), new Uri("http://localhost:8000/diagnostics"));  
  
            //The WebServiceHost will automatically provide a default endpoint at the base address  
            //using the proper binding (the WebHttpBinding) and endpoint behavior (the WebHttpBehavior)  
```  
  
 Vous pouvez aussi utiliser <xref:System.ServiceModel.Activation.WebServiceHostFactory> à partir d'un fichier .svc hébergé dans IIS pour fournir des fonctionnalités équivalentes (cette technique n'est pas démontrée dans cet exemple de code).  
  
```xml
<%@ ServiceHost Language="C#|VB" Debug="true" Service="ProcessService" %>
```
  
 Ce service reçoit des demandes à l'aide d'une demande HTTP GET standard ; par conséquent, vous pouvez utiliser tout client RSS ou ATOM pour accéder au service. Par exemple, vous pouvez afficher la sortie `http://localhost:8000/diagnostics/feed/?format=atom` de `http://localhost:8000/diagnostics/feed/?format=rss` ce service en naviguant vers ou dans un navigateur conscient de RSS.
  
 Vous pouvez également utiliser le [Comment le WCF Syndication Object Model Maps to Atom et RSS](../../../../docs/framework/wcf/feature-details/how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md) pour lire les données syndiquées et les traiter à l’aide de code impératif.  
  
```csharp
XmlReader reader = XmlReader.Create( "http://localhost:8000/diagnostics/feed/?format=rss",
    new XmlReaderSettings()
    {
        //MaxCharactersInDocument can be used to control the maximum amount of data
        //read from the reader and helps prevent OutOfMemoryException
        MaxCharactersInDocument = 1024 * 64
    } );

SyndicationFeed feed = SyndicationFeed.Load(reader);

foreach (SyndicationItem i in feed.Items)
{
    XmlSyndicationContent content = i.Content as XmlSyndicationContent;
    ProcessData pd = content.ReadContent<ProcessData>();

    Console.WriteLine(i.Title.Text);
    Console.WriteLine(pd.ToString());
}
```
  
## <a name="set-up-build-and-run-the-sample"></a>Configurez, construisez et exécutez l’échantillon
  
1. Assurez-vous d’avoir la bonne autorisation d’enregistrement d’adresse pour HTTP et HTTPS sur l’ordinateur comme expliqué dans les instructions mises en place dans [la procédure d’installation unique pour les échantillons de la Fondation de communication Windows](one-time-setup-procedure-for-the-wcf-samples.md).

2. Générez la solution.

3. Exécutez l’application console.

4. Pendant que l’application de `http://localhost:8000/diagnostics/feed/?format=atom` `http://localhost:8000/diagnostics/feed/?format=rss` console est en cours d’exécution, naviguez vers ou à l’aide d’un navigateur RSS-conscient.

> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Si ce répertoire n’existe pas, rendez-vous sur [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) Samples pour .NET Framework 4 pour](https://www.microsoft.com/download/details.aspx?id=21459) télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] des échantillons. Cet exemple se trouve dans le répertoire suivant.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\DiagnosticsFeed`

## <a name="see-also"></a>Voir aussi

- [Modèle de programmation HTTP Web WCF](../feature-details/wcf-web-http-programming-model.md)
- [Syndication WCF](../feature-details/wcf-syndication.md)

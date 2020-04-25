---
title: Stand-Alone Diagnostics Feed, exemple
ms.date: 03/30/2017
ms.assetid: d31c6c1f-292c-4d95-8e23-ed8565970ea5
ms.openlocfilehash: e8edb6c603e21a517244901993226fce3f055bbe
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82141106"
---
# <a name="stand-alone-diagnostics-feed-sample"></a>Stand-Alone Diagnostics Feed, exemple
Cet exemple montre comment créer un flux RSS/Atom pour la syndication avec Windows Communication Foundation (WCF). Il s’agit d’un programme « Hello World » de base qui montre les principes fondamentaux du modèle objet et comment le configurer sur un service Windows Communication Foundation (WCF).  
  
 Les flux de syndication des modèles WCF sont des opérations de service qui retournent un type de données spécial, <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>. Les instances de <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> peuvent sérialiser un flux aux formats RSS 2.0 et Atom 1.0. L'exemple de code suivant illustre le contrat utilisé.  
  
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
  
 L' `GetProcesses` opération est annotée avec <xref:System.ServiceModel.Web.WebGetAttribute> l’attribut qui vous permet de contrôler la manière dont WCF distribue les requêtes http d’obtention aux opérations de service et spécifie le format des messages envoyés.  
  
 Comme n’importe quel service WCF, les flux de syndication peuvent être auto-hébergés dans n’importe quelle application gérée. Les services de syndication nécessitent une liaison spécifique (<xref:System.ServiceModel.WebHttpBinding>) et un comportement de point de terminaison spécifique (<xref:System.ServiceModel.Description.WebHttpBehavior>) afin de fonctionner correctement. La nouvelle classe <xref:System.ServiceModel.Web.WebServiceHost> fournit une API pratique pour créer ces points de terminaison sans configuration spécifique.  
  
```csharp  
WebServiceHost host = new WebServiceHost(typeof(ProcessService), new Uri("http://localhost:8000/diagnostics"));  
  
            //The WebServiceHost will automatically provide a default endpoint at the base address  
            //using the proper binding (the WebHttpBinding) and endpoint behavior (the WebHttpBehavior)  
```  
  
 Vous pouvez aussi utiliser <xref:System.ServiceModel.Activation.WebServiceHostFactory> à partir d'un fichier .svc hébergé dans IIS pour fournir des fonctionnalités équivalentes (cette technique n'est pas démontrée dans cet exemple de code).  
  
```xml
<% @ServiceHost Language="C#|VB" Debug="true" Service="ProcessService" %>
```
  
 Ce service reçoit des demandes à l'aide d'une demande HTTP GET standard ; par conséquent, vous pouvez utiliser tout client RSS ou ATOM pour accéder au service. Par exemple, vous pouvez afficher la sortie de ce service en accédant à `http://localhost:8000/diagnostics/feed/?format=atom` ou `http://localhost:8000/diagnostics/feed/?format=rss` dans un navigateur compatible RSS.
  
 Vous pouvez également utiliser la [manière dont le modèle objet de syndication WCF est mappé à Atom et RSS](../../../../docs/framework/wcf/feature-details/how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md) pour lire les données syndiquées et les traiter à l’aide du code impératif.  
  
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
  
## <a name="set-up-build-and-run-the-sample"></a>Configurer, générer et exécuter l’exemple
  
1. Assurez-vous que vous disposez de l’autorisation d’inscription d’adresse appropriée pour HTTP et HTTPs sur l’ordinateur, comme expliqué dans les instructions de configuration d' [une procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).

2. Générez la solution.

3. Exécutez l’application console.

4. Pendant que l’application console est en cours d' `http://localhost:8000/diagnostics/feed/?format=atom` exécution `http://localhost:8000/diagnostics/feed/?format=rss` , accédez à ou à l’aide d’un navigateur compatible RSS.

> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ) et. Cet exemple se trouve dans le répertoire suivant.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\DiagnosticsFeed`

## <a name="see-also"></a>Voir aussi

- [Modèle de programmation HTTP Web WCF](../feature-details/wcf-web-http-programming-model.md)
- [Syndication WCF](../feature-details/wcf-syndication.md)

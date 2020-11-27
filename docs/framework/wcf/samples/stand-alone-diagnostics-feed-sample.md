---
title: Stand-Alone Diagnostics Feed, exemple
ms.date: 03/30/2017
ms.assetid: d31c6c1f-292c-4d95-8e23-ed8565970ea5
ms.openlocfilehash: b4c3613656e0aec42c0d3f5cd7cde0af6540a69a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96268246"
---
# <a name="stand-alone-diagnostics-feed-sample"></a><span data-ttu-id="6b378-102">Stand-Alone Diagnostics Feed, exemple</span><span class="sxs-lookup"><span data-stu-id="6b378-102">Stand-Alone Diagnostics Feed Sample</span></span>

<span data-ttu-id="6b378-103">Cet exemple montre comment créer un flux RSS/Atom pour la syndication avec Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="6b378-103">This sample demonstrates how to create an RSS/Atom feed for syndication with Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="6b378-104">Il s’agit d’un programme « Hello World » de base qui montre les principes fondamentaux du modèle objet et comment le configurer sur un service Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="6b378-104">It is a basic "Hello World" program that shows the basics of the object model and how to set it up on a Windows Communication Foundation (WCF) service.</span></span>  
  
 <span data-ttu-id="6b378-105">Les flux de syndication des modèles WCF sont des opérations de service qui retournent un type de données spécial, <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> .</span><span class="sxs-lookup"><span data-stu-id="6b378-105">WCF models syndication feeds as service operations that return a special data type, <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>.</span></span> <span data-ttu-id="6b378-106">Les instances de <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> peuvent sérialiser un flux aux formats RSS 2.0 et Atom 1.0.</span><span class="sxs-lookup"><span data-stu-id="6b378-106">Instances of <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> can serialize a feed into both the RSS 2.0 and Atom 1.0 formats.</span></span> <span data-ttu-id="6b378-107">L'exemple de code suivant illustre le contrat utilisé.</span><span class="sxs-lookup"><span data-stu-id="6b378-107">The following sample code shows the contract used.</span></span>  
  
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
  
 <span data-ttu-id="6b378-108">L' `GetProcesses` opération est annotée avec l' <xref:System.ServiceModel.Web.WebGetAttribute> attribut qui vous permet de contrôler la manière dont WCF distribue les requêtes http d’obtention aux opérations de service et spécifie le format des messages envoyés.</span><span class="sxs-lookup"><span data-stu-id="6b378-108">The `GetProcesses` operation is annotated with the <xref:System.ServiceModel.Web.WebGetAttribute> attribute that enables you to control how WCF dispatches HTTP GET requests to service operations and specify the format of the messages sent.</span></span>  
  
 <span data-ttu-id="6b378-109">Comme n’importe quel service WCF, les flux de syndication peuvent être auto-hébergés dans n’importe quelle application gérée.</span><span class="sxs-lookup"><span data-stu-id="6b378-109">Like any WCF service, syndication feeds can be self hosted in any managed application.</span></span> <span data-ttu-id="6b378-110">Les services de syndication nécessitent une liaison spécifique (<xref:System.ServiceModel.WebHttpBinding>) et un comportement de point de terminaison spécifique (<xref:System.ServiceModel.Description.WebHttpBehavior>) afin de fonctionner correctement.</span><span class="sxs-lookup"><span data-stu-id="6b378-110">Syndication services require a specific binding (the <xref:System.ServiceModel.WebHttpBinding>) and a specific endpoint behavior (the <xref:System.ServiceModel.Description.WebHttpBehavior>) to function correctly.</span></span> <span data-ttu-id="6b378-111">La nouvelle classe <xref:System.ServiceModel.Web.WebServiceHost> fournit une API pratique pour créer ces points de terminaison sans configuration spécifique.</span><span class="sxs-lookup"><span data-stu-id="6b378-111">The new <xref:System.ServiceModel.Web.WebServiceHost> class provides a convenient API for creating such endpoints without specific configuration.</span></span>  
  
```csharp  
WebServiceHost host = new WebServiceHost(typeof(ProcessService), new Uri("http://localhost:8000/diagnostics"));  
  
            //The WebServiceHost will automatically provide a default endpoint at the base address  
            //using the proper binding (the WebHttpBinding) and endpoint behavior (the WebHttpBehavior)  
```  
  
 <span data-ttu-id="6b378-112">Vous pouvez aussi utiliser <xref:System.ServiceModel.Activation.WebServiceHostFactory> à partir d'un fichier .svc hébergé dans IIS pour fournir des fonctionnalités équivalentes (cette technique n'est pas démontrée dans cet exemple de code).</span><span class="sxs-lookup"><span data-stu-id="6b378-112">Alternatively, you can use <xref:System.ServiceModel.Activation.WebServiceHostFactory> from within an IIS-hosted .svc file to provide equivalent functionality (this technique is not demonstrated in this sample code).</span></span>  
  
```xml
<% @ServiceHost Language="C#|VB" Debug="true" Service="ProcessService" %>
```
  
 <span data-ttu-id="6b378-113">Ce service reçoit des demandes à l'aide d'une demande HTTP GET standard ; par conséquent, vous pouvez utiliser tout client RSS ou ATOM pour accéder au service.</span><span class="sxs-lookup"><span data-stu-id="6b378-113">Because this service receives requests using the standard HTTP GET, you can use any RSS or ATOM-aware client to access the service.</span></span> <span data-ttu-id="6b378-114">Par exemple, vous pouvez afficher la sortie de ce service en accédant à `http://localhost:8000/diagnostics/feed/?format=atom` ou `http://localhost:8000/diagnostics/feed/?format=rss` dans un navigateur compatible RSS.</span><span class="sxs-lookup"><span data-stu-id="6b378-114">For example, you can view the output of this service by navigating to `http://localhost:8000/diagnostics/feed/?format=atom` or `http://localhost:8000/diagnostics/feed/?format=rss` in an RSS-aware browser.</span></span>
  
 <span data-ttu-id="6b378-115">Vous pouvez également utiliser la [manière dont le modèle objet de syndication WCF est mappé à Atom et RSS](../feature-details/how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md) pour lire les données syndiquées et les traiter à l’aide du code impératif.</span><span class="sxs-lookup"><span data-stu-id="6b378-115">You can also use the [How the WCF Syndication Object Model Maps to Atom and RSS](../feature-details/how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md) to read syndicated data and process it using imperative code.</span></span>  
  
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
  
## <a name="set-up-build-and-run-the-sample"></a><span data-ttu-id="6b378-116">Configurer, générer et exécuter l’exemple</span><span class="sxs-lookup"><span data-stu-id="6b378-116">Set up, build, and run the sample</span></span>
  
1. <span data-ttu-id="6b378-117">Assurez-vous que vous disposez de l’autorisation d’inscription d’adresse appropriée pour HTTP et HTTPs sur l’ordinateur, comme expliqué dans les instructions de configuration d' [une procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6b378-117">Ensure that you have the right address registration permission for HTTP and HTTPS on the computer as explained in the set up instructions in [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="6b378-118">Générez la solution.</span><span class="sxs-lookup"><span data-stu-id="6b378-118">Build the solution.</span></span>

3. <span data-ttu-id="6b378-119">Exécutez l’application console.</span><span class="sxs-lookup"><span data-stu-id="6b378-119">Run the console application.</span></span>

4. <span data-ttu-id="6b378-120">Pendant que l’application console est en cours d’exécution, accédez à `http://localhost:8000/diagnostics/feed/?format=atom` ou `http://localhost:8000/diagnostics/feed/?format=rss` à l’aide d’un navigateur compatible RSS.</span><span class="sxs-lookup"><span data-stu-id="6b378-120">While the console application is running, navigate to `http://localhost:8000/diagnostics/feed/?format=atom` or `http://localhost:8000/diagnostics/feed/?format=rss` using an RSS-aware browser.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6b378-121">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="6b378-121">The samples may already be installed on your computer.</span></span> <span data-ttu-id="6b378-122">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="6b378-122">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="6b378-123">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="6b378-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6b378-124">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="6b378-124">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\DiagnosticsFeed`

## <a name="see-also"></a><span data-ttu-id="6b378-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6b378-125">See also</span></span>

- [<span data-ttu-id="6b378-126">Modèle de programmation HTTP Web WCF</span><span class="sxs-lookup"><span data-stu-id="6b378-126">WCF Web HTTP Programming Model</span></span>](../feature-details/wcf-web-http-programming-model.md)
- [<span data-ttu-id="6b378-127">Syndication WCF</span><span class="sxs-lookup"><span data-stu-id="6b378-127">WCF Syndication</span></span>](../feature-details/wcf-syndication.md)

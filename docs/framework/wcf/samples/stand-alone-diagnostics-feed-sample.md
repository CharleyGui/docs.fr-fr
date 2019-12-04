---
title: Stand-Alone Diagnostics Feed, exemple
ms.date: 03/30/2017
ms.assetid: d31c6c1f-292c-4d95-8e23-ed8565970ea5
ms.openlocfilehash: 40e7e2b704204278e6a8754134a952b8235ee528
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716667"
---
# <a name="stand-alone-diagnostics-feed-sample"></a><span data-ttu-id="d0a2b-102">Stand-Alone Diagnostics Feed, exemple</span><span class="sxs-lookup"><span data-stu-id="d0a2b-102">Stand-Alone Diagnostics Feed Sample</span></span>
<span data-ttu-id="d0a2b-103">Cet exemple montre comment créer un flux RSS/Atom pour la syndication avec Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="d0a2b-103">This sample demonstrates how to create an RSS/Atom feed for syndication with Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="d0a2b-104">Il s’agit d’un programme « Hello World » de base qui montre les principes fondamentaux du modèle objet et comment le configurer sur un service Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="d0a2b-104">It is a basic "Hello World" program that shows the basics of the object model and how to set it up on a Windows Communication Foundation (WCF) service.</span></span>  
  
 <span data-ttu-id="d0a2b-105">Les flux de syndication des modèles WCF sont des opérations de service qui retournent un type de données spécial, <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>.</span><span class="sxs-lookup"><span data-stu-id="d0a2b-105">WCF models syndication feeds as service operations that return a special data type, <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>.</span></span> <span data-ttu-id="d0a2b-106">Les instances de <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> peuvent sérialiser un flux aux formats RSS 2.0 et Atom 1.0.</span><span class="sxs-lookup"><span data-stu-id="d0a2b-106">Instances of <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> can serialize a feed into both the RSS 2.0 and Atom 1.0 formats.</span></span> <span data-ttu-id="d0a2b-107">L'exemple de code suivant illustre le contrat utilisé.</span><span class="sxs-lookup"><span data-stu-id="d0a2b-107">The following sample code shows the contract used.</span></span>  
  
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
  
 <span data-ttu-id="d0a2b-108">L’opération de `GetProcesses` est annotée avec l’attribut <xref:System.ServiceModel.Web.WebGetAttribute> qui vous permet de contrôler la manière dont WCF distribue les requêtes HTTP d’obtention aux opérations de service et spécifie le format des messages envoyés.</span><span class="sxs-lookup"><span data-stu-id="d0a2b-108">The `GetProcesses` operation is annotated with the <xref:System.ServiceModel.Web.WebGetAttribute> attribute that enables you to control how WCF dispatches HTTP GET requests to service operations and specify the format of the messages sent.</span></span>  
  
 <span data-ttu-id="d0a2b-109">Comme n’importe quel service WCF, les flux de syndication peuvent être auto-hébergés dans n’importe quelle application gérée.</span><span class="sxs-lookup"><span data-stu-id="d0a2b-109">Like any WCF service, syndication feeds can be self hosted in any managed application.</span></span> <span data-ttu-id="d0a2b-110">Les services de syndication nécessitent une liaison spécifique (<xref:System.ServiceModel.WebHttpBinding>) et un comportement de point de terminaison spécifique (<xref:System.ServiceModel.Description.WebHttpBehavior>) afin de fonctionner correctement.</span><span class="sxs-lookup"><span data-stu-id="d0a2b-110">Syndication services require a specific binding (the <xref:System.ServiceModel.WebHttpBinding>) and a specific endpoint behavior (the <xref:System.ServiceModel.Description.WebHttpBehavior>) to function correctly.</span></span> <span data-ttu-id="d0a2b-111">La nouvelle classe <xref:System.ServiceModel.Web.WebServiceHost> fournit une API pratique pour créer ces points de terminaison sans configuration spécifique.</span><span class="sxs-lookup"><span data-stu-id="d0a2b-111">The new <xref:System.ServiceModel.Web.WebServiceHost> class provides a convenient API for creating such endpoints without specific configuration.</span></span>  
  
```csharp  
WebServiceHost host = new WebServiceHost(typeof(ProcessService), new Uri("http://localhost:8000/diagnostics"));  
  
            //The WebServiceHost will automatically provide a default endpoint at the base address  
            //using the proper binding (the WebHttpBinding) and endpoint behavior (the WebHttpBehavior)  
```  
  
 <span data-ttu-id="d0a2b-112">Vous pouvez aussi utiliser <xref:System.ServiceModel.Activation.WebServiceHostFactory> à partir d'un fichier .svc hébergé dans IIS pour fournir des fonctionnalités équivalentes (cette technique n'est pas démontrée dans cet exemple de code).</span><span class="sxs-lookup"><span data-stu-id="d0a2b-112">Alternatively, you can use <xref:System.ServiceModel.Activation.WebServiceHostFactory> from within an IIS-hosted .svc file to provide equivalent functionality (this technique is not demonstrated in this sample code).</span></span>  
  
```  
<%@ ServiceHost Language="C#|VB" Debug="true" Service="ProcessService" %>  
```  
  
 <span data-ttu-id="d0a2b-113">Ce service reçoit des demandes à l'aide d'une demande HTTP GET standard ; par conséquent, vous pouvez utiliser tout client RSS ou ATOM pour accéder au service.</span><span class="sxs-lookup"><span data-stu-id="d0a2b-113">Because this service receives requests using the standard HTTP GET, you can use any RSS or ATOM-aware client to access the service.</span></span> <span data-ttu-id="d0a2b-114">Par exemple, vous pouvez afficher la sortie de ce service en accédant à `http://localhost:8000/diagnostics/feed/?format=atom` ou `http://localhost:8000/diagnostics/feed/?format=rss` dans un navigateur compatible RSS.</span><span class="sxs-lookup"><span data-stu-id="d0a2b-114">For example, you can view the output of this service by navigating to `http://localhost:8000/diagnostics/feed/?format=atom` or `http://localhost:8000/diagnostics/feed/?format=rss` in an RSS-aware browser.</span></span>
  
 <span data-ttu-id="d0a2b-115">Vous pouvez également utiliser la [manière dont le modèle objet de syndication WCF est mappé à Atom et RSS](../../../../docs/framework/wcf/feature-details/how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md) pour lire les données syndiquées et les traiter à l’aide du code impératif.</span><span class="sxs-lookup"><span data-stu-id="d0a2b-115">You can also use the [How the WCF Syndication Object Model Maps to Atom and RSS](../../../../docs/framework/wcf/feature-details/how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md) to read syndicated data and process it using imperative code.</span></span>  
  
```csharp  
XmlReader reader = XmlReader.Create( "http://localhost:8000/diagnostics/feed/?format=rss",  
new XmlReaderSettings()  
{  
//MaxCharactersInDocument can be used to control the maximum amount of data   
//read from the reader and helps prevent OutOfMemoryException  
MaxCharactersInDocument = 1024 * 64  
} );  
  
SyndicationFeed feed = SyndicationFeed.Load( reader );  
  
foreach (SyndicationItem i in feed.Items)  
{  
        XmlSyndicationContent content = i.Content as XmlSyndicationContent;  
        ProcessData pd = content.ReadContent<ProcessData>();  
  
        Console.WriteLine(i.Title.Text);  
        Console.WriteLine(pd.ToString());  
}  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d0a2b-116">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="d0a2b-116">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="d0a2b-117">Assurez-vous que vous disposez de l’autorisation d’inscription d’adresse appropriée pour HTTP et HTTPs sur l’ordinateur, comme expliqué dans les instructions de configuration d' [une procédure d’installation unique pour les exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d0a2b-117">Ensure that you have the right address registration permission for HTTP and HTTPS on the computer as explained in the set up instructions in [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="d0a2b-118">Générez la solution.</span><span class="sxs-lookup"><span data-stu-id="d0a2b-118">Build the solution.</span></span>  
  
3. <span data-ttu-id="d0a2b-119">Exécutez l'application console.</span><span class="sxs-lookup"><span data-stu-id="d0a2b-119">Run the console application.</span></span>  
  
4. <span data-ttu-id="d0a2b-120">Pendant l’exécution de l’application console, accédez à `http://localhost:8000/diagnostics/feed/?format=atom` ou `http://localhost:8000/diagnostics/feed/?format=rss` à l’aide d’un navigateur compatible RSS.</span><span class="sxs-lookup"><span data-stu-id="d0a2b-120">While the console application is running, navigate to `http://localhost:8000/diagnostics/feed/?format=atom` or `http://localhost:8000/diagnostics/feed/?format=rss` using an RSS-aware browser.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d0a2b-121">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="d0a2b-121">The samples may already be installed on your computer.</span></span> <span data-ttu-id="d0a2b-122">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="d0a2b-122">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="d0a2b-123">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d0a2b-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d0a2b-124">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="d0a2b-124">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\DiagnosticsFeed`  
  
## <a name="see-also"></a><span data-ttu-id="d0a2b-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d0a2b-125">See also</span></span>

- [<span data-ttu-id="d0a2b-126">Modèle de programmation HTTP web WCF</span><span class="sxs-lookup"><span data-stu-id="d0a2b-126">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- [<span data-ttu-id="d0a2b-127">Syndication WCF</span><span class="sxs-lookup"><span data-stu-id="d0a2b-127">WCF Syndication</span></span>](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)

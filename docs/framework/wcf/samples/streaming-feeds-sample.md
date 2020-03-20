---
title: Streaming Feeds, exemple
ms.date: 03/30/2017
ms.assetid: 1f1228c0-daaa-45f0-b93e-c4a158113744
ms.openlocfilehash: 7a887fa1eceac4d8ee323f03fd5bc536bb1dc579
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143965"
---
# <a name="streaming-feeds-sample"></a><span data-ttu-id="426d8-102">Streaming Feeds, exemple</span><span class="sxs-lookup"><span data-stu-id="426d8-102">Streaming Feeds Sample</span></span>
<span data-ttu-id="426d8-103">Cet exemple indique comment gérer des flux de syndication qui contiennent de grandes quantités d'éléments.</span><span class="sxs-lookup"><span data-stu-id="426d8-103">This sample demonstrates how to manage syndication feeds that contain large numbers of items.</span></span> <span data-ttu-id="426d8-104">Sur le serveur, l'exemple décrit comment différer la création d'objets <xref:System.ServiceModel.Syndication.SyndicationItem> individuels dans le flux jusqu'au moment précédant immédiatement l'écriture de l'élément dans le flux de données réseau.</span><span class="sxs-lookup"><span data-stu-id="426d8-104">On the server, the sample demonstrates how to delay the creation of individual <xref:System.ServiceModel.Syndication.SyndicationItem> objects within the feed until immediately before the item is written to the network stream.</span></span>  
  
 <span data-ttu-id="426d8-105">Sur le client, l'exemple décrit comment un module de formatage de flux de syndication personnalisé peut être utilisé pour lire des éléments du flux de réseau, afin que le flux qui est lu ne soit jamais complètement mis en mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="426d8-105">On the client, the sample shows how a custom syndication feed formatter can be used to read individual items from the network stream so that the feed being read is never fully buffered into memory.</span></span>  
  
 <span data-ttu-id="426d8-106">Pour mieux illustrer la fonction de diffusion en continu de l'API de syndication, cet exemple utilise un scénario quelque peu improbable dans lequel le serveur expose un flux qui contient un nombre infini d'éléments.</span><span class="sxs-lookup"><span data-stu-id="426d8-106">To best demonstrate the streaming capability of the syndication API, this sample uses a somewhat unlikely scenario in which the server exposes a feed that contains an infinite number of items.</span></span> <span data-ttu-id="426d8-107">Dans ce cas, le serveur continue à générer de nouveaux éléments dans le flux jusqu'à ce qu'il détermine que le client a lu un nombre spécifié d'éléments du flux (10 par défaut).</span><span class="sxs-lookup"><span data-stu-id="426d8-107">In this case, the server continues generating new items into the feed until it determines that the client has read a specified number of items from the feed (by default, 10).</span></span> <span data-ttu-id="426d8-108">Pour plus de simplicité, le client et le serveur sont tous deux implémentés dans le même processus et utilisent un objet `ItemCounter` partagé pour assurer le suivi du nombre d'éléments que le client a générés.</span><span class="sxs-lookup"><span data-stu-id="426d8-108">For simplicity, both the client and the server are implemented in the same process and use a shared `ItemCounter` object to keep track of how many items the client has produced.</span></span> <span data-ttu-id="426d8-109">Le type `ItemCounter` existe uniquement pour permettre à l’exemple de scénario de se terminer convenablement et n’est pas un élément essentiel du modèle qui est illustré.</span><span class="sxs-lookup"><span data-stu-id="426d8-109">The `ItemCounter` type exists only for the purpose of allowing the sample scenario to terminate cleanly, and is not a core element of the pattern being demonstrated.</span></span>  
  
 <span data-ttu-id="426d8-110">La démonstration utilise des itérateurs Visual `yield return` C (à l’aide de la construction du mot clé).</span><span class="sxs-lookup"><span data-stu-id="426d8-110">The demonstration makes use of Visual C# iterators (using the `yield return` keyword construct).</span></span> <span data-ttu-id="426d8-111">Pour plus d’informations sur les itérateurs, consultez le sujet « Utiliser des itérateurs » sur MSDN.</span><span class="sxs-lookup"><span data-stu-id="426d8-111">For more information about iterators, see the "Using Iterators" topic on MSDN.</span></span>  
  
## <a name="service"></a><span data-ttu-id="426d8-112">Service</span><span class="sxs-lookup"><span data-stu-id="426d8-112">Service</span></span>  
 <span data-ttu-id="426d8-113">Le service implémente un contrat <xref:System.ServiceModel.Web.WebGetAttribute> de base qui se compose d'une opération, comme l'illustre le code suivant.</span><span class="sxs-lookup"><span data-stu-id="426d8-113">The service implements a basic <xref:System.ServiceModel.Web.WebGetAttribute> contract that consists of one operation, as shown in the following code.</span></span>  
  
```csharp  
[ServiceContract]  
interface IStreamingFeedService  
{  
    [WebGet]  
    [OperationContract]  
    Atom10FeedFormatter StreamedFeed();  
}  
```  
  
 <span data-ttu-id="426d8-114">Le service implémente ce contrat en utilisant une classe `ItemGenerator` pour créer un flux potentiellement infini d'instances <xref:System.ServiceModel.Syndication.SyndicationItem> à l'aide d'un itérateur, comme l'illustre le code suivant.</span><span class="sxs-lookup"><span data-stu-id="426d8-114">The service implements this contract by using an `ItemGenerator` class to create a potentially infinite stream of <xref:System.ServiceModel.Syndication.SyndicationItem> instances using an iterator, as shown in the following code.</span></span>  
  
```csharp
class ItemGenerator  
{  
    public IEnumerable<SyndicationItem> GenerateItems()  
    {  
        while (counter.GetCount() < maxItemsRead)  
        {  
            itemsReturned++;  
            yield return CreateNextItem();  
        }  
  
    }  
    ...  
}  
```  
  
 <span data-ttu-id="426d8-115">Lorsque l'implémentation de service crée le flux, la sortie de `ItemGenerator.GenerateItems()` est utilisée à la place d'une collection d'éléments mise en mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="426d8-115">When the service implementation creates the feed, the output of `ItemGenerator.GenerateItems()` is used instead of a buffered collection of items.</span></span>  
  
```csharp
public Atom10FeedFormatter StreamedFeed()  
{  
    SyndicationFeed feed = new SyndicationFeed("Streamed feed", "Feed to test streaming", null);  
    //Generate an infinite stream of items. Both the client and the service share  
    //a reference to the ItemCounter, which allows the sample to terminate  
    //execution after the client has read 10 items from the stream  
    ItemGenerator itemGenerator = new ItemGenerator(this.counter, 10);  
  
    feed.Items = itemGenerator.GenerateItems();  
    return feed.GetAtom10Formatter();  
}  
```  
  
 <span data-ttu-id="426d8-116">En conséquence, le flux d'éléments n'est jamais complètement mis en mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="426d8-116">As a result, the item stream is never fully buffered into memory.</span></span> <span data-ttu-id="426d8-117">Vous pouvez observer ce comportement en `yield return` définissant un `ItemGenerator.GenerateItems()` point d’arrêt sur la déclaration à l’intérieur de la `StreamedFeed()` méthode et en notant que ce point de rupture est rencontré pour la première fois après que le service a retourné le résultat de la méthode.</span><span class="sxs-lookup"><span data-stu-id="426d8-117">You can observe this behavior by setting a breakpoint on the `yield return` statement inside of the `ItemGenerator.GenerateItems()` method and noting that this breakpoint is encountered for the first time after the service has returned the result of the `StreamedFeed()` method.</span></span>  
  
## <a name="client"></a><span data-ttu-id="426d8-118">Client</span><span class="sxs-lookup"><span data-stu-id="426d8-118">Client</span></span>  
 <span data-ttu-id="426d8-119">Le client de cet exemple utilise une implémentation <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> personnalisée qui diffère la matérialisation d'éléments individuels dans le flux au lieu de les mettre en mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="426d8-119">The client in this sample uses a custom <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> implementation that delays the materialization of individual items in the feed instead of buffering them into memory.</span></span> <span data-ttu-id="426d8-120">L'instance `StreamedAtom10FeedFormatter` personnalisée est utilisée comme suit.</span><span class="sxs-lookup"><span data-stu-id="426d8-120">The custom `StreamedAtom10FeedFormatter` instance is used as follows.</span></span>  
  
```csharp  
XmlReader reader = XmlReader.Create("http://localhost:8000/Service/Feeds/StreamedFeed");  
StreamedAtom10FeedFormatter formatter = new StreamedAtom10FeedFormatter(counter);  
  
SyndicationFeed feed = formatter.ReadFrom(reader);  
```  
  
 <span data-ttu-id="426d8-121">Normalement, un appel à <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter.ReadFrom%28System.Xml.XmlReader%29> ne retourne rien jusqu'à ce que le contenu entier du flux ait été lu depuis le réseau et mis en mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="426d8-121">Normally, a call to <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter.ReadFrom%28System.Xml.XmlReader%29> does not return until the entire contents of the feed have been read from the network and buffered into memory.</span></span> <span data-ttu-id="426d8-122">Toutefois, l'objet `StreamedAtom10FeedFormatter` substitue <xref:System.ServiceModel.Syndication.Atom10FeedFormatter.ReadItems%28System.Xml.XmlReader%2CSystem.ServiceModel.Syndication.SyndicationFeed%2CSystem.Boolean%40%29> pour retourner un itérateur au lieu d'une collection mise en mémoire tampon, comme l'illustre le code suivant.</span><span class="sxs-lookup"><span data-stu-id="426d8-122">However, the `StreamedAtom10FeedFormatter` object overrides <xref:System.ServiceModel.Syndication.Atom10FeedFormatter.ReadItems%28System.Xml.XmlReader%2CSystem.ServiceModel.Syndication.SyndicationFeed%2CSystem.Boolean%40%29> to return an iterator instead of a buffered collection, as shown in the following code.</span></span>  
  
```csharp  
protected override IEnumerable<SyndicationItem> ReadItems(XmlReader reader, SyndicationFeed feed, out bool areAllItemsRead)  
{  
    areAllItemsRead = false;  
    return DelayReadItems(reader, feed);  
}  
  
private IEnumerable<SyndicationItem> DelayReadItems(XmlReader reader, SyndicationFeed feed)  
{  
    while (reader.IsStartElement("entry", "http://www.w3.org/2005/Atom"))  
    {  
        yield return this.ReadItem(reader, feed);  
    }  
  
    reader.ReadEndElement();  
}  
```  
  
 <span data-ttu-id="426d8-123">En conséquence, aucun élément n'est lu depuis le réseau avant que l'application cliente qui parcourt les résultats de `ReadItems()` ne soit prête à l'utiliser.</span><span class="sxs-lookup"><span data-stu-id="426d8-123">As a result, each item is not read from the network until the client application traversing the results of `ReadItems()` is ready to use it.</span></span> <span data-ttu-id="426d8-124">Vous pouvez observer ce comportement en `yield return` définissant `StreamedAtom10FeedFormatter.DelayReadItems()` un point d’arrêt sur la déclaration à l’intérieur et en remarquant que ce point d’arrêt est rencontré pour la première fois après l’appel à `ReadFrom()` compléter.</span><span class="sxs-lookup"><span data-stu-id="426d8-124">You can observe this behavior by setting a breakpoint on the `yield return` statement inside of `StreamedAtom10FeedFormatter.DelayReadItems()` and noticing that this breakpoint is encountered for the first time after the call to `ReadFrom()` completes.</span></span>  
  
 <span data-ttu-id="426d8-125">Les instructions suivantes indiquent comment générer et exécuter l'exemple.</span><span class="sxs-lookup"><span data-stu-id="426d8-125">The following instructions show how to build and run the sample.</span></span> <span data-ttu-id="426d8-126">Notez que bien que le serveur cesse de générer des éléments après que le client a lu 10 éléments, la sortie indique que le client lit bien plus que 10 éléments.</span><span class="sxs-lookup"><span data-stu-id="426d8-126">Note that although the server stops generating items after the client has read 10 items, the output shows that the client reads significantly more than 10 items.</span></span> <span data-ttu-id="426d8-127">Cela est dû au fait que la liaison de mise en réseau utilisée par l’exemple transmet les données dans des segments de quatre kilo-octets (Ko).</span><span class="sxs-lookup"><span data-stu-id="426d8-127">This is because the networking binding used by the sample transmits data in four-kilobyte (KB) segments.</span></span> <span data-ttu-id="426d8-128">Le client reçoit donc 4 Ko de données d'éléments avant qu'il ait la possibilité de lire ne serait-ce qu'un élément.</span><span class="sxs-lookup"><span data-stu-id="426d8-128">As such, the client receives 4KB of item data before it has the opportunity to read even one item.</span></span> <span data-ttu-id="426d8-129">Il s'agit du comportement normal (l'envoi de données HTTP diffusées en continu dans des segments de taille raisonnable améliore les performances).</span><span class="sxs-lookup"><span data-stu-id="426d8-129">This is normal behavior (sending streamed HTTP data in reasonably-sized segments increases performance).</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="426d8-130">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="426d8-130">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="426d8-131">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les échantillons de la Fondation De communication Windows.](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)</span><span class="sxs-lookup"><span data-stu-id="426d8-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="426d8-132">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="426d8-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="426d8-133">Pour exécuter l’échantillon dans une configuration mono-ou cross-machine, suivez les instructions dans [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="426d8-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="426d8-134">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="426d8-134">The samples may already be installed on your computer.</span></span> <span data-ttu-id="426d8-135">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="426d8-135">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="426d8-136">Si ce répertoire n’existe pas, rendez-vous sur [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) Samples pour .NET Framework 4 pour](https://www.microsoft.com/download/details.aspx?id=21459) télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] des échantillons.</span><span class="sxs-lookup"><span data-stu-id="426d8-136">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="426d8-137">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="426d8-137">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\StreamingFeeds`  
  
## <a name="see-also"></a><span data-ttu-id="426d8-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="426d8-138">See also</span></span>

- [<span data-ttu-id="426d8-139">Flux de diagnostics autonome</span><span class="sxs-lookup"><span data-stu-id="426d8-139">Stand-Alone Diagnostics Feed</span></span>](../../../../docs/framework/wcf/samples/stand-alone-diagnostics-feed-sample.md)

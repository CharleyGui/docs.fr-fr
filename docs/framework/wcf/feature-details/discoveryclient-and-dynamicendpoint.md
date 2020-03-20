---
title: DiscoveryClient et DynamicEndpoint
ms.date: 03/30/2017
ms.assetid: 7cd418f0-0eab-48d1-a493-7eb907867ec3
ms.openlocfilehash: c6d87a04a6787725ad7c4546650485af932882b0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185182"
---
# <a name="discoveryclient-and-dynamicendpoint"></a><span data-ttu-id="44900-102">DiscoveryClient et DynamicEndpoint</span><span class="sxs-lookup"><span data-stu-id="44900-102">DiscoveryClient and DynamicEndpoint</span></span>
<span data-ttu-id="44900-103"><xref:System.ServiceModel.Discovery.DiscoveryClient> et <xref:System.ServiceModel.Discovery.DynamicEndpoint> sont deux classes utilisées sur le côté client pour rechercher des services.</span><span class="sxs-lookup"><span data-stu-id="44900-103"><xref:System.ServiceModel.Discovery.DiscoveryClient> and <xref:System.ServiceModel.Discovery.DynamicEndpoint> are two classes used on the client side to search for services.</span></span> <span data-ttu-id="44900-104"><xref:System.ServiceModel.Discovery.DiscoveryClient> fournit une liste de services correspondant à un jeu de critères spécifiques et permet de se connecter à ces services.</span><span class="sxs-lookup"><span data-stu-id="44900-104"><xref:System.ServiceModel.Discovery.DiscoveryClient> provides you with a list of services that match a specific set of criteria and allows you to connect to the services.</span></span> <span data-ttu-id="44900-105"><xref:System.ServiceModel.Discovery.DynamicEndpoint> effectue la même opération et, de plus, se connecte automatiquement à l'un des services trouvé dans la liste.</span><span class="sxs-lookup"><span data-stu-id="44900-105"><xref:System.ServiceModel.Discovery.DynamicEndpoint> performs the same operation and in addition, automatically connects to one of the services that was found.</span></span> <span data-ttu-id="44900-106">N'importe quel point de terminaison peut être transformé en <xref:System.ServiceModel.Discovery.DynamicEndpoint>, les critères de recherche peuvent également être ajoutés par configuration, en conséquence <xref:System.ServiceModel.Discovery.DynamicEndpoint> est utile lorsque vous avez besoin de la découverte dans votre solution, mais que vous ne souhaitez pas modifier la logique cliente ; il vous suffit de modifier les points de terminaison.</span><span class="sxs-lookup"><span data-stu-id="44900-106">Any endpoint can be made into a <xref:System.ServiceModel.Discovery.DynamicEndpoint>, the search criteria can also be added in configuration, thus <xref:System.ServiceModel.Discovery.DynamicEndpoint> is useful when you need discovery in your solution but do not want to modify the client logic – you only need to modify the endpoints.</span></span> <span data-ttu-id="44900-107"><xref:System.ServiceModel.Discovery.DiscoveryClient> en revanche peut être utilisé pour obtenir un contrôle plus précis de la recherche.</span><span class="sxs-lookup"><span data-stu-id="44900-107"><xref:System.ServiceModel.Discovery.DiscoveryClient> on the other hand can be used to gain finer control over your search operation.</span></span> <span data-ttu-id="44900-108">Les utilisations et les avantages de chacun sont détaillés ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="44900-108">The uses and benefits of each are elaborated below.</span></span>  
  
## <a name="discoveryclient"></a><span data-ttu-id="44900-109">DiscoveryClient</span><span class="sxs-lookup"><span data-stu-id="44900-109">DiscoveryClient</span></span>  
 <span data-ttu-id="44900-110">La classe <xref:System.ServiceModel.Discovery.DiscoveryClient> définit des méthodes Find synchrones et asynchrones, ainsi que des événements <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> et <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged>.</span><span class="sxs-lookup"><span data-stu-id="44900-110">The <xref:System.ServiceModel.Discovery.DiscoveryClient> defines synchronous and asynchronous Find methods, <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> and <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> events.</span></span>  <span data-ttu-id="44900-111">Elle définit également des méthodes Resolve synchrones et asynchrones et un événement <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveCompleted>.</span><span class="sxs-lookup"><span data-stu-id="44900-111">It also defines synchronous and asynchronous Resolve methods and a <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveCompleted> event.</span></span> <span data-ttu-id="44900-112">Utilisez les méthodes <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> ou <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> pour rechercher des services.</span><span class="sxs-lookup"><span data-stu-id="44900-112">Use the <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> or <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> methods to search for services.</span></span> <span data-ttu-id="44900-113">Ces deux méthodes prennent une instance <xref:System.ServiceModel.Discovery.FindCriteria> qui vous permet de spécifier des noms de types de contrat, des étendues, le nombre maximal de résultats demandés et des règles de correspondance d'étendue.</span><span class="sxs-lookup"><span data-stu-id="44900-113">Both of these methods take a <xref:System.ServiceModel.Discovery.FindCriteria> instance that allows you to specify contract type names, scopes, maximum number of results requested, and scope matching rules.</span></span> <span data-ttu-id="44900-114">Les événements <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> et <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> peuvent être utilisés lors de l'appel de la méthode <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A>.</span><span class="sxs-lookup"><span data-stu-id="44900-114">The <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> and <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> events can be used when calling the <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> method.</span></span> <span data-ttu-id="44900-115"><xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> est déclenché chaque fois que le <xref:System.ServiceModel.Discovery.DiscoveryClient> reçoit une réponse d'un service.</span><span class="sxs-lookup"><span data-stu-id="44900-115"><xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> is fired whenever the <xref:System.ServiceModel.Discovery.DiscoveryClient> receives a response from a service.</span></span> <span data-ttu-id="44900-116">Il peut servir à afficher une barre de progression indiquant la progression de l'opération de recherche.</span><span class="sxs-lookup"><span data-stu-id="44900-116">It can be used to display a progress bar showing the progress of the find operation.</span></span> <span data-ttu-id="44900-117">Il peut également être utilisé pour agir sur les réponses de recherche au moment de leur réception.</span><span class="sxs-lookup"><span data-stu-id="44900-117">It can also be used to act on find responses as they are received.</span></span> <span data-ttu-id="44900-118">L'événement <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> est déclenché à la fin de l'opération de recherche.</span><span class="sxs-lookup"><span data-stu-id="44900-118">The <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> event is fired when the find operation completes.</span></span> <span data-ttu-id="44900-119">Il peut se produire si le nombre maximal de réponses a été reçu ou si la propriété <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> a expiré.</span><span class="sxs-lookup"><span data-stu-id="44900-119">This may happen because the maximum number of responses has been received or if the <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> has elapsed.</span></span> <span data-ttu-id="44900-120">Lorsque l'opération de recherche est terminée, les résultats sont retournés dans une instance <xref:System.ServiceModel.Discovery.FindResponse>.</span><span class="sxs-lookup"><span data-stu-id="44900-120">When the find operation completes the results are returned in a <xref:System.ServiceModel.Discovery.FindResponse> instance.</span></span> <span data-ttu-id="44900-121">L’instance <xref:System.ServiceModel.Discovery.FindResponse> contient une collection d’objets <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> qui contient les adresses, les noms de type de contrat, les extensions, les URI d’écoute et les étendues des services correspondants.</span><span class="sxs-lookup"><span data-stu-id="44900-121">The <xref:System.ServiceModel.Discovery.FindResponse> contains a collection of <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> which contains the addresses, contract type names, extensions, listen URIs, and scopes of the matching services.</span></span> <span data-ttu-id="44900-122">Vous pouvez utiliser ces informations pour vous connecter à l'un des services correspondants et l'appeler.</span><span class="sxs-lookup"><span data-stu-id="44900-122">You can then use this information to connect to and call one of the matching services.</span></span> <span data-ttu-id="44900-123">L’exemple suivant montre comment appeler la méthode System.ServiceModel.Discovery.DiscoveryClient.Find (System.ServiceModel.Discovery.FindCriteria) et utiliser les métadonnées retournées pour appeler le service trouvé.</span><span class="sxs-lookup"><span data-stu-id="44900-123">The following example shows how to call the System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria) method and use the returned metadata to call the found service.</span></span> <span data-ttu-id="44900-124">Un avantage <xref:System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria)> de l’utilisation est que vous pouvez mettre en cache la liste des points de terminaison que vous avez trouvés et les utiliser à une date ultérieure.</span><span class="sxs-lookup"><span data-stu-id="44900-124">A benefit of using <xref:System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria)> is that you can cache the list of endpoints you’ve found and use them at a later time.</span></span> <span data-ttu-id="44900-125">Grâce à ce cache, vous pouvez générer une logique personnalisée pour gérer diverses conditions d'échec.</span><span class="sxs-lookup"><span data-stu-id="44900-125">With this cache, you can build custom logic to handle various failure conditions.</span></span>  
  
```csharp
DiscoveryClient dc = new DiscoveryClient(new UdpDiscoveryEndpoint());  
  
FindCriteria criteria = new FindCriteria(typeof(ICalculatorService));  
FindResponse fr = dc.Find(criteria);  
  
if (fr.Endpoints.Count > 0)  
{  
   EndpointAddress ep = fr.Endpoints[0].Address;  
   CalculatorServiceClient client = new CalculatorServiceClient();  
  
    // Connect to the discovered service endpoint  
   client.Endpoint.Address = endpointAddress;  
   Console.WriteLine("Invoking CalculatorService at {0}", endpointAddress);  
  
   double value1 = 100.00D;  
   double value2 = 15.99D;  
  
   // Call the Add service operation.  
   double result = client.Add(value1, value2);  
   Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
}  
else  
   Console.WriteLine("No matching endpoints found");  
```  
  
 <span data-ttu-id="44900-126">L'exemple suivant montre comment effectuer une opération de recherche de façon asynchrone.</span><span class="sxs-lookup"><span data-stu-id="44900-126">The following example shows how to perform a find operation asynchronously.</span></span>  
  
```csharp
static void FindServiceAsync()  
{  
   DiscoveryClient dc = new DiscoveryClient(new UdpDiscoveryEndpoint());
   dc.FindCompleted += new EventHandler<FindCompletedEventArgs>( discoveryClient_FindCompleted);  
   dc.FindProgressChanged += new EventHandler<FindProgressChangedEventArgs>(discoveryClient_FindProgressChanged);  
   dc.FindAsync(new FindCriteria(typeof(ICalculatorService)));
}
static void discoveryClient_FindProgressChanged(object sender, FindProgressChangedEventArgs e)  
{  
   Console.WriteLine("Found service at: " + e.EndpointDiscoveryMetadata.Address  
}
  
static void discoveryClient_FindCompleted(object sender, FindCompletedEventArgs e)  
{
      if (e.Result.Endpoints.Count > 0)  
            {  
                EndpointAddress ep = e.Result.Endpoints[0].Address;  
                CalculatorServiceClient client = new CalculatorServiceClient();  
  
                // Connect to the discovered service endpoint  
                client.Endpoint.Address = ep;  
                Console.WriteLine("Invoking CalculatorService at {0}", ep);  
  
                double value1 = 100.00D;  
                double value2 = 15.99D;  
  
                double result = client.Add(value1, value2);  
                Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
            }  
            else  
                Console.WriteLine("No matching endpoints found");  
  
        }  
```
  
 <span data-ttu-id="44900-127">Utilisez les méthodes <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> et <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveAsync%28System.ServiceModel.Discovery.ResolveCriteria%29> pour trouver un service en fonction de l'adresse de son point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="44900-127">Use the <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> and <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveAsync%28System.ServiceModel.Discovery.ResolveCriteria%29> methods to locate a service based on its endpoint address.</span></span> <span data-ttu-id="44900-128">C'est utile lorsque l'adresse du point de terminaison n'est pas adressable par réseau.</span><span class="sxs-lookup"><span data-stu-id="44900-128">This is useful when the endpoint address is not network addressable.</span></span> <span data-ttu-id="44900-129">Les méthodes Resolve prennent une instance de <xref:System.ServiceModel.Discovery.ResolveCriteria> qui vous permet de spécifier l’adresse du point de terminaison du service que vous résolvez, la durée maximale de l’opération de résolution et un jeu d’extensions.</span><span class="sxs-lookup"><span data-stu-id="44900-129">The Resolve methods take an instance of <xref:System.ServiceModel.Discovery.ResolveCriteria> which allows you to specify the endpoint address of the service you are resolving, the maximum duration of the resolve operation, and a set of extensions.</span></span> <span data-ttu-id="44900-130">L'exemple suivant montre comment utiliser la méthode <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> pour résoudre un service.</span><span class="sxs-lookup"><span data-stu-id="44900-130">The following example shows how to use the <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> method to resolve a service.</span></span>  
  
```csharp  
DiscoveryClient dc = new DiscoveryClient(new UdpDiscoveryEndpoint());  
ResolveCriteria criteria = new ResolveCriteria(endpointAddress);  
ResolveResponse response = dc.Resolve(criteria);  
EndpointAddress newEp = response.EndpointDiscoveryMetadata.Address;  
```  
  
## <a name="dynamicendpoint"></a><span data-ttu-id="44900-131">DynamicEndpoint</span><span class="sxs-lookup"><span data-stu-id="44900-131">DynamicEndpoint</span></span>  
 <span data-ttu-id="44900-132"><xref:System.ServiceModel.Discovery.DynamicEndpoint>est un critère d’évaluation standard (Pour plus d’informations, voir [Standard Endpoints](../../../../docs/framework/wcf/feature-details/standard-endpoints.md)) qui effectue la découverte et sélectionne automatiquement un service de correspondance.</span><span class="sxs-lookup"><span data-stu-id="44900-132"><xref:System.ServiceModel.Discovery.DynamicEndpoint> is a standard endpoint (For more information, see [Standard Endpoints](../../../../docs/framework/wcf/feature-details/standard-endpoints.md)) which performs discovery and automatically selects a matching service.</span></span> <span data-ttu-id="44900-133">Créez simplement un <xref:System.ServiceModel.Discovery.DynamicEndpoint>, en passant le contrat à rechercher et la liaison à utiliser, et passez l'instance <xref:System.ServiceModel.Discovery.DynamicEndpoint> au client WCF.</span><span class="sxs-lookup"><span data-stu-id="44900-133">Just create a <xref:System.ServiceModel.Discovery.DynamicEndpoint> passing in the contract to search for and the binding to use and pass the <xref:System.ServiceModel.Discovery.DynamicEndpoint> instance to the WCF client.</span></span> <span data-ttu-id="44900-134">L'exemple suivant indique comment créer et utiliser un <xref:System.ServiceModel.Discovery.DynamicEndpoint> pour appeler le service de calculatrice.</span><span class="sxs-lookup"><span data-stu-id="44900-134">The following example shows how to create and use a <xref:System.ServiceModel.Discovery.DynamicEndpoint> to call the calculator service.</span></span> <span data-ttu-id="44900-135">La découverte est effectuée à chaque ouverture du client.</span><span class="sxs-lookup"><span data-stu-id="44900-135">The discovery is performed every time the client is opened.</span></span> <span data-ttu-id="44900-136">Tout point de terminaison défini <xref:System.ServiceModel.Discovery.DynamicEndpoint> dans la `kind ="dynamicEndpoint"` configuration peut également être transformé en un en ajoutant l’attribut à l’élément de configuration de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="44900-136">Any endpoint defined in configuration can also be turned into a <xref:System.ServiceModel.Discovery.DynamicEndpoint> by adding the `kind ="dynamicEndpoint"` attribute to the endpoint configuration element.</span></span>  
  
```csharp  
DynamicEndpoint dynamicEndpoint = new DynamicEndpoint(ContractDescription.GetContract(typeof(ICalculatorService)), new WSHttpBinding());  
CalculatorServiceClient client = new CalculatorServiceClient(dynamicEndpoint);  
  
Console.WriteLine("Invoking CalculatorService");  
Console.WriteLine();  
  
double value1 = 100.00D;  
double value2 = 15.99D;  
  
double result = client.Add(value1, value2);  
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
```  
  
## <a name="see-also"></a><span data-ttu-id="44900-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="44900-137">See also</span></span>

- [<span data-ttu-id="44900-138">Découverte avec étendues</span><span class="sxs-lookup"><span data-stu-id="44900-138">Discovery with Scopes</span></span>](../../../../docs/framework/wcf/samples/discovery-with-scopes-sample.md)
- [<span data-ttu-id="44900-139">Base</span><span class="sxs-lookup"><span data-stu-id="44900-139">Basic</span></span>](../../../../docs/framework/wcf/samples/basic-sample.md)

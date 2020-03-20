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
# <a name="discoveryclient-and-dynamicendpoint"></a>DiscoveryClient et DynamicEndpoint
<xref:System.ServiceModel.Discovery.DiscoveryClient> et <xref:System.ServiceModel.Discovery.DynamicEndpoint> sont deux classes utilisées sur le côté client pour rechercher des services. <xref:System.ServiceModel.Discovery.DiscoveryClient> fournit une liste de services correspondant à un jeu de critères spécifiques et permet de se connecter à ces services. <xref:System.ServiceModel.Discovery.DynamicEndpoint> effectue la même opération et, de plus, se connecte automatiquement à l'un des services trouvé dans la liste. N'importe quel point de terminaison peut être transformé en <xref:System.ServiceModel.Discovery.DynamicEndpoint>, les critères de recherche peuvent également être ajoutés par configuration, en conséquence <xref:System.ServiceModel.Discovery.DynamicEndpoint> est utile lorsque vous avez besoin de la découverte dans votre solution, mais que vous ne souhaitez pas modifier la logique cliente ; il vous suffit de modifier les points de terminaison. <xref:System.ServiceModel.Discovery.DiscoveryClient> en revanche peut être utilisé pour obtenir un contrôle plus précis de la recherche. Les utilisations et les avantages de chacun sont détaillés ci-dessous.  
  
## <a name="discoveryclient"></a>DiscoveryClient  
 La classe <xref:System.ServiceModel.Discovery.DiscoveryClient> définit des méthodes Find synchrones et asynchrones, ainsi que des événements <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> et <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged>.  Elle définit également des méthodes Resolve synchrones et asynchrones et un événement <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveCompleted>. Utilisez les méthodes <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> ou <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> pour rechercher des services. Ces deux méthodes prennent une instance <xref:System.ServiceModel.Discovery.FindCriteria> qui vous permet de spécifier des noms de types de contrat, des étendues, le nombre maximal de résultats demandés et des règles de correspondance d'étendue. Les événements <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> et <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> peuvent être utilisés lors de l'appel de la méthode <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A>. <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> est déclenché chaque fois que le <xref:System.ServiceModel.Discovery.DiscoveryClient> reçoit une réponse d'un service. Il peut servir à afficher une barre de progression indiquant la progression de l'opération de recherche. Il peut également être utilisé pour agir sur les réponses de recherche au moment de leur réception. L'événement <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> est déclenché à la fin de l'opération de recherche. Il peut se produire si le nombre maximal de réponses a été reçu ou si la propriété <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> a expiré. Lorsque l'opération de recherche est terminée, les résultats sont retournés dans une instance <xref:System.ServiceModel.Discovery.FindResponse>. L’instance <xref:System.ServiceModel.Discovery.FindResponse> contient une collection d’objets <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> qui contient les adresses, les noms de type de contrat, les extensions, les URI d’écoute et les étendues des services correspondants. Vous pouvez utiliser ces informations pour vous connecter à l'un des services correspondants et l'appeler. L’exemple suivant montre comment appeler la méthode System.ServiceModel.Discovery.DiscoveryClient.Find (System.ServiceModel.Discovery.FindCriteria) et utiliser les métadonnées retournées pour appeler le service trouvé. Un avantage <xref:System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria)> de l’utilisation est que vous pouvez mettre en cache la liste des points de terminaison que vous avez trouvés et les utiliser à une date ultérieure. Grâce à ce cache, vous pouvez générer une logique personnalisée pour gérer diverses conditions d'échec.  
  
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
  
 L'exemple suivant montre comment effectuer une opération de recherche de façon asynchrone.  
  
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
  
 Utilisez les méthodes <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> et <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveAsync%28System.ServiceModel.Discovery.ResolveCriteria%29> pour trouver un service en fonction de l'adresse de son point de terminaison. C'est utile lorsque l'adresse du point de terminaison n'est pas adressable par réseau. Les méthodes Resolve prennent une instance de <xref:System.ServiceModel.Discovery.ResolveCriteria> qui vous permet de spécifier l’adresse du point de terminaison du service que vous résolvez, la durée maximale de l’opération de résolution et un jeu d’extensions. L'exemple suivant montre comment utiliser la méthode <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> pour résoudre un service.  
  
```csharp  
DiscoveryClient dc = new DiscoveryClient(new UdpDiscoveryEndpoint());  
ResolveCriteria criteria = new ResolveCriteria(endpointAddress);  
ResolveResponse response = dc.Resolve(criteria);  
EndpointAddress newEp = response.EndpointDiscoveryMetadata.Address;  
```  
  
## <a name="dynamicendpoint"></a>DynamicEndpoint  
 <xref:System.ServiceModel.Discovery.DynamicEndpoint>est un critère d’évaluation standard (Pour plus d’informations, voir [Standard Endpoints](../../../../docs/framework/wcf/feature-details/standard-endpoints.md)) qui effectue la découverte et sélectionne automatiquement un service de correspondance. Créez simplement un <xref:System.ServiceModel.Discovery.DynamicEndpoint>, en passant le contrat à rechercher et la liaison à utiliser, et passez l'instance <xref:System.ServiceModel.Discovery.DynamicEndpoint> au client WCF. L'exemple suivant indique comment créer et utiliser un <xref:System.ServiceModel.Discovery.DynamicEndpoint> pour appeler le service de calculatrice. La découverte est effectuée à chaque ouverture du client. Tout point de terminaison défini <xref:System.ServiceModel.Discovery.DynamicEndpoint> dans la `kind ="dynamicEndpoint"` configuration peut également être transformé en un en ajoutant l’attribut à l’élément de configuration de point de terminaison.  
  
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
  
## <a name="see-also"></a>Voir aussi

- [Découverte avec étendues](../../../../docs/framework/wcf/samples/discovery-with-scopes-sample.md)
- [Base](../../../../docs/framework/wcf/samples/basic-sample.md)

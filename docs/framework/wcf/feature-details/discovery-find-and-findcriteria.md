---
title: Recherche de découverte et FindCriteria
ms.date: 03/30/2017
ms.assetid: 99016fa4-1778-495b-b4cc-0e22fbec42c6
ms.openlocfilehash: 1d6a0e3fcca45c3fe57aab84b0f2b6b86fabb404
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599176"
---
# <a name="discovery-find-and-findcriteria"></a>Recherche de découverte et FindCriteria

Une opération de recherche de découverte est lancée par un client pour découvrir un ou plusieurs services ; il s'agit de l'une des principales actions de la découverte. Effectuer une recherche envoie un message Probe WS-Discovery sur le réseau. Les services qui correspondent aux critères spécifiés répondent avec des messages WS-Discovery ProbeMatch. Pour plus d’informations sur les messages de découverte, consultez la [spécification WS-Discovery](http://schemas.xmlsoap.org/ws/2004/10/discovery/ws-discovery.pdf).

## <a name="discoveryclient"></a>DiscoveryClient

La classe <xref:System.ServiceModel.Discovery.DiscoveryClient> fournit le mécanisme pour effectuer des opérations de recherche et permet d'effectuer plus facilement des opérations clientes de découverte. Elle contient une méthode <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A>, qui effectue une recherche synchrone (bloquante), et une méthode <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A>, qui initialise une recherche asynchrone non bloquante. Ces deux méthodes prennent un paramètre <xref:System.ServiceModel.Discovery.FindCriteria> et fournissent les résultats à l'utilisateur via un objet <xref:System.ServiceModel.Discovery.FindResponse>.

## <a name="findcriteria"></a>FindCriteria

<xref:System.ServiceModel.Discovery.FindCriteria> possède plusieurs propriétés, qui peuvent être regroupées en critères de recherche (spécifiant les services recherchés) et critères d'arrêt de la recherche (durée de la recherche). Un <xref:System.ServiceModel.Discovery.FindCriteria> peut contenir plusieurs critères de recherche. Par défaut, le service doit correspondre à tous les composants, autrement, il ne se considère pas comme un service correspondant. Si vous souhaitez rechercher des services qui correspondent uniquement à certains critères, vous pouvez implémenter une logique de recherche personnalisée sur le service ou utiliser plusieurs requêtes.

Les critères de recherche incluent :

- <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElement> : facultatif. Nom de contrat du service recherché et critères habituellement utilisés lors de la recherche d'un service. Si plusieurs noms de contrat sont spécifiés, seuls les points de terminaison de service correspondant à TOUS les contrats répondent. Notez que dans WCF, un point de terminaison ne peut prendre en charge qu’un seul contrat.

- <xref:System.ServiceModel.Discovery.Configuration.ScopeElement> : facultatif. Les étendues sont des URI absolus utilisés pour définir les catégories de points de terminaison de service individuels. Vous pouvez les utiliser dans des scénarios où plusieurs points de terminaison exposent le même contrat, lorsque vous souhaitez rechercher un sous-ensemble des points de terminaison. Si plusieurs étendues sont spécifiées, seuls les points de terminaison de service correspondant à TOUTES les étendues répondent.

- <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchBy%2A> : spécifie l'algorithme de correspondance à utiliser, lors de la comparaison des étendues dans le message Probe avec celles du point de terminaison. Il existe cinq règles de correspondance d'étendues prises en charge :

  - <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByExact?displayProperty=nameWithType> fait une comparaison de chaînes de base sensible à la casse.

  - <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByPrefix?displayProperty=nameWithType>correspond aux segments séparés par « / ». Une recherche `http://contoso/building1` correspond à un service avec une étendue `http://contoso/building/floor1` . Notez qu’elle ne correspond pas `http://contoso/building100` , car les deux derniers segments ne correspondent pas.

  - <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByLdap?displayProperty=nameWithType> établit une correspondance des étendues par segments à l'aide d'une URL LDAP.

  - <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByUuid?displayProperty=nameWithType> établit une correspondance exacte des étendues, à l'aide d'une chaîne UUID.

  - <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByNone?displayProperty=nameWithType> correspond uniquement aux services qui ne spécifient pas d'étendue.

  Si une règle de correspondance d'étendue n'est pas spécifiée, <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByPrefix> est utilisée.

Les critères d'arrêt sont les suivants :

1. <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> : temps d'attente maximal pour que les services répondent sur le réseau. La durée par défaut est de 20 secondes.

2. <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> : nombre maximal de réponses à attendre. Si les réponses <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> sont reçues avant que la propriété <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> expire, l'opération de recherche prend fin.

## <a name="findresponse"></a>FindResponse

<xref:System.ServiceModel.Discovery.FindResponse> a une propriété de collection <xref:System.ServiceModel.Discovery.FindResponse.Endpoints%2A> qui contient toutes les réponses envoyées en mettant en correspondance les services sur le réseau. Si aucun service n’a répondu, la collection est vide. Si un ou plusieurs services ont répondu, chaque réponse est stockée dans un objet <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>, qui contient l'adresse, le contrat et quelques informations supplémentaires sur le service.

L'exemple suivant indique comment effectuer une opération de recherche dans le code.

```csharp
// Create DiscoveryClient
DiscoveryClient discoveryClient = new DiscoveryClient(new UdpDiscoveryEndpoint());

// Create FindCriteria
FindCriteria findCriteria = new FindCriteria(typeof(IPrinterService));
findCriteria.Scopes.Add(new Uri("http://www.contoso.com/building1/floor1"));
findCriteria.Duration = TimeSpan.FromSeconds(10);

// Find ICalculatorService endpoints
FindResponse findResponse = discoveryClient.Find(findCriteria);

Console.WriteLine("Found {0} ICalculatorService endpoint(s).", findResponse.Endpoints.Count)
```

## <a name="see-also"></a>Voir aussi

- [Vue d'ensemble de la découverte WCF](wcf-discovery-overview.md)
- [Utilisation du canal client de découverte](using-the-discovery-client-channel.md)
- [Découverte avec étendues](../samples/discovery-with-scopes-sample.md)
- [De base](../samples/basic-sample.md)

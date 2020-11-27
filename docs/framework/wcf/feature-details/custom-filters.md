---
title: Filtres personnalisés
ms.date: 03/30/2017
ms.assetid: 97cf247d-be0a-4057-bba9-3be5c45029d5
ms.openlocfilehash: b5ec07c2e2a77c7de8b240d21b1eb54bf858b43b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96258424"
---
# <a name="custom-filters"></a><span data-ttu-id="fe3db-102">Filtres personnalisés</span><span class="sxs-lookup"><span data-stu-id="fe3db-102">Custom Filters</span></span>

<span data-ttu-id="fe3db-103">Les filtres personnalisés vous permettent de définir une logique de correspondance qui ne peut pas être réalisée à l'aide des filtres de messages fournis par le système.</span><span class="sxs-lookup"><span data-stu-id="fe3db-103">Custom filters allow you to define matching logic that cannot be accomplished using the system-provided message filters.</span></span> <span data-ttu-id="fe3db-104">Par exemple, vous pouvez créer un filtre personnalisé qui hache un élément de message particulier, puis examine la valeur pour déterminer si le filtre doit retourner la valeur true ou false.</span><span class="sxs-lookup"><span data-stu-id="fe3db-104">For example, you might create a custom filter that hashes a particular message element and then examines the value to determine whether the filter should return true or false.</span></span>  
  
## <a name="implementation"></a><span data-ttu-id="fe3db-105">Implémentation</span><span class="sxs-lookup"><span data-stu-id="fe3db-105">Implementation</span></span>  

 <span data-ttu-id="fe3db-106">Un filtre personnalisé est une implémentation de la classe de base abstraite <xref:System.ServiceModel.Dispatcher.MessageFilter>.</span><span class="sxs-lookup"><span data-stu-id="fe3db-106">A custom filter is an implementation of the <xref:System.ServiceModel.Dispatcher.MessageFilter> abstract base class.</span></span> <span data-ttu-id="fe3db-107">Lors de l'implémentation de votre filtre personnalisé, le constructeur peut éventuellement accepter un paramètre de chaîne unique.</span><span class="sxs-lookup"><span data-stu-id="fe3db-107">When implementing your custom filter, the constructor can optionally accept a single string parameter.</span></span> <span data-ttu-id="fe3db-108">Ce paramètre contient les informations de configuration transmises au constructeur MessageFilter, afin de fournir les valeurs ou la configuration nécessaires au filtre pour effectuer des correspondances lors de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="fe3db-108">This parameter contains the configuration information that is passed to the MessageFilter constructor in order to provide any values or configuration that the filter needs at runtime in order to perform matches.</span></span> <span data-ttu-id="fe3db-109">Par exemple, cela permet de fournir une valeur que le filtre cherche dans le message qui est évalué.</span><span class="sxs-lookup"><span data-stu-id="fe3db-109">For example, this might be used to provide a value that the filter looks for within the message being evaluated.</span></span> <span data-ttu-id="fe3db-110">L'exemple suivant montre une implémentation de base d'un filtre de messages personnalisé qui accepte un paramètre de chaîne :</span><span class="sxs-lookup"><span data-stu-id="fe3db-110">The following example demonstrates a basic implementation of a custom message filter that accepts a string parameter:</span></span>  
  
```csharp  
public class MyMessageFilter: MessageFilter  
{  
    string filterData;  
    public MyMessageFilter(string filterData)  
    {  
        if(string.IsNullOrEmpty(filterData)  
            throw new ArgumentNullException("filterData");  
        this.filterData=filterData;  
    }  
    public override bool Match(System.ServiceModel.Channels.Message message)  
    {  
        ...  
        return retValue;  
    }  
    public override bool Match(System.ServiceModel.Channels.MessageBuffer buffer)  
    {  
        ...  
        return retValue;  
    }  
}  
```  
  
> [!NOTE]
> <span data-ttu-id="fe3db-111">Dans une implémentation réelle, la ou les méthodes match contiennent une logique qui examine le message pour déterminer si ce filtre de messages doit retourner **true** ou **false**.</span><span class="sxs-lookup"><span data-stu-id="fe3db-111">In an actual implementation, the Match method(s) contains logic that will examine the message to determine if this message filter should return **true** or **false**.</span></span>  
  
### <a name="performance"></a><span data-ttu-id="fe3db-112">Performances</span><span class="sxs-lookup"><span data-stu-id="fe3db-112">Performance</span></span>  

 <span data-ttu-id="fe3db-113">Lors de l'implémentation d'un filtre personnalisé, il est important de prendre en considération le temps maximal nécessaire au filtre pour procéder à l'évaluation d'un message.</span><span class="sxs-lookup"><span data-stu-id="fe3db-113">When implementing a custom filter, it is important to take into consideration the maximum length of time required for the filter to complete the evaluation of a message.</span></span> <span data-ttu-id="fe3db-114">Dans la mesure où un message peut être évalué selon plusieurs filtres avant qu'une correspondance ne soit trouvée, il est essentiel de s'assurer que la demande du client n'expirera pas avant l'évaluation de tous les filtres.</span><span class="sxs-lookup"><span data-stu-id="fe3db-114">Since a message may be evaluated against multiple filters before a match is found, it is important to ensure that the client request does not time out before all filters can be evaluated.</span></span> <span data-ttu-id="fe3db-115">Par conséquent, un filtre personnalisé doit contenir uniquement le code nécessaire pour évaluer le contenu ou les attributs d'un message afin de déterminer s'il correspond aux critères de filtre.</span><span class="sxs-lookup"><span data-stu-id="fe3db-115">Therefore a custom filter should contain only the code necessary to evaluate the contents or attributes of a message in order to determine if it matches the filter criteria.</span></span>  
  
 <span data-ttu-id="fe3db-116">En règle générale, lors de l'implémentation d'un filtre personnalisé, il convient d'éviter :</span><span class="sxs-lookup"><span data-stu-id="fe3db-116">In general, you should avoid the following when implementing a custom filter:</span></span>  
  
- <span data-ttu-id="fe3db-117">les E/S, comme l'enregistrement de données sur un disque ou dans une base de données ;</span><span class="sxs-lookup"><span data-stu-id="fe3db-117">IO, such as saving data to disk or to a database.</span></span>  
  
- <span data-ttu-id="fe3db-118">un traitement inutile, comme une boucle sur plusieurs enregistrements d'un document ;</span><span class="sxs-lookup"><span data-stu-id="fe3db-118">Unnecessary processing, such as looping over multiple records in a document.</span></span>  
  
- <span data-ttu-id="fe3db-119">les opérations bloquantes, comme des appels qui impliquent l'obtention d'un verrou sur des ressources partagées ou la réalisation de recherches dans une base de données.</span><span class="sxs-lookup"><span data-stu-id="fe3db-119">Blocking operations, such as calls that involve obtaining a lock on shared resources or performing lookups against a database.</span></span>  
  
 <span data-ttu-id="fe3db-120">Avant d'utiliser un filtre personnalisé dans un environnement de production, vous devez exécuter des tests de performance pour déterminer la durée moyenne nécessaire au filtre pour évaluer un message.</span><span class="sxs-lookup"><span data-stu-id="fe3db-120">Before using a custom filter in a production environment, you should run performance tests to determine the average length of time that the filter takes to evaluate a message.</span></span> <span data-ttu-id="fe3db-121">En combinaison avec le temps de traitement moyen des autres filtres utilisés dans la table de filtres, cela vous permettra de déterminer correctement la valeur maximale de délai d'attente qui doit être spécifiée par l'application cliente.</span><span class="sxs-lookup"><span data-stu-id="fe3db-121">When combined with the average processing time of the other filters used in the filter table, this will allow you to accurately determine the maximum timeout value that should be specified by the client application.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="fe3db-122">Usage</span><span class="sxs-lookup"><span data-stu-id="fe3db-122">Usage</span></span>  

 <span data-ttu-id="fe3db-123">Pour pouvoir utiliser votre filtre personnalisé avec le service de routage, vous devez l’ajouter à la table de filtres en spécifiant une nouvelle entrée de filtre de type « personnalisé », le nom de type complet du filtre de messages et le nom de votre assembly.</span><span class="sxs-lookup"><span data-stu-id="fe3db-123">In order to use your custom filter with the Routing Service, you must add it to the filter table by specifying a new filter entry of type "Custom," the fully qualified type name of the message filter, and the name of your assembly.</span></span>  <span data-ttu-id="fe3db-124">Comme avec d'autres MessageFilters, vous pouvez spécifier le filterData de chaîne qui sera transmis au constructeur de votre filtre personnalisé.</span><span class="sxs-lookup"><span data-stu-id="fe3db-124">As with other MessageFilters, you can specify the string filterData that will be passed to your custom filter’s constructor.</span></span>  
  
 <span data-ttu-id="fe3db-125">Les exemples suivants montrent l'utilisation d'un filtre personnalisé avec le service de routage :</span><span class="sxs-lookup"><span data-stu-id="fe3db-125">The following examples demonstrate using a custom filter with the Routing Service:</span></span>  
  
```xml  
<!--ROUTING SECTION -->  
<routing>  
  <filters>  
    <filter name="CustomFilter1" filterType="Custom"
            customType="CustomAssembly.MyMessageFilter,
            CustomAssembly" filterData="custom data" />  
  </filters>  
  <filterTables>  
    <table name="routingTable1">  
      <filters>  
        <add filterName="CustomFilter1" endpointName="CalculatorService" />  
      </filters>  
    </table>  
  </filterTables>  
</routing>  
```  
  
```csharp  
RoutingConfiguration rc = new RoutingConfiguration();  
List<ServiceEndpoint> endpointList = new List<ServiceEndpoint>();  
endpointList.Add(client);  
rc.FilterTable.Add(new MyMessageFilter("CustomData"), endpointList);  
```

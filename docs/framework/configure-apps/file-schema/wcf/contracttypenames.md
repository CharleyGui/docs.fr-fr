---
title: <contractTypeNames>
ms.date: 03/30/2017
ms.assetid: 5ec5efc6-87f8-4160-9be0-dcd2e01df3df
ms.openlocfilehash: 12f9d4eca02ae3b306646826667c4eafef51a95c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919377"
---
# <a name="contracttypenames"></a><span data-ttu-id="4d953-101">\<contractTypeNames></span><span class="sxs-lookup"><span data-stu-id="4d953-101">\<contractTypeNames></span></span>
<span data-ttu-id="4d953-102">Section de configuration qui spécifie une liste de noms de type de contrat, qui sont les noms de contrat des services recherchés, et les critères généralement utilisés lors de la recherche d'un service.</span><span class="sxs-lookup"><span data-stu-id="4d953-102">A configuration section that specifies a list of contract type names, which are the contract names of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="4d953-103">Si plusieurs noms de contrat sont spécifiés, seuls les points de terminaison de service correspondant à TOUS les contrats répondent.</span><span class="sxs-lookup"><span data-stu-id="4d953-103">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="4d953-104">Notez que dans Windows Communication Foundation (WCF), un point de terminaison ne peut prendre en charge qu’un seul contrat.</span><span class="sxs-lookup"><span data-stu-id="4d953-104">Note that in Windows Communication Foundation (WCF), an endpoint can only support one contract.</span></span>  
  
 <span data-ttu-id="4d953-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="4d953-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="4d953-106">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="4d953-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d953-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4d953-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <dynamicEndpoint>
      <standardEndpoint>
        <discoveryClientSettings discoveryEndpoint="String">
          <findCriteria duration="TimeSpan"
                        maxResults="Integer"
                        scopeMatchBy="Uri">
            <contractTypeNames>
              <add name="String"
                   namespace="String" />
            <contractTypeNames>
            <extensions />
            <scopes>
              <add scope="URI"/>
            </scopes>
          </findCriteria>
        </discoveryClientSettings>
      <standardEndpoint>
    </dynamicEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4d953-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="4d953-108">Attributes and Elements</span></span>  
 <span data-ttu-id="4d953-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="4d953-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4d953-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="4d953-110">Attributes</span></span>  
 <span data-ttu-id="4d953-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="4d953-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4d953-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="4d953-112">Child Elements</span></span>  
  
|<span data-ttu-id="4d953-113">Élément</span><span class="sxs-lookup"><span data-stu-id="4d953-113">Element</span></span>|<span data-ttu-id="4d953-114">Description</span><span class="sxs-lookup"><span data-stu-id="4d953-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4d953-115">\<add></span><span class="sxs-lookup"><span data-stu-id="4d953-115">\<add></span></span>](contracttypenames.md)|<span data-ttu-id="4d953-116">Un nom de type de contrat est une propriété qui fait référence au jeu de critères utilisé en général au cours de la recherche d'un service.</span><span class="sxs-lookup"><span data-stu-id="4d953-116">A contract type name is a property that refers to the set of criteria typically used when searching for a service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4d953-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="4d953-117">Parent Elements</span></span>  
  
|<span data-ttu-id="4d953-118">Élément</span><span class="sxs-lookup"><span data-stu-id="4d953-118">Element</span></span>|<span data-ttu-id="4d953-119">Description</span><span class="sxs-lookup"><span data-stu-id="4d953-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4d953-120">\<findCriteria></span><span class="sxs-lookup"><span data-stu-id="4d953-120">\<findCriteria></span></span>](findcriteria.md)|<span data-ttu-id="4d953-121">Élément de configuration qui fournit un jeu de critères utilisé par une application cliente pour rechercher un service de découverte.</span><span class="sxs-lookup"><span data-stu-id="4d953-121">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="4d953-122">Vous pouvez regrouper les critères dans des critères de recherche (en spécifiant les services que vous recherchez) et rechercher les critères de fin (la durée de la recherche en dernier).</span><span class="sxs-lookup"><span data-stu-id="4d953-122">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4d953-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4d953-123">See also</span></span>

- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
- <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElementCollection>

---
title: <findCriteria>
ms.date: 03/30/2017
ms.assetid: 5454cd19-6bf5-4ba8-94d1-f58d10dc1917
ms.openlocfilehash: eb8ff3905f7696f4c71a79e31db1b8f82c9f0d3b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925583"
---
# <a name="findcriteria"></a><span data-ttu-id="4935b-101">\<findCriteria></span><span class="sxs-lookup"><span data-stu-id="4935b-101">\<findCriteria></span></span>
<span data-ttu-id="4935b-102">Élément de configuration qui fournit un jeu de critères utilisé par une application cliente pour rechercher un service de découverte.</span><span class="sxs-lookup"><span data-stu-id="4935b-102">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="4935b-103">Vous pouvez regrouper les critères dans des critères de recherche (en spécifiant les services que vous recherchez) et rechercher les critères de fin (la durée de la recherche en dernier).</span><span class="sxs-lookup"><span data-stu-id="4935b-103">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>  
  
 <span data-ttu-id="4935b-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="4935b-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="4935b-105">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="4935b-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4935b-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4935b-106">Syntax</span></span>  
  
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
            </contractTypeNames>
            <extensions />
            <scopes>
              <add scope="URI" />
            </scopes>
          </findCriteria>
        </discoveryClientSettings>
      </standardEndpoint>
    </dynamicEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4935b-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="4935b-107">Attributes and Elements</span></span>  
 <span data-ttu-id="4935b-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="4935b-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4935b-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="4935b-109">Attributes</span></span>  
  
|<span data-ttu-id="4935b-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="4935b-110">Attribute</span></span>|<span data-ttu-id="4935b-111">Description</span><span class="sxs-lookup"><span data-stu-id="4935b-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4935b-112">duration</span><span class="sxs-lookup"><span data-stu-id="4935b-112">duration</span></span>|<span data-ttu-id="4935b-113">Valeur Timespan qui spécifie le temps d'attente maximal des réponses envoyées par les services sur le réseau.</span><span class="sxs-lookup"><span data-stu-id="4935b-113">A Timespan value that specifies the maximum time to wait for replies from services on the network.</span></span> <span data-ttu-id="4935b-114">La durée par défaut est de 20 secondes.</span><span class="sxs-lookup"><span data-stu-id="4935b-114">The default duration is 20 seconds.</span></span>|  
|<span data-ttu-id="4935b-115">maxResults</span><span class="sxs-lookup"><span data-stu-id="4935b-115">maxResults</span></span>|<span data-ttu-id="4935b-116">Entier qui spécifie le nombre maximal de réponses à attendre en provenance des services sur un réseau ou sur Internet.</span><span class="sxs-lookup"><span data-stu-id="4935b-116">An integer that specifies the maximum number of replies to wait for, from services on a network or the Internet.</span></span> <span data-ttu-id="4935b-117">Si le nombre maximal de réponses est reçu avant l'écoulement du délai d'attente spécifié dans l'attribut `duration`, l'opération de recherche prend fin.</span><span class="sxs-lookup"><span data-stu-id="4935b-117">If maximum replies are received before the value specified in the `duration` attribute has elapsed, the find operation ends.</span></span>|  
|<span data-ttu-id="4935b-118">scopeMatchBy</span><span class="sxs-lookup"><span data-stu-id="4935b-118">scopeMatchBy</span></span>|<span data-ttu-id="4935b-119">URI qui spécifie l'algorithme de correspondance à utiliser, lors de la comparaison des portées dans le message Probe avec celles du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="4935b-119">A URI that specify the matching algorithm to use while matching the scopes in the Probe message with that of the endpoint.</span></span><br /><br /> <span data-ttu-id="4935b-120">Il existe cinq règles de correspondance de portée prises en charge.</span><span class="sxs-lookup"><span data-stu-id="4935b-120">There are five supported scope-matching rules.</span></span> <span data-ttu-id="4935b-121">Si vous ne spécifiez pas de règle de correspondance de portée, `ScopeMatchByPrefix` est utilisé.</span><span class="sxs-lookup"><span data-stu-id="4935b-121">If you do not specify a scope-matching rule, `ScopeMatchByPrefix` is used.</span></span> <span data-ttu-id="4935b-122">Pour plus d'informations, consultez <xref:System.ServiceModel.Discovery.FindCriteria>.</span><span class="sxs-lookup"><span data-stu-id="4935b-122">For more information on this, see <xref:System.ServiceModel.Discovery.FindCriteria>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4935b-123">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="4935b-123">Child Elements</span></span>  
  
|<span data-ttu-id="4935b-124">Élément</span><span class="sxs-lookup"><span data-stu-id="4935b-124">Element</span></span>|<span data-ttu-id="4935b-125">Description</span><span class="sxs-lookup"><span data-stu-id="4935b-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4935b-126">\<contractTypeNames></span><span class="sxs-lookup"><span data-stu-id="4935b-126">\<contractTypeNames></span></span>](contracttypenames.md)|<span data-ttu-id="4935b-127">Collection d’éléments de configuration qui contiennent les noms des types de contrat de service de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="4935b-127">A collection of configuration elements that contain the names of workflow service contract types.</span></span>|  
|<span data-ttu-id="4935b-128">\<> des extensions \<de findCriteria ></span><span class="sxs-lookup"><span data-stu-id="4935b-128">\<extensions> of \<findCriteria></span></span>|<span data-ttu-id="4935b-129">Collection d'objets d'élément XML qui fournissent des extensions.</span><span class="sxs-lookup"><span data-stu-id="4935b-129">A collection of XML element objects that provide extensions.</span></span>|  
|[<span data-ttu-id="4935b-130">\<scopes></span><span class="sxs-lookup"><span data-stu-id="4935b-130">\<scopes></span></span>](scopes.md)|<span data-ttu-id="4935b-131">Collection d’objets qui contiennent des URI absolus utilisés pendant une opération de recherche afin de localiser des services ou un service particulier.</span><span class="sxs-lookup"><span data-stu-id="4935b-131">A collection of objects that contain absolute URIs that are used during a find operation to locate a specific service or services.</span></span><br /><br /> <span data-ttu-id="4935b-132">Si le service particulier est trouvé, une correspondance réussie est établie entre l'URI de service et l'URI de portée, parfois à l'aide de règles de portée qui gèrent les problèmes de correspondance.</span><span class="sxs-lookup"><span data-stu-id="4935b-132">If the specific service is found, a successful match has been made between the service URI and the Scope URI, sometimes with the help of scope rules that handle complications of matching.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4935b-133">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="4935b-133">Parent Elements</span></span>  
  
|<span data-ttu-id="4935b-134">Élément</span><span class="sxs-lookup"><span data-stu-id="4935b-134">Element</span></span>|<span data-ttu-id="4935b-135">Description</span><span class="sxs-lookup"><span data-stu-id="4935b-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4935b-136">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="4935b-136">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="4935b-137">Contient les paramètres requis par une application pour participer au processus de découverte de service en tant que client.</span><span class="sxs-lookup"><span data-stu-id="4935b-137">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4935b-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4935b-138">See also</span></span>

- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>

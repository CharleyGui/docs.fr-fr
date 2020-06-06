---
title: <findCriteria>
ms.date: 03/30/2017
ms.assetid: 5454cd19-6bf5-4ba8-94d1-f58d10dc1917
ms.openlocfilehash: 44e068ee205bc5e04382164e7ab00716b2c07dcf
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855168"
---
# \<findCriteria>
<span data-ttu-id="1bc4c-101">Élément de configuration qui fournit un jeu de critères utilisé par une application cliente pour rechercher un service de découverte.</span><span class="sxs-lookup"><span data-stu-id="1bc4c-101">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="1bc4c-102">Les critères peuvent être regroupés en critères de recherche (spécifiant les services recherchés) et critères d'arrêt de la recherche (durée de la recherche).</span><span class="sxs-lookup"><span data-stu-id="1bc4c-102">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dynamicEndpoint>**](dynamicendpoint.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<standardEndpoint>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<discoveryClientSettings>**](discoveryclientsettings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<findCriteria>**  
  
## <a name="syntax"></a><span data-ttu-id="1bc4c-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1bc4c-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1bc4c-104">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="1bc4c-104">Attributes and Elements</span></span>  
 <span data-ttu-id="1bc4c-105">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="1bc4c-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1bc4c-106">Attributs</span><span class="sxs-lookup"><span data-stu-id="1bc4c-106">Attributes</span></span>  
  
|<span data-ttu-id="1bc4c-107">Attribut</span><span class="sxs-lookup"><span data-stu-id="1bc4c-107">Attribute</span></span>|<span data-ttu-id="1bc4c-108">Description</span><span class="sxs-lookup"><span data-stu-id="1bc4c-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1bc4c-109">duration</span><span class="sxs-lookup"><span data-stu-id="1bc4c-109">duration</span></span>|<span data-ttu-id="1bc4c-110">Valeur Timespan qui spécifie le temps d'attente maximal des réponses envoyées par les services sur le réseau.</span><span class="sxs-lookup"><span data-stu-id="1bc4c-110">A Timespan value that specifies the maximum time to wait for replies from services on the network.</span></span> <span data-ttu-id="1bc4c-111">La durée par défaut est de 20 secondes.</span><span class="sxs-lookup"><span data-stu-id="1bc4c-111">The default duration is 20 seconds.</span></span>|  
|<span data-ttu-id="1bc4c-112">maxResults</span><span class="sxs-lookup"><span data-stu-id="1bc4c-112">maxResults</span></span>|<span data-ttu-id="1bc4c-113">Entier qui spécifie le nombre maximal de réponses à attendre en provenance des services sur un réseau ou sur Internet.</span><span class="sxs-lookup"><span data-stu-id="1bc4c-113">An integer that specifies the maximum number of replies to wait for, from services on a network or the Internet.</span></span> <span data-ttu-id="1bc4c-114">Si le nombre maximal de réponses est reçu avant l'écoulement du délai d'attente spécifié dans l'attribut `duration`, l'opération de recherche prend fin.</span><span class="sxs-lookup"><span data-stu-id="1bc4c-114">If maximum replies are received before the value specified in the `duration` attribute has elapsed, the find operation ends.</span></span>|  
|<span data-ttu-id="1bc4c-115">scopeMatchBy</span><span class="sxs-lookup"><span data-stu-id="1bc4c-115">scopeMatchBy</span></span>|<span data-ttu-id="1bc4c-116">URI qui spécifie l'algorithme de correspondance à utiliser, lors de la comparaison des portées dans le message Probe avec celles du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="1bc4c-116">A URI that specify the matching algorithm to use while matching the scopes in the Probe message with that of the endpoint.</span></span><br /><br /> <span data-ttu-id="1bc4c-117">Il existe cinq règles de correspondance de portée prises en charge.</span><span class="sxs-lookup"><span data-stu-id="1bc4c-117">There are five supported scope-matching rules.</span></span> <span data-ttu-id="1bc4c-118">Si vous ne spécifiez pas de règle de correspondance de portée, `ScopeMatchByPrefix` est utilisé.</span><span class="sxs-lookup"><span data-stu-id="1bc4c-118">If you do not specify a scope-matching rule, `ScopeMatchByPrefix` is used.</span></span> <span data-ttu-id="1bc4c-119">Pour plus d'informations, consultez <xref:System.ServiceModel.Discovery.FindCriteria>.</span><span class="sxs-lookup"><span data-stu-id="1bc4c-119">For more information on this, see <xref:System.ServiceModel.Discovery.FindCriteria>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1bc4c-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="1bc4c-120">Child Elements</span></span>  
  
|<span data-ttu-id="1bc4c-121">Élément</span><span class="sxs-lookup"><span data-stu-id="1bc4c-121">Element</span></span>|<span data-ttu-id="1bc4c-122">Description</span><span class="sxs-lookup"><span data-stu-id="1bc4c-122">Description</span></span>|  
|-------------|-----------------|  
|[\<contractTypeNames>](contracttypenames.md)|<span data-ttu-id="1bc4c-123">Collection d’éléments de configuration qui contiennent les noms des types de contrat de service de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="1bc4c-123">A collection of configuration elements that contain the names of workflow service contract types.</span></span>|  
|<span data-ttu-id="1bc4c-124">\<extensions> de \<findCriteria></span><span class="sxs-lookup"><span data-stu-id="1bc4c-124">\<extensions> of \<findCriteria></span></span>|<span data-ttu-id="1bc4c-125">Collection d'objets d'élément XML qui fournissent des extensions.</span><span class="sxs-lookup"><span data-stu-id="1bc4c-125">A collection of XML element objects that provide extensions.</span></span>|  
|[\<scopes>](scopes.md)|<span data-ttu-id="1bc4c-126">Collection d’objets qui contiennent des URI absolus utilisés pendant une opération de recherche afin de localiser des services ou un service particulier.</span><span class="sxs-lookup"><span data-stu-id="1bc4c-126">A collection of objects that contain absolute URIs that are used during a find operation to locate a specific service or services.</span></span><br /><br /> <span data-ttu-id="1bc4c-127">Si le service particulier est trouvé, une correspondance réussie est établie entre l'URI de service et l'URI de portée, parfois à l'aide de règles de portée qui gèrent les problèmes de correspondance.</span><span class="sxs-lookup"><span data-stu-id="1bc4c-127">If the specific service is found, a successful match has been made between the service URI and the Scope URI, sometimes with the help of scope rules that handle complications of matching.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1bc4c-128">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="1bc4c-128">Parent Elements</span></span>  
  
|<span data-ttu-id="1bc4c-129">Élément</span><span class="sxs-lookup"><span data-stu-id="1bc4c-129">Element</span></span>|<span data-ttu-id="1bc4c-130">Description</span><span class="sxs-lookup"><span data-stu-id="1bc4c-130">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="1bc4c-131">Contient les paramètres requis par une application pour participer au processus de découverte de service en tant que client.</span><span class="sxs-lookup"><span data-stu-id="1bc4c-131">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1bc4c-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1bc4c-132">See also</span></span>

- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>

---
title: <discoveryClientSettings>
ms.date: 03/30/2017
ms.assetid: 02e1b823-a8bb-4074-90d5-8599f71e8f9d
ms.openlocfilehash: 2783796166d56be3d4983ab09a60d62491699fe3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925862"
---
# <a name="discoveryclientsettings"></a><span data-ttu-id="0436b-101">\<discoveryClientSettings></span><span class="sxs-lookup"><span data-stu-id="0436b-101">\<discoveryClientSettings></span></span>
<span data-ttu-id="0436b-102">Contient les paramètres requis par une application pour participer au processus de découverte de service en tant que client.</span><span class="sxs-lookup"><span data-stu-id="0436b-102">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>  
  
<span data-ttu-id="0436b-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="0436b-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="0436b-104">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="0436b-104">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0436b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0436b-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0436b-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="0436b-106">Attributes and Elements</span></span>  
 <span data-ttu-id="0436b-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="0436b-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0436b-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="0436b-108">Attributes</span></span>  
  
|<span data-ttu-id="0436b-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="0436b-109">Attribute</span></span>|<span data-ttu-id="0436b-110">Description</span><span class="sxs-lookup"><span data-stu-id="0436b-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0436b-111">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="0436b-111">discoveryEndpoint</span></span>|<span data-ttu-id="0436b-112">Chaîne qui contient le nom du point de terminaison de découverte permettant à une application cliente de rechercher automatiquement un service détectable et de trouver son adresse au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="0436b-112">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0436b-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="0436b-113">Child Elements</span></span>  
  
|<span data-ttu-id="0436b-114">Élément</span><span class="sxs-lookup"><span data-stu-id="0436b-114">Element</span></span>|<span data-ttu-id="0436b-115">Description</span><span class="sxs-lookup"><span data-stu-id="0436b-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0436b-116">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="0436b-116">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="0436b-117">Élément de configuration qui fournit un jeu de critères utilisé par une application cliente pour rechercher un service de découverte.</span><span class="sxs-lookup"><span data-stu-id="0436b-117">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="0436b-118">Vous pouvez regrouper les critères dans des critères de recherche (en spécifiant les services que vous recherchez) et rechercher les critères de fin (la durée de la recherche en dernier).</span><span class="sxs-lookup"><span data-stu-id="0436b-118">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0436b-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="0436b-119">Parent Elements</span></span>  
  
|<span data-ttu-id="0436b-120">Élément</span><span class="sxs-lookup"><span data-stu-id="0436b-120">Element</span></span>|<span data-ttu-id="0436b-121">Description</span><span class="sxs-lookup"><span data-stu-id="0436b-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0436b-122">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="0436b-122">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="0436b-123">Définit un point de terminaison standard qui contient des informations pour permettre à une application de fonctionner en tant que programme client qui peut rechercher l'adresse du point de terminaison de manière dynamique au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="0436b-123">Defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0436b-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0436b-124">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>
- <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientSettingsElement>

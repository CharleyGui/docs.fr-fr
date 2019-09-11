---
title: <discoveryClientSettings>
ms.date: 03/30/2017
ms.assetid: 02e1b823-a8bb-4074-90d5-8599f71e8f9d
ms.openlocfilehash: 929c5d170bfc27160e3e15b8bd2f9f26e0ed8975
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855414"
---
# <a name="discoveryclientsettings"></a><span data-ttu-id="951f1-101">\<discoveryClientSettings></span><span class="sxs-lookup"><span data-stu-id="951f1-101">\<discoveryClientSettings></span></span>
<span data-ttu-id="951f1-102">Contient les paramètres requis par une application pour participer au processus de découverte de service en tant que client.</span><span class="sxs-lookup"><span data-stu-id="951f1-102">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>  
  
<span data-ttu-id="951f1-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="951f1-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="951f1-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="951f1-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="951f1-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<standardEndpoints >** ](standardendpoints.md)</span><span class="sxs-lookup"><span data-stu-id="951f1-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)</span></span>\
<span data-ttu-id="951f1-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<dynamicEndpoint >** ](dynamicendpoint.md)</span><span class="sxs-lookup"><span data-stu-id="951f1-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dynamicEndpoint>**](dynamicendpoint.md)</span></span>\
<span data-ttu-id="951f1-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<standardEndpoint >** </span><span class="sxs-lookup"><span data-stu-id="951f1-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<standardEndpoint>**</span></span>\
<span data-ttu-id="951f1-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<discoveryClientSettings >**</span><span class="sxs-lookup"><span data-stu-id="951f1-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<discoveryClientSettings>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="951f1-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="951f1-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="951f1-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="951f1-110">Attributes and Elements</span></span>  
 <span data-ttu-id="951f1-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="951f1-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="951f1-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="951f1-112">Attributes</span></span>  
  
|<span data-ttu-id="951f1-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="951f1-113">Attribute</span></span>|<span data-ttu-id="951f1-114">Description</span><span class="sxs-lookup"><span data-stu-id="951f1-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="951f1-115">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="951f1-115">discoveryEndpoint</span></span>|<span data-ttu-id="951f1-116">Chaîne qui contient le nom du point de terminaison de découverte permettant à une application cliente de rechercher automatiquement un service détectable et de trouver son adresse au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="951f1-116">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="951f1-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="951f1-117">Child Elements</span></span>  
  
|<span data-ttu-id="951f1-118">Élément</span><span class="sxs-lookup"><span data-stu-id="951f1-118">Element</span></span>|<span data-ttu-id="951f1-119">Description</span><span class="sxs-lookup"><span data-stu-id="951f1-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="951f1-120">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="951f1-120">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="951f1-121">Élément de configuration qui fournit un jeu de critères utilisé par une application cliente pour rechercher un service de découverte.</span><span class="sxs-lookup"><span data-stu-id="951f1-121">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="951f1-122">Vous pouvez regrouper les critères dans des critères de recherche (en spécifiant les services que vous recherchez) et rechercher les critères de fin (la durée de la recherche en dernier).</span><span class="sxs-lookup"><span data-stu-id="951f1-122">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="951f1-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="951f1-123">Parent Elements</span></span>  
  
|<span data-ttu-id="951f1-124">Élément</span><span class="sxs-lookup"><span data-stu-id="951f1-124">Element</span></span>|<span data-ttu-id="951f1-125">Description</span><span class="sxs-lookup"><span data-stu-id="951f1-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="951f1-126">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="951f1-126">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="951f1-127">Définit un point de terminaison standard qui contient des informations pour permettre à une application de fonctionner en tant que programme client qui peut rechercher l'adresse du point de terminaison de manière dynamique au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="951f1-127">Defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="951f1-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="951f1-128">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>
- <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientSettingsElement>

---
title: <discoveryClientSettings>
ms.date: 03/30/2017
ms.assetid: 02e1b823-a8bb-4074-90d5-8599f71e8f9d
ms.openlocfilehash: 6e3f273af807eb362f005fef63246013ecc88581
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91192241"
---
# \<discoveryClientSettings>

<span data-ttu-id="9aa1a-101">Contient les paramètres requis par une application pour participer au processus de découverte de service en tant que client.</span><span class="sxs-lookup"><span data-stu-id="9aa1a-101">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dynamicEndpoint>**](dynamicendpoint.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<standardEndpoint>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<discoveryClientSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="9aa1a-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9aa1a-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9aa1a-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="9aa1a-103">Attributes and Elements</span></span>  

 <span data-ttu-id="9aa1a-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="9aa1a-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9aa1a-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="9aa1a-105">Attributes</span></span>  
  
|<span data-ttu-id="9aa1a-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="9aa1a-106">Attribute</span></span>|<span data-ttu-id="9aa1a-107">Description</span><span class="sxs-lookup"><span data-stu-id="9aa1a-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9aa1a-108">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="9aa1a-108">discoveryEndpoint</span></span>|<span data-ttu-id="9aa1a-109">Chaîne qui contient le nom du point de terminaison de découverte permettant à une application cliente de rechercher automatiquement un service détectable et de trouver son adresse au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="9aa1a-109">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9aa1a-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="9aa1a-110">Child Elements</span></span>  
  
|<span data-ttu-id="9aa1a-111">Élément</span><span class="sxs-lookup"><span data-stu-id="9aa1a-111">Element</span></span>|<span data-ttu-id="9aa1a-112">Description</span><span class="sxs-lookup"><span data-stu-id="9aa1a-112">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="9aa1a-113">Élément de configuration qui fournit un jeu de critères utilisé par une application cliente pour rechercher un service de découverte.</span><span class="sxs-lookup"><span data-stu-id="9aa1a-113">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="9aa1a-114">Les critères peuvent être regroupés en critères de recherche (spécifiant les services recherchés) et critères d'arrêt de la recherche (durée de la recherche).</span><span class="sxs-lookup"><span data-stu-id="9aa1a-114">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9aa1a-115">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="9aa1a-115">Parent Elements</span></span>  
  
|<span data-ttu-id="9aa1a-116">Élément</span><span class="sxs-lookup"><span data-stu-id="9aa1a-116">Element</span></span>|<span data-ttu-id="9aa1a-117">Description</span><span class="sxs-lookup"><span data-stu-id="9aa1a-117">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="9aa1a-118">Définit un point de terminaison standard qui contient des informations pour permettre à une application de fonctionner en tant que programme client qui peut rechercher l'adresse du point de terminaison de manière dynamique au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="9aa1a-118">Defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9aa1a-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9aa1a-119">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>
- <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientSettingsElement>

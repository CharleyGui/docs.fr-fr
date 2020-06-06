---
title: <discoveryClientSettings>
ms.date: 03/30/2017
ms.assetid: 02e1b823-a8bb-4074-90d5-8599f71e8f9d
ms.openlocfilehash: 929c5d170bfc27160e3e15b8bd2f9f26e0ed8975
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855414"
---
# \<discoveryClientSettings>
<span data-ttu-id="6ed87-101">Contient les paramètres requis par une application pour participer au processus de découverte de service en tant que client.</span><span class="sxs-lookup"><span data-stu-id="6ed87-101">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dynamicEndpoint>**](dynamicendpoint.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<standardEndpoint>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<discoveryClientSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="6ed87-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6ed87-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6ed87-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="6ed87-103">Attributes and Elements</span></span>  
 <span data-ttu-id="6ed87-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="6ed87-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6ed87-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="6ed87-105">Attributes</span></span>  
  
|<span data-ttu-id="6ed87-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="6ed87-106">Attribute</span></span>|<span data-ttu-id="6ed87-107">Description</span><span class="sxs-lookup"><span data-stu-id="6ed87-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6ed87-108">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="6ed87-108">discoveryEndpoint</span></span>|<span data-ttu-id="6ed87-109">Chaîne qui contient le nom du point de terminaison de découverte permettant à une application cliente de rechercher automatiquement un service détectable et de trouver son adresse au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="6ed87-109">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6ed87-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="6ed87-110">Child Elements</span></span>  
  
|<span data-ttu-id="6ed87-111">Élément</span><span class="sxs-lookup"><span data-stu-id="6ed87-111">Element</span></span>|<span data-ttu-id="6ed87-112">Description</span><span class="sxs-lookup"><span data-stu-id="6ed87-112">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="6ed87-113">Élément de configuration qui fournit un jeu de critères utilisé par une application cliente pour rechercher un service de découverte.</span><span class="sxs-lookup"><span data-stu-id="6ed87-113">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="6ed87-114">Les critères peuvent être regroupés en critères de recherche (spécifiant les services recherchés) et critères d'arrêt de la recherche (durée de la recherche).</span><span class="sxs-lookup"><span data-stu-id="6ed87-114">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6ed87-115">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="6ed87-115">Parent Elements</span></span>  
  
|<span data-ttu-id="6ed87-116">Élément</span><span class="sxs-lookup"><span data-stu-id="6ed87-116">Element</span></span>|<span data-ttu-id="6ed87-117">Description</span><span class="sxs-lookup"><span data-stu-id="6ed87-117">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="6ed87-118">Définit un point de terminaison standard qui contient des informations pour permettre à une application de fonctionner en tant que programme client qui peut rechercher l'adresse du point de terminaison de manière dynamique au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="6ed87-118">Defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6ed87-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6ed87-119">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>
- <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientSettingsElement>

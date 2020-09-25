---
title: <discoveryClient>
ms.date: 03/30/2017
ms.assetid: a78f74c3-1152-4149-ab29-3f12d316caeb
ms.openlocfilehash: af9cf127652f1e12ae57948f9b4a6a26285af793
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91192254"
---
# \<discoveryClient>

<span data-ttu-id="70eb2-101">Élément de configuration qui crée une liaison personnalisée permettant à une application cliente de rechercher automatiquement un service détectable et de trouver son adresse au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="70eb2-101">A configuration element for creating a custom binding that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<discoveryClient>**  
  
## <a name="syntax"></a><span data-ttu-id="70eb2-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="70eb2-102">Syntax</span></span>  
  
```xml  
<discoveryClient discoveryEndpoint="String">
  <findCriteria duration="TimeSpan"
                maxResults="Integer"
                scopeMatchBy="Uri">
    <contractTypeNames>
      <add name="String"
           namespace="String" />
    </contractTypeNames>
    <extensions />
    <scopes>
      <add scope="URI"/>
    </scopes>
  </findCriteria>
</discoveryClient>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="70eb2-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="70eb2-103">Attributes and Elements</span></span>  

 <span data-ttu-id="70eb2-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="70eb2-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="70eb2-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="70eb2-105">Attributes</span></span>  
  
|<span data-ttu-id="70eb2-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="70eb2-106">Attribute</span></span>|<span data-ttu-id="70eb2-107">Description</span><span class="sxs-lookup"><span data-stu-id="70eb2-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="70eb2-108">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="70eb2-108">discoveryEndpoint</span></span>|<span data-ttu-id="70eb2-109">Chaîne qui contient le nom du point de terminaison de découverte permettant à une application cliente de rechercher automatiquement un service détectable et de trouver son adresse au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="70eb2-109">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="70eb2-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="70eb2-110">Child Elements</span></span>  
  
|<span data-ttu-id="70eb2-111">Élément</span><span class="sxs-lookup"><span data-stu-id="70eb2-111">Element</span></span>|<span data-ttu-id="70eb2-112">Description</span><span class="sxs-lookup"><span data-stu-id="70eb2-112">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="70eb2-113">Élément de configuration qui fournit un jeu de critères utilisé par une application cliente pour rechercher un service de découverte.</span><span class="sxs-lookup"><span data-stu-id="70eb2-113">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="70eb2-114">Les critères peuvent être regroupés en critères de recherche (spécifiant les services recherchés) et critères d'arrêt de la recherche (durée de la recherche).</span><span class="sxs-lookup"><span data-stu-id="70eb2-114">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="70eb2-115">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="70eb2-115">Parent Elements</span></span>  
  
|<span data-ttu-id="70eb2-116">Élément</span><span class="sxs-lookup"><span data-stu-id="70eb2-116">Element</span></span>|<span data-ttu-id="70eb2-117">Description</span><span class="sxs-lookup"><span data-stu-id="70eb2-117">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="70eb2-118">Définit toutes les fonctions de liaison d’une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="70eb2-118">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="70eb2-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="70eb2-119">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>
- <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientElement>

---
title: <discoveryClient>
ms.date: 03/30/2017
ms.assetid: a78f74c3-1152-4149-ab29-3f12d316caeb
ms.openlocfilehash: 71305720cad0206ec3dabb1863e2f1cd72eb85f0
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73739032"
---
# \<discoveryClient>
<span data-ttu-id="c0357-101">Élément de configuration qui crée une liaison personnalisée permettant à une application cliente de rechercher automatiquement un service détectable et de trouver son adresse au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="c0357-101">A configuration element for creating a custom binding that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<discoveryClient>**  
  
## <a name="syntax"></a><span data-ttu-id="c0357-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c0357-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c0357-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="c0357-103">Attributes and Elements</span></span>  
 <span data-ttu-id="c0357-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="c0357-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c0357-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="c0357-105">Attributes</span></span>  
  
|<span data-ttu-id="c0357-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="c0357-106">Attribute</span></span>|<span data-ttu-id="c0357-107">Description</span><span class="sxs-lookup"><span data-stu-id="c0357-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c0357-108">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="c0357-108">discoveryEndpoint</span></span>|<span data-ttu-id="c0357-109">Chaîne qui contient le nom du point de terminaison de découverte permettant à une application cliente de rechercher automatiquement un service détectable et de trouver son adresse au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="c0357-109">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c0357-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="c0357-110">Child Elements</span></span>  
  
|<span data-ttu-id="c0357-111">Élément</span><span class="sxs-lookup"><span data-stu-id="c0357-111">Element</span></span>|<span data-ttu-id="c0357-112">Description</span><span class="sxs-lookup"><span data-stu-id="c0357-112">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="c0357-113">Élément de configuration qui fournit un jeu de critères utilisé par une application cliente pour rechercher un service de découverte.</span><span class="sxs-lookup"><span data-stu-id="c0357-113">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="c0357-114">Les critères peuvent être regroupés en critères de recherche (spécifiant les services recherchés) et critères d'arrêt de la recherche (durée de la recherche).</span><span class="sxs-lookup"><span data-stu-id="c0357-114">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c0357-115">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="c0357-115">Parent Elements</span></span>  
  
|<span data-ttu-id="c0357-116">Élément</span><span class="sxs-lookup"><span data-stu-id="c0357-116">Element</span></span>|<span data-ttu-id="c0357-117">Description</span><span class="sxs-lookup"><span data-stu-id="c0357-117">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="c0357-118">Définit toutes les fonctions de liaison d’une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="c0357-118">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c0357-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c0357-119">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>
- <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientElement>

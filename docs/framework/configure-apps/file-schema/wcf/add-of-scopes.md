---
title: <add> de <scopes>
ms.date: 03/30/2017
ms.assetid: 0563a7d8-fc84-4c85-9066-af32665857c2
ms.openlocfilehash: bcde6b18c34dccf1716c809dddeb45b1b4da90f0
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398308"
---
# <a name="add-of-scopes"></a><span data-ttu-id="4a477-102">\<add> de \<scopes></span><span class="sxs-lookup"><span data-stu-id="4a477-102">\<add> of \<scopes></span></span>
<span data-ttu-id="4a477-103">Ajoute un URI de portée personnalisé qui permet de filtrer les points de terminaison de service pendant la requête.</span><span class="sxs-lookup"><span data-stu-id="4a477-103">Adds a custom scope Uri that can be used to filter service endpoints during query.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointDiscovery>**](endpointdiscovery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<scopes>**](scopes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="4a477-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4a477-104">Syntax</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="String">
      <endpointDiscovery enable="Boolean">
        <scopes>
          <add scope="URI" />
        </scopes>
      </endpointDiscovery>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4a477-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="4a477-105">Attributes and Elements</span></span>  
 <span data-ttu-id="4a477-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="4a477-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4a477-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="4a477-107">Attributes</span></span>  
  
|<span data-ttu-id="4a477-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="4a477-108">Attribute</span></span>|<span data-ttu-id="4a477-109">Description</span><span class="sxs-lookup"><span data-stu-id="4a477-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4a477-110">scope</span><span class="sxs-lookup"><span data-stu-id="4a477-110">scope</span></span>|<span data-ttu-id="4a477-111">URI qui contient les informations de portée du point de terminaison à utiliser lors de la mise en correspondance des critères de recherche des services.</span><span class="sxs-lookup"><span data-stu-id="4a477-111">A URI that contains scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4a477-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="4a477-112">Child Elements</span></span>  
 <span data-ttu-id="4a477-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="4a477-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4a477-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="4a477-114">Parent Elements</span></span>  
  
|<span data-ttu-id="4a477-115">Élément</span><span class="sxs-lookup"><span data-stu-id="4a477-115">Element</span></span>|<span data-ttu-id="4a477-116">Description</span><span class="sxs-lookup"><span data-stu-id="4a477-116">Description</span></span>|  
|-------------|-----------------|  
|[\<scopes>](scopes.md)|<span data-ttu-id="4a477-117">Contient une collection d’éléments de configuration qui spécifient des URI de portée personnalisés à utiliser pour filtrer des points de terminaison de service pendant la requête.</span><span class="sxs-lookup"><span data-stu-id="4a477-117">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4a477-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4a477-118">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>

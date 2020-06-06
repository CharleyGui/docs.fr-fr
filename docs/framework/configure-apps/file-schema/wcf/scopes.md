---
title: <scopes>
ms.date: 03/30/2017
ms.assetid: 9a0dd3ce-e383-4ac3-b7be-7d604388304a
ms.openlocfilehash: 57e9e19025db5e1fa588f073fdf30de09837a25d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399937"
---
# \<scopes>
<span data-ttu-id="12a52-101">Contient une collection d’éléments de configuration qui spécifient des URI de portée personnalisés à utiliser pour filtrer des points de terminaison de service pendant la requête.</span><span class="sxs-lookup"><span data-stu-id="12a52-101">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointDiscovery>**](endpointdiscovery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<scopes>**  
  
## <a name="syntax"></a><span data-ttu-id="12a52-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="12a52-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="12a52-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="12a52-103">Attributes and Elements</span></span>  
 <span data-ttu-id="12a52-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="12a52-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="12a52-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="12a52-105">Attributes</span></span>  
 <span data-ttu-id="12a52-106">Aucun.</span><span class="sxs-lookup"><span data-stu-id="12a52-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="12a52-107">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="12a52-107">Child Elements</span></span>  
  
|<span data-ttu-id="12a52-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="12a52-108">Attribute</span></span>|<span data-ttu-id="12a52-109">Description</span><span class="sxs-lookup"><span data-stu-id="12a52-109">Description</span></span>|  
|---------------|-----------------|  
|[\<add>](add-of-scopes.md)|<span data-ttu-id="12a52-110">Ajoute les informations de portée du point de terminaison à utiliser lors de la mise en correspondance des critères de recherche des services.</span><span class="sxs-lookup"><span data-stu-id="12a52-110">Adds the scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="12a52-111">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="12a52-111">Parent Elements</span></span>  
  
|<span data-ttu-id="12a52-112">Élément</span><span class="sxs-lookup"><span data-stu-id="12a52-112">Element</span></span>|<span data-ttu-id="12a52-113">Description</span><span class="sxs-lookup"><span data-stu-id="12a52-113">Description</span></span>|  
|-------------|-----------------|  
|[\<endpointDiscovery>](endpointdiscovery.md)|<span data-ttu-id="12a52-114">Spécifie les différents paramètres de découverte d’un point de terminaison, tels que la fonctionnalité de découverte, les portées et toutes les extensions personnalisées de ses métadonnées.</span><span class="sxs-lookup"><span data-stu-id="12a52-114">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="12a52-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="12a52-115">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>

---
title: <baseAddresses>
ms.date: 03/30/2017
ms.assetid: 78918102-2898-46e0-9ea8-6b8afe65603e
ms.openlocfilehash: 9b3ed6b39f1743249925d5b6d9a47845c87983bc
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850206"
---
# \<baseAddresses>
<span data-ttu-id="09a14-101">Représente une collection d’éléments `baseAddress`, qui sont les adresses de base d’un hôte de service dans un environnement auto-hébergé.</span><span class="sxs-lookup"><span data-stu-id="09a14-101">Represents a collection of `baseAddress` elements, which are base addresses for a service host in a self-hosted environment.</span></span> <span data-ttu-id="09a14-102">Si une adresse de base est présente, les points de terminaison peuvent être configurés avec des adresses relatives à l'adresse de base.</span><span class="sxs-lookup"><span data-stu-id="09a14-102">If a base address is present, endpoints can be configured with addresses relative to the base address.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<host>**](host.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<baseAddresses>**  
  
## <a name="syntax"></a><span data-ttu-id="09a14-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="09a14-103">Syntax</span></span>  
  
```xml  
<baseAddresses>
  <add baseAddress="string" />
</baseAddresses>
```  
  
## <a name="type"></a><span data-ttu-id="09a14-104">Type</span><span class="sxs-lookup"><span data-stu-id="09a14-104">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="09a14-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="09a14-105">Attributes and Elements</span></span>  
 <span data-ttu-id="09a14-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="09a14-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="09a14-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="09a14-107">Attributes</span></span>  
 <span data-ttu-id="09a14-108">Aucun.</span><span class="sxs-lookup"><span data-stu-id="09a14-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="09a14-109">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="09a14-109">Child Elements</span></span>  
  
|<span data-ttu-id="09a14-110">Élément</span><span class="sxs-lookup"><span data-stu-id="09a14-110">Element</span></span>|<span data-ttu-id="09a14-111">Description</span><span class="sxs-lookup"><span data-stu-id="09a14-111">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-baseaddresses.md)|<span data-ttu-id="09a14-112">Élément de configuration qui spécifie les adresses de base utilisées par l'hôte de service.</span><span class="sxs-lookup"><span data-stu-id="09a14-112">A configuration element that specifies the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="09a14-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="09a14-113">Parent Elements</span></span>  
  
|<span data-ttu-id="09a14-114">Élément</span><span class="sxs-lookup"><span data-stu-id="09a14-114">Element</span></span>|<span data-ttu-id="09a14-115">Description</span><span class="sxs-lookup"><span data-stu-id="09a14-115">Description</span></span>|  
|-------------|-----------------|  
|[\<host>](host.md)|<span data-ttu-id="09a14-116">Élément de configuration qui spécifie des paramètres pour un hôte de service.</span><span class="sxs-lookup"><span data-stu-id="09a14-116">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="09a14-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="09a14-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [<span data-ttu-id="09a14-118">Hosting</span><span class="sxs-lookup"><span data-stu-id="09a14-118">Hosting</span></span>](../../../wcf/feature-details/hosting.md)

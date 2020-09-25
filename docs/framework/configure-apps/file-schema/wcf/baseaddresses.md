---
title: <baseAddresses>
ms.date: 03/30/2017
ms.assetid: 78918102-2898-46e0-9ea8-6b8afe65603e
ms.openlocfilehash: 3b6cebd178ac5cd30fa034bd961d2d08075771d2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201536"
---
# \<baseAddresses>

<span data-ttu-id="79be6-101">Représente une collection d’éléments `baseAddress`, qui sont les adresses de base d’un hôte de service dans un environnement auto-hébergé.</span><span class="sxs-lookup"><span data-stu-id="79be6-101">Represents a collection of `baseAddress` elements, which are base addresses for a service host in a self-hosted environment.</span></span> <span data-ttu-id="79be6-102">Si une adresse de base est présente, les points de terminaison peuvent être configurés avec des adresses relatives à l'adresse de base.</span><span class="sxs-lookup"><span data-stu-id="79be6-102">If a base address is present, endpoints can be configured with addresses relative to the base address.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<host>**](host.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<baseAddresses>**  
  
## <a name="syntax"></a><span data-ttu-id="79be6-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="79be6-103">Syntax</span></span>  
  
```xml  
<baseAddresses>
  <add baseAddress="string" />
</baseAddresses>
```  
  
## <a name="type"></a><span data-ttu-id="79be6-104">Type</span><span class="sxs-lookup"><span data-stu-id="79be6-104">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="79be6-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="79be6-105">Attributes and Elements</span></span>  

 <span data-ttu-id="79be6-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="79be6-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="79be6-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="79be6-107">Attributes</span></span>  

 <span data-ttu-id="79be6-108">Aucun.</span><span class="sxs-lookup"><span data-stu-id="79be6-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="79be6-109">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="79be6-109">Child Elements</span></span>  
  
|<span data-ttu-id="79be6-110">Élément</span><span class="sxs-lookup"><span data-stu-id="79be6-110">Element</span></span>|<span data-ttu-id="79be6-111">Description</span><span class="sxs-lookup"><span data-stu-id="79be6-111">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-baseaddresses.md)|<span data-ttu-id="79be6-112">Élément de configuration qui spécifie les adresses de base utilisées par l'hôte de service.</span><span class="sxs-lookup"><span data-stu-id="79be6-112">A configuration element that specifies the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="79be6-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="79be6-113">Parent Elements</span></span>  
  
|<span data-ttu-id="79be6-114">Élément</span><span class="sxs-lookup"><span data-stu-id="79be6-114">Element</span></span>|<span data-ttu-id="79be6-115">Description</span><span class="sxs-lookup"><span data-stu-id="79be6-115">Description</span></span>|  
|-------------|-----------------|  
|[\<host>](host.md)|<span data-ttu-id="79be6-116">Élément de configuration qui spécifie des paramètres pour un hôte de service.</span><span class="sxs-lookup"><span data-stu-id="79be6-116">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="79be6-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="79be6-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [<span data-ttu-id="79be6-118">Hosting</span><span class="sxs-lookup"><span data-stu-id="79be6-118">Hosting</span></span>](../../../wcf/feature-details/hosting.md)

---
title: <services>
ms.date: 03/30/2017
ms.assetid: 80d76ba9-2058-48ad-9b91-5e4be7e5c113
ms.openlocfilehash: b8cb5075ba41bed5a22b152a231c7213b326a62f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153714"
---
# \<services>

<span data-ttu-id="a5da3-101">Les services sont définis dans la section `services` du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="a5da3-101">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="a5da3-102">Chacun dispose de sa propre section de configuration de `service`.</span><span class="sxs-lookup"><span data-stu-id="a5da3-102">Each service has its own `service` configuration section.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<services>**  
  
## <a name="syntax"></a><span data-ttu-id="a5da3-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a5da3-103">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service>
    </service>
  </services>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a5da3-104">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a5da3-104">Attributes and Elements</span></span>  

 <span data-ttu-id="a5da3-105">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="a5da3-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a5da3-106">Attributs</span><span class="sxs-lookup"><span data-stu-id="a5da3-106">Attributes</span></span>  

 <span data-ttu-id="a5da3-107">None</span><span class="sxs-lookup"><span data-stu-id="a5da3-107">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a5da3-108">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a5da3-108">Child Elements</span></span>  
  
|<span data-ttu-id="a5da3-109">Élément</span><span class="sxs-lookup"><span data-stu-id="a5da3-109">Element</span></span>|<span data-ttu-id="a5da3-110">Description</span><span class="sxs-lookup"><span data-stu-id="a5da3-110">Description</span></span>|  
|-------------|-----------------|  
|[\<service>](service.md)|<span data-ttu-id="a5da3-111">Définissez le contrat de service, le comportement et les points de terminaison du service particulier.</span><span class="sxs-lookup"><span data-stu-id="a5da3-111">Define the service contract, behavior, and endpoints of the particular service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a5da3-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a5da3-112">Parent Elements</span></span>  
  
|<span data-ttu-id="a5da3-113">Élément</span><span class="sxs-lookup"><span data-stu-id="a5da3-113">Element</span></span>|<span data-ttu-id="a5da3-114">Description</span><span class="sxs-lookup"><span data-stu-id="a5da3-114">Description</span></span>|  
|-------------|-----------------|  
|[\<system.serviceModel>](system-servicemodel.md)|<span data-ttu-id="a5da3-115">Élément racine de tous les éléments de configuration Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="a5da3-115">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a5da3-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a5da3-116">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServicesSection>

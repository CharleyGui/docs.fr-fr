---
title: <services>
ms.date: 03/30/2017
ms.assetid: 80d76ba9-2058-48ad-9b91-5e4be7e5c113
ms.openlocfilehash: 1f9cb6c95fa14a5b8a55cc561699e2a07e1dc80c
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399597"
---
# <a name="services"></a><span data-ttu-id="482b1-101">\<services></span><span class="sxs-lookup"><span data-stu-id="482b1-101">\<services></span></span>
<span data-ttu-id="482b1-102">Les services sont définis dans la section `services` du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="482b1-102">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="482b1-103">Chacun dispose de sa propre section de configuration de `service`.</span><span class="sxs-lookup"><span data-stu-id="482b1-103">Each service has its own `service` configuration section.</span></span>  
  
<span data-ttu-id="482b1-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="482b1-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="482b1-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="482b1-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="482b1-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<services >**</span><span class="sxs-lookup"><span data-stu-id="482b1-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<services>**</span></span>  
## <a name="syntax"></a><span data-ttu-id="482b1-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="482b1-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service>
    </service>
  </services>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="482b1-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="482b1-108">Attributes and Elements</span></span>  
 <span data-ttu-id="482b1-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="482b1-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="482b1-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="482b1-110">Attributes</span></span>  
 <span data-ttu-id="482b1-111">Aucun</span><span class="sxs-lookup"><span data-stu-id="482b1-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="482b1-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="482b1-112">Child Elements</span></span>  
  
|<span data-ttu-id="482b1-113">Élément</span><span class="sxs-lookup"><span data-stu-id="482b1-113">Element</span></span>|<span data-ttu-id="482b1-114">Description</span><span class="sxs-lookup"><span data-stu-id="482b1-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="482b1-115">\<service></span><span class="sxs-lookup"><span data-stu-id="482b1-115">\<service></span></span>](service.md)|<span data-ttu-id="482b1-116">Définissez le contrat de service, le comportement et les points de terminaison du service particulier.</span><span class="sxs-lookup"><span data-stu-id="482b1-116">Define the service contract, behavior, and endpoints of the particular service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="482b1-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="482b1-117">Parent Elements</span></span>  
  
|<span data-ttu-id="482b1-118">Élément</span><span class="sxs-lookup"><span data-stu-id="482b1-118">Element</span></span>|<span data-ttu-id="482b1-119">Description</span><span class="sxs-lookup"><span data-stu-id="482b1-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="482b1-120">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="482b1-120">\<system.serviceModel></span></span>](system-servicemodel.md)|<span data-ttu-id="482b1-121">Élément racine de tous les éléments de configuration Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="482b1-121">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="482b1-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="482b1-122">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServicesSection>

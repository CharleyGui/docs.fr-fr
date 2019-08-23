---
title: <privacyNoticeAt>
ms.date: 03/30/2017
ms.assetid: 4cc96942-4eb9-4241-b2fd-45aa239915e8
ms.openlocfilehash: f7349bf61082c5d8e5bd4249e01b8835a1861cb9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934254"
---
# <a name="privacynoticeat"></a><span data-ttu-id="facd7-101">\<privacyNoticeAt></span><span class="sxs-lookup"><span data-stu-id="facd7-101">\<privacyNoticeAt></span></span>
<span data-ttu-id="facd7-102">Représente un élément de configuration qui spécifie un avis de confidentialité utilisé dans la liaison `wsFederationHttp`.</span><span class="sxs-lookup"><span data-stu-id="facd7-102">Represents a configuration element that specifies a privacy notice used in `wsFederationHttp` binding.</span></span>  
  
 <span data-ttu-id="facd7-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="facd7-103">\<system.serviceModel></span></span>  
<span data-ttu-id="facd7-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="facd7-104">\<bindings></span></span>  
<span data-ttu-id="facd7-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="facd7-105">\<customBinding></span></span>  
<span data-ttu-id="facd7-106">\<binding></span><span class="sxs-lookup"><span data-stu-id="facd7-106">\<binding></span></span>  
<span data-ttu-id="facd7-107">\<privacyNotice></span><span class="sxs-lookup"><span data-stu-id="facd7-107">\<privacyNotice></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="facd7-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="facd7-108">Syntax</span></span>  
  
```xml  
<privacyNotice url="String"
               version="Integer" />
```  
  
## <a name="type"></a><span data-ttu-id="facd7-109">Type</span><span class="sxs-lookup"><span data-stu-id="facd7-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="facd7-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="facd7-110">Attributes and Elements</span></span>  
 <span data-ttu-id="facd7-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="facd7-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="facd7-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="facd7-112">Attributes</span></span>  
  
|<span data-ttu-id="facd7-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="facd7-113">Attribute</span></span>|<span data-ttu-id="facd7-114">Description</span><span class="sxs-lookup"><span data-stu-id="facd7-114">Description</span></span>|  
|---------------|-----------------|  
|`url`|<span data-ttu-id="facd7-115">Chaîne qui spécifie l'URI dans lequel l'information préalable de confidentialité est située.</span><span class="sxs-lookup"><span data-stu-id="facd7-115">A string that specifies the URI at which the privacy notice is located.</span></span>|  
|`version`|<span data-ttu-id="facd7-116">Entier qui spécifie la version de cet avis de confidentialité.</span><span class="sxs-lookup"><span data-stu-id="facd7-116">An integer that specifies the version of this privacy notice.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="facd7-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="facd7-117">Child Elements</span></span>  
 <span data-ttu-id="facd7-118">Aucun.</span><span class="sxs-lookup"><span data-stu-id="facd7-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="facd7-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="facd7-119">Parent Elements</span></span>  
  
|<span data-ttu-id="facd7-120">Élément</span><span class="sxs-lookup"><span data-stu-id="facd7-120">Element</span></span>|<span data-ttu-id="facd7-121">Description</span><span class="sxs-lookup"><span data-stu-id="facd7-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="facd7-122">\<binding></span><span class="sxs-lookup"><span data-stu-id="facd7-122">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="facd7-123">Définit toutes les fonctions de liaison d’une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="facd7-123">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="facd7-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="facd7-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.PrivacyNoticeElement>
- <xref:System.ServiceModel.Channels.PrivacyNoticeBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="facd7-125">Liaisons</span><span class="sxs-lookup"><span data-stu-id="facd7-125">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="facd7-126">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="facd7-126">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="facd7-127">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="facd7-127">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="facd7-128">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="facd7-128">\<customBinding></span></span>](custombinding.md)

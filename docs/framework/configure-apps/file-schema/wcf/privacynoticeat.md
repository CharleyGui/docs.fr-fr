---
title: <privacyNoticeAt>
ms.date: 03/30/2017
ms.assetid: 4cc96942-4eb9-4241-b2fd-45aa239915e8
ms.openlocfilehash: 624b52c0618362f48063c8f7e7c53c5a68d7de8f
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400029"
---
# <a name="privacynoticeat"></a><span data-ttu-id="7a340-101">\<privacyNoticeAt></span><span class="sxs-lookup"><span data-stu-id="7a340-101">\<privacyNoticeAt></span></span>
<span data-ttu-id="7a340-102">Représente un élément de configuration qui spécifie un avis de confidentialité utilisé dans la liaison `wsFederationHttp`.</span><span class="sxs-lookup"><span data-stu-id="7a340-102">Represents a configuration element that specifies a privacy notice used in `wsFederationHttp` binding.</span></span>  
  
<span data-ttu-id="7a340-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="7a340-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7a340-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="7a340-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="7a340-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<liaisons >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="7a340-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="7a340-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="7a340-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="7a340-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de liaison**</span><span class="sxs-lookup"><span data-stu-id="7a340-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="7a340-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<privacyNotice >**</span><span class="sxs-lookup"><span data-stu-id="7a340-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<privacyNotice>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a340-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7a340-109">Syntax</span></span>  
  
```xml  
<privacyNotice url="String"
               version="Integer" />
```  
  
## <a name="type"></a><span data-ttu-id="7a340-110">Type</span><span class="sxs-lookup"><span data-stu-id="7a340-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7a340-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="7a340-111">Attributes and Elements</span></span>  
 <span data-ttu-id="7a340-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="7a340-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7a340-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="7a340-113">Attributes</span></span>  
  
|<span data-ttu-id="7a340-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="7a340-114">Attribute</span></span>|<span data-ttu-id="7a340-115">Description</span><span class="sxs-lookup"><span data-stu-id="7a340-115">Description</span></span>|  
|---------------|-----------------|  
|`url`|<span data-ttu-id="7a340-116">Chaîne qui spécifie l'URI dans lequel l'information préalable de confidentialité est située.</span><span class="sxs-lookup"><span data-stu-id="7a340-116">A string that specifies the URI at which the privacy notice is located.</span></span>|  
|`version`|<span data-ttu-id="7a340-117">Entier qui spécifie la version de cet avis de confidentialité.</span><span class="sxs-lookup"><span data-stu-id="7a340-117">An integer that specifies the version of this privacy notice.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7a340-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="7a340-118">Child Elements</span></span>  
 <span data-ttu-id="7a340-119">Aucun.</span><span class="sxs-lookup"><span data-stu-id="7a340-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7a340-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="7a340-120">Parent Elements</span></span>  
  
|<span data-ttu-id="7a340-121">Élément</span><span class="sxs-lookup"><span data-stu-id="7a340-121">Element</span></span>|<span data-ttu-id="7a340-122">Description</span><span class="sxs-lookup"><span data-stu-id="7a340-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7a340-123">\<binding></span><span class="sxs-lookup"><span data-stu-id="7a340-123">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="7a340-124">Définit toutes les fonctions de liaison d’une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="7a340-124">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7a340-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7a340-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.PrivacyNoticeElement>
- <xref:System.ServiceModel.Channels.PrivacyNoticeBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="7a340-126">Liaisons</span><span class="sxs-lookup"><span data-stu-id="7a340-126">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="7a340-127">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="7a340-127">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="7a340-128">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="7a340-128">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="7a340-129">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="7a340-129">\<customBinding></span></span>](custombinding.md)

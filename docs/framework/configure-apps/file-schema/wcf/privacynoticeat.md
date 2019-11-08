---
title: <privacyNoticeAt>
ms.date: 03/30/2017
ms.assetid: 4cc96942-4eb9-4241-b2fd-45aa239915e8
ms.openlocfilehash: 2ff70d3a8636970434582e417e4549ab6b433fc1
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738767"
---
# <a name="privacynoticeat"></a><span data-ttu-id="9f06e-101">\<privacyNoticeAt ></span><span class="sxs-lookup"><span data-stu-id="9f06e-101">\<privacyNoticeAt></span></span>
<span data-ttu-id="9f06e-102">Représente un élément de configuration qui spécifie un avis de confidentialité utilisé dans la liaison `wsFederationHttp`.</span><span class="sxs-lookup"><span data-stu-id="9f06e-102">Represents a configuration element that specifies a privacy notice used in `wsFederationHttp` binding.</span></span>  
  
<span data-ttu-id="9f06e-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="9f06e-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="9f06e-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="9f06e-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="9f06e-105">&nbsp;&nbsp;&nbsp;&nbsp;[**liaisons**](bindings.md)\<</span><span class="sxs-lookup"><span data-stu-id="9f06e-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\</span></span>
<span data-ttu-id="9f06e-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="9f06e-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="9f06e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\< \**\**</span><span class="sxs-lookup"><span data-stu-id="9f06e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\</span></span>
<span data-ttu-id="9f06e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**privacyNotice >**</span><span class="sxs-lookup"><span data-stu-id="9f06e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<privacyNotice>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f06e-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9f06e-109">Syntax</span></span>  
  
```xml  
<privacyNotice url="String"
               version="Integer" />
```  
  
## <a name="type"></a><span data-ttu-id="9f06e-110">Tapez</span><span class="sxs-lookup"><span data-stu-id="9f06e-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9f06e-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="9f06e-111">Attributes and Elements</span></span>  
 <span data-ttu-id="9f06e-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="9f06e-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9f06e-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="9f06e-113">Attributes</span></span>  
  
|<span data-ttu-id="9f06e-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="9f06e-114">Attribute</span></span>|<span data-ttu-id="9f06e-115">Description</span><span class="sxs-lookup"><span data-stu-id="9f06e-115">Description</span></span>|  
|---------------|-----------------|  
|`url`|<span data-ttu-id="9f06e-116">Chaîne qui spécifie l'URI dans lequel l'information préalable de confidentialité est située.</span><span class="sxs-lookup"><span data-stu-id="9f06e-116">A string that specifies the URI at which the privacy notice is located.</span></span>|  
|`version`|<span data-ttu-id="9f06e-117">Entier qui spécifie la version de cet avis de confidentialité.</span><span class="sxs-lookup"><span data-stu-id="9f06e-117">An integer that specifies the version of this privacy notice.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9f06e-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="9f06e-118">Child Elements</span></span>  
 <span data-ttu-id="9f06e-119">Aucun(e).</span><span class="sxs-lookup"><span data-stu-id="9f06e-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9f06e-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="9f06e-120">Parent Elements</span></span>  
  
|<span data-ttu-id="9f06e-121">Élément</span><span class="sxs-lookup"><span data-stu-id="9f06e-121">Element</span></span>|<span data-ttu-id="9f06e-122">Description</span><span class="sxs-lookup"><span data-stu-id="9f06e-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9f06e-123">liaison de \<</span><span class="sxs-lookup"><span data-stu-id="9f06e-123">\<binding></span></span>](bindings.md)|<span data-ttu-id="9f06e-124">Définit toutes les fonctions de liaison d’une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="9f06e-124">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9f06e-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9f06e-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.PrivacyNoticeElement>
- <xref:System.ServiceModel.Channels.PrivacyNoticeBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="9f06e-126">Liaisons</span><span class="sxs-lookup"><span data-stu-id="9f06e-126">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="9f06e-127">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="9f06e-127">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="9f06e-128">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="9f06e-128">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="9f06e-129">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="9f06e-129">\<customBinding></span></span>](custombinding.md)

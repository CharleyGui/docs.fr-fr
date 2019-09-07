---
title: <pnrpPeerResolver>
ms.date: 03/30/2017
ms.assetid: c1b34f3b-68e5-4911-a367-de49fb61dbc6
ms.openlocfilehash: d7c6c8efa971fb60f0257cc1c74ceda72e31cb84
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400053"
---
# <a name="pnrppeerresolver"></a><span data-ttu-id="22c6d-101">\<pnrpPeerResolver></span><span class="sxs-lookup"><span data-stu-id="22c6d-101">\<pnrpPeerResolver></span></span>
<span data-ttu-id="22c6d-102">Spécifie que le programme de résolution PNRP (Peer Name Resolution Protocol) doit être utilisé comme un programme de résolution.</span><span class="sxs-lookup"><span data-stu-id="22c6d-102">Specifies that the PNRP (Peer Name Resolution Protocol) resolver is to be used as a resolver.</span></span> <span data-ttu-id="22c6d-103">Cet élément est facultatif parce que PNRP est le programme de résolution par défaut.</span><span class="sxs-lookup"><span data-stu-id="22c6d-103">This element is optional because PNRP is the default resolver.</span></span>  
  
<span data-ttu-id="22c6d-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="22c6d-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="22c6d-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="22c6d-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="22c6d-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<liaisons >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="22c6d-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="22c6d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="22c6d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="22c6d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de liaison**</span><span class="sxs-lookup"><span data-stu-id="22c6d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="22c6d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<pnrpResolver >**</span><span class="sxs-lookup"><span data-stu-id="22c6d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<pnrpResolver>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22c6d-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="22c6d-110">Syntax</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="22c6d-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="22c6d-111">Attributes and Elements</span></span>  
 <span data-ttu-id="22c6d-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="22c6d-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="22c6d-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="22c6d-113">Attributes</span></span>  
  
|<span data-ttu-id="22c6d-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="22c6d-114">Attribute</span></span>|<span data-ttu-id="22c6d-115">Description</span><span class="sxs-lookup"><span data-stu-id="22c6d-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="22c6d-116">resolverType</span><span class="sxs-lookup"><span data-stu-id="22c6d-116">resolverType</span></span>|<span data-ttu-id="22c6d-117">Chaîne qui spécifie le programme de résolution à utiliser.</span><span class="sxs-lookup"><span data-stu-id="22c6d-117">A string that specifies the resolver to be used.</span></span> <span data-ttu-id="22c6d-118">Cet attribut est facultatif.</span><span class="sxs-lookup"><span data-stu-id="22c6d-118">This attribute is optional.</span></span> <span data-ttu-id="22c6d-119">S'il n'est pas défini ou s'il a pour valeur une chaîne vide, PNRP est utilisé.</span><span class="sxs-lookup"><span data-stu-id="22c6d-119">If it is not set, or if it is set to an empty string, PNRP is used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="22c6d-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="22c6d-120">Child Elements</span></span>  
 <span data-ttu-id="22c6d-121">Aucun</span><span class="sxs-lookup"><span data-stu-id="22c6d-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="22c6d-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="22c6d-122">Parent Elements</span></span>  
  
|<span data-ttu-id="22c6d-123">Élément</span><span class="sxs-lookup"><span data-stu-id="22c6d-123">Element</span></span>|<span data-ttu-id="22c6d-124">Description</span><span class="sxs-lookup"><span data-stu-id="22c6d-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="22c6d-125">\<binding></span><span class="sxs-lookup"><span data-stu-id="22c6d-125">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="22c6d-126">Définit toutes les fonctions de liaison d’une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="22c6d-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="22c6d-127">Exemples</span><span class="sxs-lookup"><span data-stu-id="22c6d-127">Example</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="see-also"></a><span data-ttu-id="22c6d-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="22c6d-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>
- <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="22c6d-129">Liaisons</span><span class="sxs-lookup"><span data-stu-id="22c6d-129">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="22c6d-130">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="22c6d-130">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="22c6d-131">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="22c6d-131">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="22c6d-132">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="22c6d-132">\<customBinding></span></span>](custombinding.md)
- [<span data-ttu-id="22c6d-133">Programmes de résolution d’homologue</span><span class="sxs-lookup"><span data-stu-id="22c6d-133">Peer Resolvers</span></span>](../../../wcf/feature-details/peer-resolvers.md)

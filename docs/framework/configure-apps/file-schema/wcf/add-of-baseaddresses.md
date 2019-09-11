---
title: <add> de <baseAddresses>
ms.date: 03/30/2017
ms.assetid: 1bd7426f-5f4f-43fc-b8e9-de842219aa32
ms.openlocfilehash: d75142209ad8706d0cad5ce188d9d991a5e881bc
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850583"
---
# <a name="add-of-baseaddresses"></a><span data-ttu-id="c0796-102">\<Ajouter > de \<la > baseAddresses</span><span class="sxs-lookup"><span data-stu-id="c0796-102">\<add> of \<baseAddresses></span></span>
<span data-ttu-id="c0796-103">Représente un élément de configuration qui spécifie les adresses de base utilisées par l'hôte de service.</span><span class="sxs-lookup"><span data-stu-id="c0796-103">Represents a configuration element that specifies the base addresses used by the service host.</span></span>  
  
<span data-ttu-id="c0796-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c0796-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c0796-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="c0796-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="c0796-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<services >** ](services.md)</span><span class="sxs-lookup"><span data-stu-id="c0796-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)</span></span>\
<span data-ttu-id="c0796-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de service**](service.md)</span><span class="sxs-lookup"><span data-stu-id="c0796-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)</span></span>\
<span data-ttu-id="c0796-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> d’hôte**](host.md)</span><span class="sxs-lookup"><span data-stu-id="c0796-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<host>**](host.md)</span></span>\
<span data-ttu-id="c0796-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<baseAddresses >** ](baseaddresses.md)</span><span class="sxs-lookup"><span data-stu-id="c0796-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<baseAddresses>**](baseaddresses.md)</span></span>\
<span data-ttu-id="c0796-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Ajouter >**</span><span class="sxs-lookup"><span data-stu-id="c0796-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0796-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c0796-111">Syntax</span></span>  
  
```xml  
<add baseAddress="string" />
```  
  
## <a name="type"></a><span data-ttu-id="c0796-112">Type</span><span class="sxs-lookup"><span data-stu-id="c0796-112">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c0796-113">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="c0796-113">Attributes and Elements</span></span>  
 <span data-ttu-id="c0796-114">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="c0796-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c0796-115">Attributs</span><span class="sxs-lookup"><span data-stu-id="c0796-115">Attributes</span></span>  
  
|<span data-ttu-id="c0796-116">Attribut</span><span class="sxs-lookup"><span data-stu-id="c0796-116">Attribute</span></span>|<span data-ttu-id="c0796-117">Description</span><span class="sxs-lookup"><span data-stu-id="c0796-117">Description</span></span>|  
|---------------|-----------------|  
|`baseAddress`|<span data-ttu-id="c0796-118">Chaîne indiquant une adresse de base utilisée par l'hôte de service.</span><span class="sxs-lookup"><span data-stu-id="c0796-118">A string that specifies a base address used by the service host.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c0796-119">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="c0796-119">Child Elements</span></span>  
 <span data-ttu-id="c0796-120">Aucun.</span><span class="sxs-lookup"><span data-stu-id="c0796-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c0796-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="c0796-121">Parent Elements</span></span>  
  
|<span data-ttu-id="c0796-122">Élément</span><span class="sxs-lookup"><span data-stu-id="c0796-122">Element</span></span>|<span data-ttu-id="c0796-123">Description</span><span class="sxs-lookup"><span data-stu-id="c0796-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c0796-124">\<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="c0796-124">\<baseAddresses></span></span>](baseaddresses.md)|<span data-ttu-id="c0796-125">Collection d'éléments `baseAddress`.</span><span class="sxs-lookup"><span data-stu-id="c0796-125">A collection of `baseAddress` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c0796-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c0796-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [<span data-ttu-id="c0796-127">Hébergement</span><span class="sxs-lookup"><span data-stu-id="c0796-127">Hosting</span></span>](../../../wcf/feature-details/hosting.md)

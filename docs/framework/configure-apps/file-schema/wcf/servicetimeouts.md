---
title: <serviceTimeouts>
ms.date: 03/30/2017
ms.assetid: ada536cf-97dc-4cd7-89ec-ed1466c1c557
ms.openlocfilehash: 801a7aaf1f0d0fa267fa8cca3d2e7fd02919c475
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399546"
---
# <a name="servicetimeouts"></a><span data-ttu-id="9bcec-101">\<serviceTimeouts></span><span class="sxs-lookup"><span data-stu-id="9bcec-101">\<serviceTimeouts></span></span>
<span data-ttu-id="9bcec-102">Spécifie le délai d'attente pour un service.</span><span class="sxs-lookup"><span data-stu-id="9bcec-102">Specifies the timeout for a service.</span></span>  
  
<span data-ttu-id="9bcec-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="9bcec-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="9bcec-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="9bcec-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="9bcec-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportements >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="9bcec-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="9bcec-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="9bcec-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="9bcec-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportement**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="9bcec-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="9bcec-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<serviceTimeouts >**</span><span class="sxs-lookup"><span data-stu-id="9bcec-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceTimeouts>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bcec-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9bcec-109">Syntax</span></span>  
  
```xml  
<serviceTimeouts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="9bcec-110">Type</span><span class="sxs-lookup"><span data-stu-id="9bcec-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9bcec-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="9bcec-111">Attributes and Elements</span></span>  
 <span data-ttu-id="9bcec-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="9bcec-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9bcec-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="9bcec-113">Attributes</span></span>  
  
|<span data-ttu-id="9bcec-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="9bcec-114">Attribute</span></span>|<span data-ttu-id="9bcec-115">Description</span><span class="sxs-lookup"><span data-stu-id="9bcec-115">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="9bcec-116">Valeur <xref:System.TimeSpan> qui spécifie l’intervalle de temps pour le transfert d’une transaction du client au serveur.</span><span class="sxs-lookup"><span data-stu-id="9bcec-116">A <xref:System.TimeSpan> value that specifies the interval of time a transaction must flow from client to server.</span></span> <span data-ttu-id="9bcec-117">La valeur par défaut est « 00:00:00 ».</span><span class="sxs-lookup"><span data-stu-id="9bcec-117">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9bcec-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="9bcec-118">Child Elements</span></span>  
 <span data-ttu-id="9bcec-119">Aucun.</span><span class="sxs-lookup"><span data-stu-id="9bcec-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9bcec-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="9bcec-120">Parent Elements</span></span>  
  
|<span data-ttu-id="9bcec-121">Élément</span><span class="sxs-lookup"><span data-stu-id="9bcec-121">Element</span></span>|<span data-ttu-id="9bcec-122">Description</span><span class="sxs-lookup"><span data-stu-id="9bcec-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9bcec-123">\<behavior></span><span class="sxs-lookup"><span data-stu-id="9bcec-123">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="9bcec-124">Spécifie un élément de comportement.</span><span class="sxs-lookup"><span data-stu-id="9bcec-124">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9bcec-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9bcec-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>

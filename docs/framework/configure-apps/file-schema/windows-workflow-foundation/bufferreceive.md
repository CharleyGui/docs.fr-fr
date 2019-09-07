---
title: <bufferReceive>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b23c3a54-10d4-4f13-ab6d-98b26b76f22a
ms.openlocfilehash: be5173ea43c6f7fca7180a311885a26c889b12db
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398833"
---
# <a name="bufferreceive"></a><span data-ttu-id="3a3a3-101">\<bufferReceive></span><span class="sxs-lookup"><span data-stu-id="3a3a3-101">\<bufferReceive></span></span>
<span data-ttu-id="3a3a3-102">Comportement de service qui permet à un service d'utiliser le traitement de la réception mise en mémoire tampon, ce qui permet à un service de flux de travail de traiter les messages dans le désordre.</span><span class="sxs-lookup"><span data-stu-id="3a3a3-102">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>  
  
<span data-ttu-id="3a3a3-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="3a3a3-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="3a3a3-104">&nbsp;&nbsp;[ **\<requise. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="3a3a3-104">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="3a3a3-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportements >** ](behaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="3a3a3-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)</span></span>\
<span data-ttu-id="3a3a3-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="3a3a3-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="3a3a3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportement**](behavior-of-servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="3a3a3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="3a3a3-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bufferReceive >**</span><span class="sxs-lookup"><span data-stu-id="3a3a3-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bufferReceive>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a3a3-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3a3a3-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <bufferReceive maxPendingMessagesPerChannel="Integer" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3a3a3-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="3a3a3-110">Attributes and Elements</span></span>  
 <span data-ttu-id="3a3a3-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="3a3a3-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3a3a3-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="3a3a3-112">Attributes</span></span>  
  
|<span data-ttu-id="3a3a3-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="3a3a3-113">Attribute</span></span>|<span data-ttu-id="3a3a3-114">Description</span><span class="sxs-lookup"><span data-stu-id="3a3a3-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3a3a3-115">maxPendingMessagesPerChannel</span><span class="sxs-lookup"><span data-stu-id="3a3a3-115">maxPendingMessagesPerChannel</span></span>|<span data-ttu-id="3a3a3-116">Entier qui spécifie le nombre maximal de messages en attente autorisé pour chaque canal.</span><span class="sxs-lookup"><span data-stu-id="3a3a3-116">An integer that specifies the maximum number of pending messages allowed for each channel.</span></span> <span data-ttu-id="3a3a3-117">La valeur par défaut est 512.</span><span class="sxs-lookup"><span data-stu-id="3a3a3-117">The default value is 512.</span></span> <span data-ttu-id="3a3a3-118">Cette propriété limite le nombre de messages non ordonnés qui peuvent être reçus par un service de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="3a3a3-118">This property limits the number of out-of-order messages that can be received by a workflow service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3a3a3-119">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="3a3a3-119">Child Elements</span></span>  
 <span data-ttu-id="3a3a3-120">Aucun.</span><span class="sxs-lookup"><span data-stu-id="3a3a3-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3a3a3-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="3a3a3-121">Parent Elements</span></span>  
  
|<span data-ttu-id="3a3a3-122">Élément</span><span class="sxs-lookup"><span data-stu-id="3a3a3-122">Element</span></span>|<span data-ttu-id="3a3a3-123">Description</span><span class="sxs-lookup"><span data-stu-id="3a3a3-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3a3a3-124">\<> de comportement \<de la > serviceBehaviors</span><span class="sxs-lookup"><span data-stu-id="3a3a3-124">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="3a3a3-125">Spécifie un élément de comportement.</span><span class="sxs-lookup"><span data-stu-id="3a3a3-125">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3a3a3-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3a3a3-126">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.BufferedReceiveServiceBehavior>
- <xref:System.ServiceModel.Activities.Configuration.BufferedReceiveElement>

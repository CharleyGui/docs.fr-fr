---
title: <bufferReceive>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b23c3a54-10d4-4f13-ab6d-98b26b76f22a
ms.openlocfilehash: 1d4611d6fee9dad057985f7d8f5ef961d384efcd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945971"
---
# <a name="bufferreceive"></a><span data-ttu-id="1997c-101">\<bufferReceive></span><span class="sxs-lookup"><span data-stu-id="1997c-101">\<bufferReceive></span></span>
<span data-ttu-id="1997c-102">Comportement de service qui permet à un service d'utiliser le traitement de la réception mise en mémoire tampon, ce qui permet à un service de flux de travail de traiter les messages dans le désordre.</span><span class="sxs-lookup"><span data-stu-id="1997c-102">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>  
  
<span data-ttu-id="1997c-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="1997c-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="1997c-104">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="1997c-104">\<behaviors></span></span>  
<span data-ttu-id="1997c-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="1997c-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="1997c-106">\<> de comportement</span><span class="sxs-lookup"><span data-stu-id="1997c-106">\<behavior></span></span>  
<span data-ttu-id="1997c-107">\<bufferReceive></span><span class="sxs-lookup"><span data-stu-id="1997c-107">\<bufferReceive></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1997c-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1997c-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <bufferReceive maxPendingMessagesPerChannel="Integer" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1997c-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="1997c-109">Attributes and Elements</span></span>  
 <span data-ttu-id="1997c-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="1997c-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1997c-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="1997c-111">Attributes</span></span>  
  
|<span data-ttu-id="1997c-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="1997c-112">Attribute</span></span>|<span data-ttu-id="1997c-113">Description</span><span class="sxs-lookup"><span data-stu-id="1997c-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1997c-114">maxPendingMessagesPerChannel</span><span class="sxs-lookup"><span data-stu-id="1997c-114">maxPendingMessagesPerChannel</span></span>|<span data-ttu-id="1997c-115">Entier qui spécifie le nombre maximal de messages en attente autorisé pour chaque canal.</span><span class="sxs-lookup"><span data-stu-id="1997c-115">An integer that specifies the maximum number of pending messages allowed for each channel.</span></span> <span data-ttu-id="1997c-116">La valeur par défaut est 512.</span><span class="sxs-lookup"><span data-stu-id="1997c-116">The default value is 512.</span></span> <span data-ttu-id="1997c-117">Cette propriété limite le nombre de messages non ordonnés qui peuvent être reçus par un service de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="1997c-117">This property limits the number of out-of-order messages that can be received by a workflow service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1997c-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="1997c-118">Child Elements</span></span>  
 <span data-ttu-id="1997c-119">Aucun.</span><span class="sxs-lookup"><span data-stu-id="1997c-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1997c-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="1997c-120">Parent Elements</span></span>  
  
|<span data-ttu-id="1997c-121">Élément</span><span class="sxs-lookup"><span data-stu-id="1997c-121">Element</span></span>|<span data-ttu-id="1997c-122">Description</span><span class="sxs-lookup"><span data-stu-id="1997c-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1997c-123">\<> de comportement \<de la > serviceBehaviors</span><span class="sxs-lookup"><span data-stu-id="1997c-123">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="1997c-124">Spécifie un élément de comportement.</span><span class="sxs-lookup"><span data-stu-id="1997c-124">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1997c-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1997c-125">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.BufferedReceiveServiceBehavior>
- <xref:System.ServiceModel.Activities.Configuration.BufferedReceiveElement>

---
title: <bufferReceive>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b23c3a54-10d4-4f13-ab6d-98b26b76f22a
ms.openlocfilehash: 16d4546bce461b55695e0deed093396ce1c2b0b6
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189563"
---
# \<bufferReceive>

<span data-ttu-id="4dffd-101">Comportement de service qui permet à un service d'utiliser le traitement de la réception mise en mémoire tampon, ce qui permet à un service de flux de travail de traiter les messages dans le désordre.</span><span class="sxs-lookup"><span data-stu-id="4dffd-101">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bufferReceive>**  
  
## <a name="syntax"></a><span data-ttu-id="4dffd-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4dffd-102">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <bufferReceive maxPendingMessagesPerChannel="Integer" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4dffd-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="4dffd-103">Attributes and Elements</span></span>  

 <span data-ttu-id="4dffd-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="4dffd-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4dffd-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="4dffd-105">Attributes</span></span>  
  
|<span data-ttu-id="4dffd-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="4dffd-106">Attribute</span></span>|<span data-ttu-id="4dffd-107">Description</span><span class="sxs-lookup"><span data-stu-id="4dffd-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4dffd-108">maxPendingMessagesPerChannel</span><span class="sxs-lookup"><span data-stu-id="4dffd-108">maxPendingMessagesPerChannel</span></span>|<span data-ttu-id="4dffd-109">Entier qui spécifie le nombre maximal de messages en attente autorisé pour chaque canal.</span><span class="sxs-lookup"><span data-stu-id="4dffd-109">An integer that specifies the maximum number of pending messages allowed for each channel.</span></span> <span data-ttu-id="4dffd-110">La valeur par défaut est 512.</span><span class="sxs-lookup"><span data-stu-id="4dffd-110">The default value is 512.</span></span> <span data-ttu-id="4dffd-111">Cette propriété limite le nombre de messages non ordonnés qui peuvent être reçus par un service de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="4dffd-111">This property limits the number of out-of-order messages that can be received by a workflow service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4dffd-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="4dffd-112">Child Elements</span></span>  

 <span data-ttu-id="4dffd-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="4dffd-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4dffd-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="4dffd-114">Parent Elements</span></span>  
  
|<span data-ttu-id="4dffd-115">Élément</span><span class="sxs-lookup"><span data-stu-id="4dffd-115">Element</span></span>|<span data-ttu-id="4dffd-116">Description</span><span class="sxs-lookup"><span data-stu-id="4dffd-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4dffd-117">\<behavior> of \<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="4dffd-117">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="4dffd-118">Spécifie un élément de comportement.</span><span class="sxs-lookup"><span data-stu-id="4dffd-118">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4dffd-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4dffd-119">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.BufferedReceiveServiceBehavior>
- <xref:System.ServiceModel.Activities.Configuration.BufferedReceiveElement>

---
title: <synchronousReceive>, élément
ms.date: 03/30/2017
ms.assetid: cc070387-3d11-4b02-a952-bc08ad2df05a
ms.openlocfilehash: b3f4860be6b7edac776a1c30611271b2eb36968e
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399498"
---
# <a name="synchronousreceive-element"></a><span data-ttu-id="b7ab6-102">\<synchronousReceive >, élément</span><span class="sxs-lookup"><span data-stu-id="b7ab6-102">\<synchronousReceive> element</span></span>
<span data-ttu-id="b7ab6-103">Cet élément de configuration est utilisé en vue de spécifier le comportement de réception des messages au moment de l'exécution dans une application cliente ou de service.</span><span class="sxs-lookup"><span data-stu-id="b7ab6-103">This configuration element is used to specify run-time behavior for receiving messages in either a service or client application.</span></span> <span data-ttu-id="b7ab6-104">Il n'a aucun attribut ou élément enfant.</span><span class="sxs-lookup"><span data-stu-id="b7ab6-104">It does not have any attributes or child elements.</span></span>  
  
<span data-ttu-id="b7ab6-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b7ab6-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b7ab6-106">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="b7ab6-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="b7ab6-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportements >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="b7ab6-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="b7ab6-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="b7ab6-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="b7ab6-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportement**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="b7ab6-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="b7ab6-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<synchronousReceive >**</span><span class="sxs-lookup"><span data-stu-id="b7ab6-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<synchronousReceive>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7ab6-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b7ab6-111">Syntax</span></span>  
  
```xml  
<synchronousReceive />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b7ab6-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="b7ab6-112">Attributes and Elements</span></span>  
 <span data-ttu-id="b7ab6-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="b7ab6-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b7ab6-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="b7ab6-114">Attributes</span></span>  
 <span data-ttu-id="b7ab6-115">Aucun.</span><span class="sxs-lookup"><span data-stu-id="b7ab6-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b7ab6-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="b7ab6-116">Child Elements</span></span>  
 <span data-ttu-id="b7ab6-117">Aucun.</span><span class="sxs-lookup"><span data-stu-id="b7ab6-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b7ab6-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="b7ab6-118">Parent Elements</span></span>  
  
|<span data-ttu-id="b7ab6-119">Élément</span><span class="sxs-lookup"><span data-stu-id="b7ab6-119">Element</span></span>|<span data-ttu-id="b7ab6-120">Description</span><span class="sxs-lookup"><span data-stu-id="b7ab6-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b7ab6-121">\<behavior></span><span class="sxs-lookup"><span data-stu-id="b7ab6-121">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="b7ab6-122">Spécifie un comportement de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="b7ab6-122">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b7ab6-123">Notes</span><span class="sxs-lookup"><span data-stu-id="b7ab6-123">Remarks</span></span>  
 <span data-ttu-id="b7ab6-124">Utilisez ce comportement pour indiquer à l'écouteur de canal d'utiliser une réception synchrone au lieu de celle par défaut (asynchrone).</span><span class="sxs-lookup"><span data-stu-id="b7ab6-124">Use this behavior to instruct the channel listener to use a synchronous receive rather than the default, asynchronous.</span></span> <span data-ttu-id="b7ab6-125">Windows Communication Foundation (WCF) émet un nouveau thread pour pomper chaque canal accepté.</span><span class="sxs-lookup"><span data-stu-id="b7ab6-125">Windows Communication Foundation (WCF) issues a new thread to pump for each accepted channel.</span></span> <span data-ttu-id="b7ab6-126">Si le nombre de canaux est important, il est possible de rencontrer une insuffisance de threads.</span><span class="sxs-lookup"><span data-stu-id="b7ab6-126">If there are a lot of channels, there is the possibility of running out of threads.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7ab6-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b7ab6-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.SynchronousReceiveElement>
- <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>

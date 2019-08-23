---
title: <synchronousReceive>, élément
ms.date: 03/30/2017
ms.assetid: cc070387-3d11-4b02-a952-bc08ad2df05a
ms.openlocfilehash: fa14d4606303b2d67cf5ef845d428bb086680204
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938967"
---
# <a name="synchronousreceive-element"></a><span data-ttu-id="d0278-102">\<synchronousReceive >, élément</span><span class="sxs-lookup"><span data-stu-id="d0278-102">\<synchronousReceive> element</span></span>
<span data-ttu-id="d0278-103">Cet élément de configuration est utilisé en vue de spécifier le comportement de réception des messages au moment de l'exécution dans une application cliente ou de service.</span><span class="sxs-lookup"><span data-stu-id="d0278-103">This configuration element is used to specify run-time behavior for receiving messages in either a service or client application.</span></span> <span data-ttu-id="d0278-104">Il n'a aucun attribut ou élément enfant.</span><span class="sxs-lookup"><span data-stu-id="d0278-104">It does not have any attributes or child elements.</span></span>  
  
 <span data-ttu-id="d0278-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d0278-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="d0278-106">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="d0278-106">\<behaviors></span></span>  
<span data-ttu-id="d0278-107">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="d0278-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="d0278-108">\<> de comportement</span><span class="sxs-lookup"><span data-stu-id="d0278-108">\<behavior></span></span>  
<span data-ttu-id="d0278-109">\<synchronousReceive></span><span class="sxs-lookup"><span data-stu-id="d0278-109">\<synchronousReceive></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0278-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d0278-110">Syntax</span></span>  
  
```xml  
<synchronousReceive />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d0278-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="d0278-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d0278-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="d0278-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d0278-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="d0278-113">Attributes</span></span>  
 <span data-ttu-id="d0278-114">Aucun.</span><span class="sxs-lookup"><span data-stu-id="d0278-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d0278-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="d0278-115">Child Elements</span></span>  
 <span data-ttu-id="d0278-116">Aucun.</span><span class="sxs-lookup"><span data-stu-id="d0278-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d0278-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="d0278-117">Parent Elements</span></span>  
  
|<span data-ttu-id="d0278-118">Élément</span><span class="sxs-lookup"><span data-stu-id="d0278-118">Element</span></span>|<span data-ttu-id="d0278-119">Description</span><span class="sxs-lookup"><span data-stu-id="d0278-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d0278-120">\<behavior></span><span class="sxs-lookup"><span data-stu-id="d0278-120">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="d0278-121">Spécifie un comportement de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="d0278-121">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d0278-122">Notes</span><span class="sxs-lookup"><span data-stu-id="d0278-122">Remarks</span></span>  
 <span data-ttu-id="d0278-123">Utilisez ce comportement pour indiquer à l'écouteur de canal d'utiliser une réception synchrone au lieu de celle par défaut (asynchrone).</span><span class="sxs-lookup"><span data-stu-id="d0278-123">Use this behavior to instruct the channel listener to use a synchronous receive rather than the default, asynchronous.</span></span> <span data-ttu-id="d0278-124">Windows Communication Foundation (WCF) émet un nouveau thread pour pomper chaque canal accepté.</span><span class="sxs-lookup"><span data-stu-id="d0278-124">Windows Communication Foundation (WCF) issues a new thread to pump for each accepted channel.</span></span> <span data-ttu-id="d0278-125">Si le nombre de canaux est important, il est possible de rencontrer une insuffisance de threads.</span><span class="sxs-lookup"><span data-stu-id="d0278-125">If there are a lot of channels, there is the possibility of running out of threads.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0278-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d0278-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.SynchronousReceiveElement>
- <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>

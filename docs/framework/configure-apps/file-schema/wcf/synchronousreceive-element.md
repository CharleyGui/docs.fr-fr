---
title: <synchronousReceive> (élément)
ms.date: 03/30/2017
ms.assetid: cc070387-3d11-4b02-a952-bc08ad2df05a
ms.openlocfilehash: b3f4860be6b7edac776a1c30611271b2eb36968e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399498"
---
# <a name="synchronousreceive-element"></a><span data-ttu-id="7ded3-102">\<synchronousReceive>, élément</span><span class="sxs-lookup"><span data-stu-id="7ded3-102">\<synchronousReceive> element</span></span>
<span data-ttu-id="7ded3-103">Cet élément de configuration est utilisé en vue de spécifier le comportement de réception des messages au moment de l'exécution dans une application cliente ou de service.</span><span class="sxs-lookup"><span data-stu-id="7ded3-103">This configuration element is used to specify run-time behavior for receiving messages in either a service or client application.</span></span> <span data-ttu-id="7ded3-104">Il n'a aucun attribut ou élément enfant.</span><span class="sxs-lookup"><span data-stu-id="7ded3-104">It does not have any attributes or child elements.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<synchronousReceive>**  
  
## <a name="syntax"></a><span data-ttu-id="7ded3-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7ded3-105">Syntax</span></span>  
  
```xml  
<synchronousReceive />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7ded3-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="7ded3-106">Attributes and Elements</span></span>  
 <span data-ttu-id="7ded3-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="7ded3-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7ded3-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="7ded3-108">Attributes</span></span>  
 <span data-ttu-id="7ded3-109">Aucun.</span><span class="sxs-lookup"><span data-stu-id="7ded3-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7ded3-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="7ded3-110">Child Elements</span></span>  
 <span data-ttu-id="7ded3-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="7ded3-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7ded3-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="7ded3-112">Parent Elements</span></span>  
  
|<span data-ttu-id="7ded3-113">Élément</span><span class="sxs-lookup"><span data-stu-id="7ded3-113">Element</span></span>|<span data-ttu-id="7ded3-114">Description</span><span class="sxs-lookup"><span data-stu-id="7ded3-114">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="7ded3-115">Spécifie un comportement de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="7ded3-115">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7ded3-116">Remarques</span><span class="sxs-lookup"><span data-stu-id="7ded3-116">Remarks</span></span>  
 <span data-ttu-id="7ded3-117">Utilisez ce comportement pour indiquer à l'écouteur de canal d'utiliser une réception synchrone au lieu de celle par défaut (asynchrone).</span><span class="sxs-lookup"><span data-stu-id="7ded3-117">Use this behavior to instruct the channel listener to use a synchronous receive rather than the default, asynchronous.</span></span> <span data-ttu-id="7ded3-118">Windows Communication Foundation (WCF) émet un nouveau thread pour pomper chaque canal accepté.</span><span class="sxs-lookup"><span data-stu-id="7ded3-118">Windows Communication Foundation (WCF) issues a new thread to pump for each accepted channel.</span></span> <span data-ttu-id="7ded3-119">Si le nombre de canaux est important, il est possible de rencontrer une insuffisance de threads.</span><span class="sxs-lookup"><span data-stu-id="7ded3-119">If there are a lot of channels, there is the possibility of running out of threads.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ded3-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7ded3-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.SynchronousReceiveElement>
- <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>

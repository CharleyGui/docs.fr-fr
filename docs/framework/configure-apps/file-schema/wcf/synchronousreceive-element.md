---
title: <synchronousReceive> (élément)
ms.date: 03/30/2017
ms.assetid: cc070387-3d11-4b02-a952-bc08ad2df05a
ms.openlocfilehash: 2073d115dd87d513a6e48b8b585fed4b49d5bb32
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91157172"
---
# <a name="synchronousreceive-element"></a><span data-ttu-id="846db-102">\<synchronousReceive>, élément</span><span class="sxs-lookup"><span data-stu-id="846db-102">\<synchronousReceive> element</span></span>

<span data-ttu-id="846db-103">Cet élément de configuration est utilisé en vue de spécifier le comportement de réception des messages au moment de l'exécution dans une application cliente ou de service.</span><span class="sxs-lookup"><span data-stu-id="846db-103">This configuration element is used to specify run-time behavior for receiving messages in either a service or client application.</span></span> <span data-ttu-id="846db-104">Il n'a aucun attribut ou élément enfant.</span><span class="sxs-lookup"><span data-stu-id="846db-104">It does not have any attributes or child elements.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<synchronousReceive>**  
  
## <a name="syntax"></a><span data-ttu-id="846db-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="846db-105">Syntax</span></span>  
  
```xml  
<synchronousReceive />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="846db-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="846db-106">Attributes and Elements</span></span>  

 <span data-ttu-id="846db-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="846db-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="846db-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="846db-108">Attributes</span></span>  

 <span data-ttu-id="846db-109">Aucun.</span><span class="sxs-lookup"><span data-stu-id="846db-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="846db-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="846db-110">Child Elements</span></span>  

 <span data-ttu-id="846db-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="846db-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="846db-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="846db-112">Parent Elements</span></span>  
  
|<span data-ttu-id="846db-113">Élément</span><span class="sxs-lookup"><span data-stu-id="846db-113">Element</span></span>|<span data-ttu-id="846db-114">Description</span><span class="sxs-lookup"><span data-stu-id="846db-114">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="846db-115">Spécifie un comportement de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="846db-115">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="846db-116">Notes</span><span class="sxs-lookup"><span data-stu-id="846db-116">Remarks</span></span>  

 <span data-ttu-id="846db-117">Utilisez ce comportement pour indiquer à l'écouteur de canal d'utiliser une réception synchrone au lieu de celle par défaut (asynchrone).</span><span class="sxs-lookup"><span data-stu-id="846db-117">Use this behavior to instruct the channel listener to use a synchronous receive rather than the default, asynchronous.</span></span> <span data-ttu-id="846db-118">Windows Communication Foundation (WCF) émet un nouveau thread pour pomper chaque canal accepté.</span><span class="sxs-lookup"><span data-stu-id="846db-118">Windows Communication Foundation (WCF) issues a new thread to pump for each accepted channel.</span></span> <span data-ttu-id="846db-119">Si le nombre de canaux est important, il est possible de rencontrer une insuffisance de threads.</span><span class="sxs-lookup"><span data-stu-id="846db-119">If there are a lot of channels, there is the possibility of running out of threads.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="846db-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="846db-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.SynchronousReceiveElement>
- <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>

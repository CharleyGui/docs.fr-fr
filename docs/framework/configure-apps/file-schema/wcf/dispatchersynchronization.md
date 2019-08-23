---
title: <dispatcherSynchronization>
ms.date: 03/30/2017
ms.assetid: cc030f9c-4e38-4b14-94dc-9a0e41ec8e2d
ms.openlocfilehash: 7336c9f7d8a117f9a9bfd338e47941eeb648fa51
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925845"
---
# <a name="dispatchersynchronization"></a><span data-ttu-id="ec4d9-101">\<dispatcherSynchronization></span><span class="sxs-lookup"><span data-stu-id="ec4d9-101">\<dispatcherSynchronization></span></span>
  
<span data-ttu-id="ec4d9-102">Spécifie un comportement de point de terminaison qui permet à un service d'envoyer des réponses de manière asynchrone.</span><span class="sxs-lookup"><span data-stu-id="ec4d9-102">Specifies an endpoint behavior that enables a service to send replies asynchronously.</span></span>  
  
<span data-ttu-id="ec4d9-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="ec4d9-103">\<system.serviceModel></span></span>  
<span data-ttu-id="ec4d9-104">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="ec4d9-104">\<behaviors></span></span>  
<span data-ttu-id="ec4d9-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="ec4d9-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="ec4d9-106">\<> de comportement</span><span class="sxs-lookup"><span data-stu-id="ec4d9-106">\<behavior></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec4d9-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ec4d9-107">Syntax</span></span>  
  
```xml  
<dispatcherSynchronizationBehavior asynchronousSendEnabled="Boolean"
                                   maxPendingReceives="Integer" />
```  
  
## <a name="type"></a><span data-ttu-id="ec4d9-108">Type</span><span class="sxs-lookup"><span data-stu-id="ec4d9-108">Type</span></span>  
  
`Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ec4d9-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="ec4d9-109">Attributes and elements</span></span>  
  
<span data-ttu-id="ec4d9-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="ec4d9-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ec4d9-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="ec4d9-111">Attributes</span></span>

| <span data-ttu-id="ec4d9-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="ec4d9-112">Attribute</span></span>               | <span data-ttu-id="ec4d9-113">Description</span><span class="sxs-lookup"><span data-stu-id="ec4d9-113">Description</span></span>       |
| ----------------------- | ----------------- |
| <span data-ttu-id="ec4d9-114">asynchronousSendEnabled</span><span class="sxs-lookup"><span data-stu-id="ec4d9-114">asynchronousSendEnabled</span></span> | <span data-ttu-id="ec4d9-115">Valeur booléenne qui indique si un comportement d'envoi asynchrone est activé.</span><span class="sxs-lookup"><span data-stu-id="ec4d9-115">A Boolean that specifies whether asynchronous send behavior is enabled.</span></span> |
| `maxPendingReceives`    | <span data-ttu-id="ec4d9-116">Entier qui spécifie le nombre de réceptions simultanées qui peuvent être émises sur le canal.</span><span class="sxs-lookup"><span data-stu-id="ec4d9-116">An integer that specifies the number of concurrent receives that can be issued on the channel.</span></span><br /><br /> <span data-ttu-id="ec4d9-117">Cette valeur doit être configurée uniquement après avoir correctement configuré le comportement de limitation de service.</span><span class="sxs-lookup"><span data-stu-id="ec4d9-117">This value should be configured only after you have properly configured service throttling behavior.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="ec4d9-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ec4d9-118">Child elements</span></span>

<span data-ttu-id="ec4d9-119">Aucun.</span><span class="sxs-lookup"><span data-stu-id="ec4d9-119">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ec4d9-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ec4d9-120">Parent elements</span></span>

| <span data-ttu-id="ec4d9-121">Élément</span><span class="sxs-lookup"><span data-stu-id="ec4d9-121">Element</span></span> | <span data-ttu-id="ec4d9-122">Description</span><span class="sxs-lookup"><span data-stu-id="ec4d9-122">Description</span></span> |  
| ------- | ----------- |  
| [<span data-ttu-id="ec4d9-123">\<behavior></span><span class="sxs-lookup"><span data-stu-id="ec4d9-123">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="ec4d9-124">Spécifie un comportement de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="ec4d9-124">Specifies an endpoint behavior.</span></span> |

## <a name="see-also"></a><span data-ttu-id="ec4d9-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ec4d9-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement>
- <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior>

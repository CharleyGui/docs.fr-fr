---
title: <dispatcherSynchronization>
ms.date: 03/30/2017
ms.assetid: cc030f9c-4e38-4b14-94dc-9a0e41ec8e2d
ms.openlocfilehash: b95f25217c2a3558846cc7a0ef43e21aacd2ee2a
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397999"
---
# <a name="dispatchersynchronization"></a><span data-ttu-id="9e075-101">\<dispatcherSynchronization></span><span class="sxs-lookup"><span data-stu-id="9e075-101">\<dispatcherSynchronization></span></span>
  
<span data-ttu-id="9e075-102">Spécifie un comportement de point de terminaison qui permet à un service d'envoyer des réponses de manière asynchrone.</span><span class="sxs-lookup"><span data-stu-id="9e075-102">Specifies an endpoint behavior that enables a service to send replies asynchronously.</span></span>  
  
<span data-ttu-id="9e075-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="9e075-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="9e075-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="9e075-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="9e075-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportements >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="9e075-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="9e075-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="9e075-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="9e075-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportement**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="9e075-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="9e075-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<dispatcherSynchronization >**</span><span class="sxs-lookup"><span data-stu-id="9e075-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dispatcherSynchronization>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e075-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9e075-109">Syntax</span></span>  
  
```xml  
<dispatcherSynchronizationBehavior asynchronousSendEnabled="Boolean"
                                   maxPendingReceives="Integer" />
```  
  
## <a name="type"></a><span data-ttu-id="9e075-110">Type</span><span class="sxs-lookup"><span data-stu-id="9e075-110">Type</span></span>  
  
`Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9e075-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="9e075-111">Attributes and elements</span></span>  
  
<span data-ttu-id="9e075-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="9e075-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9e075-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="9e075-113">Attributes</span></span>

| <span data-ttu-id="9e075-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="9e075-114">Attribute</span></span>               | <span data-ttu-id="9e075-115">Description</span><span class="sxs-lookup"><span data-stu-id="9e075-115">Description</span></span>       |
| ----------------------- | ----------------- |
| <span data-ttu-id="9e075-116">asynchronousSendEnabled</span><span class="sxs-lookup"><span data-stu-id="9e075-116">asynchronousSendEnabled</span></span> | <span data-ttu-id="9e075-117">Valeur booléenne qui indique si un comportement d'envoi asynchrone est activé.</span><span class="sxs-lookup"><span data-stu-id="9e075-117">A Boolean that specifies whether asynchronous send behavior is enabled.</span></span> |
| `maxPendingReceives`    | <span data-ttu-id="9e075-118">Entier qui spécifie le nombre de réceptions simultanées qui peuvent être émises sur le canal.</span><span class="sxs-lookup"><span data-stu-id="9e075-118">An integer that specifies the number of concurrent receives that can be issued on the channel.</span></span><br /><br /> <span data-ttu-id="9e075-119">Cette valeur doit être configurée uniquement après avoir correctement configuré le comportement de limitation de service.</span><span class="sxs-lookup"><span data-stu-id="9e075-119">This value should be configured only after you have properly configured service throttling behavior.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="9e075-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="9e075-120">Child elements</span></span>

<span data-ttu-id="9e075-121">Aucun.</span><span class="sxs-lookup"><span data-stu-id="9e075-121">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9e075-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="9e075-122">Parent elements</span></span>

| <span data-ttu-id="9e075-123">Élément</span><span class="sxs-lookup"><span data-stu-id="9e075-123">Element</span></span> | <span data-ttu-id="9e075-124">Description</span><span class="sxs-lookup"><span data-stu-id="9e075-124">Description</span></span> |  
| ------- | ----------- |  
| [<span data-ttu-id="9e075-125">\<behavior></span><span class="sxs-lookup"><span data-stu-id="9e075-125">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="9e075-126">Spécifie un comportement de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="9e075-126">Specifies an endpoint behavior.</span></span> |

## <a name="see-also"></a><span data-ttu-id="9e075-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9e075-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement>
- <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior>

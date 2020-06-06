---
title: <dispatcherSynchronization>
ms.date: 03/30/2017
ms.assetid: cc030f9c-4e38-4b14-94dc-9a0e41ec8e2d
ms.openlocfilehash: b95f25217c2a3558846cc7a0ef43e21aacd2ee2a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397999"
---
# \<dispatcherSynchronization>
  
<span data-ttu-id="9ea08-101">Spécifie un comportement de point de terminaison qui permet à un service d'envoyer des réponses de manière asynchrone.</span><span class="sxs-lookup"><span data-stu-id="9ea08-101">Specifies an endpoint behavior that enables a service to send replies asynchronously.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dispatcherSynchronization>**  
  
## <a name="syntax"></a><span data-ttu-id="9ea08-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9ea08-102">Syntax</span></span>  
  
```xml  
<dispatcherSynchronizationBehavior asynchronousSendEnabled="Boolean"
                                   maxPendingReceives="Integer" />
```  
  
## <a name="type"></a><span data-ttu-id="9ea08-103">Type</span><span class="sxs-lookup"><span data-stu-id="9ea08-103">Type</span></span>  
  
`Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9ea08-104">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="9ea08-104">Attributes and elements</span></span>  
  
<span data-ttu-id="9ea08-105">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="9ea08-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9ea08-106">Attributs</span><span class="sxs-lookup"><span data-stu-id="9ea08-106">Attributes</span></span>

| <span data-ttu-id="9ea08-107">Attribut</span><span class="sxs-lookup"><span data-stu-id="9ea08-107">Attribute</span></span>               | <span data-ttu-id="9ea08-108">Description</span><span class="sxs-lookup"><span data-stu-id="9ea08-108">Description</span></span>       |
| ----------------------- | ----------------- |
| <span data-ttu-id="9ea08-109">asynchronousSendEnabled</span><span class="sxs-lookup"><span data-stu-id="9ea08-109">asynchronousSendEnabled</span></span> | <span data-ttu-id="9ea08-110">Valeur booléenne qui indique si un comportement d'envoi asynchrone est activé.</span><span class="sxs-lookup"><span data-stu-id="9ea08-110">A Boolean that specifies whether asynchronous send behavior is enabled.</span></span> |
| `maxPendingReceives`    | <span data-ttu-id="9ea08-111">Entier qui spécifie le nombre de réceptions simultanées qui peuvent être émises sur le canal.</span><span class="sxs-lookup"><span data-stu-id="9ea08-111">An integer that specifies the number of concurrent receives that can be issued on the channel.</span></span><br /><br /> <span data-ttu-id="9ea08-112">Cette valeur doit être configurée uniquement après avoir correctement configuré le comportement de limitation de service.</span><span class="sxs-lookup"><span data-stu-id="9ea08-112">This value should be configured only after you have properly configured service throttling behavior.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="9ea08-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="9ea08-113">Child elements</span></span>

<span data-ttu-id="9ea08-114">Aucun.</span><span class="sxs-lookup"><span data-stu-id="9ea08-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9ea08-115">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="9ea08-115">Parent elements</span></span>

| <span data-ttu-id="9ea08-116">Élément</span><span class="sxs-lookup"><span data-stu-id="9ea08-116">Element</span></span> | <span data-ttu-id="9ea08-117">Description</span><span class="sxs-lookup"><span data-stu-id="9ea08-117">Description</span></span> |  
| ------- | ----------- |  
| [\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="9ea08-118">Spécifie un comportement de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="9ea08-118">Specifies an endpoint behavior.</span></span> |

## <a name="see-also"></a><span data-ttu-id="9ea08-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9ea08-119">See also</span></span>

- <xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement>
- <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior>

---
title: <serviceTimeouts>
ms.date: 03/30/2017
ms.assetid: ada536cf-97dc-4cd7-89ec-ed1466c1c557
ms.openlocfilehash: a1792fec4f86c9ac31107c043b976cfafcfa4c13
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937093"
---
# <a name="servicetimeouts"></a><span data-ttu-id="0614f-101">\<serviceTimeouts></span><span class="sxs-lookup"><span data-stu-id="0614f-101">\<serviceTimeouts></span></span>
<span data-ttu-id="0614f-102">Spécifie le délai d'attente pour un service.</span><span class="sxs-lookup"><span data-stu-id="0614f-102">Specifies the timeout for a service.</span></span>  
  
 <span data-ttu-id="0614f-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="0614f-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="0614f-104">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="0614f-104">\<behaviors></span></span>  
<span data-ttu-id="0614f-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="0614f-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="0614f-106">\<> de comportement</span><span class="sxs-lookup"><span data-stu-id="0614f-106">\<behavior></span></span>  
<span data-ttu-id="0614f-107">\<serviceTimeouts></span><span class="sxs-lookup"><span data-stu-id="0614f-107">\<serviceTimeouts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0614f-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0614f-108">Syntax</span></span>  
  
```xml  
<serviceTimeouts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="0614f-109">Type</span><span class="sxs-lookup"><span data-stu-id="0614f-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0614f-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="0614f-110">Attributes and Elements</span></span>  
 <span data-ttu-id="0614f-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="0614f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0614f-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="0614f-112">Attributes</span></span>  
  
|<span data-ttu-id="0614f-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="0614f-113">Attribute</span></span>|<span data-ttu-id="0614f-114">Description</span><span class="sxs-lookup"><span data-stu-id="0614f-114">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="0614f-115">Valeur <xref:System.TimeSpan> qui spécifie l’intervalle de temps pour le transfert d’une transaction du client au serveur.</span><span class="sxs-lookup"><span data-stu-id="0614f-115">A <xref:System.TimeSpan> value that specifies the interval of time a transaction must flow from client to server.</span></span> <span data-ttu-id="0614f-116">La valeur par défaut est «00:00:00».</span><span class="sxs-lookup"><span data-stu-id="0614f-116">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0614f-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="0614f-117">Child Elements</span></span>  
 <span data-ttu-id="0614f-118">Aucun.</span><span class="sxs-lookup"><span data-stu-id="0614f-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0614f-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="0614f-119">Parent Elements</span></span>  
  
|<span data-ttu-id="0614f-120">Élément</span><span class="sxs-lookup"><span data-stu-id="0614f-120">Element</span></span>|<span data-ttu-id="0614f-121">Description</span><span class="sxs-lookup"><span data-stu-id="0614f-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0614f-122">\<behavior></span><span class="sxs-lookup"><span data-stu-id="0614f-122">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="0614f-123">Spécifie un élément de comportement.</span><span class="sxs-lookup"><span data-stu-id="0614f-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0614f-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0614f-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>

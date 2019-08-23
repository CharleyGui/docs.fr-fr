---
title: <behaviors>de flux de travail
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 3c6017b6-0c4f-4192-bd67-9515f5d1ec82
ms.openlocfilehash: 7dd3b0b20c9d7accd80a85b3693e67ffc9b729e5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945993"
---
# <a name="behaviors-of-workflow"></a><span data-ttu-id="1d872-102">\<comportements > du flux de travail</span><span class="sxs-lookup"><span data-stu-id="1d872-102">\<behaviors> of workflow</span></span>
<span data-ttu-id="1d872-103">Cet élément contient la collection **serviceBehaviors** .</span><span class="sxs-lookup"><span data-stu-id="1d872-103">This element contains the **serviceBehaviors** collection.</span></span>  <span data-ttu-id="1d872-104">Chaque élément dans la collection définit des éléments de comportement consommés par des services de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="1d872-104">Each element in the collection defines behavior elements consumed by workflow services.</span></span> <span data-ttu-id="1d872-105">Chaque élément de comportement est identifié par son attribut de **nom** unique.</span><span class="sxs-lookup"><span data-stu-id="1d872-105">Each behavior element is identified by its unique **name** attribute.</span></span>  
  
 <span data-ttu-id="1d872-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="1d872-106">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d872-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1d872-107">Syntax</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1d872-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="1d872-108">Attributes and Elements</span></span>  
 <span data-ttu-id="1d872-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="1d872-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1d872-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="1d872-110">Attributes</span></span>  
 <span data-ttu-id="1d872-111">Aucun</span><span class="sxs-lookup"><span data-stu-id="1d872-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1d872-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="1d872-112">Child Elements</span></span>  
  
|<span data-ttu-id="1d872-113">Élément</span><span class="sxs-lookup"><span data-stu-id="1d872-113">Element</span></span>|<span data-ttu-id="1d872-114">Description</span><span class="sxs-lookup"><span data-stu-id="1d872-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1d872-115">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="1d872-115">\<serviceBehaviors></span></span>](servicebehaviors-of-workflow.md)|<span data-ttu-id="1d872-116">Cette section de configuration représente tous les comportements définis pour un service de flux de travail spécifique.</span><span class="sxs-lookup"><span data-stu-id="1d872-116">This configuration section represents all the behaviors defined for a specific workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1d872-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="1d872-117">Parent Elements</span></span>  
  
|<span data-ttu-id="1d872-118">Élément</span><span class="sxs-lookup"><span data-stu-id="1d872-118">Element</span></span>|<span data-ttu-id="1d872-119">Description</span><span class="sxs-lookup"><span data-stu-id="1d872-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1d872-120">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="1d872-120">\<system.serviceModel></span></span>](../wcf/system-servicemodel.md)|<span data-ttu-id="1d872-121">Élément racine de tous les éléments de configuration de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="1d872-121">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1d872-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1d872-122">See also</span></span>

- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [<span data-ttu-id="1d872-123">Configuration et extension de l’exécution à l’aide de comportements</span><span class="sxs-lookup"><span data-stu-id="1d872-123">Configuring and Extending the Runtime with Behaviors</span></span>](../../../wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)

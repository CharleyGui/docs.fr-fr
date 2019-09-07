---
title: <behaviors>de flux de travail
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 3c6017b6-0c4f-4192-bd67-9515f5d1ec82
ms.openlocfilehash: 05a15cdf5c043eb5d94b36028324310d2b7a8413
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398875"
---
# <a name="behaviors-of-workflow"></a><span data-ttu-id="30875-102">\<comportements > du flux de travail</span><span class="sxs-lookup"><span data-stu-id="30875-102">\<behaviors> of workflow</span></span>
<span data-ttu-id="30875-103">Cet élément contient la collection **serviceBehaviors** .</span><span class="sxs-lookup"><span data-stu-id="30875-103">This element contains the **serviceBehaviors** collection.</span></span>  <span data-ttu-id="30875-104">Chaque élément dans la collection définit des éléments de comportement consommés par des services de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="30875-104">Each element in the collection defines behavior elements consumed by workflow services.</span></span> <span data-ttu-id="30875-105">Chaque élément de comportement est identifié par son attribut de **nom** unique.</span><span class="sxs-lookup"><span data-stu-id="30875-105">Each behavior element is identified by its unique **name** attribute.</span></span>  
  
<span data-ttu-id="30875-106">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="30875-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="30875-107">&nbsp;&nbsp;[ **\<requise. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="30875-107">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="30875-108">&nbsp;&nbsp;&nbsp;&nbsp; **\<comportements >**</span><span class="sxs-lookup"><span data-stu-id="30875-108">&nbsp;&nbsp;&nbsp;&nbsp;**\<behaviors>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30875-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="30875-109">Syntax</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="30875-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="30875-110">Attributes and Elements</span></span>  
 <span data-ttu-id="30875-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="30875-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="30875-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="30875-112">Attributes</span></span>  
 <span data-ttu-id="30875-113">Aucun</span><span class="sxs-lookup"><span data-stu-id="30875-113">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="30875-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="30875-114">Child Elements</span></span>  
  
|<span data-ttu-id="30875-115">Élément</span><span class="sxs-lookup"><span data-stu-id="30875-115">Element</span></span>|<span data-ttu-id="30875-116">Description</span><span class="sxs-lookup"><span data-stu-id="30875-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="30875-117">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="30875-117">\<serviceBehaviors></span></span>](servicebehaviors-of-workflow.md)|<span data-ttu-id="30875-118">Cette section de configuration représente tous les comportements définis pour un service de flux de travail spécifique.</span><span class="sxs-lookup"><span data-stu-id="30875-118">This configuration section represents all the behaviors defined for a specific workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="30875-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="30875-119">Parent Elements</span></span>  
  
|<span data-ttu-id="30875-120">Élément</span><span class="sxs-lookup"><span data-stu-id="30875-120">Element</span></span>|<span data-ttu-id="30875-121">Description</span><span class="sxs-lookup"><span data-stu-id="30875-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="30875-122">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="30875-122">\<system.serviceModel></span></span>](../wcf/system-servicemodel.md)|<span data-ttu-id="30875-123">Élément racine de tous les éléments de configuration de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="30875-123">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="30875-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="30875-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [<span data-ttu-id="30875-125">Configuration et extension de l’exécution à l’aide de comportements</span><span class="sxs-lookup"><span data-stu-id="30875-125">Configuring and Extending the Runtime with Behaviors</span></span>](../../../wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)

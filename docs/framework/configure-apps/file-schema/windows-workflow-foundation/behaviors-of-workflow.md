---
title: <behaviors>de flux de travail
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 3c6017b6-0c4f-4192-bd67-9515f5d1ec82
ms.openlocfilehash: 05a15cdf5c043eb5d94b36028324310d2b7a8413
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398875"
---
# <a name="behaviors-of-workflow"></a><span data-ttu-id="fbe19-102">\<behaviors>de flux de travail</span><span class="sxs-lookup"><span data-stu-id="fbe19-102">\<behaviors> of workflow</span></span>
<span data-ttu-id="fbe19-103">Cet élément contient la collection **serviceBehaviors** .</span><span class="sxs-lookup"><span data-stu-id="fbe19-103">This element contains the **serviceBehaviors** collection.</span></span>  <span data-ttu-id="fbe19-104">Chaque élément dans la collection définit des éléments de comportement consommés par des services de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="fbe19-104">Each element in the collection defines behavior elements consumed by workflow services.</span></span> <span data-ttu-id="fbe19-105">Chaque élément de comportement est identifié par son attribut de **nom** unique.</span><span class="sxs-lookup"><span data-stu-id="fbe19-105">Each behavior element is identified by its unique **name** attribute.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<behaviors>**  
  
## <a name="syntax"></a><span data-ttu-id="fbe19-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fbe19-106">Syntax</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fbe19-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="fbe19-107">Attributes and Elements</span></span>  
 <span data-ttu-id="fbe19-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="fbe19-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fbe19-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="fbe19-109">Attributes</span></span>  
 <span data-ttu-id="fbe19-110">Aucune</span><span class="sxs-lookup"><span data-stu-id="fbe19-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="fbe19-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="fbe19-111">Child Elements</span></span>  
  
|<span data-ttu-id="fbe19-112">Élément</span><span class="sxs-lookup"><span data-stu-id="fbe19-112">Element</span></span>|<span data-ttu-id="fbe19-113">Description</span><span class="sxs-lookup"><span data-stu-id="fbe19-113">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceBehaviors>](servicebehaviors-of-workflow.md)|<span data-ttu-id="fbe19-114">Cette section de configuration représente tous les comportements définis pour un service de flux de travail spécifique.</span><span class="sxs-lookup"><span data-stu-id="fbe19-114">This configuration section represents all the behaviors defined for a specific workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fbe19-115">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="fbe19-115">Parent Elements</span></span>  
  
|<span data-ttu-id="fbe19-116">Élément</span><span class="sxs-lookup"><span data-stu-id="fbe19-116">Element</span></span>|<span data-ttu-id="fbe19-117">Description</span><span class="sxs-lookup"><span data-stu-id="fbe19-117">Description</span></span>|  
|-------------|-----------------|  
|[\<system.serviceModel>](../wcf/system-servicemodel.md)|<span data-ttu-id="fbe19-118">Élément racine de tous les éléments de configuration de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="fbe19-118">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fbe19-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fbe19-119">See also</span></span>

- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [<span data-ttu-id="fbe19-120">Configuration et extension de l'exécution à l'aide de comportements</span><span class="sxs-lookup"><span data-stu-id="fbe19-120">Configuring and Extending the Runtime with Behaviors</span></span>](../../../wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)

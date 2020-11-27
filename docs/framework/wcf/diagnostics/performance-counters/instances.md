---
title: Instances
ms.date: 03/30/2017
ms.assetid: c8cf3460-0ca1-4411-8262-e9ecaf7f0a31
ms.openlocfilehash: f4bf639e626945c7e753ac352dfecc7a79541bfd
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96266075"
---
# <a name="instances"></a><span data-ttu-id="bdd90-102">Instances</span><span class="sxs-lookup"><span data-stu-id="bdd90-102">Instances</span></span>

<span data-ttu-id="bdd90-103">Nom du compteur : Instances.</span><span class="sxs-lookup"><span data-stu-id="bdd90-103">Counter Name: Instances.</span></span>  
  
## <a name="description"></a><span data-ttu-id="bdd90-104">Description</span><span class="sxs-lookup"><span data-stu-id="bdd90-104">Description</span></span>  

 <span data-ttu-id="bdd90-105">Nombre de contextes d'instance que le service contient actuellement.</span><span class="sxs-lookup"><span data-stu-id="bdd90-105">Number of instance contexts that the service currently contains.</span></span>  
  
 <span data-ttu-id="bdd90-106">La plupart du temps, le nombre de contextes d'instance est identique au nombre d'instances.</span><span class="sxs-lookup"><span data-stu-id="bdd90-106">Most of the time, the number of instance contexts is identical to the number of instances.</span></span> <span data-ttu-id="bdd90-107">Toutefois, les scénarios suivants constituent des exceptions à cette règle.</span><span class="sxs-lookup"><span data-stu-id="bdd90-107">However, the following scenarios are exception to this rule.</span></span>  
  
- <span data-ttu-id="bdd90-108">Une méthode de service appelle la méthode <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> de manière explicite.</span><span class="sxs-lookup"><span data-stu-id="bdd90-108">A service method calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> method explicitly.</span></span>  
  
- <span data-ttu-id="bdd90-109">Un <xref:System.ServiceModel.ReleaseInstanceMode> est appliqué à une instance <xref:System.ServiceModel.OperationBehaviorAttribute>.</span><span class="sxs-lookup"><span data-stu-id="bdd90-109">A <xref:System.ServiceModel.ReleaseInstanceMode> is applied to an <xref:System.ServiceModel.OperationBehaviorAttribute> instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdd90-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bdd90-110">See also</span></span>

- <xref:System.ServiceModel.OperationBehaviorAttribute>

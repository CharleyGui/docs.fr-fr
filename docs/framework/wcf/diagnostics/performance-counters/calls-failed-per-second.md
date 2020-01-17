---
title: Nombre d'appels ayant échoué par seconde
ms.date: 03/30/2017
ms.assetid: e4ef3773-f650-4876-99cf-4d0c02aa03d4
ms.openlocfilehash: 110ee5c264094f80d5c7c6542c3e388e758e1665
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163161"
---
# <a name="calls-failed-per-second"></a><span data-ttu-id="955ea-102">Nombre d'appels ayant échoué par seconde</span><span class="sxs-lookup"><span data-stu-id="955ea-102">Calls Failed Per Second</span></span>
<span data-ttu-id="955ea-103">Nom du compteur : appels ayant échoué par seconde</span><span class="sxs-lookup"><span data-stu-id="955ea-103">Counter Name: Calls Failed Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="955ea-104">Description</span><span class="sxs-lookup"><span data-stu-id="955ea-104">Description</span></span>  
 <span data-ttu-id="955ea-105">Nombre d'appels à cette opération avec des exceptions non prises en charge par seconde.</span><span class="sxs-lookup"><span data-stu-id="955ea-105">Number of calls with unhandled exceptions in this operation in a second.</span></span>  
  
 <span data-ttu-id="955ea-106">Ce compteur est de type de compteur de performance [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), dont la valeur est calculée à l’aide de la formule suivante.</span><span class="sxs-lookup"><span data-stu-id="955ea-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="955ea-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="955ea-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="955ea-108">Ce compteur est incrémenté chaque fois qu’il y a une exception non gérée dans cette opération.</span><span class="sxs-lookup"><span data-stu-id="955ea-108">This counter is incremented every time there is an unhandled exception in this operation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="955ea-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="955ea-109">See also</span></span>

- [<span data-ttu-id="955ea-110">Spécification et gestion des erreurs dans les contrats et les services</span><span class="sxs-lookup"><span data-stu-id="955ea-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../specifying-and-handling-faults-in-contracts-and-services.md)

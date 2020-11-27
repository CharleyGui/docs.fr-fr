---
title: Nombre d'appels ayant échoué par seconde
ms.date: 03/30/2017
ms.assetid: e4ef3773-f650-4876-99cf-4d0c02aa03d4
ms.openlocfilehash: d3eafc4b31f0e62093a972b7c9f2325a3648d21b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96285458"
---
# <a name="calls-failed-per-second"></a><span data-ttu-id="39f9e-102">Nombre d'appels ayant échoué par seconde</span><span class="sxs-lookup"><span data-stu-id="39f9e-102">Calls Failed Per Second</span></span>

<span data-ttu-id="39f9e-103">Nom du compteur : appels ayant échoué par seconde</span><span class="sxs-lookup"><span data-stu-id="39f9e-103">Counter Name: Calls Failed Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="39f9e-104">Description</span><span class="sxs-lookup"><span data-stu-id="39f9e-104">Description</span></span>  

 <span data-ttu-id="39f9e-105">Nombre d'appels à cette opération avec des exceptions non prises en charge par seconde.</span><span class="sxs-lookup"><span data-stu-id="39f9e-105">Number of calls with unhandled exceptions in this operation in a second.</span></span>  
  
 <span data-ttu-id="39f9e-106">Ce compteur est de type de compteur de performance [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), dont la valeur est calculée à l’aide de la formule suivante.</span><span class="sxs-lookup"><span data-stu-id="39f9e-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="39f9e-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="39f9e-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="39f9e-108">Ce compteur est incrémenté chaque fois qu’il y a une exception non gérée dans cette opération.</span><span class="sxs-lookup"><span data-stu-id="39f9e-108">This counter is incremented every time there is an unhandled exception in this operation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39f9e-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="39f9e-109">See also</span></span>

- [<span data-ttu-id="39f9e-110">Spécification et gestion des erreurs dans les contrats et les services</span><span class="sxs-lookup"><span data-stu-id="39f9e-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../specifying-and-handling-faults-in-contracts-and-services.md)

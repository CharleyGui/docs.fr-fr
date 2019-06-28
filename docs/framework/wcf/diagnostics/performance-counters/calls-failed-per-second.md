---
title: Nombre d'appels ayant échoué par seconde
ms.date: 03/30/2017
ms.assetid: e4ef3773-f650-4876-99cf-4d0c02aa03d4
ms.openlocfilehash: aa8cd4c2d9f642b525b2b9ccb931c4f2101a5129
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67421789"
---
# <a name="calls-failed-per-second"></a><span data-ttu-id="0f7fe-102">Nombre d'appels ayant échoué par seconde</span><span class="sxs-lookup"><span data-stu-id="0f7fe-102">Calls Failed Per Second</span></span>
<span data-ttu-id="0f7fe-103">Nom du compteur : Nombre d'appels ayant échoué par seconde</span><span class="sxs-lookup"><span data-stu-id="0f7fe-103">Counter Name: Calls Failed Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="0f7fe-104">Description</span><span class="sxs-lookup"><span data-stu-id="0f7fe-104">Description</span></span>  
 <span data-ttu-id="0f7fe-105">Nombre d'appels à cette opération avec des exceptions non prises en charge par seconde.</span><span class="sxs-lookup"><span data-stu-id="0f7fe-105">Number of calls with unhandled exceptions in this operation in a second.</span></span>  
  
 <span data-ttu-id="0f7fe-106">Ce compteur est de type de compteur de performances [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), dont la valeur est calculée à l’aide de la formule suivante.</span><span class="sxs-lookup"><span data-stu-id="0f7fe-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="0f7fe-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="0f7fe-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="0f7fe-108">Ce compteur est incrémenté chaque fois qu’une exception non gérée dans cette opération.</span><span class="sxs-lookup"><span data-stu-id="0f7fe-108">This counter is incremented every time there is an unhandled exception in this operation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f7fe-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0f7fe-109">See also</span></span>

- [<span data-ttu-id="0f7fe-110">Spécification et gestion des erreurs dans les contrats et les services</span><span class="sxs-lookup"><span data-stu-id="0f7fe-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)

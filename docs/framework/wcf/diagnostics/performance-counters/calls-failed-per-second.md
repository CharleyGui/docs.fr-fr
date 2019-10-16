---
title: Nombre d'appels ayant échoué par seconde
ms.date: 03/30/2017
ms.assetid: e4ef3773-f650-4876-99cf-4d0c02aa03d4
ms.openlocfilehash: e7c0b53f4c2b1a7e87a5791b44e452ec9146c459
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321124"
---
# <a name="calls-failed-per-second"></a><span data-ttu-id="d8179-102">Nombre d'appels ayant échoué par seconde</span><span class="sxs-lookup"><span data-stu-id="d8179-102">Calls Failed Per Second</span></span>
<span data-ttu-id="d8179-103">Nom du compteur : appels ayant échoué par seconde</span><span class="sxs-lookup"><span data-stu-id="d8179-103">Counter Name: Calls Failed Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="d8179-104">Description</span><span class="sxs-lookup"><span data-stu-id="d8179-104">Description</span></span>  
 <span data-ttu-id="d8179-105">Nombre d'appels à cette opération avec des exceptions non prises en charge par seconde.</span><span class="sxs-lookup"><span data-stu-id="d8179-105">Number of calls with unhandled exceptions in this operation in a second.</span></span>  
  
 <span data-ttu-id="d8179-106">Ce compteur est du type de compteur de performance [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), dont la valeur est calculée à l’aide de la formule suivante.</span><span class="sxs-lookup"><span data-stu-id="d8179-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="d8179-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="d8179-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="d8179-108">Ce compteur est incrémenté chaque fois qu’il y a une exception non gérée dans cette opération.</span><span class="sxs-lookup"><span data-stu-id="d8179-108">This counter is incremented every time there is an unhandled exception in this operation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8179-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d8179-109">See also</span></span>

- [<span data-ttu-id="d8179-110">Spécification et gestion des erreurs dans les contrats et les services</span><span class="sxs-lookup"><span data-stu-id="d8179-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../specifying-and-handling-faults-in-contracts-and-services.md)

---
title: 'Point de terminaison : appels ayant échoué par seconde'
ms.date: 03/30/2017
ms.assetid: bcbe9da4-c8dd-4e27-b630-11611adc7580
ms.openlocfilehash: 9634f8a170bb2fae2f15c3f00dcabb95d512c74e
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321456"
---
# <a name="endpoint-calls-failed-per-second"></a><span data-ttu-id="2b3d8-102">Point de terminaison : appels ayant échoué par seconde</span><span class="sxs-lookup"><span data-stu-id="2b3d8-102">Endpoint: Calls Failed Per Second</span></span>
<span data-ttu-id="2b3d8-103">Nom du compteur : appels ayant échoué par seconde.</span><span class="sxs-lookup"><span data-stu-id="2b3d8-103">Counter Name: Calls Failed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="2b3d8-104">Description</span><span class="sxs-lookup"><span data-stu-id="2b3d8-104">Description</span></span>  
 <span data-ttu-id="2b3d8-105">Nombre d'appels ayant des exceptions non traitées et reçus par ce point de terminaison en une seconde.</span><span class="sxs-lookup"><span data-stu-id="2b3d8-105">Number of calls that have unhandled exceptions and are received by this endpoint in a second.</span></span>  
  
 <span data-ttu-id="2b3d8-106">Ce compteur est du type de compteur de performance [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), dont la valeur est calculée à l’aide de la formule suivante.</span><span class="sxs-lookup"><span data-stu-id="2b3d8-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="2b3d8-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="2b3d8-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="2b3d8-108">Ce compteur est incrémenté à chaque exception non traitée à ce point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="2b3d8-108">This counter is incremented every time there is an unhandled exception at this endpoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b3d8-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2b3d8-109">See also</span></span>

- [<span data-ttu-id="2b3d8-110">Spécification et gestion des erreurs dans les contrats et les services</span><span class="sxs-lookup"><span data-stu-id="2b3d8-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../specifying-and-handling-faults-in-contracts-and-services.md)

---
title: 'Point de terminaison : appels ayant échoué par seconde'
ms.date: 03/30/2017
ms.assetid: bcbe9da4-c8dd-4e27-b630-11611adc7580
ms.openlocfilehash: 25e504221097505e622a3ba60f0c7e85ec455f36
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163616"
---
# <a name="endpoint-calls-failed-per-second"></a><span data-ttu-id="8773f-102">Point de terminaison : appels ayant échoué par seconde</span><span class="sxs-lookup"><span data-stu-id="8773f-102">Endpoint: Calls Failed Per Second</span></span>
<span data-ttu-id="8773f-103">Nom du compteur : appels ayant échoué par seconde.</span><span class="sxs-lookup"><span data-stu-id="8773f-103">Counter Name: Calls Failed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="8773f-104">Description</span><span class="sxs-lookup"><span data-stu-id="8773f-104">Description</span></span>  
 <span data-ttu-id="8773f-105">Nombre d'appels ayant des exceptions non traitées et reçus par ce point de terminaison en une seconde.</span><span class="sxs-lookup"><span data-stu-id="8773f-105">Number of calls that have unhandled exceptions and are received by this endpoint in a second.</span></span>  
  
 <span data-ttu-id="8773f-106">Ce compteur est de type de compteur de performance [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), dont la valeur est calculée à l’aide de la formule suivante.</span><span class="sxs-lookup"><span data-stu-id="8773f-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="8773f-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="8773f-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="8773f-108">Ce compteur est incrémenté à chaque exception non traitée à ce point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="8773f-108">This counter is incremented every time there is an unhandled exception at this endpoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8773f-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8773f-109">See also</span></span>

- [<span data-ttu-id="8773f-110">Spécification et gestion des erreurs dans les contrats et les services</span><span class="sxs-lookup"><span data-stu-id="8773f-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../specifying-and-handling-faults-in-contracts-and-services.md)

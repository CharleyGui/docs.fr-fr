---
title: "Service : nombre d'appels ayant échoué par seconde"
ms.date: 03/30/2017
ms.assetid: 5a2c7939-107d-4f0c-b43c-e02e079e8a9d
ms.openlocfilehash: 5629c55cba6f21de24a1de7e8d38a9c08fcf4fb1
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90559107"
---
# <a name="service-calls-failed-per-second"></a><span data-ttu-id="a3bc5-102">Service : nombre d'appels ayant échoué par seconde</span><span class="sxs-lookup"><span data-stu-id="a3bc5-102">Service: Calls Failed Per Second</span></span>
<span data-ttu-id="a3bc5-103">Nom du compteur : appels ayant échoué par seconde.</span><span class="sxs-lookup"><span data-stu-id="a3bc5-103">Counter Name: Calls Failed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="a3bc5-104">Description</span><span class="sxs-lookup"><span data-stu-id="a3bc5-104">Description</span></span>  
 <span data-ttu-id="a3bc5-105">Nombre d'appels qui ont des exceptions non prises en charge et qui sont reçus par ce service par seconde.</span><span class="sxs-lookup"><span data-stu-id="a3bc5-105">Number of calls that have unhandled exceptions, and are received by this service in a second.</span></span>  
  
 <span data-ttu-id="a3bc5-106">Ce compteur est de type de compteur de performance [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), dont la valeur est calculée à l’aide de la formule suivante.</span><span class="sxs-lookup"><span data-stu-id="a3bc5-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="a3bc5-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="a3bc5-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="a3bc5-108">Dans le code managé, des exceptions sont levées en cas de conditions d'erreur.</span><span class="sxs-lookup"><span data-stu-id="a3bc5-108">In managed code, exceptions are thrown when error conditions occur.</span></span>  
  
 <span data-ttu-id="a3bc5-109">Dans le code managé, des exceptions sont levées en cas de conditions d'erreur.</span><span class="sxs-lookup"><span data-stu-id="a3bc5-109">In managed code, exceptions are thrown when error conditions occur.</span></span>  
  
 <span data-ttu-id="a3bc5-110">Ce compteur est incrémenté à chaque exception non prise en charge dans ce service.</span><span class="sxs-lookup"><span data-stu-id="a3bc5-110">This counter is incremented every time there is an unhandled exception in this service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3bc5-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a3bc5-111">See also</span></span>

- [<span data-ttu-id="a3bc5-112">Spécification et gestion des erreurs dans les contrats et les services</span><span class="sxs-lookup"><span data-stu-id="a3bc5-112">Specifying and Handling Faults in Contracts and Services</span></span>](../../specifying-and-handling-faults-in-contracts-and-services.md)

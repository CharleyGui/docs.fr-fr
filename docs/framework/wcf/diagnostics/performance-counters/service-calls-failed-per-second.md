---
title: "Service : nombre d'appels ayant échoué par seconde"
ms.date: 03/30/2017
ms.assetid: 5a2c7939-107d-4f0c-b43c-e02e079e8a9d
ms.openlocfilehash: 5431144a4618b146a10dfaa3bbdaae34c519319e
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72315787"
---
# <a name="service-calls-failed-per-second"></a><span data-ttu-id="5e4b1-102">Service : nombre d'appels ayant échoué par seconde</span><span class="sxs-lookup"><span data-stu-id="5e4b1-102">Service: Calls Failed Per Second</span></span>
<span data-ttu-id="5e4b1-103">Nom du compteur : appels ayant échoué par seconde.</span><span class="sxs-lookup"><span data-stu-id="5e4b1-103">Counter Name: Calls Failed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="5e4b1-104">Description</span><span class="sxs-lookup"><span data-stu-id="5e4b1-104">Description</span></span>  
 <span data-ttu-id="5e4b1-105">Nombre d'appels qui ont des exceptions non prises en charge et qui sont reçus par ce service par seconde.</span><span class="sxs-lookup"><span data-stu-id="5e4b1-105">Number of calls that have unhandled exceptions, and are received by this service in a second.</span></span>  
  
 <span data-ttu-id="5e4b1-106">Ce compteur est du type de compteur de performance [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), dont la valeur est calculée à l’aide de la formule suivante.</span><span class="sxs-lookup"><span data-stu-id="5e4b1-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="5e4b1-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="5e4b1-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="5e4b1-108">Dans le code managé, des exceptions sont levées en cas de conditions d'erreur.</span><span class="sxs-lookup"><span data-stu-id="5e4b1-108">In managed code, exceptions are thrown when error conditions occur.</span></span>  
  
 <span data-ttu-id="5e4b1-109">Dans le code managé, des exceptions sont levées en cas de conditions d'erreur.</span><span class="sxs-lookup"><span data-stu-id="5e4b1-109">In managed code, exceptions are thrown when error conditions occur.</span></span>  
  
 <span data-ttu-id="5e4b1-110">Ce compteur est incrémenté à chaque exception non prise en charge dans ce service.</span><span class="sxs-lookup"><span data-stu-id="5e4b1-110">This counter is incremented every time there is an unhandled exception in this service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e4b1-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5e4b1-111">See also</span></span>

- [<span data-ttu-id="5e4b1-112">Spécification et gestion des erreurs dans les contrats et les services</span><span class="sxs-lookup"><span data-stu-id="5e4b1-112">Specifying and Handling Faults in Contracts and Services</span></span>](../../specifying-and-handling-faults-in-contracts-and-services.md)

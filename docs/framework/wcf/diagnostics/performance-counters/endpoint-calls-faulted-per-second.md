---
title: 'Point de terminaison : appels ayant renvoyé une erreur par seconde'
ms.date: 03/30/2017
ms.assetid: 9840fc0a-0e4d-4638-96fd-40e3ab9e4667
ms.openlocfilehash: 84dabf1215a02133874f3a0a55578c684a3308d9
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319976"
---
# <a name="endpoint-calls-faulted-per-second"></a><span data-ttu-id="0e5e3-102">Point de terminaison : appels ayant renvoyé une erreur par seconde</span><span class="sxs-lookup"><span data-stu-id="0e5e3-102">Endpoint: Calls Faulted Per Second</span></span>
<span data-ttu-id="0e5e3-103">Nom du compteur : appels ayant renvoyé une erreur par seconde.</span><span class="sxs-lookup"><span data-stu-id="0e5e3-103">Counter Name: Calls Faulted Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="0e5e3-104">Description</span><span class="sxs-lookup"><span data-stu-id="0e5e3-104">Description</span></span>  
 <span data-ttu-id="0e5e3-105">Nombre d'appels qui ont retourné des erreurs à ce point de terminaison en une seconde.</span><span class="sxs-lookup"><span data-stu-id="0e5e3-105">Number of calls that have returned faults to this endpoint in a second.</span></span>  
  
 <span data-ttu-id="0e5e3-106">Ce compteur est du type de compteur de performance [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), dont la valeur est calculée à l’aide de la formule suivante.</span><span class="sxs-lookup"><span data-stu-id="0e5e3-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="0e5e3-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="0e5e3-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="0e5e3-108">Dans les applications Windows Communication Foundation (WCF), les méthodes de service communiquent les informations d’erreur à l’aide de messages d’erreur SOAP.</span><span class="sxs-lookup"><span data-stu-id="0e5e3-108">In Windows Communication Foundation (WCF) applications, service methods communicate processing error information using SOAP fault messages.</span></span> <span data-ttu-id="0e5e3-109">Les erreurs SOAP sont des types de message inclus dans les métadonnées d'une opération de service et créent, par conséquent, un contrat d'erreur permettant aux clients d'améliorer la fiabilité ou l'interactivité de leur exécution.</span><span class="sxs-lookup"><span data-stu-id="0e5e3-109">SOAP faults are message types that are included in the metadata for a service operation and therefore create a fault contract that clients can use to make their execution more robust or interactive.</span></span> <span data-ttu-id="0e5e3-110">Les erreurs SOAP étant exprimées aux clients dans un format XML, elles sont très interopérables.</span><span class="sxs-lookup"><span data-stu-id="0e5e3-110">Since SOAP faults are expressed to clients in XML form, they are highly interoperable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e5e3-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0e5e3-111">See also</span></span>

- [<span data-ttu-id="0e5e3-112">Spécification et gestion des erreurs dans les contrats et les services</span><span class="sxs-lookup"><span data-stu-id="0e5e3-112">Specifying and Handling Faults in Contracts and Services</span></span>](../../specifying-and-handling-faults-in-contracts-and-services.md)

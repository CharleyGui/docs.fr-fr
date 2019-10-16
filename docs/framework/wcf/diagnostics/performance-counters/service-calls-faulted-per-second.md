---
title: 'Service : appels ayant renvoyé une erreur par seconde'
ms.date: 03/30/2017
ms.assetid: 94247356-2b29-4b50-b639-91ca8c1cf3a9
ms.openlocfilehash: 85c38f12c4d9bacf08597d465d831cf73e907cab
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321450"
---
# <a name="service-calls-faulted-per-second"></a><span data-ttu-id="dd7da-102">Service : appels ayant renvoyé une erreur par seconde</span><span class="sxs-lookup"><span data-stu-id="dd7da-102">Service: Calls Faulted Per Second</span></span>
<span data-ttu-id="dd7da-103">Nom du compteur : appels ayant renvoyé une erreur par seconde.</span><span class="sxs-lookup"><span data-stu-id="dd7da-103">Counter Name: Calls Faulted Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="dd7da-104">Description</span><span class="sxs-lookup"><span data-stu-id="dd7da-104">Description</span></span>  
 <span data-ttu-id="dd7da-105">Nombre d'appels qui ont retourné des erreurs à ce service en une seconde.</span><span class="sxs-lookup"><span data-stu-id="dd7da-105">Number of calls that have returned faults to this service in a second.</span></span>  
  
 <span data-ttu-id="dd7da-106">Ce compteur est du type de compteur de performance [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), dont la valeur est calculée à l’aide de la formule suivante.</span><span class="sxs-lookup"><span data-stu-id="dd7da-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="dd7da-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="dd7da-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="dd7da-108">Dans les applications Windows Communication Foundation (WCF), les méthodes de service communiquent les informations d’erreur à l’aide de messages d’erreur SOAP.</span><span class="sxs-lookup"><span data-stu-id="dd7da-108">In Windows Communication Foundation (WCF) applications, service methods communicate processing error information using SOAP fault messages.</span></span> <span data-ttu-id="dd7da-109">Les erreurs SOAP sont des types de message inclus dans les métadonnées d'une opération de service et créent, par conséquent, un contrat d'erreur permettant aux clients d'améliorer la fiabilité ou l'interactivité de leur exécution.</span><span class="sxs-lookup"><span data-stu-id="dd7da-109">SOAP faults are message types that are included in the metadata for a service operation and therefore create a fault contract that clients can use to make their execution more robust or interactive.</span></span> <span data-ttu-id="dd7da-110">Les erreurs SOAP étant exprimées aux clients dans un format XML, elles sont très interopérables.</span><span class="sxs-lookup"><span data-stu-id="dd7da-110">Since SOAP faults are expressed to clients in XML form, they are highly interoperable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd7da-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dd7da-111">See also</span></span>

- [<span data-ttu-id="dd7da-112">Spécification et gestion des erreurs dans les contrats et les services</span><span class="sxs-lookup"><span data-stu-id="dd7da-112">Specifying and Handling Faults in Contracts and Services</span></span>](../../specifying-and-handling-faults-in-contracts-and-services.md)

---
title: 'Service : appels ayant renvoyé une erreur'
ms.date: 03/30/2017
ms.assetid: 6da7f100-3f61-4b3c-9409-fe1360829b8a
ms.openlocfilehash: 613de88df8aaa955539a4e9586dacd64e155161e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96252931"
---
# <a name="service-calls-faulted"></a><span data-ttu-id="11d24-102">Service : appels ayant renvoyé une erreur</span><span class="sxs-lookup"><span data-stu-id="11d24-102">Service: Calls Faulted</span></span>

<span data-ttu-id="11d24-103">Nom du compteur : appels ayant renvoyé des erreurs.</span><span class="sxs-lookup"><span data-stu-id="11d24-103">Counter Name: Calls Faulted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="11d24-104">Description</span><span class="sxs-lookup"><span data-stu-id="11d24-104">Description</span></span>  

 <span data-ttu-id="11d24-105">Nombre d'appels effectués vers ce service ayant retourné une erreur.</span><span class="sxs-lookup"><span data-stu-id="11d24-105">Number of calls to this service that have returned faults.</span></span> <span data-ttu-id="11d24-106">Dans les applications Windows Communication Foundation (WCF), les méthodes de service communiquent les informations d’erreur à l’aide de messages d’erreur SOAP.</span><span class="sxs-lookup"><span data-stu-id="11d24-106">In Windows Communication Foundation (WCF) applications, service methods communicate processing error information using SOAP fault messages.</span></span> <span data-ttu-id="11d24-107">Les erreurs SOAP sont des types de message inclus dans les métadonnées d'une opération de service et créent, par conséquent, un contrat d'erreur permettant aux clients d'améliorer la fiabilité ou l'interactivité de leur exécution.</span><span class="sxs-lookup"><span data-stu-id="11d24-107">SOAP faults are message types that are included in the metadata for a service operation and therefore create a fault contract that clients can use to make their execution more robust or interactive.</span></span> <span data-ttu-id="11d24-108">Les erreurs SOAP étant exprimées aux clients dans un format XML, elles sont très interopérables.</span><span class="sxs-lookup"><span data-stu-id="11d24-108">Since SOAP faults are expressed to clients in XML form, they are highly interoperable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11d24-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="11d24-109">See also</span></span>

- [<span data-ttu-id="11d24-110">Spécification et gestion des erreurs dans les contrats et les services</span><span class="sxs-lookup"><span data-stu-id="11d24-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../specifying-and-handling-faults-in-contracts-and-services.md)

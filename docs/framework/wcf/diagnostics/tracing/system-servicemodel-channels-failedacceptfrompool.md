---
title: System.ServiceModel.Channels.FailedAcceptFromPool
ms.date: 03/30/2017
ms.assetid: d535b1b5-ee58-45e8-b400-7d9570f4eb9a
ms.openlocfilehash: 8615cca7d4ed8ea1f40baa9502e7136d4349eb9c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96256311"
---
# <a name="systemservicemodelchannelsfailedacceptfrompool"></a><span data-ttu-id="d505e-102">System.ServiceModel.Channels.FailedAcceptFromPool</span><span class="sxs-lookup"><span data-stu-id="d505e-102">System.ServiceModel.Channels.FailedAcceptFromPool</span></span>

<span data-ttu-id="d505e-103">Échec de la tentative de réutilisation d'une connexion en groupe.</span><span class="sxs-lookup"><span data-stu-id="d505e-103">An attempt to reuse a pooled connection failed.</span></span> <span data-ttu-id="d505e-104">Une autre tentative est effectuée dans le délai d'attente spécifié.</span><span class="sxs-lookup"><span data-stu-id="d505e-104">Another attempt is made within the specified timeout period.</span></span>  
  
## <a name="description"></a><span data-ttu-id="d505e-105">Description</span><span class="sxs-lookup"><span data-stu-id="d505e-105">Description</span></span>  

 <span data-ttu-id="d505e-106">Ce suivi d'informations indique qu'une erreur s'est produite lors de la tentative de réutilisation d'une connexion en groupe.</span><span class="sxs-lookup"><span data-stu-id="d505e-106">This informational trace indicates that an error has occurred while attempting to reuse a pooled connection.</span></span> <span data-ttu-id="d505e-107">Cela peut se produire si la connexion en groupe n'est pas compatible, prête ou toujours active.</span><span class="sxs-lookup"><span data-stu-id="d505e-107">This could happen because the pooled connection was not compatible, ready, or still active.</span></span> <span data-ttu-id="d505e-108">Toute tentative supplémentaire pour réutiliser une autre connexion en groupe est effectuée au cours d'un délai d'expiration donné et une nouvelle connexion est créée si aucune connexion utilisable n'est trouvée.</span><span class="sxs-lookup"><span data-stu-id="d505e-108">Additional attempts to reuse other pooled connection are made within a given timeout and a new connection is created in case no usable connections are found.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d505e-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d505e-109">See also</span></span>

- [<span data-ttu-id="d505e-110">Suivi</span><span class="sxs-lookup"><span data-stu-id="d505e-110">Tracing</span></span>](index.md)
- [<span data-ttu-id="d505e-111">Utilisation du suivi pour résoudre les problèmes posés par votre application</span><span class="sxs-lookup"><span data-stu-id="d505e-111">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="d505e-112">Administration et diagnostics</span><span class="sxs-lookup"><span data-stu-id="d505e-112">Administration and Diagnostics</span></span>](../index.md)

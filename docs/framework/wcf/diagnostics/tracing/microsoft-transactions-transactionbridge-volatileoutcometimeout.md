---
title: Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout
ms.date: 03/30/2017
ms.assetid: 2dbe34c5-57c7-4b64-9257-63021911d03c
ms.openlocfilehash: bc2cdc2221ec522b44c36ef3320b77124d61850e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96236700"
---
# <a name="microsofttransactionstransactionbridgevolatileoutcometimeout"></a><span data-ttu-id="9952f-102">Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout</span><span class="sxs-lookup"><span data-stu-id="9952f-102">Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout</span></span>

<span data-ttu-id="9952f-103">Le service du protocole WS-AT a dépassé le délai spécifié lors de l'attente d'une réponse à un message de résultat provenant d'un participant volatil.</span><span class="sxs-lookup"><span data-stu-id="9952f-103">The WS-AT protocol service timed out waiting for a response to an outcome message from a volatile participant.</span></span> <span data-ttu-id="9952f-104">Le résultat de la transaction peut s'avérer incertain si le participant retourne.</span><span class="sxs-lookup"><span data-stu-id="9952f-104">The transaction outcome may be in doubt if the participant returns.</span></span>  
  
## <a name="description"></a><span data-ttu-id="9952f-105">Description</span><span class="sxs-lookup"><span data-stu-id="9952f-105">Description</span></span>  

 <span data-ttu-id="9952f-106">Suivi lorsqu’un participant volatil a décidé de valider ou d’abandonner mais n’a pas répondu à une demande de validation ou de restauration dans un délai donné.</span><span class="sxs-lookup"><span data-stu-id="9952f-106">Traced when a Volatile participant has decided to Commit or Abort but has not responded to a Commit or Rollback request within a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="9952f-107">Dépannage</span><span class="sxs-lookup"><span data-stu-id="9952f-107">Troubleshooting</span></span>  

 <span data-ttu-id="9952f-108">Assurez-vous que tous les participants volatils sont en mesure de répondre dans le délai imparti.</span><span class="sxs-lookup"><span data-stu-id="9952f-108">Ensure that all Volatile participants are able to respond within the given amount of time.</span></span> <span data-ttu-id="9952f-109">Le délai par défaut est de 180 secondes.</span><span class="sxs-lookup"><span data-stu-id="9952f-109">The default time period is 180 seconds.</span></span>  <span data-ttu-id="9952f-110">S'il est insuffisant, augmentez le délai du minuteur `VolatileOutcomeDelay` de WS-AT.</span><span class="sxs-lookup"><span data-stu-id="9952f-110">If this is insufficient, increase the `VolatileOutcomeDelay` timer policy for WS-AT.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9952f-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9952f-111">See also</span></span>

- [<span data-ttu-id="9952f-112">Suivi</span><span class="sxs-lookup"><span data-stu-id="9952f-112">Tracing</span></span>](index.md)
- [<span data-ttu-id="9952f-113">Utilisation du suivi pour résoudre les problèmes posés par votre application</span><span class="sxs-lookup"><span data-stu-id="9952f-113">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="9952f-114">Administration et diagnostics</span><span class="sxs-lookup"><span data-stu-id="9952f-114">Administration and Diagnostics</span></span>](../index.md)

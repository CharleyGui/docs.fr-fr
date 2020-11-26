---
title: Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing
ms.date: 03/30/2017
ms.assetid: 10ef3876-6f8e-4d4e-8444-f47847b64795
ms.openlocfilehash: bfa279887339f025e4cb7c9c455fd25098684073
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96236609"
---
# <a name="microsofttransactionstransactionbridgedurableparticipantreplaywhilepreparing"></a><span data-ttu-id="bb5a0-102">Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing</span><span class="sxs-lookup"><span data-stu-id="bb5a0-102">Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing</span></span>

<span data-ttu-id="bb5a0-103">Le service de protocole WS-AT a reçu un message Replay d'un participant durable n'ayant pas répondu au message Prepared.</span><span class="sxs-lookup"><span data-stu-id="bb5a0-103">The WS-AT protocol service received a Replay message from a durable participant, which did not respond to Prepare.</span></span> <span data-ttu-id="bb5a0-104">Par conséquent, la transaction a été abandonnée.</span><span class="sxs-lookup"><span data-stu-id="bb5a0-104">Consequently, the transaction was aborted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="bb5a0-105">Description</span><span class="sxs-lookup"><span data-stu-id="bb5a0-105">Description</span></span>  

 <span data-ttu-id="bb5a0-106">Un suivi est généré si un message Replay est reçu lorsqu'un participant durable est encore en cours de préparation.</span><span class="sxs-lookup"><span data-stu-id="bb5a0-106">Traced if a Replay message is received while a Durable participant is still Preparing.</span></span> <span data-ttu-id="bb5a0-107">Il s’agit d’un message illégal pour cet état et la transaction va être abandonnée.</span><span class="sxs-lookup"><span data-stu-id="bb5a0-107">This is an illegal message for this state and the transaction is going to be aborted.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="bb5a0-108">Dépannage</span><span class="sxs-lookup"><span data-stu-id="bb5a0-108">Troubleshooting</span></span>

<span data-ttu-id="bb5a0-109">La réception de cette erreur peut indiquer qu’un participant durable (y compris subalterne subordonné) a récupéré d’une défaillance ; Toutefois, il ne garantit pas le résultat de la transaction et demande son état.</span><span class="sxs-lookup"><span data-stu-id="bb5a0-109">Receiving this error can indicate that a Durable participant (including Subordinate TransactionManagers) has recovered from failure; however, it is unsure of the transaction outcome and requests its status.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb5a0-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bb5a0-110">See also</span></span>

- [<span data-ttu-id="bb5a0-111">Suivi</span><span class="sxs-lookup"><span data-stu-id="bb5a0-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="bb5a0-112">Utilisation du suivi pour résoudre les problèmes posés par votre application</span><span class="sxs-lookup"><span data-stu-id="bb5a0-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="bb5a0-113">Administration et diagnostics</span><span class="sxs-lookup"><span data-stu-id="bb5a0-113">Administration and Diagnostics</span></span>](../index.md)

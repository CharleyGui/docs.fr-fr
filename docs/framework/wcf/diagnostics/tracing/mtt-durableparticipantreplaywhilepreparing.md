---
title: Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing
ms.date: 03/30/2017
ms.assetid: 10ef3876-6f8e-4d4e-8444-f47847b64795
ms.openlocfilehash: 93354fbdd0c1726280526ca07a8b3dd1c57c8a25
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2019
ms.locfileid: "67486770"
---
# <a name="microsofttransactionstransactionbridgedurableparticipantreplaywhilepreparing"></a><span data-ttu-id="8b4ce-102">Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing</span><span class="sxs-lookup"><span data-stu-id="8b4ce-102">Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing</span></span>
<span data-ttu-id="8b4ce-103">Le service de protocole WS-AT a reçu un message Replay d'un participant durable n'ayant pas répondu au message Prepared.</span><span class="sxs-lookup"><span data-stu-id="8b4ce-103">The WS-AT protocol service received a Replay message from a durable participant, which did not respond to Prepare.</span></span> <span data-ttu-id="8b4ce-104">Par conséquent, la transaction a été abandonnée.</span><span class="sxs-lookup"><span data-stu-id="8b4ce-104">Consequently, the transaction was aborted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="8b4ce-105">Description</span><span class="sxs-lookup"><span data-stu-id="8b4ce-105">Description</span></span>  
 <span data-ttu-id="8b4ce-106">Un suivi est généré si un message Replay est reçu lorsqu'un participant durable est encore en cours de préparation.</span><span class="sxs-lookup"><span data-stu-id="8b4ce-106">Traced if a Replay message is received while a Durable participant is still Preparing.</span></span> <span data-ttu-id="8b4ce-107">Il s’agit d’un message illégal pour cet état et la transaction va être abandonnée.</span><span class="sxs-lookup"><span data-stu-id="8b4ce-107">This is an illegal message for this state and the transaction is going to be aborted.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="8b4ce-108">Résolution des problèmes</span><span class="sxs-lookup"><span data-stu-id="8b4ce-108">Troubleshooting</span></span>

<span data-ttu-id="8b4ce-109">Réception de cette erreur peut indiquer qu’un participant Durable (y compris le subalterne) a récupéré à partir de l’échec ; Toutefois, il n’est pas sûr du résultat et demande son état.</span><span class="sxs-lookup"><span data-stu-id="8b4ce-109">Receiving this error can indicate that a Durable participant (including Subordinate TransactionManagers) has recovered from failure; however, it is unsure of the transaction outcome and requests its status.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b4ce-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8b4ce-110">See also</span></span>

- [<span data-ttu-id="8b4ce-111">Suivi</span><span class="sxs-lookup"><span data-stu-id="8b4ce-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="8b4ce-112">Utilisation du suivi pour résoudre les problèmes posés par votre application</span><span class="sxs-lookup"><span data-stu-id="8b4ce-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="8b4ce-113">Administration et diagnostics</span><span class="sxs-lookup"><span data-stu-id="8b4ce-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)

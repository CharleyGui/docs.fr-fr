---
title: Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt
ms.date: 03/30/2017
ms.assetid: 3e8fc825-9f22-47e7-9c16-d64ef291c932
ms.openlocfilehash: 9ad9dc9fd078f7ad4c0934c8bf9bb73feb935014
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96236648"
---
# <a name="microsofttransactionstransactionbridgevolatileparticipantindoubt"></a><span data-ttu-id="b507f-102">Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt</span><span class="sxs-lookup"><span data-stu-id="b507f-102">Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt</span></span>

<span data-ttu-id="b507f-103">Le service du protocole WS-AT a reçu un message Prepared ou Replay d'un participant volatil non reconnu.</span><span class="sxs-lookup"><span data-stu-id="b507f-103">The WS-AT protocol service received a Prepared or Replay message from an unrecognized volatile participant.</span></span> <span data-ttu-id="b507f-104">Une faute a été renvoyée au participant, qui déclarera que le résultat de la transaction est douteux.</span><span class="sxs-lookup"><span data-stu-id="b507f-104">A fault was returned to the participant, declares that the transaction's outcome is in doubt.</span></span>  
  
## <a name="description"></a><span data-ttu-id="b507f-105">Description</span><span class="sxs-lookup"><span data-stu-id="b507f-105">Description</span></span>  

 <span data-ttu-id="b507f-106">Suivi généré lorsque le gestionnaire de transactions local reçoit un message Prepared ou Replay d’une inscription volatile qu’il a déjà oubliée.</span><span class="sxs-lookup"><span data-stu-id="b507f-106">Traced when the local Transaction Manager receives a Prepared or Replay message from a Volatile enlistment that it has already forgotten.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="b507f-107">Dépannage</span><span class="sxs-lookup"><span data-stu-id="b507f-107">Troubleshooting</span></span>  

 <span data-ttu-id="b507f-108">Recherchez les causes potentielles de retard des messages qui viennent du participant volatil.</span><span class="sxs-lookup"><span data-stu-id="b507f-108">Investigate potential causes of late messages coming from the Volatile participant.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b507f-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b507f-109">See also</span></span>

- [<span data-ttu-id="b507f-110">Suivi</span><span class="sxs-lookup"><span data-stu-id="b507f-110">Tracing</span></span>](index.md)
- [<span data-ttu-id="b507f-111">Utilisation du suivi pour résoudre les problèmes posés par votre application</span><span class="sxs-lookup"><span data-stu-id="b507f-111">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="b507f-112">Administration et diagnostics</span><span class="sxs-lookup"><span data-stu-id="b507f-112">Administration and Diagnostics</span></span>](../index.md)

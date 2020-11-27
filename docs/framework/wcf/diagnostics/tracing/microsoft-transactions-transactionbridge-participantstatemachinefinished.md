---
title: Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished
ms.date: 03/30/2017
ms.assetid: 54b677f7-03ad-40f2-9c5d-297a8ad9bf90
ms.openlocfilehash: bd6c9124e6346437e2bb35df620e00bad13b60f3
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96258944"
---
# <a name="microsofttransactionstransactionbridgeparticipantstatemachinefinished"></a><span data-ttu-id="6cace-102">Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished</span><span class="sxs-lookup"><span data-stu-id="6cace-102">Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished</span></span>

<span data-ttu-id="6cace-103">La machine à états pour un enrôlement de participant est passée à l'état Finished.</span><span class="sxs-lookup"><span data-stu-id="6cace-103">The state machine for a participant enlistment entered the finished state.</span></span>  
  
## <a name="description"></a><span data-ttu-id="6cace-104">Description</span><span class="sxs-lookup"><span data-stu-id="6cace-104">Description</span></span>  

 <span data-ttu-id="6cace-105">Suivi lorsqu'un enrôlement de participant subalterne a terminé le traitement 2PC.</span><span class="sxs-lookup"><span data-stu-id="6cace-105">Traced when a subordinate participant enlistment has completed 2pc processing.</span></span> <span data-ttu-id="6cace-106">Le résultat peut être Committed ou Aborted.</span><span class="sxs-lookup"><span data-stu-id="6cace-106">The outcome for the enlistment can be Committed or Aborted.</span></span> <span data-ttu-id="6cace-107">Il est également suivi lorsque les participants votent ReadOnly pendant la préparation.</span><span class="sxs-lookup"><span data-stu-id="6cace-107">It is also traced if any participant votes ReadOnly during Prepare.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cace-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6cace-108">See also</span></span>

- [<span data-ttu-id="6cace-109">Suivi</span><span class="sxs-lookup"><span data-stu-id="6cace-109">Tracing</span></span>](index.md)
- [<span data-ttu-id="6cace-110">Utilisation du suivi pour résoudre les problèmes posés par votre application</span><span class="sxs-lookup"><span data-stu-id="6cace-110">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="6cace-111">Administration et diagnostics</span><span class="sxs-lookup"><span data-stu-id="6cace-111">Administration and Diagnostics</span></span>](../index.md)

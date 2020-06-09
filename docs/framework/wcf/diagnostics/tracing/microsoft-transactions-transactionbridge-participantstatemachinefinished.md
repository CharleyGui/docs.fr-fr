---
title: Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished
ms.date: 03/30/2017
ms.assetid: 54b677f7-03ad-40f2-9c5d-297a8ad9bf90
ms.openlocfilehash: 0652b3b76c155431b68c5ee0dc8f83977f9845a5
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594359"
---
# <a name="microsofttransactionstransactionbridgeparticipantstatemachinefinished"></a><span data-ttu-id="7ec6c-102">Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished</span><span class="sxs-lookup"><span data-stu-id="7ec6c-102">Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished</span></span>
<span data-ttu-id="7ec6c-103">La machine à états pour un enrôlement de participant est passée à l'état Finished.</span><span class="sxs-lookup"><span data-stu-id="7ec6c-103">The state machine for a participant enlistment entered the finished state.</span></span>  
  
## <a name="description"></a><span data-ttu-id="7ec6c-104">Description</span><span class="sxs-lookup"><span data-stu-id="7ec6c-104">Description</span></span>  
 <span data-ttu-id="7ec6c-105">Suivi lorsqu'un enrôlement de participant subalterne a terminé le traitement 2PC.</span><span class="sxs-lookup"><span data-stu-id="7ec6c-105">Traced when a subordinate participant enlistment has completed 2pc processing.</span></span> <span data-ttu-id="7ec6c-106">Le résultat peut être Committed ou Aborted.</span><span class="sxs-lookup"><span data-stu-id="7ec6c-106">The outcome for the enlistment can be Committed or Aborted.</span></span> <span data-ttu-id="7ec6c-107">Il est également suivi lorsque les participants votent ReadOnly pendant la préparation.</span><span class="sxs-lookup"><span data-stu-id="7ec6c-107">It is also traced if any participant votes ReadOnly during Prepare.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ec6c-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7ec6c-108">See also</span></span>

- [<span data-ttu-id="7ec6c-109">Suivi</span><span class="sxs-lookup"><span data-stu-id="7ec6c-109">Tracing</span></span>](index.md)
- [<span data-ttu-id="7ec6c-110">Utilisation du suivi pour résoudre les problèmes posés par votre application</span><span class="sxs-lookup"><span data-stu-id="7ec6c-110">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="7ec6c-111">Administration et diagnostics</span><span class="sxs-lookup"><span data-stu-id="7ec6c-111">Administration and Diagnostics</span></span>](../index.md)

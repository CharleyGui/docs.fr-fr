---
title: Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished
ms.date: 03/30/2017
ms.assetid: 16cb428d-d886-4789-a961-6fded4b0dbba
ms.openlocfilehash: 3b9a3703e49c3932f62fcfb6994c9028b074bbe8
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594411"
---
# <a name="microsofttransactionstransactionbridgecoordinatorstatemachinefinished"></a><span data-ttu-id="89b42-102">Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished</span><span class="sxs-lookup"><span data-stu-id="89b42-102">Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished</span></span>
<span data-ttu-id="89b42-103">La machine à états pour un enrôlement de coordinateur est passée à l'état Finished.</span><span class="sxs-lookup"><span data-stu-id="89b42-103">The state machine for a coordinator enlistment has entered the finished state.</span></span>  
  
## <a name="description"></a><span data-ttu-id="89b42-104">Description</span><span class="sxs-lookup"><span data-stu-id="89b42-104">Description</span></span>  
 <span data-ttu-id="89b42-105">Suivi lorsque le gestionnaire de transactions local croit qu’un enrôlement de coordinateur supérieur a terminé le traitement 2PC.</span><span class="sxs-lookup"><span data-stu-id="89b42-105">Traced when the local Transaction Manager believes a superior coordinator enlistment has completed 2pc processing.</span></span> <span data-ttu-id="89b42-106">Le résultat peut être Committed, Aborted ou Forgotten.</span><span class="sxs-lookup"><span data-stu-id="89b42-106">The outcome for the enlistment can be Committed or Aborted or Forgotten.</span></span> <span data-ttu-id="89b42-107">Suivi également lorsque le gestionnaire de transaction local vote ReadOnly pendant la préparation.</span><span class="sxs-lookup"><span data-stu-id="89b42-107">It is also traced if the local Transaction Manager votes ReadOnly during Prepare.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89b42-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="89b42-108">See also</span></span>

- [<span data-ttu-id="89b42-109">Suivi</span><span class="sxs-lookup"><span data-stu-id="89b42-109">Tracing</span></span>](index.md)
- [<span data-ttu-id="89b42-110">Utilisation du suivi pour résoudre les problèmes posés par votre application</span><span class="sxs-lookup"><span data-stu-id="89b42-110">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="89b42-111">Administration et diagnostics</span><span class="sxs-lookup"><span data-stu-id="89b42-111">Administration and Diagnostics</span></span>](../index.md)

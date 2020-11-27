---
title: System.ServiceModel.TxCompletionStatusAbortedOnSessionClose
ms.date: 03/30/2017
ms.assetid: 7e142e9d-e81b-4309-974a-02e9cc064ea0
ms.openlocfilehash: 0d8c77d01351b0c62e0186e5aee69ca70aebe15e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96274320"
---
# <a name="systemservicemodeltxcompletionstatusabortedonsessionclose"></a><span data-ttu-id="24948-102">System.ServiceModel.TxCompletionStatusAbortedOnSessionClose</span><span class="sxs-lookup"><span data-stu-id="24948-102">System.ServiceModel.TxCompletionStatusAbortedOnSessionClose</span></span>

<span data-ttu-id="24948-103">La transaction spécifiée a été abandonnée car elle était inachevée lorsque la session a été fermée et le OperationBehaviorAttribute TransactionAutoCompleteOnSessionClose a été défini à false.</span><span class="sxs-lookup"><span data-stu-id="24948-103">The specified transaction was aborted because it was uncompleted when the session was closed and the TransactionAutoCompleteOnSessionClose OperationBehaviorAttribute was set to false.</span></span>  
  
## <a name="description"></a><span data-ttu-id="24948-104">Description</span><span class="sxs-lookup"><span data-stu-id="24948-104">Description</span></span>  

 <span data-ttu-id="24948-105">Suivi si la session active actuelle a été fermée, que la transaction n'a pas été achevée et que TransactionAutoCompleteOnSessionClose a la valeur `false`.</span><span class="sxs-lookup"><span data-stu-id="24948-105">Traced if the current active session was closed, and the transaction was not completed, and TransactionAutoCompleteOnSessionClose is set to `false`.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="24948-106">Dépannage</span><span class="sxs-lookup"><span data-stu-id="24948-106">Troubleshooting</span></span>  

 <span data-ttu-id="24948-107">Cette trace indique un bogue d'application potentiel qui doit être étudié.</span><span class="sxs-lookup"><span data-stu-id="24948-107">This trace indicates a potential application bug that should be investigated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24948-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="24948-108">See also</span></span>

- [<span data-ttu-id="24948-109">Suivi</span><span class="sxs-lookup"><span data-stu-id="24948-109">Tracing</span></span>](index.md)
- [<span data-ttu-id="24948-110">Utilisation du suivi pour résoudre les problèmes posés par votre application</span><span class="sxs-lookup"><span data-stu-id="24948-110">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="24948-111">Administration et diagnostics</span><span class="sxs-lookup"><span data-stu-id="24948-111">Administration and Diagnostics</span></span>](../index.md)

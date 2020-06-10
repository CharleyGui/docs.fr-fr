---
title: Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure
ms.date: 03/30/2017
ms.assetid: 1b9f5139-e122-4716-9ef7-2f38e1813993
ms.openlocfilehash: 742e80a3115e8f8caa728e0d8c460ee8b964ddc9
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84588715"
---
# <a name="microsofttransactionstransactionbridgeenlisttransactionfailure"></a><span data-ttu-id="29545-102">Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure</span><span class="sxs-lookup"><span data-stu-id="29545-102">Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure</span></span>
<span data-ttu-id="29545-103">Le service du protocole WS-AT a échoué l'enrôlement sur une transaction en utilisant le contexte de coordination fourni.</span><span class="sxs-lookup"><span data-stu-id="29545-103">The WS-AT protocol service failed to enlist on a transaction using the provided coordination context.</span></span>  
  
## <a name="description"></a><span data-ttu-id="29545-104">Description</span><span class="sxs-lookup"><span data-stu-id="29545-104">Description</span></span>  
 <span data-ttu-id="29545-105">Suivi lorsque MSDTC ne peut pas enrôler sur une transaction pour un protocole 2PC donné.</span><span class="sxs-lookup"><span data-stu-id="29545-105">Traced when MSDTC is unable to enlist on a transaction for a given 2pc protocol.</span></span>  <span data-ttu-id="29545-106">Cela peut être dû au fait que la transaction n'existe plus, que l'enrôlement n'est plus autorisé, ou qu'un trop grand nombre d'enrôlements sont déjà présents.</span><span class="sxs-lookup"><span data-stu-id="29545-106">This can happen because the transaction no longer exists, enlisting is no longer allowed, or too many enlistments are already present.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="29545-107">Dépannage</span><span class="sxs-lookup"><span data-stu-id="29545-107">Troubleshooting</span></span>  
 <span data-ttu-id="29545-108">Inspectez la chaîne d'état dans le message de suivi pour déterminer la présence éventuelle d'éléments actionnables.</span><span class="sxs-lookup"><span data-stu-id="29545-108">Inspect the status string within the trace message to determine if any actionable item exists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29545-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="29545-109">See also</span></span>

- [<span data-ttu-id="29545-110">Suivi</span><span class="sxs-lookup"><span data-stu-id="29545-110">Tracing</span></span>](index.md)
- [<span data-ttu-id="29545-111">Utilisation du suivi pour résoudre les problèmes posés par votre application</span><span class="sxs-lookup"><span data-stu-id="29545-111">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="29545-112">Administration et diagnostics</span><span class="sxs-lookup"><span data-stu-id="29545-112">Administration and Diagnostics</span></span>](../index.md)

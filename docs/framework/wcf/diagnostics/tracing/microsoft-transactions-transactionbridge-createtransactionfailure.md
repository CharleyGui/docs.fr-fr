---
title: Microsoft.Transactions.TransactionBridge.CreateTransactionFailure
ms.date: 03/30/2017
ms.assetid: c3468e23-49a9-4a84-972d-a79a658851b3
ms.openlocfilehash: 09b93ce4b72416cfea9f8c9850fd1e50c77035b7
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96270218"
---
# <a name="microsofttransactionstransactionbridgecreatetransactionfailure"></a><span data-ttu-id="45aa8-102">Microsoft.Transactions.TransactionBridge.CreateTransactionFailure</span><span class="sxs-lookup"><span data-stu-id="45aa8-102">Microsoft.Transactions.TransactionBridge.CreateTransactionFailure</span></span>

<span data-ttu-id="45aa8-103">Une transaction n’a pas pu être créée.</span><span class="sxs-lookup"><span data-stu-id="45aa8-103">A transaction could not be created.</span></span>  
  
## <a name="description"></a><span data-ttu-id="45aa8-104">Description</span><span class="sxs-lookup"><span data-stu-id="45aa8-104">Description</span></span>  

 <span data-ttu-id="45aa8-105">Ce suivi est généré lorsque MSDTC ne peut pas créer de transaction.</span><span class="sxs-lookup"><span data-stu-id="45aa8-105">This trace is generated when MSDTC is unable to create a transaction.</span></span> <span data-ttu-id="45aa8-106">Cela peut être dû à des ressources faibles, un espace de journal insuffisant ou d'autres erreurs.</span><span class="sxs-lookup"><span data-stu-id="45aa8-106">This can be due to low resources, insufficient log space, or other errors.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="45aa8-107">Dépannage</span><span class="sxs-lookup"><span data-stu-id="45aa8-107">Troubleshooting</span></span>  

 <span data-ttu-id="45aa8-108">Inspectez la chaîne d'état dans le message de suivi pour déterminer la présence éventuelle d'éléments actionnables.</span><span class="sxs-lookup"><span data-stu-id="45aa8-108">Inspect the status string within the trace message to determine if any actionable item exists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45aa8-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="45aa8-109">See also</span></span>

- [<span data-ttu-id="45aa8-110">Suivi</span><span class="sxs-lookup"><span data-stu-id="45aa8-110">Tracing</span></span>](index.md)
- [<span data-ttu-id="45aa8-111">Utilisation du suivi pour résoudre les problèmes posés par votre application</span><span class="sxs-lookup"><span data-stu-id="45aa8-111">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="45aa8-112">Administration et diagnostics</span><span class="sxs-lookup"><span data-stu-id="45aa8-112">Administration and Diagnostics</span></span>](../index.md)

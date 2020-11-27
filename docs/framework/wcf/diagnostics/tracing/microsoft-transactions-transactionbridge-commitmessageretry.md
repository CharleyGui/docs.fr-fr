---
title: Microsoft.Transactions.TransactionBridge.CommitMessageRetry
ms.date: 03/30/2017
ms.assetid: 4abe01f0-6398-4fba-b2f3-c054b7f7e971
ms.openlocfilehash: 28b83b293570adf3b1cfdc15c77afd0f0cf768eb
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96259023"
---
# <a name="microsofttransactionstransactionbridgecommitmessageretry"></a><span data-ttu-id="9c30b-102">Microsoft.Transactions.TransactionBridge.CommitMessageRetry</span><span class="sxs-lookup"><span data-stu-id="9c30b-102">Microsoft.Transactions.TransactionBridge.CommitMessageRetry</span></span>

<span data-ttu-id="9c30b-103">Une nouvelle tentative de message de validation a été envoyée à un participant qui ne répond pas.</span><span class="sxs-lookup"><span data-stu-id="9c30b-103">A commit message retry was sent to an unresponsive participant.</span></span>  
  
## <a name="description"></a><span data-ttu-id="9c30b-104">Description</span><span class="sxs-lookup"><span data-stu-id="9c30b-104">Description</span></span>  

 <span data-ttu-id="9c30b-105">Suivi lorsque le gestionnaire de transactions local a dû renvoyer un message de validation à un participant subalterne parce qu'il n'a pas reçu de réponse dans un délai donné.</span><span class="sxs-lookup"><span data-stu-id="9c30b-105">Traced if the local Transaction Manager needed to resend a Commit message to a subordinate participant because it did not receive a response in a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="9c30b-106">Dépannage</span><span class="sxs-lookup"><span data-stu-id="9c30b-106">Troubleshooting</span></span>  

 <span data-ttu-id="9c30b-107">Recherchez d'éventuels problèmes liés au réseau ou au produit pouvant empêcher la réponse d'être remise à temps.</span><span class="sxs-lookup"><span data-stu-id="9c30b-107">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="9c30b-108">Si un nombre élevé de ces messages apparaissent, cela peut indiquer des problèmes d'infrastructure ou des délais de réponse anormalement longs.</span><span class="sxs-lookup"><span data-stu-id="9c30b-108">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="9c30b-109">Ces deux problèmes réduiront considérablement le débit des transactions au sein du système.</span><span class="sxs-lookup"><span data-stu-id="9c30b-109">Both issues will drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c30b-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9c30b-110">See also</span></span>

- [<span data-ttu-id="9c30b-111">Suivi</span><span class="sxs-lookup"><span data-stu-id="9c30b-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="9c30b-112">Utilisation du suivi pour résoudre les problèmes posés par votre application</span><span class="sxs-lookup"><span data-stu-id="9c30b-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="9c30b-113">Administration et diagnostics</span><span class="sxs-lookup"><span data-stu-id="9c30b-113">Administration and Diagnostics</span></span>](../index.md)

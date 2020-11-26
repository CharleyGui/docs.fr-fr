---
title: Microsoft.Transactions.TransactionBridge.ReplayMessageRetry
ms.date: 03/30/2017
ms.assetid: e5b820ae-504d-405a-926a-9effa41d2369
ms.openlocfilehash: 23a0113488b1b1ef0bc161d4134b9325ef81406c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96236713"
---
# <a name="microsofttransactionstransactionbridgereplaymessageretry"></a><span data-ttu-id="bfac3-102">Microsoft.Transactions.TransactionBridge.ReplayMessageRetry</span><span class="sxs-lookup"><span data-stu-id="bfac3-102">Microsoft.Transactions.TransactionBridge.ReplayMessageRetry</span></span>

<span data-ttu-id="bfac3-103">Une nouvelle tentative de message Replay a été envoyée à un coordinateur qui ne répond pas.</span><span class="sxs-lookup"><span data-stu-id="bfac3-103">A replay message retry was sent to an unresponsive coordinator.</span></span>  
  
## <a name="description"></a><span data-ttu-id="bfac3-104">Description</span><span class="sxs-lookup"><span data-stu-id="bfac3-104">Description</span></span>  

 <span data-ttu-id="bfac3-105">Suivi si le gestionnaire de transactions local a dû renvoyer un message Replay à un coordinateur supérieur parce qu’il n’a pas reçu de réponse dans un délai donné.</span><span class="sxs-lookup"><span data-stu-id="bfac3-105">Traced if the local Transaction Manager needed to resend a Replay message to a superior coordinator because it did not receive a response in a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="bfac3-106">Dépannage</span><span class="sxs-lookup"><span data-stu-id="bfac3-106">Troubleshooting</span></span>  

 <span data-ttu-id="bfac3-107">Recherchez d'éventuels problèmes liés au réseau ou au produit pouvant empêcher la réponse d'être remise à temps.</span><span class="sxs-lookup"><span data-stu-id="bfac3-107">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="bfac3-108">Si un nombre élevé de ces messages apparaissent, cela peut indiquer des problèmes d'infrastructure ou des délais de réponse anormalement longs.</span><span class="sxs-lookup"><span data-stu-id="bfac3-108">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="bfac3-109">Ces deux problèmes réduiront considérablement le débit des transactions au sein du système.</span><span class="sxs-lookup"><span data-stu-id="bfac3-109">Both issues will drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfac3-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bfac3-110">See also</span></span>

- [<span data-ttu-id="bfac3-111">Suivi</span><span class="sxs-lookup"><span data-stu-id="bfac3-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="bfac3-112">Utilisation du suivi pour résoudre les problèmes posés par votre application</span><span class="sxs-lookup"><span data-stu-id="bfac3-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="bfac3-113">Administration et diagnostics</span><span class="sxs-lookup"><span data-stu-id="bfac3-113">Administration and Diagnostics</span></span>](../index.md)

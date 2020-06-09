---
title: Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure
ms.date: 03/30/2017
ms.assetid: 3a4ead79-8550-4037-84e3-fd70ff56e001
ms.openlocfilehash: 1819a269a6775c8541f38f4aa5d733002e3c1e9f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599675"
---
# <a name="microsofttransactionstransactionbridgeregisterparticipantfailure"></a><span data-ttu-id="617d7-102">Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure</span><span class="sxs-lookup"><span data-stu-id="617d7-102">Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure</span></span>
<span data-ttu-id="617d7-103">Le service de protocole WS-AT n'a pas pu inscrire un participant à un protocole de contrôle.</span><span class="sxs-lookup"><span data-stu-id="617d7-103">The WS-AT protocol service failed to register a participant for a control protocol.</span></span>  
  
## <a name="description"></a><span data-ttu-id="617d7-104">Description</span><span class="sxs-lookup"><span data-stu-id="617d7-104">Description</span></span>  
 <span data-ttu-id="617d7-105">Suivi lorsque MSDTC détecte une demande d'inscription non valide.</span><span class="sxs-lookup"><span data-stu-id="617d7-105">Traced if MSDTC detects an invalid Registration request.</span></span> <span data-ttu-id="617d7-106">Cela peut être provoqué par plusieurs demandes d'inscription pour achèvement et erreurs internes.</span><span class="sxs-lookup"><span data-stu-id="617d7-106">This can be caused by  multiple Completion registration requests and internal errors.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="617d7-107">Dépannage</span><span class="sxs-lookup"><span data-stu-id="617d7-107">Troubleshooting</span></span>  
 <span data-ttu-id="617d7-108">Ne procédez pas à plusieurs demandes d'inscription pour achèvement.</span><span class="sxs-lookup"><span data-stu-id="617d7-108">Do not try to Register for Completion more than once.</span></span>  <span data-ttu-id="617d7-109">Par ailleurs, inspectez la chaîne d'état dans le message de suivi pour déterminer la présence éventuelle d'éléments actionnables.</span><span class="sxs-lookup"><span data-stu-id="617d7-109">Also, inspect the status string within the trace message to determine if any actionable item exists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="617d7-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="617d7-110">See also</span></span>

- [<span data-ttu-id="617d7-111">Suivi</span><span class="sxs-lookup"><span data-stu-id="617d7-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="617d7-112">Utilisation du suivi pour résoudre les problèmes posés par votre application</span><span class="sxs-lookup"><span data-stu-id="617d7-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="617d7-113">Administration et diagnostics</span><span class="sxs-lookup"><span data-stu-id="617d7-113">Administration and Diagnostics</span></span>](../index.md)

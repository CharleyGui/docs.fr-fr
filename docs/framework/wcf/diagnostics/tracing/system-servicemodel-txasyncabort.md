---
title: System.ServiceModel.TxAsyncAbort
ms.date: 03/30/2017
ms.assetid: bce47ff2-abd0-4b58-8667-ebf1ef3580b8
ms.openlocfilehash: fd21428279a68cd8480b6ff0617bb2a70033a40d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96269949"
---
# <a name="systemservicemodeltxasyncabort"></a><span data-ttu-id="8083c-102">System.ServiceModel.TxAsyncAbort</span><span class="sxs-lookup"><span data-stu-id="8083c-102">System.ServiceModel.TxAsyncAbort</span></span>

<span data-ttu-id="8083c-103">La transaction spécifiée a été abandonnée de façon asynchrone.</span><span class="sxs-lookup"><span data-stu-id="8083c-103">The specified transaction was asynchronously aborted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="8083c-104">Description</span><span class="sxs-lookup"><span data-stu-id="8083c-104">Description</span></span>  

 <span data-ttu-id="8083c-105">La transaction courante a été abandonnée car un autre participant a voté Abort, le délai a été dépassé et une autre erreur s’est produite à l’intérieur du participant d’une transaction.</span><span class="sxs-lookup"><span data-stu-id="8083c-105">The current transaction was aborted due to another participant voting for Abort, time-outs occurring, or another error inside the participant of a transaction.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="8083c-106">Dépannage</span><span class="sxs-lookup"><span data-stu-id="8083c-106">Troubleshooting</span></span>  

 <span data-ttu-id="8083c-107">Vérifiez tous les journaux système si cet abandon est inattendu afin de déterminer la vraie raison de l'abandon.</span><span class="sxs-lookup"><span data-stu-id="8083c-107">Check all system logs if this abort is unexpected to determine the real reason for the abort.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8083c-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8083c-108">See also</span></span>

- [<span data-ttu-id="8083c-109">Suivi</span><span class="sxs-lookup"><span data-stu-id="8083c-109">Tracing</span></span>](index.md)
- [<span data-ttu-id="8083c-110">Utilisation du suivi pour résoudre les problèmes posés par votre application</span><span class="sxs-lookup"><span data-stu-id="8083c-110">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="8083c-111">Administration et diagnostics</span><span class="sxs-lookup"><span data-stu-id="8083c-111">Administration and Diagnostics</span></span>](../index.md)

---
title: Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFailed
ms.date: 03/30/2017
ms.assetid: 96474056-0418-41e4-8c75-bbc0a853eaba
ms.openlocfilehash: 83bb67f2a5eb1a9353129bce9ec22f18eb382259
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96251969"
---
# <a name="microsofttransactionstransactionbridgeregistrationcoordinatorfailed"></a><span data-ttu-id="50f3d-102">Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFailed</span><span class="sxs-lookup"><span data-stu-id="50f3d-102">Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFailed</span></span>

<span data-ttu-id="50f3d-103">Le service du protocole WS-AT a échoué l'envoi d'un message Register à son coordinateur</span><span class="sxs-lookup"><span data-stu-id="50f3d-103">The WS-AT protocol service failed to send a Register message to its coordinator</span></span>  
  
## <a name="description"></a><span data-ttu-id="50f3d-104">Description</span><span class="sxs-lookup"><span data-stu-id="50f3d-104">Description</span></span>  

 <span data-ttu-id="50f3d-105">Un suivi est effectué si le TransactionManager local n’est pas en mesure de s’inscrire auprès de son supérieur TransactionManager en raison de l’incapacité à envoyer un message.</span><span class="sxs-lookup"><span data-stu-id="50f3d-105">Traced if the local TransactionManager is not able to Register with its superior TransactionManager due to the inability to send a message.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="50f3d-106">Dépannage</span><span class="sxs-lookup"><span data-stu-id="50f3d-106">Troubleshooting</span></span>  

 <span data-ttu-id="50f3d-107">Inspectez le message de suivi pour l'exception qui provoque l'échec de l'envoi du message.</span><span class="sxs-lookup"><span data-stu-id="50f3d-107">Inspect the trace message for the exception causing the message send failure</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50f3d-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="50f3d-108">See also</span></span>

- [<span data-ttu-id="50f3d-109">Suivi</span><span class="sxs-lookup"><span data-stu-id="50f3d-109">Tracing</span></span>](index.md)
- [<span data-ttu-id="50f3d-110">Utilisation du suivi pour résoudre les problèmes posés par votre application</span><span class="sxs-lookup"><span data-stu-id="50f3d-110">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="50f3d-111">Administration et diagnostics</span><span class="sxs-lookup"><span data-stu-id="50f3d-111">Administration and Diagnostics</span></span>](../index.md)

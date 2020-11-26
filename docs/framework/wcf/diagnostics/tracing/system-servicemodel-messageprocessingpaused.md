---
title: System.ServiceModel.MessageProcessingPaused
ms.date: 03/30/2017
ms.assetid: 36b5302a-93cc-478a-9bb2-8a1601fba1df
ms.openlocfilehash: e4c8040d2350e3824b5d68dc6f32376007792a7f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96235114"
---
# <a name="systemservicemodelmessageprocessingpaused"></a><span data-ttu-id="ce671-102">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="ce671-102">System.ServiceModel.MessageProcessingPaused</span></span>

<span data-ttu-id="ce671-103">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="ce671-103">System.ServiceModel.MessageProcessingPaused</span></span>  
  
## <a name="description"></a><span data-ttu-id="ce671-104">Description</span><span class="sxs-lookup"><span data-stu-id="ce671-104">Description</span></span>  

 <span data-ttu-id="ce671-105">Les threads ont été basculés pendant le traitement d'un message.</span><span class="sxs-lookup"><span data-stu-id="ce671-105">The threads were switched while processing a message.</span></span>  
  
 <span data-ttu-id="ce671-106">Le traitement des messages peut être suspendu pour les raisons suivantes :</span><span class="sxs-lookup"><span data-stu-id="ce671-106">Message processing can be paused by the following reasons:</span></span>  
  
- <span data-ttu-id="ce671-107">ConcurrencyMode est unique ou réentrant, et le service traite un autre message.</span><span class="sxs-lookup"><span data-stu-id="ce671-107">ConcurrencyMode is single or reentrant, and the service is processing another message.</span></span>  
  
- <span data-ttu-id="ce671-108">La transaction est activée et le service traite une autre transaction.</span><span class="sxs-lookup"><span data-stu-id="ce671-108">Transaction is enabled and the service is processing another transaction.</span></span>  
  
- <span data-ttu-id="ce671-109">Le contexte de synchronisation n’est pas à jour.</span><span class="sxs-lookup"><span data-stu-id="ce671-109">Synchronization context is not current.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce671-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ce671-110">See also</span></span>

- [<span data-ttu-id="ce671-111">Suivi</span><span class="sxs-lookup"><span data-stu-id="ce671-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="ce671-112">Utilisation du suivi pour résoudre les problèmes posés par votre application</span><span class="sxs-lookup"><span data-stu-id="ce671-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="ce671-113">Administration et diagnostics</span><span class="sxs-lookup"><span data-stu-id="ce671-113">Administration and Diagnostics</span></span>](../index.md)

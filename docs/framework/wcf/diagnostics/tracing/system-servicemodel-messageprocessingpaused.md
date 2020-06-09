---
title: System.ServiceModel.MessageProcessingPaused
ms.date: 03/30/2017
ms.assetid: 36b5302a-93cc-478a-9bb2-8a1601fba1df
ms.openlocfilehash: 85bec8255e0d20d6e76ea354e5b8c42b83d7d8e6
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598149"
---
# <a name="systemservicemodelmessageprocessingpaused"></a><span data-ttu-id="cedd6-102">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="cedd6-102">System.ServiceModel.MessageProcessingPaused</span></span>
<span data-ttu-id="cedd6-103">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="cedd6-103">System.ServiceModel.MessageProcessingPaused</span></span>  
  
## <a name="description"></a><span data-ttu-id="cedd6-104">Description</span><span class="sxs-lookup"><span data-stu-id="cedd6-104">Description</span></span>  
 <span data-ttu-id="cedd6-105">Les threads ont été basculés pendant le traitement d'un message.</span><span class="sxs-lookup"><span data-stu-id="cedd6-105">The threads were switched while processing a message.</span></span>  
  
 <span data-ttu-id="cedd6-106">Le traitement des messages peut être suspendu pour les raisons suivantes :</span><span class="sxs-lookup"><span data-stu-id="cedd6-106">Message processing can be paused by the following reasons:</span></span>  
  
- <span data-ttu-id="cedd6-107">ConcurrencyMode est unique ou réentrant, et le service traite un autre message.</span><span class="sxs-lookup"><span data-stu-id="cedd6-107">ConcurrencyMode is single or reentrant, and the service is processing another message.</span></span>  
  
- <span data-ttu-id="cedd6-108">La transaction est activée et le service traite une autre transaction.</span><span class="sxs-lookup"><span data-stu-id="cedd6-108">Transaction is enabled and the service is processing another transaction.</span></span>  
  
- <span data-ttu-id="cedd6-109">Le contexte de synchronisation n’est pas à jour.</span><span class="sxs-lookup"><span data-stu-id="cedd6-109">Synchronization context is not current.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cedd6-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cedd6-110">See also</span></span>

- [<span data-ttu-id="cedd6-111">Suivi</span><span class="sxs-lookup"><span data-stu-id="cedd6-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="cedd6-112">Utilisation du suivi pour résoudre les problèmes posés par votre application</span><span class="sxs-lookup"><span data-stu-id="cedd6-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="cedd6-113">Administration et diagnostics</span><span class="sxs-lookup"><span data-stu-id="cedd6-113">Administration and Diagnostics</span></span>](../index.md)

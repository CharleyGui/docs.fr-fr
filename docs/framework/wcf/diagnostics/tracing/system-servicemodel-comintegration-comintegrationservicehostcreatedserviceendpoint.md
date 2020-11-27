---
title: System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
ms.date: 03/30/2017
ms.assetid: d75d39da-7502-4a6a-91b9-eaa05b8e24d5
ms.openlocfilehash: aeeba38eaf674453f4c87cf62f5088c55b5fde2d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96290814"
---
# <a name="systemservicemodelchannelsmsmqmoveordeleteattemptfailed"></a><span data-ttu-id="a124a-102">System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed</span><span class="sxs-lookup"><span data-stu-id="a124a-102">System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed</span></span>

<span data-ttu-id="a124a-103">Impossible de déplacer ou de supprimer le message.</span><span class="sxs-lookup"><span data-stu-id="a124a-103">Cannot move or delete message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="a124a-104">Description</span><span class="sxs-lookup"><span data-stu-id="a124a-104">Description</span></span>  

 <span data-ttu-id="a124a-105">Le suivi indique qu'un échec a eu lieu lors de la tentative de déplacement, d'élimination ou de rejet d'un message MSMQ.</span><span class="sxs-lookup"><span data-stu-id="a124a-105">The trace indicates that a failure occurred when attempting to move, delete, or reject an MSMQ message.</span></span>  
  
 <span data-ttu-id="a124a-106">Les messages MSMQ sont utilisés par Windows Communication Foundation (WCF) (lorsqu’ils sont utilisés avec NetMsmqBinding ou MsmqIntegrationBinding). Ce suivi est lié à la valeur choisie de la `ReceiveErrorHandling` propriété sur NetMsmqBinding ou MsmqIntegrationBinding.</span><span class="sxs-lookup"><span data-stu-id="a124a-106">MSMQ messages are employed by Windows Communication Foundation (WCF) (when used with either the NetMsmqBinding or the MsmqIntegrationBinding).This trace is related to the chosen value of the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding.</span></span>  
  
 <span data-ttu-id="a124a-107">Ce suivi n'indique pas une défaillance générale du système.</span><span class="sxs-lookup"><span data-stu-id="a124a-107">This trace is not indicative of an overall system failure.</span></span> <span data-ttu-id="a124a-108">Toutefois, il indique que la disposition de message incohérent choisie a échoué pour un message.</span><span class="sxs-lookup"><span data-stu-id="a124a-108">However, it indicates that the chosen poison message disposition failed for a message.</span></span> <span data-ttu-id="a124a-109">Pour plus d’informations sur le moment où les messages deviennent incohérents et sur la façon de configurer votre service pour les gérer de manière appropriée, consultez [gestion des messages incohérents](../../feature-details/poison-message-handling.md).</span><span class="sxs-lookup"><span data-stu-id="a124a-109">For more information on when messages become poison and how to configure your service to handle them appropriately, see [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a124a-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a124a-110">See also</span></span>

- [<span data-ttu-id="a124a-111">Suivi</span><span class="sxs-lookup"><span data-stu-id="a124a-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="a124a-112">Utilisation du suivi pour résoudre les problèmes posés par votre application</span><span class="sxs-lookup"><span data-stu-id="a124a-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="a124a-113">Administration et diagnostics</span><span class="sxs-lookup"><span data-stu-id="a124a-113">Administration and Diagnostics</span></span>](../index.md)

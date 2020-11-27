---
title: System.ServiceModel.Channels.MsmqMessageDropped
ms.date: 03/30/2017
ms.assetid: 8b6e644d-fa68-4be7-abe9-3659671a37c1
ms.openlocfilehash: 6e8b134f61d2dc9bd5daf541db4ec81604166baa
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96260381"
---
# <a name="systemservicemodelchannelsmsmqmessagedropped"></a><span data-ttu-id="0bd1a-102">System.ServiceModel.Channels.MsmqMessageDropped</span><span class="sxs-lookup"><span data-stu-id="0bd1a-102">System.ServiceModel.Channels.MsmqMessageDropped</span></span>

<span data-ttu-id="0bd1a-103">MSMQ a supprimé le message.</span><span class="sxs-lookup"><span data-stu-id="0bd1a-103">MSMQ dropped the message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="0bd1a-104">Description</span><span class="sxs-lookup"><span data-stu-id="0bd1a-104">Description</span></span>  

 <span data-ttu-id="0bd1a-105">Cette trace indique qu'un message MSMQ a été supprimé.</span><span class="sxs-lookup"><span data-stu-id="0bd1a-105">The trace indicates that an MSMQ message was dropped.</span></span> <span data-ttu-id="0bd1a-106">Les messages MSMQ peuvent être supprimés lorsque Windows Communication Foundation (WCF) (utilisé avec NetMsmqBinding ou MsmqIntegrationBinding) ne peut pas les traiter.</span><span class="sxs-lookup"><span data-stu-id="0bd1a-106">MSMQ messages can be dropped when Windows Communication Foundation (WCF) (used with either the NetMsmqBinding or MsmqIntegrationBinding) is unable to process them.</span></span> <span data-ttu-id="0bd1a-107">Ces messages sont appelés des messages incohérents.</span><span class="sxs-lookup"><span data-stu-id="0bd1a-107">Such messages are referred to as poison messages.</span></span>  
  
 <span data-ttu-id="0bd1a-108">Un message incohérent est supprimé lorsque la propriété `ReceiveErrorHandling` sur NetMsmqBinding ou MsmqIntegrationBinding a la valeur `Drop`.</span><span class="sxs-lookup"><span data-stu-id="0bd1a-108">A poison message is dropped when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Drop`.</span></span> <span data-ttu-id="0bd1a-109">Ce message est supprimé de la file d’attente et ne peut plus être récupéré.</span><span class="sxs-lookup"><span data-stu-id="0bd1a-109">A dropped message is removed from the queue and is no longer recoverable.</span></span>  
  
 <span data-ttu-id="0bd1a-110">Pour plus d’informations sur le moment où les messages deviennent incohérents et sur la façon de configurer votre service pour les gérer de manière appropriée, consultez [gestion des messages incohérents](../../feature-details/poison-message-handling.md).</span><span class="sxs-lookup"><span data-stu-id="0bd1a-110">For more information on when messages become poison and how to configure your service to handle them appropriately, see [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bd1a-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0bd1a-111">See also</span></span>

- [<span data-ttu-id="0bd1a-112">Suivi</span><span class="sxs-lookup"><span data-stu-id="0bd1a-112">Tracing</span></span>](index.md)
- [<span data-ttu-id="0bd1a-113">Utilisation du suivi pour résoudre les problèmes posés par votre application</span><span class="sxs-lookup"><span data-stu-id="0bd1a-113">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="0bd1a-114">Administration et diagnostics</span><span class="sxs-lookup"><span data-stu-id="0bd1a-114">Administration and Diagnostics</span></span>](../index.md)
- [<span data-ttu-id="0bd1a-115">Gestion des messages incohérents</span><span class="sxs-lookup"><span data-stu-id="0bd1a-115">Poison-Message Handling</span></span>](../../feature-details/poison-message-handling.md)

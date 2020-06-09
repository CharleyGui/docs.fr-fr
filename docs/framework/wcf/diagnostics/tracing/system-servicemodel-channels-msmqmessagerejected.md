---
title: System.ServiceModel.Channels.MsmqMessageRejected
ms.date: 03/30/2017
ms.assetid: 9b7c10a7-2af6-44a2-8b1a-90bba0c7cf26
ms.openlocfilehash: c388a9dc3569e20639de09abc5f4941b73c561ad
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84578049"
---
# <a name="systemservicemodelchannelsmsmqmessagerejected"></a><span data-ttu-id="e2ac9-102">System.ServiceModel.Channels.MsmqMessageRejected</span><span class="sxs-lookup"><span data-stu-id="e2ac9-102">System.ServiceModel.Channels.MsmqMessageRejected</span></span>
<span data-ttu-id="e2ac9-103">MSMQ a refusé le message.</span><span class="sxs-lookup"><span data-stu-id="e2ac9-103">MSMQ rejected the message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="e2ac9-104">Description</span><span class="sxs-lookup"><span data-stu-id="e2ac9-104">Description</span></span>  
 <span data-ttu-id="e2ac9-105">Ce suivi indique qu'un message MSMQ a été refusé.</span><span class="sxs-lookup"><span data-stu-id="e2ac9-105">This trace indicates that an MSMQ message was rejected.</span></span>  
  
 <span data-ttu-id="e2ac9-106">Les messages MSMQ peuvent être rejetés lorsque Windows Communication Foundation (WCF) (utilisé avec NetMsmqBinding ou MsmqIntegrationBinding) ne peut pas les traiter.</span><span class="sxs-lookup"><span data-stu-id="e2ac9-106">MSMQ messages can be rejected when Windows Communication Foundation (WCF) (used with either the NetMsmqBinding or MsmqIntegrationBinding) is unable to process them.</span></span> <span data-ttu-id="e2ac9-107">Ces messages sont appelés des messages incohérents.</span><span class="sxs-lookup"><span data-stu-id="e2ac9-107">Such messages are referred to as poison messages.</span></span> <span data-ttu-id="e2ac9-108">Un message incohérent est refusé lorsque la propriété `ReceiveErrorHandling` sur NetMsmqBinding ou MsmqIntegrationBinding a la valeur `Reject`.</span><span class="sxs-lookup"><span data-stu-id="e2ac9-108">A poison message is rejected when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Reject`.</span></span> <span data-ttu-id="e2ac9-109">Un message rejeté est remis à la [file d’attente de lettres mortes](https://docs.microsoft.com/dotnet/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures)de l’expéditeur.</span><span class="sxs-lookup"><span data-stu-id="e2ac9-109">A rejected message is delivered back to the sender’s [Dead-Letter Queue](https://docs.microsoft.com/dotnet/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures).</span></span>  
  
 <span data-ttu-id="e2ac9-110">Pour plus d’informations sur le moment où les messages deviennent incohérents et sur la façon de configurer votre service pour les gérer de manière appropriée, consultez [gestion des messages incohérents](../../feature-details/poison-message-handling.md).</span><span class="sxs-lookup"><span data-stu-id="e2ac9-110">For more information on when messages become poison and how to configure your service to handle them appropriately, see [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span></span>  
  
 <span data-ttu-id="e2ac9-111">Pour plus d’informations sur ce qu’implique un message rejeté dans MSMQ, consultez [MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85)).</span><span class="sxs-lookup"><span data-stu-id="e2ac9-111">For more information on what a rejected message means in MSMQ, see [MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2ac9-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e2ac9-112">See also</span></span>

- [<span data-ttu-id="e2ac9-113">Suivi</span><span class="sxs-lookup"><span data-stu-id="e2ac9-113">Tracing</span></span>](index.md)
- [<span data-ttu-id="e2ac9-114">Utilisation du suivi pour résoudre les problèmes posés par votre application</span><span class="sxs-lookup"><span data-stu-id="e2ac9-114">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="e2ac9-115">Administration et diagnostics</span><span class="sxs-lookup"><span data-stu-id="e2ac9-115">Administration and Diagnostics</span></span>](../index.md)
- [<span data-ttu-id="e2ac9-116">Gestion des messages incohérents</span><span class="sxs-lookup"><span data-stu-id="e2ac9-116">Poison-Message Handling</span></span>](../../feature-details/poison-message-handling.md)
- <span data-ttu-id="e2ac9-117">[MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))</span><span class="sxs-lookup"><span data-stu-id="e2ac9-117">[MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))</span></span>

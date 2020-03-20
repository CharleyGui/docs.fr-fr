---
title: System.ServiceModel.Channels.MsmqMessageRejected
ms.date: 03/30/2017
ms.assetid: 9b7c10a7-2af6-44a2-8b1a-90bba0c7cf26
ms.openlocfilehash: 8f783dcd4b966ed89c24d724918a3923c5a2d0b1
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78674772"
---
# <a name="systemservicemodelchannelsmsmqmessagerejected"></a><span data-ttu-id="ae4ba-102">System.ServiceModel.Channels.MsmqMessageRejected</span><span class="sxs-lookup"><span data-stu-id="ae4ba-102">System.ServiceModel.Channels.MsmqMessageRejected</span></span>
<span data-ttu-id="ae4ba-103">MSMQ a refusé le message.</span><span class="sxs-lookup"><span data-stu-id="ae4ba-103">MSMQ rejected the message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="ae4ba-104">Description</span><span class="sxs-lookup"><span data-stu-id="ae4ba-104">Description</span></span>  
 <span data-ttu-id="ae4ba-105">Ce suivi indique qu'un message MSMQ a été refusé.</span><span class="sxs-lookup"><span data-stu-id="ae4ba-105">This trace indicates that an MSMQ message was rejected.</span></span>  
  
 <span data-ttu-id="ae4ba-106">Les messages MSMQ peuvent être rejetés lorsque windows Communication Foundation (WCF) (utilisé avec le NetMsmqBinding ou MsmqIntegrationBinding) est incapable de les traiter.</span><span class="sxs-lookup"><span data-stu-id="ae4ba-106">MSMQ messages can be rejected when Windows Communication Foundation (WCF) (used with either the NetMsmqBinding or MsmqIntegrationBinding) is unable to process them.</span></span> <span data-ttu-id="ae4ba-107">Ces messages sont appelés des messages incohérents.</span><span class="sxs-lookup"><span data-stu-id="ae4ba-107">Such messages are referred to as poison messages.</span></span> <span data-ttu-id="ae4ba-108">Un message incohérent est refusé lorsque la propriété `ReceiveErrorHandling` sur NetMsmqBinding ou MsmqIntegrationBinding a la valeur `Reject`.</span><span class="sxs-lookup"><span data-stu-id="ae4ba-108">A poison message is rejected when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Reject`.</span></span> <span data-ttu-id="ae4ba-109">Un message rejeté est transmis à la [file d’attente de](https://docs.microsoft.com/dotnet/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures)l’expéditeur Dead-Letter .</span><span class="sxs-lookup"><span data-stu-id="ae4ba-109">A rejected message is delivered back to the sender’s [Dead-Letter Queue](https://docs.microsoft.com/dotnet/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures).</span></span>  
  
 <span data-ttu-id="ae4ba-110">Pour plus d’informations sur le moment où les messages deviennent du poison et comment configurer votre service pour les manipuler de manière appropriée, voir [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span><span class="sxs-lookup"><span data-stu-id="ae4ba-110">For more information on when messages become poison and how to configure your service to handle them appropriately, see [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span></span>  
  
 <span data-ttu-id="ae4ba-111">Pour plus d’informations sur ce qu’un message rejeté signifie dans MSMQ, voir [MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85)).</span><span class="sxs-lookup"><span data-stu-id="ae4ba-111">For more information on what a rejected message means in MSMQ, see [MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae4ba-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ae4ba-112">See also</span></span>

- [<span data-ttu-id="ae4ba-113">Traçage</span><span class="sxs-lookup"><span data-stu-id="ae4ba-113">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="ae4ba-114">Utilisation du suivi pour résoudre les problèmes posés par votre application</span><span class="sxs-lookup"><span data-stu-id="ae4ba-114">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="ae4ba-115">Administration et diagnostics</span><span class="sxs-lookup"><span data-stu-id="ae4ba-115">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
- [<span data-ttu-id="ae4ba-116">Gestion des messages incohérents</span><span class="sxs-lookup"><span data-stu-id="ae4ba-116">Poison-Message Handling</span></span>](../../feature-details/poison-message-handling.md)
- <span data-ttu-id="ae4ba-117">[MQMarkMessageR éjecté](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))</span><span class="sxs-lookup"><span data-stu-id="ae4ba-117">[MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))</span></span>

---
title: System.ServiceModel.Channels.MsmqPoisonMessageRejected
ms.date: 03/30/2017
ms.assetid: 0e64b9bd-1f12-43df-a189-d7be3c2bace1
ms.openlocfilehash: 6b0e6e3ebcf5d414e9dbbcecd09ba2e8bb3ddd3a
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78674816"
---
# <a name="systemservicemodelchannelsmsmqpoisonmessagerejected"></a><span data-ttu-id="2b643-102">System.ServiceModel.Channels.MsmqPoisonMessageRejected</span><span class="sxs-lookup"><span data-stu-id="2b643-102">System.ServiceModel.Channels.MsmqPoisonMessageRejected</span></span>
<span data-ttu-id="2b643-103">Message poison rejeté.</span><span class="sxs-lookup"><span data-stu-id="2b643-103">Poison message rejected.</span></span>  
  
## <a name="description"></a><span data-ttu-id="2b643-104">Description</span><span class="sxs-lookup"><span data-stu-id="2b643-104">Description</span></span>  

 <span data-ttu-id="2b643-105">Le suivi indique qu'un message poison a été rencontré et rejeté par la suite.</span><span class="sxs-lookup"><span data-stu-id="2b643-105">The trace indicates that a poison message was encountered and subsequently rejected.</span></span> <span data-ttu-id="2b643-106">Cela se produit seulement lorsque la propriété `ReceiveErrorHandling` sur NetMsmqBinding ou MsmqIntegrationBinding a la valeur `Reject`.</span><span class="sxs-lookup"><span data-stu-id="2b643-106">This occurs when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Reject`.</span></span> <span data-ttu-id="2b643-107">Un message rejeté est transmis à la [file d’attente de](../../feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)l’expéditeur Dead-Letter .</span><span class="sxs-lookup"><span data-stu-id="2b643-107">A rejected message is delivered back to the sender’s [Dead-Letter Queue](../../feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md).</span></span>  
  
 <span data-ttu-id="2b643-108">Pour plus d’informations sur le moment où les messages deviennent du poison et comment configurer votre service pour les manipuler de manière appropriée, voir [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span><span class="sxs-lookup"><span data-stu-id="2b643-108">For more information on when messages become poison and how to configure your service to handle them appropriately, see [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span></span> <span data-ttu-id="2b643-109">Pour plus d’informations sur ce qu’un message rejeté signifie dans MSMQ, voir [MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85)).</span><span class="sxs-lookup"><span data-stu-id="2b643-109">For more information on what a rejected message means in MSMQ, see [MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b643-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2b643-110">See also</span></span>

- [<span data-ttu-id="2b643-111">Traçage</span><span class="sxs-lookup"><span data-stu-id="2b643-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="2b643-112">Utilisation du suivi pour résoudre les problèmes posés par votre application</span><span class="sxs-lookup"><span data-stu-id="2b643-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="2b643-113">Administration et diagnostics</span><span class="sxs-lookup"><span data-stu-id="2b643-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
- [<span data-ttu-id="2b643-114">Gestion des messages incohérents</span><span class="sxs-lookup"><span data-stu-id="2b643-114">Poison-Message Handling</span></span>](../../feature-details/poison-message-handling.md)
- <span data-ttu-id="2b643-115">[MQMarkMessageR éjecté](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))</span><span class="sxs-lookup"><span data-stu-id="2b643-115">[MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))</span></span>

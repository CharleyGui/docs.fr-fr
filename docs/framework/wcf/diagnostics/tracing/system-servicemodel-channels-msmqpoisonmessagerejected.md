---
title: System.ServiceModel.Channels.MsmqPoisonMessageRejected
ms.date: 03/30/2017
ms.assetid: 0e64b9bd-1f12-43df-a189-d7be3c2bace1
ms.openlocfilehash: f0e49fcfa13bb9932a88a4e79d617343c080bb3c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598370"
---
# <a name="systemservicemodelchannelsmsmqpoisonmessagerejected"></a><span data-ttu-id="f83f2-102">System.ServiceModel.Channels.MsmqPoisonMessageRejected</span><span class="sxs-lookup"><span data-stu-id="f83f2-102">System.ServiceModel.Channels.MsmqPoisonMessageRejected</span></span>
<span data-ttu-id="f83f2-103">Message poison rejeté.</span><span class="sxs-lookup"><span data-stu-id="f83f2-103">Poison message rejected.</span></span>  
  
## <a name="description"></a><span data-ttu-id="f83f2-104">Description</span><span class="sxs-lookup"><span data-stu-id="f83f2-104">Description</span></span>  

 <span data-ttu-id="f83f2-105">Le suivi indique qu'un message poison a été rencontré et rejeté par la suite.</span><span class="sxs-lookup"><span data-stu-id="f83f2-105">The trace indicates that a poison message was encountered and subsequently rejected.</span></span> <span data-ttu-id="f83f2-106">Cela se produit seulement lorsque la propriété `ReceiveErrorHandling` sur NetMsmqBinding ou MsmqIntegrationBinding a la valeur `Reject`.</span><span class="sxs-lookup"><span data-stu-id="f83f2-106">This occurs when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Reject`.</span></span> <span data-ttu-id="f83f2-107">Un message rejeté est remis à la [file d’attente de lettres mortes](../../feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)de l’expéditeur.</span><span class="sxs-lookup"><span data-stu-id="f83f2-107">A rejected message is delivered back to the sender’s [Dead-Letter Queue](../../feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md).</span></span>  
  
 <span data-ttu-id="f83f2-108">Pour plus d’informations sur le moment où les messages deviennent incohérents et sur la façon de configurer votre service pour les gérer de manière appropriée, consultez [gestion des messages incohérents](../../feature-details/poison-message-handling.md).</span><span class="sxs-lookup"><span data-stu-id="f83f2-108">For more information on when messages become poison and how to configure your service to handle them appropriately, see [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span></span> <span data-ttu-id="f83f2-109">Pour plus d’informations sur ce qu’implique un message rejeté dans MSMQ, consultez [MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85)).</span><span class="sxs-lookup"><span data-stu-id="f83f2-109">For more information on what a rejected message means in MSMQ, see [MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f83f2-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f83f2-110">See also</span></span>

- [<span data-ttu-id="f83f2-111">Suivi</span><span class="sxs-lookup"><span data-stu-id="f83f2-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="f83f2-112">Utilisation du suivi pour résoudre les problèmes posés par votre application</span><span class="sxs-lookup"><span data-stu-id="f83f2-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="f83f2-113">Administration et diagnostics</span><span class="sxs-lookup"><span data-stu-id="f83f2-113">Administration and Diagnostics</span></span>](../index.md)
- [<span data-ttu-id="f83f2-114">Gestion des messages incohérents</span><span class="sxs-lookup"><span data-stu-id="f83f2-114">Poison-Message Handling</span></span>](../../feature-details/poison-message-handling.md)
- <span data-ttu-id="f83f2-115">[MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))</span><span class="sxs-lookup"><span data-stu-id="f83f2-115">[MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))</span></span>

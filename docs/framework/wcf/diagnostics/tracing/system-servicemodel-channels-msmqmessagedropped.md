---
title: System.ServiceModel.Channels.MsmqMessageDropped
ms.date: 03/30/2017
ms.assetid: 8b6e644d-fa68-4be7-abe9-3659671a37c1
ms.openlocfilehash: e80fecf508158dcb53f08b75c8f9486c13e403a4
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78674795"
---
# <a name="systemservicemodelchannelsmsmqmessagedropped"></a><span data-ttu-id="9db8c-102">System.ServiceModel.Channels.MsmqMessageDropped</span><span class="sxs-lookup"><span data-stu-id="9db8c-102">System.ServiceModel.Channels.MsmqMessageDropped</span></span>
<span data-ttu-id="9db8c-103">MSMQ a supprimé le message.</span><span class="sxs-lookup"><span data-stu-id="9db8c-103">MSMQ dropped the message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="9db8c-104">Description</span><span class="sxs-lookup"><span data-stu-id="9db8c-104">Description</span></span>  
 <span data-ttu-id="9db8c-105">Cette trace indique qu'un message MSMQ a été supprimé.</span><span class="sxs-lookup"><span data-stu-id="9db8c-105">The trace indicates that an MSMQ message was dropped.</span></span> <span data-ttu-id="9db8c-106">Les messages MSMQ peuvent être supprimés lorsque windows Communication Foundation (WCF) (utilisé avec le NetMsmqBinding ou MsmqIntegrationBinding) est incapable de les traiter.</span><span class="sxs-lookup"><span data-stu-id="9db8c-106">MSMQ messages can be dropped when Windows Communication Foundation (WCF) (used with either the NetMsmqBinding or MsmqIntegrationBinding) is unable to process them.</span></span> <span data-ttu-id="9db8c-107">Ces messages sont appelés des messages incohérents.</span><span class="sxs-lookup"><span data-stu-id="9db8c-107">Such messages are referred to as poison messages.</span></span>  
  
 <span data-ttu-id="9db8c-108">Un message incohérent est supprimé lorsque la propriété `ReceiveErrorHandling` sur NetMsmqBinding ou MsmqIntegrationBinding a la valeur `Drop`.</span><span class="sxs-lookup"><span data-stu-id="9db8c-108">A poison message is dropped when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Drop`.</span></span> <span data-ttu-id="9db8c-109">Ce message est supprimé de la file d’attente et ne peut plus être récupéré.</span><span class="sxs-lookup"><span data-stu-id="9db8c-109">A dropped message is removed from the queue and is no longer recoverable.</span></span>  
  
 <span data-ttu-id="9db8c-110">Pour plus d’informations sur le moment où les messages deviennent du poison et comment configurer votre service pour les manipuler de manière appropriée, voir [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span><span class="sxs-lookup"><span data-stu-id="9db8c-110">For more information on when messages become poison and how to configure your service to handle them appropriately, see [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9db8c-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9db8c-111">See also</span></span>

- [<span data-ttu-id="9db8c-112">Traçage</span><span class="sxs-lookup"><span data-stu-id="9db8c-112">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="9db8c-113">Utilisation du suivi pour résoudre les problèmes posés par votre application</span><span class="sxs-lookup"><span data-stu-id="9db8c-113">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="9db8c-114">Administration et diagnostics</span><span class="sxs-lookup"><span data-stu-id="9db8c-114">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
- [<span data-ttu-id="9db8c-115">Gestion des messages incohérents</span><span class="sxs-lookup"><span data-stu-id="9db8c-115">Poison-Message Handling</span></span>](../../feature-details/poison-message-handling.md)

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
# <a name="systemservicemodelchannelsmsmqmessagerejected"></a>System.ServiceModel.Channels.MsmqMessageRejected
MSMQ a refusé le message.  
  
## <a name="description"></a>Description  
 Ce suivi indique qu'un message MSMQ a été refusé.  
  
 Les messages MSMQ peuvent être rejetés lorsque windows Communication Foundation (WCF) (utilisé avec le NetMsmqBinding ou MsmqIntegrationBinding) est incapable de les traiter. Ces messages sont appelés des messages incohérents. Un message incohérent est refusé lorsque la propriété `ReceiveErrorHandling` sur NetMsmqBinding ou MsmqIntegrationBinding a la valeur `Reject`. Un message rejeté est transmis à la [file d’attente de](https://docs.microsoft.com/dotnet/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures)l’expéditeur Dead-Letter .  
  
 Pour plus d’informations sur le moment où les messages deviennent du poison et comment configurer votre service pour les manipuler de manière appropriée, voir [Poison-Message Handling](../../feature-details/poison-message-handling.md).  
  
 Pour plus d’informations sur ce qu’un message rejeté signifie dans MSMQ, voir [MQMarkMessageRejected](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85)).  
  
## <a name="see-also"></a>Voir aussi

- [Traçage](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Utilisation du suivi pour résoudre les problèmes posés par votre application](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Administration et diagnostics](../../../../../docs/framework/wcf/diagnostics/index.md)
- [Gestion des messages incohérents](../../feature-details/poison-message-handling.md)
- [MQMarkMessageR éjecté](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))

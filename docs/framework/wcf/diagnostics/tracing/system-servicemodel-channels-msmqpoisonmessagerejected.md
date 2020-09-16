---
title: System.ServiceModel.Channels.MsmqPoisonMessageRejected
ms.date: 03/30/2017
ms.assetid: 0e64b9bd-1f12-43df-a189-d7be3c2bace1
ms.openlocfilehash: c5401bae1d8e7f61939d8de321353f59f412f966
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90535331"
---
# <a name="systemservicemodelchannelsmsmqpoisonmessagerejected"></a>System.ServiceModel.Channels.MsmqPoisonMessageRejected
Message poison rejeté.  
  
## <a name="description"></a>Description  

 Le suivi indique qu'un message poison a été rencontré et rejeté par la suite. Cela se produit seulement lorsque la propriété `ReceiveErrorHandling` sur NetMsmqBinding ou MsmqIntegrationBinding a la valeur `Reject`. Un message rejeté est remis à la [file d’attente de lettres mortes](../../feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)de l’expéditeur.  
  
 Pour plus d’informations sur le moment où les messages deviennent incohérents et sur la façon de configurer votre service pour les gérer de manière appropriée, consultez [gestion des messages incohérents](../../feature-details/poison-message-handling.md). Pour plus d’informations sur ce qu’implique un message rejeté dans MSMQ, consultez [MQMarkMessageRejected](/previous-versions/windows/desktop/msmq/ms707071(v=vs.85)).  
  
## <a name="see-also"></a>Voir aussi

- [Suivi](index.md)
- [Utilisation du suivi pour résoudre les problèmes posés par votre application](using-tracing-to-troubleshoot-your-application.md)
- [Administration et diagnostics](../index.md)
- [Gestion des messages incohérents](../../feature-details/poison-message-handling.md)
- [MQMarkMessageRejected](/previous-versions/windows/desktop/msmq/ms707071(v=vs.85))

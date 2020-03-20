---
title: System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
ms.date: 03/30/2017
ms.assetid: d75d39da-7502-4a6a-91b9-eaa05b8e24d5
ms.openlocfilehash: f89dd1373d67714046f8cb958582c3a5dea04456
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78674788"
---
# <a name="systemservicemodelchannelsmsmqmoveordeleteattemptfailed"></a>System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
Impossible de déplacer ou de supprimer le message.  
  
## <a name="description"></a>Description  
 Le suivi indique qu'un échec a eu lieu lors de la tentative de déplacement, d'élimination ou de rejet d'un message MSMQ.  
  
 Les messages MSMQ sont utilisés par Windows Communication Foundation (WCF) (lorsqu’ils sont utilisés avec le NetMsmqBinding ou le MsmqIntegrationBinding). Cette trace est liée à `ReceiveErrorHandling` la valeur choisie de la propriété sur le NetMsmqBinding ou MsmqIntegrationBinding.  
  
 Ce suivi n'indique pas une défaillance générale du système. Toutefois, il indique que la disposition de message incohérent choisie a échoué pour un message. Pour plus d’informations sur le moment où les messages deviennent du poison et comment configurer votre service pour les manipuler de manière appropriée, voir [Poison-Message Handling](../../feature-details/poison-message-handling.md).  
  
## <a name="see-also"></a>Voir aussi

- [Traçage](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Utilisation du suivi pour résoudre les problèmes posés par votre application](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Administration et diagnostics](../../../../../docs/framework/wcf/diagnostics/index.md)

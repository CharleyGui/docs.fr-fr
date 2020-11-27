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
# <a name="systemservicemodelchannelsmsmqmoveordeleteattemptfailed"></a>System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed

Impossible de déplacer ou de supprimer le message.  
  
## <a name="description"></a>Description  

 Le suivi indique qu'un échec a eu lieu lors de la tentative de déplacement, d'élimination ou de rejet d'un message MSMQ.  
  
 Les messages MSMQ sont utilisés par Windows Communication Foundation (WCF) (lorsqu’ils sont utilisés avec NetMsmqBinding ou MsmqIntegrationBinding). Ce suivi est lié à la valeur choisie de la `ReceiveErrorHandling` propriété sur NetMsmqBinding ou MsmqIntegrationBinding.  
  
 Ce suivi n'indique pas une défaillance générale du système. Toutefois, il indique que la disposition de message incohérent choisie a échoué pour un message. Pour plus d’informations sur le moment où les messages deviennent incohérents et sur la façon de configurer votre service pour les gérer de manière appropriée, consultez [gestion des messages incohérents](../../feature-details/poison-message-handling.md).  
  
## <a name="see-also"></a>Voir aussi

- [Suivi](index.md)
- [Utilisation du suivi pour résoudre les problèmes posés par votre application](using-tracing-to-troubleshoot-your-application.md)
- [Administration et diagnostics](../index.md)

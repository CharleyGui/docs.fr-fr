---
title: 'Procédure : échanger des messages avec des points de terminaison WCF et des applications Message Queuing'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 62210fd8-a372-4d55-ab9b-c99827d1885e
ms.openlocfilehash: 8f8baf345059c01b0fef3b61ef85556151269118
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96246418"
---
# <a name="how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications"></a>Procédure : échanger des messages avec des points de terminaison WCF et des applications Message Queuing

Vous pouvez intégrer des applications de Message Queuing (MSMQ) existantes à des applications Windows Communication Foundation (WCF) à l’aide de la liaison d’intégration MSMQ pour convertir des messages MSMQ vers et depuis des messages WCF. Cela vous permet d’appeler des applications de récepteur MSMQ à partir de clients WCF, ainsi que d’appeler des services WCF à partir d’applications d’expéditeur MSMQ.  
  
 Dans cette section, nous expliquons comment utiliser <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> pour la communication mise en file d’attente entre (1) un client WCF et un service d’application MSMQ écrit à l’aide de System. Messaging et (2) un client d’application MSMQ et un service WCF.  
  
 Pour obtenir un exemple complet montrant comment appeler une application MSMQ Receiver à partir d’un client WCF, consultez le [Windows Communication Foundation à Message Queuing](../samples/wcf-to-message-queuing.md) exemple.  
  
 Pour obtenir un exemple complet montrant comment appeler un service WCF à partir d’un client MSMQ, reportez-vous à l’exemple [Message Queuing à Windows Communication Foundation](../samples/message-queuing-to-wcf.md) .  
  
### <a name="to-create-a-wcf-service-that-receives-messages-from-a-msmq-client"></a>Pour créer un service WCF qui reçoit des messages depuis un client MSMQ  
  
1. Définissez une interface qui définit le contrat de service pour le service WCF qui reçoit les messages mis en file d’attente à partir d’une application d’expéditeur MSMQ, comme indiqué dans l’exemple de code suivant.  
  
     [!code-csharp[S_MsmqToWcf#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#1)]
     [!code-vb[S_MsmqToWcf#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#1)]  
  
2. Implémentez l'interface et appliquez l'attribut <xref:System.ServiceModel.ServiceBehaviorAttribute> à la classe, comme le montre l'exemple de code suivant.  
  
     [!code-csharp[S_MsmqToWcf#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#2)]
     [!code-vb[S_MsmqToWcf#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#2)]  
  
3. Créez un fichier de configuration qui spécifie la liaison <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>.  

4. Instanciez un objet <xref:System.ServiceModel.ServiceHost> qui utilise la liaison configurée.  

### <a name="to-create-a-wcf-client-that-sends-messages-to-a-msmq-receiver-application"></a>Pour créer un client WCF qui envoie des messages à une application réceptrice MSMQ  
  
1. Définissez une interface qui définit le contrat de service pour le client WCF qui envoie des messages mis en file d’attente au récepteur MSMQ, comme indiqué dans l’exemple de code suivant.  
  
     [!code-csharp[S_WcfToMsmq#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/proxy.cs#6)]
     [!code-vb[S_WcfToMsmq#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/proxy.vb#6)]  
  
2. Définissez une classe de client que le client WCF utilise pour appeler le récepteur MSMQ.  
  
     [!code-csharp[S_WcfToMsmq#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/snippets.cs#2)]
     [!code-vb[S_WcfToMsmq#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/snippets.vb#2)]  
  
3. Créez une configuration qui spécifie l’utilisation de la liaison MsmqIntegrationBinding.  
  
     [!code-csharp[S_WcfToMsmq#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/snippets.cs#3)]
     [!code-vb[S_WcfToMsmq#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/snippets.vb#3)]  
  
4. Créez une instance de la classe de client et appelez la méthode définie par le service qui reçoit le message.  
  
     [!code-csharp[S_WcfToMsmq#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/client.cs#4)]  
  
## <a name="see-also"></a>Voir aussi

- [Vue d'ensemble des files d'attente](queues-overview.md)
- [Procédure : échanger des messages mis en file d’attente avec des points de terminaison WCF](how-to-exchange-queued-messages-with-wcf-endpoints.md)
- [Windows Communication Foundation to Message Queuing](../samples/wcf-to-message-queuing.md)
- [Installation de Message Queuing (MSMQ)](../samples/installing-message-queuing-msmq.md)
- [Message Queuing to Windows Communication Foundation](../samples/message-queuing-to-wcf.md)
- [Message Security over Message Queuing](../samples/message-security-over-message-queuing.md)

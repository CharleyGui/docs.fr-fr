---
title: "Comment : échanger des messages en file d'attente avec des points de terminaison WCF"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 938e7825-f63a-4c3d-b603-63772fabfdb3
ms.openlocfilehash: 7da7ba1b680bae2b29eeff8fe669e097ea8eda32
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595373"
---
# <a name="how-to-exchange-queued-messages-with-wcf-endpoints"></a>Comment : échanger des messages en file d'attente avec des points de terminaison WCF
Les files d’attente garantissent que la messagerie fiable peut se produire entre un client et un service de Windows Communication Foundation (WCF), même si le service n’est pas disponible au moment de la communication. Les procédures suivantes montrent comment garantir une communication durable entre un client et un service à l’aide de la liaison mise en file d’attente standard lors de l’implémentation du service WCF.  
  
 Cette section explique comment utiliser pour la communication mise en <xref:System.ServiceModel.NetMsmqBinding> file d’attente entre un client WCF et un service WCF.  
  
### <a name="to-use-queuing-in-a-wcf-service"></a>Pour utiliser la mise en file d'attente dans un service WCF  
  
1. Définissez un contrat de service utilisant une interface marquée avec <xref:System.ServiceModel.ServiceContractAttribute>. Marquez les opérations dans l'interface qui font partie du contrat de service avec <xref:System.ServiceModel.OperationContractAttribute> et définissez-les comme unidirectionnelles car aucune réponse n'est retournée à la méthode. Le code ci-dessous fournit un exemple de contrat de service et sa définition d'opération.  
  
     [!code-csharp[S_Msmq_Transacted#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#1)]
     [!code-vb[S_Msmq_Transacted#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#1)]  
  
2. Lorsque le contrat de service passe des types définis par l'utilisateur, vous devez définir des contrats de données pour ces types. Le code suivant présente deux contrats de données, `PurchaseOrder` et `PurchaseOrderLineItem`. Ces deux types définissent les données qui sont envoyées au service. (Notez que les classes qui définissent ce contrat de données définissent également plusieurs méthodes. Ces méthodes ne sont pas considérées comme des parties intégrantes du contrat de données. Seuls les membres déclarés avec l'attribut <xref:System.Runtime.Serialization.DataMemberAttribute> font partie du contrat de données.)  
  
     [!code-csharp[S_Msmq_Transacted#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#2)]
     [!code-vb[S_Msmq_Transacted#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#2)]  
  
3. Implémentez dans une classe les méthodes du contrat de service définies dans l'interface.  
  
     [!code-csharp[S_Msmq_Transacted#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#3)]
     [!code-vb[S_Msmq_Transacted#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#3)]  
  
     Notez <xref:System.ServiceModel.OperationBehaviorAttribute> qui est placé sur la méthode `SubmitPurchaseOrder`. Cela indique que cette opération doit être appelée au sein d'une transaction et que la transaction se termine automatiquement à la fin de la méthode.  
  
4. Créez une file d'attente transactionnelle en utilisant <xref:System.Messaging>. Vous pouvez éventuellement décider de créer la file d'attente à l'aide de la console MMC (Microsoft Management Console) MSMQ (Microsoft Message Queuing). Dans ce cas, assurez-vous de créer une file d’attente transactionnelle.  
  
     [!code-csharp[S_Msmq_Transacted#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#4)]
     [!code-vb[S_Msmq_Transacted#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#4)]  
  
5. Définissez un <xref:System.ServiceModel.Description.ServiceEndpoint> dans la configuration qui spécifie l’adresse de service et utilise la liaison <xref:System.ServiceModel.NetMsmqBinding> standard. Pour plus d’informations sur l’utilisation de la configuration WCF, consultez [Configuration des services WCF](../configuring-services.md).  

6. Créez un hôte pour le service `OrderProcessing` à l'aide de <xref:System.ServiceModel.ServiceHost> qui lit les messages de la file d'attente et les traite. Ouvrez l'hôte de service pour rendre le service disponible. Affichez un message qui indique à l'utilisateur d'appuyer sur une touche quelconque pour terminer le service. Appelez `ReadLine` pour attendre l'appui sur la touche, puis fermez le service.  
  
     [!code-csharp[S_Msmq_Transacted#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#6)]
     [!code-vb[S_Msmq_Transacted#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#6)]  
  
### <a name="to-create-a-client-for-the-queued-service"></a>Pour créer un client pour le service mis en file d'attente  
  
1. L’exemple suivant montre comment exécuter l’application d’hébergement et utiliser l’outil Svcutil. exe pour créer le client WCF.  
  
    ```console
    svcutil http://localhost:8000/ServiceModelSamples/service  
    ```  
  
2. Définissez un <xref:System.ServiceModel.Description.ServiceEndpoint> dans la configuration qui spécifie l’adresse et utilise la liaison <xref:System.ServiceModel.NetMsmqBinding> standard, comme illustré dans l’exemple suivant.  

3. Créez une étendue de transaction pour écrire dans la file d’attente transactionnelle, appelez l' `SubmitPurchaseOrder` opération et fermez le client WCF, comme indiqué dans l’exemple suivant.  
  
     [!code-csharp[S_Msmq_Transacted#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/client.cs#8)]
     [!code-vb[S_Msmq_Transacted#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/client.vb#8)]  
  
## <a name="example"></a>Exemple  
 Les exemples suivants montrent le code de service, l'application d'hébergement, le fichier App.config et le code client inclus pour cet exemple.  
  
 [!code-csharp[S_Msmq_Transacted#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#9)]
 [!code-vb[S_Msmq_Transacted#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#9)]  
  
 [!code-csharp[S_Msmq_Transacted#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#10)]
 [!code-vb[S_Msmq_Transacted#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#10)]  

 [!code-csharp[S_Msmq_Transacted#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/client.cs#12)]
 [!code-vb[S_Msmq_Transacted#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/client.vb#12)]  

## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.NetMsmqBinding>
- [Transacted MSMQ Binding](../samples/transacted-msmq-binding.md)
- [Mise en file d'attente dans WCF](queuing-in-wcf.md)
- [Comment : échanger des messages avec des points de terminaison WCF et des applications Message Queuing](how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)
- [Windows Communication Foundation to Message Queuing](../samples/wcf-to-message-queuing.md)
- [Installation de Message Queuing (MSMQ)](../samples/installing-message-queuing-msmq.md)
- [Message Queuing to Windows Communication Foundation](../samples/message-queuing-to-wcf.md)
- [Message Security over Message Queuing](../samples/message-security-over-message-queuing.md)

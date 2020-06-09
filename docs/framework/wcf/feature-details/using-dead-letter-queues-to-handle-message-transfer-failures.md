---
title: Utilisation de files d'attente de lettres mortes pour gérer des défaillances de transfert de messages
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9e891c6a-d960-45ea-904f-1a00e202d61a
ms.openlocfilehash: f07397b4c10ffec4902dbde37b622978d00f5b63
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594983"
---
# <a name="using-dead-letter-queues-to-handle-message-transfer-failures"></a>Utilisation de files d'attente de lettres mortes pour gérer des défaillances de transfert de messages
La remise de messages en file d'attente peut échouer. Les messages qui ont échoué sont enregistrés dans une file d'attente de lettres mortes. L'échec de la remise peut être dû à des défaillances du réseau, une file d'attente supprimée, une file d'attente saturée, un échec d'authentification ou un retard de remise.  
  
 Les messages en file d'attente peuvent rester longtemps dans la file d'attente si l'application de réception ne les lit pas en temps voulu. Ce comportement peut s'avérer inapproprié pour des messages dépendants de l'heure. Les messages dépendants de l'heure ont une propriété de durée de vie définie dans la liaison en file d'attente, qui indique combien de temps les messages peuvent demeurer dans la file d'attente avant d'expirer. Les messages ayant expiré sont envoyés dans une file d'attente spéciale appelée file d'attente de lettres mortes. Les messages peuvent également être placés dans une file d'attente de lettres mortes pour d'autres raisons, telles que le dépassement d'un quota de file d'attente ou un échec d'authentification.  
  
 En général, les applications écrivent une logique de compensation pour lire les messages de la file d'attente de lettres mortes et les raisons de l'échec. La logique de compensation dépend de la cause de la défaillance. Par exemple, dans le cas d'un échec d'authentification, vous pouvez corriger le certificat joint au message et renvoyer le message. Si la remise a échoué parce que le quota de la file d'attente cible a été atteint, vous pouvez tenter de nouveau la remise dans l'espoir que le problème de quota a été résolu.  
  
 La plupart des systèmes de mise en file d'attente possèdent une file d'attente de lettres mortes à l'échelle du système qui stocke tous les messages ayant échoué issus de ce système. Message Queuing (MSMQ) fournit deux files d’attente de lettres mortes à l’échelle du système : une file d’attente de lettres mortes transactionnelle à l’échelle du système, qui stocke les messages dont la remise dans la file d’attente transactionnelle a échoué et une file d’attente de lettres mortes non transactionnelle à l’échelle du système, qui stocke les messages dont la remise dans la file d’attente non transactionnelle a échoué. Si deux clients envoient des messages à deux services différents et que, par conséquent, différentes files d’attente dans WCF partagent le même service MSMQ à envoyer, il est possible d’avoir une combinaison de messages dans la file d’attente de lettres mortes du système. Cela n'est pas toujours optimal. Dans certains cas (pour des raisons de sécurité, par exemple), vous ne souhaiterez pas qu'un client lise les messages d'un autre client à partir d'une file d'attente de lettres mortes. Dans une file d'attente de lettres mortes partagée, les clients doivent parcourir la file d'attente pour rechercher un message qu'ils ont envoyé, ce qui peut représenter un coût prohibitif en fonction du nombre de messages dans la file d'attente de lettres mortes. Par conséquent, dans WCF `NetMsmqBinding` , `MsmqIntegrationBinding,` et MSMQ sur Windows Vista fournissent une file d’attente de lettres mortes personnalisée (parfois appelée file d’attente de lettres mortes propre à l’application).  
  
 La file d'attente de lettres mortes personnalisée assure l'isolement entre les clients qui partagent le même service MSMQ pour envoyer des messages.  
  
 Sur Windows Server 2003 et Windows XP, Windows Communication Foundation (WCF) fournit une file d’attente de lettres mortes à l’ensemble du système pour toutes les applications clientes mises en file d’attente. Sur Windows Vista, WCF fournit une file d’attente de lettres mortes pour chaque application cliente en file d’attente.  
  
## <a name="specifying-use-of-the-dead-letter-queue"></a>Spécification de l'utilisation de la file d'attente de lettres mortes  
 Une file d'attente de lettres mortes est dans le gestionnaire de files d'attente de l'application émettrice. Elle stocke les messages qui ont expiré ou dont la remise ou le transfert a échoué.  
  
 La liaison a les propriétés de file d’attente de lettres mortes suivantes :  
  
- <xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A>  
  
- <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A>  
  
## <a name="reading-messages-from-the-dead-letter-queue"></a>Lecture des messages stockés dans la file d'attente de lettres mortes  
 Une application qui lit les messages dans une file d’attente de lettres mortes est similaire à un service WCF qui lit à partir d’une file d’attente d’application, à l’exception des différences mineures suivantes :  
  
- Pour lire des messages à partir d’une file d’attente de lettres mortes transactionnelle système, l’URI (Uniform Resource Identifier) doit être de la forme : net.msmq://localhost/system$;DeadXact.  
  
- Pour lire des messages à partir d'une file d'attente de lettres mortes non transactionnelle système, l'URI doit être de la forme : net.msmq://localhost/system$;DeadLetter.  
  
- Pour lire des messages à partir d’une file d’attente de lettres mortes personnalisée, l’URI doit être de la forme : net. msmq://localhost/private/ \<*custom-dlq-name*> où *Custom-lettres mortes-Name* est le nom de la file d’attente de lettres mortes personnalisée.  
  
 Pour plus d’informations sur la façon d’adresser des files d’attente, consultez [points de terminaison de service et adressage de file d’attente](service-endpoints-and-queue-addressing.md).  
  
 La pile WCF sur le récepteur correspond aux adresses sur lesquelles le service est à l’écoute avec l’adresse du message. Si les adresses correspondent, le message est distribué ; dans le cas contraire, le message n'est pas distribué. Cela peut provoquer des problèmes lors de la lecture à partir de la file d'attente de lettres mortes, parce que les messages dans la file d'attente de lettres mortes sont adressés en général au service et pas le service de file d'attente de lettres mortes. Par conséquent, le service qui lit à partir de la file d'attente de lettres mortes doit installer un filtre d'adresse `ServiceBehavior` qui indique à la pile de mettre en correspondance tous les messages de la file d'attente indépendamment du destinataire. En particulier, vous devez ajouter un filtre `ServiceBehavior` avec le paramètre <xref:System.ServiceModel.AddressFilterMode.Any> au service qui lit des messages à partir de la file d'attente de lettres mortes.  
  
## <a name="poison-message-handling-from-the-dead-letter-queue"></a>Gestion des messages incohérents à partir de la file d'attente de lettres mortes  
 La gestion des messages incohérents est disponible sur les files d'attente de lettres mortes, mais présente certaines conditions. Comme vous ne pouvez pas créer de sous-files d'attente à partir des files d'attente système, lorsque vous lisez à partir de la file d'attente de lettres mortes système, il n'est pas possible d'affecter à `ReceiveErrorHandling` la valeur `Move`. Notez que si vous lisez à partir d'une file d'attente de lettres mortes personnalisée, vous pouvez avoir des sous-files d'attente et, par conséquent, `Move` est une disposition valide pour le message incohérent.  
  
 Lorsque `ReceiveErrorHandling` a la valeur `Reject`, lors de la lecture à partir de la file d'attente de lettres mortes personnalisée, le message incohérent est placé dans la file d'attente de lettres mortes système. Lors de la lecture à partir de la file d'attente de lettres mortes système, le message est déposé (purgé). Le rejet d’une file d’attente de lettres mortes système dans MSMQ dépose (purge) le message.  
  
## <a name="example"></a>Exemple  
 L'exemple ci-dessous montre comment créer une file d'attente de lettres mortes et comment l'utiliser pour traiter les messages ayant expiré. L’exemple est basé sur l’exemple de la rubrique [Comment : échanger des messages en file d’attente avec des points de terminaison WCF](how-to-exchange-queued-messages-with-wcf-endpoints.md). L'exemple ci-dessous montre comment écrire le code client pour le service de traitement des commandes qui utilise une file d'attente de lettres mortes pour chaque application. Cet exemple montre également comment traiter les messages stockés dans la file d'attente de lettres mortes.  
  
 Le code ci-dessous correspond à un client qui spécifie une file d'attente de lettres mortes pour chaque application.  
  
 [!code-csharp[S_DeadLetter#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_deadletter/cs/client.cs#1)]
 [!code-vb[S_DeadLetter#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_deadletter/vb/client.vb#1)]  
  
 Le code ci-dessous est destiné au fichier de configuration client.  

 Le code ci-dessous est destiné à un service qui traite les messages stockés dans une file d'attente de lettres mortes.  
  
 [!code-csharp[S_DeadLetter#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_deadletter/cs/dlservice.cs#3)]
 [!code-vb[S_DeadLetter#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_deadletter/vb/dlservice.vb#3)]  
  
 Le code ci-dessous est destiné au fichier de configuration du service de file d'attente de lettres mortes.  

## <a name="see-also"></a>Voir aussi

- [Vue d'ensemble des files d'attente](queues-overview.md)
- [Comment : échanger des messages en file d'attente avec des points de terminaison WCF](how-to-exchange-queued-messages-with-wcf-endpoints.md)
- [Gestion des messages incohérents](poison-message-handling.md)

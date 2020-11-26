---
title: Transport MSMQ
ms.date: 03/30/2017
ms.assetid: 3f29a2fe-24df-4614-b64c-b0c084fb7003
ms.openlocfilehash: 407512cbb129dd2e5497de92c32b0641dd21080b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96238026"
---
# <a name="msmq-transport"></a>Transport MSMQ

Cette rubrique répertorie toutes les exceptions générées par le transport MSMQ.  
  
## <a name="exception-list"></a>Liste des exceptions  
  
|Code de la ressource|Chaîne de la ressource|  
|-------------------|---------------------|  
|MsmqActiveDirectoryRequiresNativeTransfer|La validation de la liaison pour le message a échoué. Le client ne peut pas envoyer de messages. Un conflit dans les propriétés de la liaison a provoqué cette défaillance. UseActiveDirectory a la valeur Vrai et QueueTransferProtocol a la valeur Natif. Pour résoudre le conflit, corrigez l'une des propriétés.|  
|MsmqAuthNoneRequiresProtectionNone|La validation de la liaison pour le service a échoué. Impossible de démarrer le point de terminaison du service ou le client. Un conflit dans les propriétés de la liaison a provoqué cette défaillance. MsmqAuthenticationMode a la valeur Aucun et MsmqProtectionLevel n'a pas la valeur Aucun. Pour résoudre le conflit, corrigez l'une des propriétés.|  
|MsmqCustomRequiresPerAddDLQ|La validation de la liaison pour le message a échoué. Le client ne peut pas envoyer le message. DeadLetterQueue a la valeur Personnalisé, mais CustomDeadLetterQueue n'est pas spécifié. Spécifiez l'URI de la file d'attente de lettres mortes pour chaque application dans la propriété CustomDeadLetterQueue.|  
|MsmqDeserializationError|Une erreur a été rencontrée lors de la désérialisation du message XML. Le message ne peut pas être reçu et est supprimé.|  
|MsmqDLQNotWriteable|La validation de la liaison pour le client a échoué. Le client ne peut envoyer aucun message. La file d'attente de lettres mortes spécifiée n'existe pas ou ne peut pas être écrite. Vérifiez que la file d'attente existe avec l'autorisation d'écriture appropriée.|  
|MsmqGetPrivateComputerInformationError|La vérification de la version a échoué à cause de l'erreur spécifiée. La version de MSMQ ne peut pas être détectée. Toutes les opérations qui se trouvent sur le canal mis en file d'attente échoueront. Vérifiez que MSMQ est installé et disponible.|  
|MsmqNoAssurancesForVolatile|La validation de la liaison pour le service a échoué. Impossible de démarrer le point de terminaison du service ou le client. La propriété ExactlyOnce a la valeur Vrai et la propriété Durable a la valeur Faux. Ceci n’est pas pris en charge. Pour résoudre le conflit, corrigez l'une de ces propriétés.|  
|MsmqNonTransactionalQueueNeeded|Une incompatibilité entre la liaison et la configuration de la file d’attente MSMQ a été détectée. Impossible de démarrer le point de terminaison de service. La propriété ExactlyOnce a la valeur Faux et la file d’attente depuis laquelle lire les messages est une file d’attente transactionnelle. Corrigez l’erreur en affectant la valeur Vrai à la propriété ExactlyOnce ou en créant une liaison non transactionnelle.|  
|MsmqOpenError|Une erreur s'est produite lors de l'ouverture de la file d'attente spécifiée. Impossible d'envoyer ou de recevoir le message depuis la file d'attente. Vérifiez que MSMQ est installé et en cours d'exécution. Vérifiez également que la file d'attente est disponible à l'ouverture avec le mode d'accès et l'autorisation requis.|  
|MsmqPathLookupError|Une erreur s'est produite lors de la conversion du nom du chemin d'accès de la file d'attente spécifiée en nom de format. Toutes les opérations sur le canal mis en file d'attente ont échoué. Vérifiez que l'adresse de la file d'attente est valide. MSMQ doit être installé avec l'intégration à Active Directory activée et être disponible.|  
|MsmqPerAppDLQRequiresCustom|La validation de la liaison sur le client a échoué. Le client ne peut pas envoyer de messages. La propriété CustomDeadLetterQueue a été définie, mais la propriété DeadLetterQueue n'a pas la valeur Personnalisé. Affectez la valeur Personnalisé à la propriété DeadLetterQueue.|  
|MsmqPerAppDLQRequiresExactlyOnce|La validation de la liaison pour le client a échoué. Le client ne peut pas envoyer de messages. Un conflit dans les propriétés de la liaison provoque la défaillance. Pour utiliser la file d'attente de lettres mortes personnalisée et résoudre le conflit, ExactlyOnce doit être vérifiée.|  
|MsmqPerAppDLQRequiresMsmq4|Une incompatibilité entre la liaison et la configuration de MSMQ a été détectée. Le client ne peut pas envoyer de messages. Pour utiliser la file d'attente de lettres mortes personnalisée, vous devez avoir la version 4.0 ou ultérieure de MSMQ. Si vous n'avez pas la version 4.0 ou ultérieure de MSMQ, affectez la valeur Système ou Aucun à la propriété DeadLetterQueue.|  
|MsmqReceiveError|Une erreur s'est produite lors de la réception d'un message depuis la file d'attente. Vérifiez que MSMQ est installé et en cours d'exécution. Assurez-vous que la file d'attente depuis laquelle recevoir les messages est disponible.|  
|MsmqSameTransactionExpected|Une erreur de transaction s’est produite pour cette session. Le canal de la session est défectueux. Impossible d'envoyer ou de recevoir les messages dans la session. Une session mise en file d’attente ne peut pas être associée à plus d’une transaction. Vérifiez que tous les messages de la session sont envoyés ou reçus à l’aide d’une transaction unique.|  
|MsmqSendError|Une erreur s'est produite lors de l'envoi à la file d'attente spécifiée. Vérifiez que MSMQ est installé et en cours d'exécution. Si vous envoyez des messages vers une file d'attente locale, vérifiez que la file d'attente existe avec le mode d'accès et l'autorisation requis.|  
|MsmqTimeSpanTooLarge|La durée de vie du message est trop longue. Impossible d'envoyer le message. La durée de vie (TTL, Time To Live) du message ne peut pas dépasser la valeur maximale Int32.|  
|MsmqTokenProviderNeededForCertificates|Impossible de trouver un X509SecurityTokenProvider. Impossible d'envoyer le message. Le mode d'authentification du certificat requiert un fournisseur de jetons X.509. Assurez-vous qu'un fournisseur de jetons de sécurité est disponible pour le certificat installé.|  
|MsmqTransactedDLQExpected|Une incompatibilité s'est produite entre la liaison et la configuration de MSMQ. Impossible d'envoyer les messages. La file d'attente de lettres mortes personnalisée spécifiée dans la liaison doit être une file d'attente de transaction. Vérifiez que l'adresse de la file d'attente de lettres mortes personnalisée est correcte et que la file d'attente est transactionnelle.|  
|MsmqTransactionalQueueNeeded|Une incompatibilité entre la liaison et la configuration de la file d'attente MSMQ s'est produite. Impossible de démarrer le point de terminaison de service. La propriété ExactlyOnce a la valeur Vrai et la file d’attente depuis laquelle lire les messages n’est pas une file d’attente transactionnelle. Pour corriger l’erreur, affectez la valeur Faux à la propriété ExactlyOnce ou créez une file d’attente transactionnelle pour cette liaison.|  
|MsmqTransactionCurrentRequired|Aucune transaction n'est disponible pour envoyer des messages dans la session. Pour envoyer un message dans une session mise en file d’attente, une transaction est nécessaire. Vérifiez que l'étendue de la transaction est spécifiée pour envoyer le message dans la session.|  
|MsmqTransactionRequired|Une transaction est requise mais n’est pas disponible. Impossible d'envoyer ou de recevoir des messages. Vérifiez que l'étendue de la transaction est spécifiée pour envoyer ou recevoir des messages.|  
|MsmqUnsupportedSerializationFormat|Une erreur de désérialisation s'est produite. Le message ne peut pas être reçu et est supprimé. Le format de sérialisation spécifié n'est pas pris en charge.|  
|MsmqWrongPrivateQueueSyntax|L’URL n’est pas valide. L'URL de la file d'attente ne peut pas contenir le caractère « $ ». Utilisez la syntaxe dans net.msmq://machine/private/queueName pour adresser une file d'attente privée.|

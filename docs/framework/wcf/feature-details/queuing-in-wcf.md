---
title: Mise en file d'attente dans WCF
ms.date: 03/30/2017
ms.assetid: e98d76ba-1acf-42cd-b137-0f8214661112
ms.openlocfilehash: a55e9e38472f67b609685224e5dda34729c6481a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96295182"
---
# <a name="queuing-in-wcf"></a>Mise en file d'attente dans WCF

Cette section décrit comment utiliser la communication en file d’attente dans Windows Communication Foundation (WCF).  
  
## <a name="queues-as-a-wcf-transport-binding"></a>Mises en file d'attente en tant que liaison de transport WCF  

 Dans WCF, les contrats spécifient ce qui est échangé. Les contrats sont des échanges de messages propres à une entreprise ou à une application. Le mécanisme utilisé pour échanger des messages est spécifié dans les liaisons. Dans WCF, les liaisons encapsulent les détails de l’échange de messages. Elles exposent les boutons de configuration permettant à l'utilisateur de contrôler divers aspects du transport ou du protocole que les liaisons représentent. La mise en file d’attente dans WCF est traitée comme toute autre liaison de transport, ce qui constitue un grand avantage pour de nombreuses applications de mise en file d’attente. Aujourd'hui, nombre de ces applications sont écrites différemment des autres applications distribuées de type appel de procédure distante, ce qui complique leur suivi et leur maintenance. Avec WCF, le style d’écriture d’une application distribuée est très similaire, ce qui simplifie la gestion et la maintenance. De plus, le fait de développer le mécanisme d'échange séparément de la logique métier facilite la configuration du transport ou sa modification sans affecter le code propre à l'application. La figure qui suit illustre la structure d'un service et d'un client WCF qui utilise MSMQ comme transport.  
  
 ![Diagramme d'application mise en file d'attente](media/distributed-queue-figure.jpg "File d’attente distribuée-figure")  
  
 Comme le montre la figure ci-dessus, le client et le service ne doivent définir que la sémantique de l'application ; autrement dit le contrat et l'implémentation. Le service configure une liaison mise en file d’attente avec des paramètres par défaut. Le client utilise l' [outil ServiceModel Metadata Utility (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) pour générer un client WCF pour le service et générer un fichier de configuration qui décrit les liaisons à utiliser pour envoyer des messages au service. Ainsi, pour envoyer un message mis en file d’attente, le client instancie un client WCF et appelle une opération sur celui-ci. Le message est alors envoyé dans la file d'attente de transmission, puis transféré à la file d'attente cible. L'application qui envoie et reçoit des messages est donc totalement exempte de la complexité de la communication mise en file d'attente.  
  
 Les avertissements relatifs à la liaison mise en file d’attente dans WCF sont les suivants :  
  
- Toutes les opérations de service doivent être unidirectionnelles car la liaison mise en file d’attente par défaut dans WCF ne prend pas en charge la communication duplex à l’aide de files d’attente. Un exemple de communication bidirectionnelle ([communication](../samples/two-way-communication.md)bidirectionnelle) illustre l’utilisation de contrats 2 1 pour implémenter la communication duplex à l’aide de files d’attente.  
  
- La génération d’un client WCF à l’aide de l’échange de métadonnées requiert un point de terminaison HTTP supplémentaire sur le service afin qu’il puisse être interrogé directement pour générer le client WCF et obtenir des informations de liaison pour configurer de manière appropriée la communication mise en file d’attente.  
  
- En fonction de la liaison mise en file d’attente, une configuration supplémentaire en dehors de WCF est requise. Par exemple, la <xref:System.ServiceModel.NetMsmqBinding> classe fournie avec WCF vous oblige à configurer les liaisons et à configurer au minimum Message Queuing (MSMQ).  
  
 Les sections suivantes décrivent les liaisons mises en file d’attente fournies avec WCF, qui sont basées sur MSMQ.  
  
### <a name="msmq"></a>MSMQ  

 Le transport de mise en file d’attente dans WCF utilise MSMQ pour sa communication en file d’attente.  
  
 MSMQ est fourni en tant que composant facultatif avec Windows et s'exécute en tant que service NT. Il capture les messages à transmettre dans une file d'attente de transmission et les messages à remettre dans une file d'attente cible. Les Gestionnaires des files d'attente MSMQ implémentent un protocole de transfert de message fiable qui empêche la perte de messages au cours de la transmission. Ce protocole peut être natif ou basé sur SOAP, comme le protocole SRMP (SOAP Reliable Message Protocol).  
  
 Dans MSMQ, les files d’attente peuvent être transactionnelles ou non transactionnelles. Dans une file d'attente transactionnelle, les messages sont capturés et remis dans une transaction, puis stockés durablement dans la file d'attente. Les messages envoyés dans une file d'attente transactionnelle sont transférés exactement une fois dans l'ordre. Vous pouvez utiliser une file d’attente non transactionnelle pour envoyer des messages volatils et des messages durables. Un message envoyé dans une file d'attente non transactionnelle ne revêt aucune assurance de transfert fiable et peut donc être perdu.  
  
 Les files d'attente MSMQ peuvent également être sécurisées à l'aide d'une identité Windows inscrite auprès du service d'annuaire Active Directory. Lors de l'installation de MSMQ, vous pouvez installer l'intégration Active Directory, laquelle requiert l'appartenance de l'ordinateur à un réseau de domaine Windows.  
  
 Pour plus d’informations sur MSMQ, consultez [installation de Message Queuing (MSMQ)](../samples/installing-message-queuing-msmq.md).  
  
### <a name="netmsmqbinding"></a>NetMsmqBinding  

 [\<netMsmqBinding>](../../configure-apps/file-schema/wcf/netmsmqbinding.md)Est la liaison mise en file d’attente que WCF offre à deux points de terminaison WCF pour communiquer à l’aide de MSMQ. Par conséquent, la liaison expose des propriétés qui sont spécifiques à MSMQ. Toutefois, toutes les fonctionnalités et propriétés MSMQ ne sont pas exposées dans le `NetMsmqBinding`. Le `NetMsmqBinding` compact regroupe un jeu optimal de fonctionnalités qui s’avère suffisant pour la majorité des clients.  
  
 Le `NetMsmqBinding` illustre les concepts de mise en file d’attente clés discutés jusqu’ici sous la forme de propriétés sur les liaisons. À leur tour, ces propriétés communiquent à MSMQ comment transférer et remettre les messages. Les sections qui suivent décrivent les catégories de propriétés. Pour plus d’informations, consultez les rubriques conceptuelles qui décrivent des propriétés spécifiques plus complètement.  
  
#### <a name="exactlyonce-and-durable-properties"></a>Propriétés ExactlyOnce et Durable  

 Les propriétés `ExactlyOnce` et `Durable` affectent la manière dont les messages sont transférés entre des files d'attente :  
  
- `ExactlyOnce` : si sa valeur est `true` (valeur par défaut), le canal mis en file d'attente garantit que le message remis n'est pas dupliqué. Il garantit également que le message n'est pas perdu. Si le message ne peut pas être remis ou si sa durée de vie expire avant que le message ait pu être remis, le message et la raison de l'échec de la remise sont enregistrés dans une file d'attente de lettres mortes. Lorsque sa valeur est `false`, le canal mis en file d'attente fait un effort pour transférer le message. Dans ce cas, vous pouvez éventuellement choisir une file d'attente de lettres mortes.  
  
- `Durable:` si sa valeur est `true` (valeur par défaut), le canal mis en file d'attente garantit que MSMQ stocke le message durablement sur le disque. Ainsi, en cas d'arrêt et de redémarrage du service MSMQ, les messages présents sur le disque sont transférés à la file d'attente cible ou sont remis au service. Lorsque sa valeur est `false`, les messages sont stockés dans un magasin volatil et sont perdus en cas d'arrêt et de redémarrage du service MSMQ.  
  
 Pour le transfert fiable `ExactlyOnce`, MSMQ requiert que la file d’attente soit transactionnelle. Par ailleurs, MSMQ requiert une transaction pour pouvoir lire les messages depuis une file d’attente transactionnelle. De ce fait, lorsque vous utilisez le `NetMsmqBinding`, n’oubliez pas qu’une transaction est requise pour envoyer ou recevoir des messages lorsque `ExactlyOnce` a la valeur `true`. De même, MSMQ requiert que la file d'attente soit non transactionnelle pour une garantie optimale, comme lorsque `ExactlyOnce` a la valeur `false` et pour la messagerie volatile. Ainsi, si la valeur `ExactlyOnce` est affectée à `false` ou à durable, vous ne pouvez pas envoyer ni recevoir de messages à l'aide d'une transaction.  
  
> [!NOTE]
> Assurez-vous que la file d’attente appropriée (transactionnelle ou non transactionnelle) est créée en fonction des paramètres des liaisons. Si `ExactlyOnce` a la valeur `true`, utilisez une file d'attente transactionnelle ; sinon, utilisez une file d'attente non transactionnelle.  
  
#### <a name="dead-letter-queue-properties"></a>Propriétés de la file d'attente de lettres mortes  

 La file d'attente de lettres mortes est utilisée pour stocker les messages dont la remise a échoué. L'utilisateur peut écrire une logique de compensation qui lit les messages à partir de la file d'attente de lettres mortes.  
  
 De nombreux systèmes de mise en file d'attente prévoient une file d'attente de lettres mortes à l'échelle du système. MSMQ propose une file d’attente de lettres mortes non transactionnelle à l’échelle du système pour les messages dont la remise à des files d’attente non transactionnelles échoue et une file d’attente de lettres mortes transactionnelle à l’échelle du système pour les messages dont la remise à des files d’attente transactionnelles échoue.  
  
 Si plusieurs clients qui envoient des messages à des files d'attente cibles différentes partagent le service MSMQ, tous les messages envoyés par les clients vont dans la même file d'attente de lettres mortes. Ceci n'est pas toujours préférable. Pour une meilleure isolation, WCF et MSMQ dans Windows Vista fournissent une file d’attente de lettres mortes personnalisée (ou une file d’attente de lettres mortes spécifique à l’application) que l’utilisateur peut spécifier pour stocker les messages dont la remise a échoué. Par conséquent, des clients différents ne partagent pas la même file d'attente de lettres mortes.  
  
 La liaison possède deux propriétés intéressantes :  
  
- `DeadLetterQueue` : cette propriété est une énumération qui indique si une file d'attente de lettres mortes est demandée. Cette énumération contient également le type de file d'attente de lettres mortes, si une est demandée. Ces valeurs sont `None`, `System` et `Custom`. Pour plus d’informations sur l’interprétation de ces propriétés, consultez [utilisation de Dead-Letter files d’attente pour gérer les échecs de transfert de messages](using-dead-letter-queues-to-handle-message-transfer-failures.md)  
  
- `CustomDeadLetterQueue` : cette propriété est l'adresse URI (Uniform Resource Identifier) de la file d'attente de lettres mortes propre à l'application. Cela est requis si `DeadLetterQueue` .`Custom` est choisi.  
  
#### <a name="poison-message-handling-properties"></a>Propriétés de gestion des messages incohérents  

 Lorsque le service lit des messages à partir de la file d'attente cible par le biais d'une transaction, il risque de ne pas pouvoir traiter le message pour différentes raisons. Le message est ensuite remis dans la file d'attente pour y être lu de nouveau. Pour traiter les messages qui échouent de manière répétée, un ensemble de propriétés de gestion des messages incohérents peut être configuré dans la liaison. Il existe quatre propriétés : `ReceiveRetryCount`, `MaxRetryCycles`, `RetryCycleDelay` et `ReceiveErrorHandling`. Pour plus d’informations sur ces propriétés, consultez [gestion des messages incohérents](poison-message-handling.md).  
  
#### <a name="security-properties"></a>Propriétés de sécurité  

 MSMQ expose son propre modèle de sécurité, comme les listes de contrôle d'accès sur une file d'attente ou l'envoi de messages authentifiés. Le `NetMsmqBinding` expose ces propriétés de sécurité dans le cadre de ses paramètres de sécurité de transport. La liaison pour la sécurité de transport a deux propriétés : `MsmqAuthenticationMode` et `MsmqProtectionLevel`. Les paramètres de ces propriétés dépendent de la configuration de MSMQ. Pour plus d’informations, consultez [sécurisation des messages à l’aide](securing-messages-using-transport-security.md)de la sécurité de transport.  
  
 Outre la sécurité de transport, le message SOAP lui-même peut être sécurisé à l'aide de la sécurité de message. Pour plus d’informations, consultez [sécurisation des messages à l’aide](securing-messages-using-message-security.md)de la sécurité de message.  
  
 `MsmqTransportSecurity` expose également deux propriétés : `MsmqEncryptionAlgorithm` et `MsmqHashAlgorithm`. Il s'agit d'énumérations de différents algorithmes que vous pouvez choisir pour le chiffrement des messages en vue du transfert entre files d'attente et pour le hachage des signatures.  
  
#### <a name="other-properties"></a>Autres propriétés  

 Outre les propriétés précédentes, les propriétés spécifiques à MSMQ suivantes sont exposées dans la liaison :  
  
- `UseSourceJournal` : propriété qui indique que la journalisation source est activée. La journalisation source est une fonctionnalité MSMQ qui effectue le suivi des messages qui ont été transmis avec succès à partir de la file d’attente de transmission.  
  
- `UseMsmqTracing` : propriété permettant d'indiquer que le suivi MSMQ est activé. Le suivi MSMQ envoie des messages de rapport à une file d'attente de rapports chaque fois qu'un message arrive sur un ordinateur hébergeant un gestionnaire de files d'attente MSMQ ou le quitte.  
  
- `QueueTransferProtocol` : énumération du protocole à utiliser pour les transferts de messages entre files d'attente. MSMQ implémente un protocole natif de transfert entre files d'attente et un protocole SOAP nommé SRMP (SOAP Reliable Messaging Protocol). Le protocole SRMP est appliqué lors de l'utilisation du transport HTTP pour les transferts entre files d'attente. Le protocole SRMP sécurisé est appliqué lors de l'utilisation d'HTTPS pour les transferts entre files d'attente.  
  
- `UseActiveDirectory` : valeur booléenne permettant d'indiquer si Active Directory doit être utilisé pour la résolution d'adresse de file d'attente. Par défaut, cette propriété a la valeur Off. Pour plus d’informations, consultez [points de terminaison de service et adressage de file d’attente](service-endpoints-and-queue-addressing.md).  
  
### <a name="msmqintegrationbinding"></a>MsmqIntegrationBinding  

 `MsmqIntegrationBinding`Est utilisé lorsque vous souhaitez qu’un point de terminaison WCF communique avec une application MSMQ existante écrite en C, C++, com ou les API System. Messaging.  
  
 Les propriétés de liaison sont les mêmes que pour `NetMsmqBinding`, avec, toutefois, les différences suivantes :  
  
- Le contrat d’opération de `MsmqIntegrationBinding` est limité à un seul paramètre de type <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>, dans lequel le paramètre de type est le type de corps.  
  
- De nombreuses propriétés de message MSMQ natives sont exposées dans le <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601> en vue d'être utilisées.  
  
- Pour faciliter la sérialisation et la désérialisation du corps des messages, des sérialiseurs, tels que XML et ActiveX, sont fournis.  
  
### <a name="sample-code"></a>Exemple de code  

 Pour obtenir des instructions étape par étape sur la manière d'écrire des services WCF qui utilisent MSMQ, consultez les rubriques suivantes :  
  
- [Procédure : échanger des messages avec des points de terminaison WCF et des applications Message Queuing](how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
  
- [Procédure : échanger des messages mis en file d’attente avec des points de terminaison WCF](how-to-exchange-queued-messages-with-wcf-endpoints.md)  
  
 Pour obtenir un exemple de code complet illustrant l'utilisation de MSMQ dans WCF, consultez les rubriques suivantes :  
  
- [Transacted MSMQ Binding](../samples/transacted-msmq-binding.md)  
  
- [Volatile Queued Communication](../samples/volatile-queued-communication.md)  
  
- [Dead Letter Queues](../samples/dead-letter-queues.md)  
  
- [Sessions and Queues](../samples/sessions-and-queues.md)  
  
- [Two-Way Communication](../samples/two-way-communication.md)
  
- [SRMP](../samples/srmp.md)  
  
- [Message Security over Message Queuing](../samples/message-security-over-message-queuing.md)  
  
## <a name="see-also"></a>Voir aussi

- [Points de terminaison de service et adressage de files d'attente](service-endpoints-and-queue-addressing.md)
- [Hébergement sur le Web d'une application en file d'attente](web-hosting-a-queued-application.md)

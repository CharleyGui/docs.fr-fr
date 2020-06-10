---
title: Gestion des messages incohérents
ms.date: 03/30/2017
ms.assetid: 8d1c5e5a-7928-4a80-95ed-d8da211b8595
ms.openlocfilehash: d219c18bb072684deb6cc1d8a2d17b1989762151
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84590564"
---
# <a name="poison-message-handling"></a>Gestion des messages incohérents
Un *message incohérent* est un message qui a dépassé le nombre maximal de tentatives de remise à l’application. Cette situation peut survenir lorsqu'une application basée sur file d'attente ne peut pas traiter un message car des erreurs se sont produites. Pour faire face aux demandes de fiabilité, une application en file d’attente reçoit des messages sous une transaction. L’abandon de la transaction dans laquelle un message en file d’attente a été reçu laisse le message dans la file d’attente afin qu’une nouvelle tentative de remise puisse être effectuée sous une nouvelle transaction. Si le problème qui a provoqué l'abandon de la transaction n'est pas résolu, l'application réceptrice peut être bloquée dans une réception et un abandon en boucle du même message jusqu'à ce que le nombre maximal de tentatives de remise soit dépassé et qu'un message incohérent soit généré.  
  
 Un message peut devenir incohérent pour de nombreuses raisons. Les raisons les plus courantes sont spécifiques à l’application. Par exemple, si une application lit un message à partir d'une file d'attente et exécute un traitement de base de données, il est possible qu'elle ne parvienne pas à obtenir un verrou sur la base de données, provoquant ainsi l'abandon de la transaction. Parce que la transaction de base de données a été abandonnée, le message reste dans la file d'attente, ce qui conduit l'application à relire le message une deuxième fois et à tenter de nouveau d'acquérir un verrou sur la base de données. Les messages peuvent également devenir incohérents s'ils contiennent des informations non valides. Par exemple, une commande fournisseur peut contenir un numéro de client non valide. Dans ces cas-là, l’application peut abandonner volontairement la transaction et forcer le message à devenir un message incohérent.  
  
 Dans de rares occasions, des messages peuvent ne pas être distribués à l'application. La couche Windows Communication Foundation (WCF) peut détecter un problème avec le message, par exemple si le message contient une trame incorrecte, des informations d’identification de message non valides qui lui sont associées ou un en-tête d’action non valide. Dans ces cas-là, l'application ne reçoit jamais le message ; toutefois, ce dernier peut encore devenir un message incohérent et être traité manuellement.  
  
## <a name="handling-poison-messages"></a>Gestion des messages incohérents  
 Dans WCF, la gestion des messages incohérents fournit un mécanisme permettant à une application réceptrice de traiter les messages qui ne peuvent pas être distribués à l’application ou les messages qui sont envoyés à l’application, mais qui ne peuvent pas être traités en raison de raisons spécifiques à l’application. Configurez la gestion des messages incohérents avec les propriétés suivantes dans chacune des liaisons mises en file d’attente disponibles :  
  
- `ReceiveRetryCount`. Valeur entière qui indique le nombre maximal de nouvelles tentatives de remise d'un message à partir de la file d'attente d'application à l'application. La valeur par défaut est 5. Elle est suffisante dans les cas où une nouvelle tentative immédiate résout le problème (par exemple, en cas d'interblocage temporaire sur une base de données).  
  
- `MaxRetryCycles`. Valeur entière qui indique le nombre maximal de cycles de nouvelle tentative. Un cycle de nouvelle tentative implique le transfert d'un message de la file d'attente d'application vers la sous-file d'attente de nouvel essai et, après un délai configurable, de la sous-file d'attente de nouvel essai vers la file d'attente d'application afin de retenter la remise. La valeur par défaut est 2. Sur Windows Vista, le message est essayé au maximum ( `ReceiveRetryCount` + 1) * ( `MaxRetryCycles` + 1) fois. `MaxRetryCycles`est ignoré sur Windows Server 2003 et Windows XP.  
  
- `RetryCycleDelay`. Délai entre les cycles de nouvelle tentative. La valeur par défaut est de 30 minutes. `MaxRetryCycles` et `RetryCycleDelay` fournissent ensemble un mécanisme permettant de gérer un problème qui peut être résolu en cas de nouvelle tentative après un délai périodique. Par exemple, cela permet de gérer le verrouillage d’un ensemble de lignes dans la validation de transaction en attente SQL Server.  
  
- `ReceiveErrorHandling`. Énumération qui indique l'action à effectuer pour un message qui n'a pas pu être remis une fois le nombre maximal de tentatives effectué. Les valeurs peuvent être Fault, Drop, Reject et Move. L'option par défaut est Fault.  
  
- Fault. Cette option envoie une erreur à l'écouteur qui a provoqué l'échec du `ServiceHost`. Le message doit être supprimé de la file d'attente d'application par un mécanisme externe pour que l'application puisse continuer à traiter les messages de la file d'attente.  
  
- Drop. Cette option supprime le message empoisonné ; celui-ci n'est jamais remis à l'application. Si la propriété `TimeToLive` du message a expiré à ce stade, le message peut apparaître dans la file d'attente de lettres mortes de l'expéditeur. Sinon, il n'apparaît nulle part. Cette option indique que l'utilisateur n'a pas spécifié quoi faire en cas de perte du message.  
  
- Reject. Cette option est disponible uniquement sur Windows Vista. Cela indique à Message Queuing (MSMQ) d’envoyer un accusé de réception négatif au gestionnaire de files d’attente d’envoi, que l’application ne peut pas recevoir le message. Le message est placé dans la file d'attente de lettres mortes du gestionnaire de files d'attente émetteur.  
  
- Move. Cette option est disponible uniquement sur Windows Vista. Elle déplace le message incohérent vers une file d'attente de messages incohérents pour un traitement ultérieur par une application de gestion de messages incohérents. La file d'attente de messages incohérents est une sous-file d'attente de la file d'attente d'application. Une application de gestion des messages incohérents peut être un service WCF qui lit les messages en dehors de la file d’attente de messages incohérents. La file d’attente de messages incohérents est une sous-file d’attente de la file d’attente de l’application. elle peut être adressée comme net. msmq:// \<*machine-name*> / *applicationQueue*;p oison, où *machine-name* est le nom de l’ordinateur sur lequel la file d’attente réside et *applicationQueue* est le nom de la file d’attente spécifique à l’application.  
  
Voici le nombre maximal de tentatives de remise effectuées pour un message :  
  
- ((ReceiveRetryCount + 1) * (MaxRetryCycles + 1)) sur Windows Vista.  
  
- (ReceiveRetryCount + 1) sur Windows Server 2003 et Windows XP.  
  
> [!NOTE]
> Aucune nouvelle tentative n'est effectuée pour un message remis avec succès.  
  
 Pour effectuer le suivi du nombre de tentatives de lecture d’un message, Windows Vista gère une propriété de message durable qui compte le nombre d’abandons et une propriété de nombre de déplacements qui compte le nombre de déplacements du message entre la file d’attente de l’application et les sous-files d’attente. Le canal WCF les utilise pour calculer le nombre de nouvelles tentatives de réception et le nombre de cycles de nouvelle tentative. Sur Windows Server 2003 et Windows XP, le nombre d’abandons est conservé en mémoire par le canal WCF et est réinitialisé en cas d’échec de l’application. En outre, le canal WCF peut contenir le nombre d’abandons pour un maximum de 256 messages en mémoire à tout moment. Si un 257ème message est lu, le nombre d'abandons du message le plus ancien est réinitialisé.  
  
 Les propriétés de nombre d'abandons et de nombre déplacements sont accessibles à l'opération de service par le biais du contexte d'opération. L'exemple de code suivant montre comment y accéder.  
  
 [!code-csharp[S_UE_MSMQ_Poison#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ue_msmq_poison/cs/service.cs#1)]  
  
 WCF fournit deux liaisons mises en file d’attente standard :  
  
- <xref:System.ServiceModel.NetMsmqBinding>. Une .NET Framework liaison adaptée à l’exécution d’une communication basée sur une file d’attente avec d’autres points de terminaison WCF.  
  
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>. Une liaison adaptée à la communication avec des applications Message Queuing existantes.  
  
> [!NOTE]
> Vous pouvez modifier les propriétés de ces liaisons en fonction des spécifications de votre service WCF. L'ensemble du mécanisme de gestion de messages incohérents est local à l'application de réception. Le processus est invisible à l'application émettrice, à moins que l'application de réception ne s'arrête finalement et ne renvoie un accusé de réception négatif à l'expéditeur. Dans ce cas, le message est déplacé vers la file d'attente de lettres mortes de l'expéditeur.  
  
## <a name="best-practice-handling-msmqpoisonmessageexception"></a>Recommandation : Gestion de MsmqPoisonMessageException  
 Lorsque le service détermine qu'un message est incohérent, le transport de mise en file d'attente lève une <xref:System.ServiceModel.MsmqPoisonMessageException> qui contient le `LookupId` du message incohérent.  
  
 Une application de réception peut implémenter l'interface <xref:System.ServiceModel.Dispatcher.IErrorHandler> pour gérer toute erreur requise par l'application. Pour plus d’informations, consultez [extension du contrôle sur la gestion des erreurs et la création de rapports](../samples/extending-control-over-error-handling-and-reporting.md).  
  
 Il est possible que l'application requière un système de gestion automatisée des messages empoisonnés qui déplace ceux-ci vers une file d'attente de messages empoisonnés afin que le service puisse accéder au reste des messages dans la file d'attente. Le seul scénario dans lequel on utilise le mécanisme de gestionnaire d'erreurs pour écouter les exceptions de message incohérent est lorsque le paramètre <xref:System.ServiceModel.Configuration.MsmqBindingElementBase.ReceiveErrorHandling%2A> a la valeur <xref:System.ServiceModel.ReceiveErrorHandling.Fault>. L'exemple de message empoisonné pour Message Queuing 3.0 illustre ce comportement. La section suivante décrit les étapes à suivre pour gérer des messages incohérents et fournit quelques recommandations :  
  
1. Assurez-vous que vos paramètres de messages empoisonnés reflètent les besoins de votre application. Lorsque vous utilisez les paramètres, assurez-vous de bien comprendre les différences entre les fonctionnalités de Message Queuing sur Windows Vista, Windows Server 2003 et Windows XP.  
  
2. Si nécessaire, implémentez le `IErrorHandler` pour gérer les erreurs de message incohérent. Étant donné que l'affectation de la valeur `ReceiveErrorHandling` à `Fault` nécessite un mécanisme manuel pour déplacer le message empoisonné hors de la file d'attente ou pour corriger un problème dépendant externe, l'utilisation typique consiste à implémenter `IErrorHandler` lorsque `ReceiveErrorHandling` a la valeur `Fault`, comme illustré dans le code suivant.  
  
     [!code-csharp[S_UE_MSMQ_Poison#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ue_msmq_poison/cs/poisonerrorhandler.cs#2)]  
  
3. Créez un `PoisonBehaviorAttribute` que le comportement de service peut utiliser. Le comportement installe le `IErrorHandler` sur le répartiteur. Voir l'exemple de code suivant.  
  
     [!code-csharp[S_UE_MSMQ_Poison#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ue_msmq_poison/cs/poisonbehaviorattribute.cs#3)]  
  
4. Assurez-vous que votre service est annoté avec l’attribut de comportement d’incohérence.  

 De plus, si `ReceiveErrorHandling` a la valeur `Fault`, `ServiceHost` renverra une erreur s'il rencontre le message empoisonné. Vous pouvez vous raccorder à l’événement d’erreur et arrêter le service, appliquer des actions correctives, puis redémarrer. Par exemple, `LookupId` dans le <xref:System.ServiceModel.MsmqPoisonMessageException> propagé au `IErrorHandler` peut être noté, et lorsque l'hôte de service renvoie une erreur, vous pouvez utiliser l'API `System.Messaging` pour recevoir le message de la file d'attente à l'aide de `LookupId`, supprimer le message de la file d'attente, puis stocker le message dans un magasin externe ou une autre file d'attente. Vous pouvez ensuite redémarrer `ServiceHost` pour continuer le traitement normal. La [gestion des messages incohérents dans MSMQ 4,0](../samples/poison-message-handling-in-msmq-4-0.md) illustre ce comportement.  
  
## <a name="transaction-time-out-and-poison-messages"></a>Délai d'expiration de transaction et messages incohérents  
 Une classe d'erreurs peut se produire entre le canal de transport de mise en file d'attente et le code utilisateur. Ces erreurs peuvent être détectées par des couches intermédiaires, telles que la couche de sécurité de message ou la logique de distribution de service. Par exemple, un certificat X.509 manquant détecté dans la couche de sécurité SOAP et une action manquante sont des cas où le message est distribué à l'application. Lorsque cela se produit, le modèle de service dépose le message. Étant donné que le message est lu dans une transaction et qu’aucun résultat pour cette transaction ne peut être fourni, le délai d’attente de transaction finit par expirer, la transaction est abandonnée et le message est remis dans la file d’attente. En d’autres termes, pour une certaine classe d’erreurs, la transaction n’abandonne pas immédiatement mais attend jusqu’à ce que la transaction expire. Vous pouvez modifier le délai d’expiration de la transaction pour un service à l’aide de <xref:System.ServiceModel.ServiceBehaviorAttribute> .  
  
 Pour modifier le délai d’expiration de la transaction à l’échelle de l’ordinateur, modifiez le fichier machine. config et définissez le délai d’expiration de la transaction approprié. Il est important de noter que, en fonction du délai d’expiration défini dans la transaction, la transaction finit par abandonner et revenir à la file d’attente et son compteur d’abandons est incrémenté. Pour finir, le message devient empoisonné et la disposition correcte est effectuée conformément aux paramètres utilisateur.  
  
## <a name="sessions-and-poison-messages"></a>Sessions et messages incohérents  
 Une session subit les mêmes procédures de nouvelle tentative et de gestion des messages incohérents qu'un simple message. Les propriétés indiquées précédemment pour les messages empoisonnés s'appliquent à la session entière. En d'autres termes, la session entière est soumise à une nouvelle tentative et finit dans une ultime file d'attente de messages empoisonnés ou dans la file d'attente de lettres mortes de l'expéditeur si le message est refusé.  
  
## <a name="batching-and-poison-messages"></a>Traitement par lot et messages incohérents  
 Si un message faisant partie d'un lot devient un message incohérent, le lot entier est annulé et le canal recommence à lire un message à la fois. Pour plus d’informations sur le traitement par lots, consultez [traitement par lot des messages dans une transaction](batching-messages-in-a-transaction.md) .  
  
## <a name="poison-message-handling-for-messages-in-a-poison-queue"></a>Gestion des messages incohérents pour les messages dans une file d'attente de messages incohérents  
 La gestion des messages incohérents ne se termine pas lorsqu'un message est placé dans la file d'attente de messages incohérents. Les messages dans la file d'attente de messages incohérents doivent encore être lus et gérés. Vous pouvez utiliser un sous-ensemble des paramètres de gestion de messages incohérents lors de la lecture des messages à partir de l'ultime sous-file d'attente de messages incohérents. Les paramètres applicables sont `ReceiveRetryCount` et `ReceiveErrorHandling`. Vous pouvez affecter la valeur Drop, Reject ou Fault à `ReceiveErrorHandling`. `MaxRetryCycles` est ignoré et une exception est levée si `ReceiveErrorHandling` a la valeur Move.  
  
## <a name="windows-vista-windows-server-2003-and-windows-xp-differences"></a>Différences entre Windows Vista, Windows Server 2003 et Windows XP  
 Comme indiqué précédemment, tous les paramètres de gestion des messages incohérents ne s’appliquent pas à Windows Server 2003 et Windows XP. Les principales différences entre Message Queuing sur Windows Server 2003, Windows XP et Windows Vista sont pertinentes pour la gestion des messages incohérents :  
  
- Message Queuing dans Windows Vista prend en charge les sous-files d’attente, tandis que Windows Server 2003 et Windows XP ne prennent pas en charge les sous-files d’attente. Les sous-files d'attente sont utilisées dans la gestion des messages incohérents. Les files d'attente de nouvel essai et la file d'attente de messages incohérents sont des sous-files d'attente de la file d'attente de l'application créée en fonction des paramètres de gestion des messages incohérents. `MaxRetryCycles` définit le nombre de sous-files de nouvel essai à créer. Par conséquent, lors de l’exécution sur Windows Server 2003 ou Windows XP, `MaxRetryCycles` est ignoré et `ReceiveErrorHandling.Move` n’est pas autorisé.  
  
- Message Queuing dans Windows Vista prend en charge l’accusé de réception négatif, contrairement à Windows Server 2003 et Windows XP. Un accusé de réception négatif provenant du gestionnaire de files d'attente de destination provoque le placement du message rejeté dans la file d'attente de lettres mortes par le gestionnaire de files d'attente source. Par conséquent, `ReceiveErrorHandling.Reject` n’est pas autorisé avec Windows Server 2003 et Windows XP.  
  
- Message Queuing dans Windows Vista prend en charge une propriété de message qui indique le nombre de tentatives de remise de messages. Cette propriété du nombre d’abandons n’est pas disponible sur Windows Server 2003 et Windows XP. Comme WCF gère le nombre d’abandons en mémoire, il est possible que cette propriété ne contienne pas une valeur exacte lorsque le même message est lu par plusieurs services WCF dans une batterie de serveurs.  
  
## <a name="see-also"></a>Voir aussi

- [Vue d'ensemble des files d'attente](queues-overview.md)
- [Différences entre les fonctionnalités de mise en file d’attente dans Windows Vista, Windows Server 2003 et Windows XP](diff-in-queue-in-vista-server-2003-windows-xp.md)
- [Spécification et gestion des erreurs dans les contrats et les services](../specifying-and-handling-faults-in-contracts-and-services.md)

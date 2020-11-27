---
title: Différences entre les fonctionnalités de mise en file d’attente dans Windows Vista, Windows Server 2003 et Windows XP
ms.date: 03/30/2017
helpviewer_keywords:
- queues [WCF], differences in operating systems
ms.assetid: aa809d93-d0a3-4ae6-a726-d015cca37c04
ms.openlocfilehash: 6ec20a0d9512b1f80da1fd423282fc1538c750ef
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96254270"
---
# <a name="differences-in-queuing-features-in-windows-vista-windows-server-2003-and-windows-xp"></a>Différences entre les fonctionnalités de mise en file d’attente dans Windows Vista, Windows Server 2003 et Windows XP

Cette rubrique résume les différences de la fonctionnalité de files d’attente Windows Communication Foundation (WCF) entre Windows Vista, Windows Server 2003 et Windows XP.  
  
## <a name="application-specific-dead-letter-queue"></a>File d'attente de lettres mortes spécifique à l'application  

 Les messages mis en file d'attente peuvent rester indéfiniment dans la file d'attente si l'application réceptrice ne les lit pas en temps voulu. Ce comportement n'est pas recommandé si les messages sont dépendants de l'heure. Les messages dépendants de l’heure ont une propriété `TimeToLive` affectée dans la liaison mise en file d’attente. Cette propriété indique la durée de vie possible des messages dans la file d'attente avant qu'ils n'expirent. Les messages ayant expiré sont envoyés dans une file d'attente spéciale appelée file d'attente de lettres mortes. Un message peut également finir dans une file d'attente de lettres mortes pour d'autres raisons, telles que le dépassement d'un quota de file d'attente ou un échec d'authentification.  
  
 En général, il existe une seule file d'attente de lettres mortes à l'échelle du système pour toutes les applications mises en file d'attente qui partagent un gestionnaire de files d'attente. Une file d'attente de lettres mortes pour chaque application permet une meilleure isolation entre les applications mises en file d'attente qui partagent un gestionnaire de files d'attente en laissant à ces applications le soin de spécifier leur propre file d'attente de lettres mortes. Une application qui partage une file d'attente de lettres mortes avec d'autres applications doit parcourir la file d'attente pour rechercher les messages qui lui sont applicables. Avec une file d'attente de lettres mortes qui lui est spécifique, l'application peut être assurée que tous les messages figurant dans sa file d'attente de lettres mortes lui sont applicables.  
  
 Windows Vista fournit des files d’attente de lettres mortes spécifiques à l’application. Les files d’attente de lettres mortes spécifiques à l’application ne sont pas disponibles dans Windows Server 2003 et Windows XP, et les applications doivent utiliser la file d’attente de lettres mortes à l’ensemble du système.  
  
## <a name="poison-message-handling"></a>Gestion des messages incohérents  

 Un message incohérent est un message qui a dépassé le nombre maximal de tentatives de remise à l'application réceptrice. Cette situation peut survenir lorsqu’une application qui lit un message d’une file d’attente transactionnelle ne peut pas traiter immédiatement le message en raison d’erreurs. Si l'application abandonne la transaction dans laquelle le message mis en file d'attente a été reçu, elle renvoie le message à la file d'attente. L’application essaie ensuite de récupérer le message dans une nouvelle transaction. Si le problème qui provoque l'erreur n'est pas résolu, l'application réceptrice peut être bloquée dans une réception et un abandon en boucle du même message jusqu'à ce que le nombre maximal de tentatives de remise soit dépassé et qu'un message incohérent soit généré.  
  
 Les principales différences entre les Message Queuing (MSMQ) sur Windows Vista, Windows Server 2003 et Windows XP qui concernent la gestion des messages incohérents sont les suivantes :  
  
- MSMQ dans Windows Vista prend en charge les sous-files d’attente, tandis que Windows Server 2003 et Windows XP ne prennent pas en charge les sous-files d’attente. Les sous-files d'attente sont utilisées dans la gestion des messages incohérents. Les files d'attente de nouvel essai et la file d'attente de messages incohérents sont des sous-files d'attente de la file d'attente de l'application créée en fonction des paramètres de gestion des messages incohérents. `MaxRetryCycles` définit le nombre de sous-files de nouvel essai à créer. Par conséquent, lors de l’exécution sur Windows Server 2003 ou Windows XP, `MaxRetryCycles` est ignoré et `ReceiveErrorHandling.Move` n’est pas autorisé.  
  
- MSMQ dans Windows Vista prend en charge l’accusé de réception négatif, contrairement à Windows Server 2003 et Windows XP. Un accusé de réception négatif provenant du gestionnaire de files d'attente de destination provoque le placement du message rejeté dans la file d'attente de lettres mortes par le gestionnaire de files d'attente source. Par conséquent, `ReceiveErrorHandling.Reject` n’est pas autorisé avec Windows Server 2003 et Windows XP.  
  
- MSMQ dans Windows Vista prend en charge une propriété de message qui indique le nombre de tentatives de remise de messages. Cette propriété du nombre d’abandons n’est pas disponible sur Windows Server 2003 et Windows XP. Comme WCF gère le nombre d’abandons en mémoire, il est possible que cette propriété ne contienne pas une valeur exacte lorsque le même message est lu par plusieurs services WCF dans une batterie de serveurs Web.  
  
## <a name="remote-transactional-read"></a>Lecture transactionnelle distante  

 MSMQ sur Windows Vista prend en charge les lectures transactionnelles distantes. Cette prise en charge permet à une application qui lit à partir d'une file d'attente d'être hébergée sur un ordinateur différent de l'ordinateur sur lequel la file d'attente est hébergée. Cela garantit la possibilité d'avoir une batterie de services qui lit à partir d'une file d'attente centrale, ce qui augmente le débit total du système. Cela garantit également que, si une défaillance se produit lors de la lecture et du traitement du message, la transaction est restaurée et le message est conservé dans la file d'attente afin d'y être traité ultérieurement.  
  
## <a name="see-also"></a>Voir aussi

- [Utilisation de files d'attente de lettres mortes pour gérer des défaillances de transfert de messages](using-dead-letter-queues-to-handle-message-transfer-failures.md)
- [Gestion des messages incohérents](poison-message-handling.md)

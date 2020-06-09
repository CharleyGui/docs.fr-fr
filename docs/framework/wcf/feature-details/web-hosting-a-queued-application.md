---
title: Hébergement sur le Web d'une application en file d'attente
ms.date: 03/30/2017
ms.assetid: c7a539fa-e442-4c08-a7f1-17b7f5a03e88
ms.openlocfilehash: 17c3d2167d3f98017c5f366ab0d700d9fb889f82
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600138"
---
# <a name="web-hosting-a-queued-application"></a>Hébergement sur le Web d'une application en file d'attente
Le service d’activation des processus Windows (WAS) gère l’activation et la durée de vie des processus de travail qui contiennent des applications qui hébergent des services Windows Communication Foundation (WCF). Le modèle de processus WAS généralise le modèle de processus IIS 6,0 pour le serveur HTTP en supprimant la dépendance sur HTTP. Cela permet aux services WCF d’utiliser à la fois des protocoles HTTP et non-HTTP, tels que net. MSMQ et MSMQ. FormatName, dans un environnement d’hébergement qui prend en charge l’activation basée sur les messages et offre la possibilité d’héberger un grand nombre d’applications sur un ordinateur donné.  
  
 WAS inclut un service d'activation Message Queuing (MSMQ) qui active une application en file d'attente lorsqu'un ou plusieurs messages sont placés dans l'une des files d'attente utilisée par l'application. Le service d'activation MSMQ est un service NT démarré automatiquement par défaut.  
  
 Pour plus d’informations sur WAS et ses avantages, consultez [hébergement dans le service d’activation des processus Windows](hosting-in-windows-process-activation-service.md). Pour plus d’informations sur MSMQ, voir [vue d’ensemble des files d’attente](queues-overview.md).
  
## <a name="queue-addressing-in-was"></a>Adressage de file d'attente dans le service WAS  
 Les applications WAS ont des adresses URI (Uniform Resource Identifier). Les adresses d'application ont deux parties : un préfixe URI de base et une adresse relative spécifique à l'application (chemin d'accès). Ces deux parties fournissent l'adresse externe d'une application lorsqu'elles sont jointes. Le préfixe URI de base est construit à partir de la liaison de site et est utilisé pour toutes les applications sous le site, par exemple « net. msmq : préfixé », « MSMQ. FormatName : préfixé » ou « net. TCP : préfixé ». Les adresses d’application sont ensuite construites en tenant des fragments de chemin d’accès spécifiques à l’application (tels que « /applicationOne ») et en les ajoutant au préfixe URI de base pour arriver à l’URI d’application complet, par exemple, « net. msmq://localhost/applicationOne ».  
  
 Le service d'activation MSMQ utilise l'URI d'application pour mettre en correspondance la file d'attente dont le service d'activation MSMQ doit surveiller les messages. Lorsque le service d'activation MSMQ démarre, il énumère toutes les files d'attente publiques et privées sur l'ordinateur à partir duquel il est configuré pour recevoir et surveille leurs messages. Toutes les 10 minutes, le service d'activation MSMQ actualise la liste de files d'attente à surveiller. Lorsqu’un message est détecté dans une file d’attente, le service d’activation fait correspondre le nom de file d’attente à l’URI d’application la plus longue correspondante pour la liaison net.msmq et active l’application.  
  
> [!NOTE]
> L'application qui est activée doit correspondre (correspondance la plus longue) au préfixe du nom de file d'attente.  
  
 Par exemple, un nom de file d'attente est le suivant : msmqWebHost/orderProcessing/service.svc. Si l'Application 1 a un répertoire virtuel /msmqWebHost/orderProcessing avec un service.svc au-dessous et que l'Application 2 a un répertoire virtuel /msmqWebHost avec un orderProcessing.svc au-dessous, l'Application 1 est activée. Si l'Application 1 est supprimée, l'Application 2 est activée.  
  
> [!NOTE]
> Lorsqu'une file d'attente est créée, les messages qui y sont envoyés n'activent l'application que lorsque le service d'activation MSMQ actualise la liste de file d'attente, à savoir au plus 10 minutes après la création de la file d'attente. Le redémarrage du service d'activation actualise également la liste de file d'attente.  
  
### <a name="the-effect-of-private-and-public-queues-on-addressing"></a>L'impact des files d'attente privées et publiques sur l'adressage  
 Le service d'activation MSMQ n'effectue aucune distinction entre le contrôle de file d'attente privée et publique. En conséquence, vous ne pouvez pas avoir de files d'attente privées et publiques avec le même nom. Si c'est le cas, une application hébergée sur le Web peut être activée suite à la lecture de l'une ou l'autre file d'attente.  
  
### <a name="queue-configuration-for-activation"></a>Configuration de file d'attente pour l'activation  
 Le service d'activation MSMQ s'exécute comme Service réseau. Il s'agit du service qui contrôle les files d'attente pour activer des applications. Pour que ce service active des applications à partir de la file d'attente, celle-ci doit autoriser le Service réseau à lire les messages dans sa liste de contrôle d'accès.  
  
### <a name="poison-messaging"></a>Messagerie empoisonnée  
 La gestion des messages incohérents dans WCF est gérée par le canal, qui détecte non seulement qu’un message est incohérent, mais sélectionne une disposition en fonction de la configuration de l’utilisateur. En conséquence, il n'y a qu'un seul message dans la file d'attente. L'application hébergée sur le Web abandonne de manière répétée et le message est déplacé vers une file d'attente des nouvelles tentatives. À un point dicté par le délai de cycle de nouvelle tentative, le message est déplacé de la file d'attente des nouvelles tentatives vers la file d'attente principale, pour une nouvelle tentative. Mais cela requiert que le canal en file d'attente soit actif. Si l'application est recyclée par le service WAS, le message reste dans la file d'attente des nouvelles tentatives jusqu'à ce qu'un autre message arrive dans la file d'attente principale pour activer l'application en file d'attente. La solution de contournement dans ce cas consiste à déplacer manuellement le message de la file d'attente des nouvelles tentatives vers la file d'attente principale afin de réactiver l'application.  
  
### <a name="subqueue-and-system-queue-caveat"></a>Limitations relatives aux sous-files d'attente et aux files d'attente système  
 Une application hébergée par le service WAS ne peut pas être activée sur la base des messages présents dans une file d'attente système, telle que la file d'attente de lettres mortes à l'échelle du système, ou dans des sous-files d'attente, telles que les sous-files d'attente de poison. Il s'agit d'une limitation pour cette version du produit.  
  
## <a name="see-also"></a>Voir aussi

- [Gestion des messages incohérents](poison-message-handling.md)
- [Points de terminaison de service et adressage de files d'attente](service-endpoints-and-queue-addressing.md)

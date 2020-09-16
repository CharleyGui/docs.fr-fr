---
title: Hébergement dans une application de service Windows
ms.date: 03/30/2017
ms.assetid: f4199998-27f3-4dd9-aee4-0a4addfa9f24
ms.openlocfilehash: cb952cfcd670a790033fbec70de00a4db2541237
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555846"
---
# <a name="hosting-in-a-windows-service-application"></a>Hébergement dans une application de service Windows
Les services Windows (autrefois connus comme services Windows NT) fournissent un modèle de processus particulièrement adapté aux applications qui doivent exister dans un exécutable à durée d’exécution longue et n’affichent aucune forme d’interface utilisateur. La durée de vie de processus d'une application de service Windows est gérée par le gestionnaire de contrôle des services (SCM) qui vous autorise à démarrer, arrêter et suspendre les applications de service Windows. Vous pouvez configurer un processus de service Windows pour qu’il démarre automatiquement lorsque l’ordinateur démarre, ce qui en fait un environnement d’hébergement approprié pour les applications « Always on ». Pour plus d’informations sur les applications de service Windows, consultez [applications de service Windows](https://go.microsoft.com/fwlink/?LinkId=89450).  
  
 Les applications qui hébergent des services WCF (Windows Communication Foundation à long terme) partagent de nombreuses caractéristiques avec les services Windows. En particulier, les services WCF sont des exécutables de serveur de longue durée qui n’interagissent pas directement avec l’utilisateur et n’implémentent donc aucune forme d’interface utilisateur. Par conséquent, l’hébergement de services WCF dans une application de service Windows est une option permettant de créer des applications WCF robustes, à long terme.  
  
 Souvent, les développeurs WCF doivent décider s’il faut héberger leur application WCF dans une application de service Windows ou à l’intérieur de l’environnement d’hébergement WAS (Internet Information Services (IIS) ou Windows Process Activation Service (WAS). Vous pouvez envisager d'utiliser des applications de service Windows dans les conditions suivantes :  
  
- Votre application requiert l'activation explicite. Par exemple, vous devez utiliser des services Windows lorsque votre application doit démarrer automatiquement quand le serveur démarre au lieu d'être démarrée dynamiquement en réponse au premier message entrant.  
  
- Le processus qui héberge votre application doit rester actif une fois démarré. Une fois démarré, un processus de service Windows reste actif à moins qu'il ne soit explicitement interrompu par l'administrateur du serveur via le gestionnaire de contrôle des services. Les applications hébergées dans IIS ou WAS peuvent être démarrées et arrêtées dynamiquement pour une utilisation optimale des ressources système. Les applications qui requièrent un contrôle explicite sur la durée de vie de leur processus d'hébergement doivent utiliser des services Windows au lieu d'IIS ou WAS.  
  
- Votre service WCF doit s’exécuter sur Windows Server 2003 et utiliser des transports autres que HTTP. Sur Windows Server 2003, l’environnement d’hébergement IIS 6,0 est limité à la communication HTTP uniquement. Les applications de service Windows ne sont pas soumises à cette restriction et peuvent utiliser n’importe quel transport WCF pris en charge, y compris net. TCP, net. pipe et net. MSMQ.  
  
### <a name="to-host-wcf-inside-of-a-windows-service-application"></a>Pour héberger WCF dans une application de service Windows  
  
1. Créez une application de service Windows. Vous pouvez écrire des applications de service Windows en code managé à l'aide des classes dans l'espace de noms <xref:System.ServiceProcess>. Cette application doit inclure une classe qui hérite de <xref:System.ServiceProcess.ServiceBase>.  
  
2. Liez la durée de vie des services WCF à la durée de vie de l’application de service Windows. En règle générale, vous souhaitez que les services WCF hébergés dans une application de service Windows deviennent actifs lorsque le service d’hébergement démarre, arrêter l’écoute des messages lorsque le service d’hébergement est arrêté, puis arrêter le processus d’hébergement lorsque le service WCF rencontre une erreur. Cela peut être accompli de la façon suivante :  
  
    - Remplacez <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> pour ouvrir une ou plusieurs instances de <xref:System.ServiceModel.ServiceHost>. Une même application de service Windows peut héberger plusieurs services WCF qui démarrent et s’arrêtent en tant que groupe.  
  
    - Substituez <xref:System.ServiceProcess.ServiceBase.OnStop%2A> pour appeler <xref:System.ServiceModel.Channels.CommunicationObject.Closed> sur <xref:System.ServiceModel.ServiceHost> tous les services WCF en cours d’exécution qui ont été démarrés pendant <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> .  
  
    - Abonnez-vous à l'événement <xref:System.ServiceModel.Channels.CommunicationObject.Faulted> de <xref:System.ServiceModel.ServiceHost> et utilisez la classe <xref:System.ServiceProcess.ServiceController> pour interrompre l'application de service Windows en cas d'erreur.  
  
     Les applications de service Windows qui hébergent les services WCF sont déployées et gérées de la même façon que les applications de service Windows qui n’utilisent pas WCF.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceProcess>
- [Procédure pas à pas : création d’une application de service Windows dans le Concepteur de composants](https://go.microsoft.com/fwlink/?LinkId=94875)
- [Procédure : héberger un service WCF dans un service Windows managé](how-to-host-a-wcf-service-in-a-managed-windows-service.md)
- [Windows Service Host](../samples/windows-service-host.md)
- [Architecture de programmation d'une application de service](https://go.microsoft.com/fwlink/?LinkId=94876)
- [Fonctionnalités d’hébergement de Windows Server AppFabric](/previous-versions/appfabric/ee677189(v=azure.10))

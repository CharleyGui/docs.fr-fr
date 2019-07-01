---
title: Hébergement de services
ms.date: 03/30/2017
helpviewer_keywords:
- hosting services [WCF]
ms.assetid: 192be927-6be2-4fda-98f0-e513c4881acc
ms.openlocfilehash: b1a0a07876e9cc111e8c5eef56f208d7bf2cb49f
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2019
ms.locfileid: "67487698"
---
# <a name="hosting-services"></a>Hébergement de services
Pour devenir actif, un service doit être hébergé dans un environnement d'exécution qui le crée et contrôle son contexte et sa durée de vie. Services de Windows Communication Foundation (WCF) sont conçus pour s’exécuter dans n’importe quel processus Windows qui prend en charge le code managé.  
  
 WCF fournit un modèle de programmation unifié pour la création d’applications orientées service. Ce modèle de programmation reste cohérent et est indépendant de l'environnement d'exécution dans lequel le service est déployé. En pratique, cela signifie que le code de vos services est essentiellement le même quelle que soit l'option d'hébergement.  
  
 Ces options d'hébergement vont de l'exécution dans une application console à une exécution dans des environnements serveur tels qu'un service Windows dans un processus de travail managé par les services IIS (Internet Information Services) ou WAS (Windows Process Activation Services). Les développeurs choisissent l'environnement d'hébergement qui répond aux spécifications de déploiement du service. Ces spécifications peuvent dériver de la plateforme sur laquelle l'application est déployée, du transport sur lequel envoyer et recevoir des messages ou du type de recyclage de processus et tout autre gestion de processus indispensable pour garantir la disponibilité adéquate, ou d'autres impératifs de gestion ou de fiabilité. La section suivante fournit des informations et des instructions sur les options d'hébergement.  
  
## <a name="hosting-options"></a>Options d'hébergement  
  
#### <a name="self-hosting-in-a-managed-application"></a>Auto-hébergement dans une application managée  
 Services WCF peuvent être hébergés dans toute application managée. Il s'agit de l'option la plus souple car l'infrastructure à déployer est la plus faible. Vous incorporez le code pour le service à l'intérieur du code d'application managée, puis créez et ouvrez une instance de <xref:System.ServiceModel.ServiceHost> pour rendre le service disponible. Pour plus d'informations, voir [Procédure : Héberger un Service WCF dans une Application managée](../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md).  
  
 Cette option active deux scénarios courants : Services WCF en cours d’exécution à l’intérieur d’applications console et les applications clientes riches tels que ceux basés sur Windows Presentation Foundation (WPF) ou Windows Forms (WinForms). Hébergement d’un service WCF à l’intérieur d’une application console est généralement utile pendant la phase de développement de l’application. Cela simplifie son débogage, l'obtention des informations de suivi pour déterminer ce qui se passe à l'intérieur de l'application, et son déplacement en la copiant vers un nouvel emplacement. Cette option d’hébergement rend également plus facile pour les applications clientes riches, telles que les applications WPF et WinForms, pour communiquer avec le monde extérieur. Par exemple, un client de collaboration pair à pair qui utilise WPF pour son interface utilisateur et héberge également un service WCF qui permet aux autres clients pour vous connecter à celui-ci et partager des informations.  
  
#### <a name="managed-windows-services"></a>Services Windows managés  
 Cette option d’hébergement consiste à enregistrer le domaine d’application (AppDomain) qui héberge un service WCF en tant qu’un Service Windows managé (anciennement service NT) afin que la durée de vie du processus du service est contrôlée par le Gestionnaire de contrôle des services (SCM) pour Services de Windows. Comme l'option d'auto-hébergement, ce type d'environnement d'hébergement requiert que du code d'hébergement soit écrit dans le cadre de l'application. Le service est implémenté comme un Service Windows et comme un service WCF en provoquant qu’elle hérite la <xref:System.ServiceProcess.ServiceBase> classe, ainsi que de l’interface de contrat de service à partir d’un WCF. Le <xref:System.ServiceModel.ServiceHost> est ensuite créé et ouvert dans une méthode <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> substituée et fermée dans une méthode <xref:System.ServiceProcess.ServiceBase.OnStop> substituée. Une classe Installer qui hérite de <xref:System.Configuration.Install.Installer> doit également être implémentée pour permettre au programme d'être installé comme un service Windows par l'outil Installutil.exe. Pour plus d'informations, voir [Procédure : Héberger un Service WCF dans un Service Windows managé](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-a-managed-windows-service.md). Le scénario activé par l’option d’hébergement du Service Windows managé est celle d’un service WCF de longs hébergé en dehors d’IIS dans un environnement sécurisé qui n’est pas activé en message. La durée de vie du service est contrôlée par le système d'exploitation. Cette option d'hébergement est disponible dans toutes les versions de Windows.  
  
#### <a name="internet-information-services-iis"></a>Services IIS (Internet Information Services)  
 L’option d’hébergement IIS est intégré à ASP.NET et utilise les fonctionnalités qu'offrent de ces technologies, telles que les processus recyclage, l’arrêt inactif, de processus sur l’intégrité et de l’activation basée sur le message. Sur les systèmes d'exploitation [!INCLUDE[wxp](../../../includes/wxp-md.md)] et [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] , il s'agit de la solution par défaut pour héberger les applications de service Web qui sont fortement sollicitées et doivent être très évolutives. Les services IIS offrent également la facilité de gestion intégrée que les clients attendent d'un produit serveur de classe d'entreprise. Cette option d'hébergement requiert que les services IIS soient configurés correctement, mais n'exige pas l'écriture d'un code d'hébergement dans le cadre de l'application. Pour plus d’informations sur la configuration d’IIS à l’hébergement d’un service WCF, consultez [Comment : Héberger un Service WCF dans IIS](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).  
  
 Notez que les services hébergés par IIS peuvent utiliser uniquement le transport HTTP. Son implémentation dans IIS 5.1 a introduit des limitations dans [!INCLUDE[wxp](../../../includes/wxp-md.md)]. L’activation basée sur message fournie pour un service WCF par IIS 5.1 sur [!INCLUDE[wxp](../../../includes/wxp-md.md)] bloque tout autre service WCF auto-hébergé sur le même ordinateur d’utiliser le port 80 pour communiquer. Services WCF peuvent être exécutés dans le même processus de travail/Pool AppDomain/Application en tant que d’autres applications quand ils sont hébergés par IIS 6.0 sur [!INCLUDE[ws2003](../../../includes/ws2003-md.md)]. Mais étant donné que WCF et IIS 6.0 utilisent la pile HTTP en mode noyau (HTTP.sys), IIS 6.0 peuvent partager le port 80 avec d’autres services WCF auto-hébergés en cours d’exécution sur le même ordinateur, contrairement à IIS 5.1.  
  
#### <a name="windows-process-activation-service-was"></a>Windows Process Activation Service (WAS)  
 Le service WAS (Windows Process Activation Service) est le nouveau mécanisme d'activation de processus pour [!INCLUDE[lserver](../../../includes/lserver-md.md)] , également disponible sur [!INCLUDE[wv](../../../includes/wv-md.md)]. Il conserve le modèle de processus IIS 6.0 familier (pools d’applications et activation de processus basée sur message) et l’hébergement des fonctionnalités (telles que la protection contre les pannes rapide sur l’intégrité et recyclage), mais il supprime la dépendance sur HTTP à partir de l’activation architecture. IIS 7.0 utilise WAS pour accomplir l’activation basée sur le message via HTTP. Les composants WCF supplémentaires s’intègrent aussi dans le service WAS pour assurer l’activation basée sur un message sur les autres protocoles WCF prend en charge, tels que TCP, MSMQ et canaux nommés. Cela permet aux applications qui utilisent des protocoles de communication d'utiliser les fonctionnalités IIS (telles que le recyclage de processus, la protection rapide contre les pannes et le système de configuration commun) qui étaient réservées exclusivement aux applications basées sur HTTP.  
  
 Cette option d'hébergement requiert que les services WAS soient configurés correctement, mais n'exige pas l'écriture d'un code d'hébergement dans le cadre de l'application. Pour plus d’informations sur la configuration de l’hébergement WAS, consultez [Comment : Héberger un Service WCF dans WAS](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md).  
  
## <a name="choosing-a-hosting-environment"></a>Choix d'un environnement d'hébergement  
 Le tableau suivant résume certains avantages et scénarios clés associés à chacune des options d'hébergement.  
  
|Environnement d'hébergement|Scénarios courants|Avantages et limitations clés|  
|-------------------------|----------------------|----------------------------------|  
|Application managée (« auto-hébergée »)|-Applications consoles utilisées pendant le développement.<br />-WinForm élaborées et les applications client WPF l’accès aux services.|-Flexible.<br />-Facile à déployer.<br />-N’est pas une solution d’entreprise pour les services.|  
|Services Windows (autrefois appelés services NT)|-Un longue service WCF hébergé en dehors d’IIS.|-Durée de vie de processus de Service contrôlée par le système d’exploitation, ne pas activé par message.<br />-Prise en charge par toutes les versions de Windows.<br />-Environnement sécurisé.|  
|IIS 5.1, IIS 6.0|-Exécuter un service WCF côte à côte avec ASP.NET contenu sur Internet en utilisant le protocole HTTP.|-Recyclage de processus.<br />-Inactive s’est arrêté.<br />-Traiter l’analyse du fonctionnement.<br />-Activation basée sur message.<br />-HTTP uniquement.|  
|Windows Process Activation Service (WAS)|-Exécution d’un service WCF sans installer IIS sur Internet à l’aide de différents protocoles de transport.|-IIS n’est pas nécessaire.<br />-Recyclage de processus.<br />-Inactive s’est arrêté.<br />-Traiter l’analyse du fonctionnement.<br />-Activation basée sur message.<br />-Fonctionne avec HTTP, TCP, canaux nommés et MSMQ.|  
|IIS 7,0|-Exécution d’un service WCF avec contenu ASP.NET.<br />-Exécution d’un service WCF sur Internet à l’aide de différents protocoles de transport.|-A des avantages.<br />-Intégré avec du contenu ASP.NET et IIS.|  
  
 Le choix d'un environnement d'hébergement dépend de la version de Windows sur lequel il est déployé, des transports requis pour envoyer les messages et du type de recyclage de processus et de domaine d'application requis. Le tableau suivant résume les données liées à ces spécifications.  
  
|Environnement d'hébergement|Disponibilité de plateforme|Transports pris en charge|Recyclage de processus et AppDomain|  
|-------------------------|---------------------------|--------------------------|-------------------------------------|  
|Applications managées (« auto-hébergées »)|[!INCLUDE[wxp](../../../includes/wxp-md.md)], [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], [!INCLUDE[wv](../../../includes/wv-md.md)],<br /><br /> [!INCLUDE[lserver](../../../includes/lserver-md.md)]|HTTP,<br /><br /> net.tcp,<br /><br /> net.pipe,<br /><br /> net.msmq|Non|  
|Services Windows (autrefois appelés services NT)|[!INCLUDE[wxp](../../../includes/wxp-md.md)], [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], [!INCLUDE[wv](../../../includes/wv-md.md)],<br /><br /> [!INCLUDE[lserver](../../../includes/lserver-md.md)]|HTTP,<br /><br /> net.tcp,<br /><br /> net.pipe,<br /><br /> net.msmq|Non|  
|IIS 5,1|[!INCLUDE[wxp](../../../includes/wxp-md.md)]|HTTP|Oui|  
|IIS 6.0|[!INCLUDE[ws2003](../../../includes/ws2003-md.md)]|HTTP|Oui|  
|Windows Process Activation Service (WAS)|[!INCLUDE[wv](../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../includes/lserver-md.md)]|HTTP,<br /><br /> net.tcp,<br /><br /> net.pipe,<br /><br /> net.msmq|Oui|  
  
 Il est important de noter que l'exécution d'un service ou d'une extension à partir d'un hôte non fiable compromet la sécurité. Notez aussi que lors de l'ouverture d'un <xref:System.ServiceModel.ServiceHost> lorsque l'emprunt d'identité est activé, une application doit garantir que l'utilisateur n'est pas déconnecté, par exemple en mettant en cache le <xref:System.Security.Principal.WindowsIdentity> de l'utilisateur.  
  
## <a name="see-also"></a>Voir aussi

- [Configuration système requise](../../../docs/framework/wcf/wcf-system-requirements.md)
- [Cycle de vie de la programmation de base](../../../docs/framework/wcf/basic-programming-lifecycle.md)
- [Implémentation de contrats de service](../../../docs/framework/wcf/implementing-service-contracts.md)
- [Guide pratique pour Héberger un Service WCF dans IIS](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)
- [Guide pratique pour Héberger un Service WCF dans WAS](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md)
- [Guide pratique pour Héberger un Service WCF dans un Service Windows managé](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-a-managed-windows-service.md)
- [Guide pratique pour Héberger un Service WCF dans une Application managée](../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)

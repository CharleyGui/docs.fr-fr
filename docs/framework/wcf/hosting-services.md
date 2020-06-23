---
title: Hébergement de services
description: En savoir plus sur les options d’hébergement pour un service WCF. Un service doit être hébergé dans un environnement d’exécution qui le crée et contrôle son contexte et sa durée de vie.
ms.date: 03/30/2017
helpviewer_keywords:
- hosting services [WCF]
ms.assetid: 192be927-6be2-4fda-98f0-e513c4881acc
ms.openlocfilehash: 86ce392bb76b22e2b6a65fa1d005ed8e9589af15
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246379"
---
# <a name="hosting-services"></a>Services d’hébergement

Pour devenir actif, un service doit être hébergé dans un environnement d'exécution qui le crée et contrôle son contexte et sa durée de vie. Les services Windows Communication Foundation (WCF) sont conçus pour s’exécuter dans n’importe quel processus Windows qui prend en charge le code managé.

WCF fournit un modèle de programmation unifié pour créer des applications orientées service. Ce modèle de programmation reste cohérent et est indépendant de l'environnement d'exécution dans lequel le service est déployé. En pratique, cela signifie que le code de vos services est essentiellement le même quelle que soit l'option d'hébergement.

Ces options d'hébergement vont de l'exécution dans une application console à une exécution dans des environnements serveur tels qu'un service Windows dans un processus de travail managé par les services IIS (Internet Information Services) ou WAS (Windows Process Activation Services). Les développeurs choisissent l'environnement d'hébergement qui répond aux spécifications de déploiement du service. Ces spécifications peuvent dériver de la plateforme sur laquelle l'application est déployée, du transport sur lequel envoyer et recevoir des messages ou du type de recyclage de processus et tout autre gestion de processus indispensable pour garantir la disponibilité adéquate, ou d'autres impératifs de gestion ou de fiabilité. La section suivante fournit des informations et des instructions sur les options d'hébergement.

## <a name="hosting-options"></a>Options d’hébergement

### <a name="self-host-in-a-managed-application"></a>Auto-hébergement dans une application managée
 Les services WCF peuvent être hébergés dans n’importe quelle application managée. Il s'agit de l'option la plus souple car l'infrastructure à déployer est la plus faible. Vous incorporez le code pour le service à l'intérieur du code d'application managée, puis créez et ouvrez une instance de <xref:System.ServiceModel.ServiceHost> pour rendre le service disponible. Pour plus d’informations, consultez [Comment : héberger un service WCF dans une application managée](how-to-host-a-wcf-service-in-a-managed-application.md).

 Cette option active deux scénarios courants : les services WCF qui s’exécutent dans les applications console et les applications clientes riches, telles que celles basées sur Windows Presentation Foundation (WPF) ou Windows Forms (WinForms). L’hébergement d’un service WCF à l’intérieur d’une application console est généralement utile pendant la phase de développement de l’application. Cela simplifie son débogage, l'obtention des informations de suivi pour déterminer ce qui se passe à l'intérieur de l'application, et son déplacement en la copiant vers un nouvel emplacement. Cette option d’hébergement permet également aux applications clientes riches, telles que les applications WPF et WinForms, de communiquer facilement avec le monde extérieur. Par exemple, un client de collaboration pair à pair qui utilise WPF pour son interface utilisateur et héberge également un service WCF qui permet à d’autres clients de s’y connecter et de partager des informations.

### <a name="managed-windows-services"></a>Services Windows managés

Cette option d’hébergement consiste à inscrire le domaine d’application (AppDomain) qui héberge un service WCF en tant que service Windows géré (anciennement appelé service NT) afin que la durée de vie du processus du service soit contrôlée par le gestionnaire de contrôle des services (SCM) pour les services Windows. Comme l'option d'auto-hébergement, ce type d'environnement d'hébergement requiert que du code d'hébergement soit écrit dans le cadre de l'application. Le service est implémenté en tant que service Windows et en tant que service WCF en l’empêchant d’hériter de la <xref:System.ServiceProcess.ServiceBase> classe, ainsi que d’une interface de contrat de service WCF. Le <xref:System.ServiceModel.ServiceHost> est ensuite créé et ouvert dans une méthode <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> substituée et fermée dans une méthode <xref:System.ServiceProcess.ServiceBase.OnStop> substituée. Une classe Installer qui hérite de <xref:System.Configuration.Install.Installer> doit également être implémentée pour permettre au programme d'être installé comme un service Windows par l'outil Installutil.exe. Pour plus d’informations, consultez [Comment : héberger un service WCF dans un service Windows managé](./feature-details/how-to-host-a-wcf-service-in-a-managed-windows-service.md). Le scénario activé par l’option d’hébergement du service Windows managé est celui d’un service WCF de longue durée hébergé en dehors d’IIS dans un environnement sécurisé qui n’est pas activé pour les messages. La durée de vie du service est contrôlée par le système d'exploitation. Cette option d'hébergement est disponible dans toutes les versions de Windows.

### <a name="internet-information-services-iis"></a>Internet Information Services (IIS)

L’option d’hébergement IIS est intégrée à ASP.NET et utilise les fonctionnalités offertes par ces technologies, telles que le recyclage de processus, l’arrêt inactif, le contrôle d’état de processus et l’activation basée sur des messages. Sur les systèmes d’exploitation Windows XP et Windows Server 2003, il s’agit de la solution recommandée pour l’hébergement d’applications de service Web qui doivent être hautement disponibles et hautement évolutives. Les services IIS offrent également la facilité de gestion intégrée que les clients attendent d'un produit serveur de classe d'entreprise. Cette option d'hébergement requiert que les services IIS soient configurés correctement, mais n'exige pas l'écriture d'un code d'hébergement dans le cadre de l'application. Pour plus d’informations sur la configuration de l’hébergement IIS pour un service WCF, consultez [Comment : héberger un service WCF dans IIS](./feature-details/how-to-host-a-wcf-service-in-iis.md).

 Les services hébergés par IIS peuvent utiliser uniquement le transport HTTP. Son implémentation dans IIS 5,1 a introduit des limitations dans Windows XP. L’activation basée sur des messages fournie pour un service WCF par IIS 5,1 sur Windows XP empêche tout autre service WCF auto-hébergé sur le même ordinateur d’utiliser le port 80 pour communiquer. Les services WCF peuvent s’exécuter dans le même pool d’applications/processus de travail que d’autres applications hébergées par IIS 6,0 sur Windows Server 2003. Toutefois, étant donné que WCF et IIS 6,0 utilisent tous deux la pile HTTP en mode noyau (HTTP.sys), IIS 6,0 peut partager le port 80 avec d’autres services WCF auto-hébergés qui s’exécutent sur le même ordinateur, contrairement à IIS 5,1.

### <a name="windows-process-activation-service-was"></a>Windows Process Activation Service (WAS)

Le service WAS (Windows Process Activation Service) est le nouveau mécanisme d’activation de processus pour Windows Server 2008 qui est également disponible sur Windows Vista. Il conserve le modèle de processus IIS 6,0 familier (pools d’applications et activation de processus basée sur des messages) et les fonctionnalités d’hébergement (telles que la protection rapide contre les défaillances, le contrôle d’intégrité et le recyclage), mais il supprime la dépendance sur HTTP de l’architecture d’activation. IIS 7,0 utilise WAS pour accomplir l’activation basée sur des messages via HTTP. Les composants WCF supplémentaires s’intègrent également à WAS pour fournir une activation basée sur les messages sur les autres protocoles pris en charge par WCF, tels que TCP, MSMQ et les canaux nommés. Cela permet aux applications qui utilisent des protocoles de communication d'utiliser les fonctionnalités IIS (telles que le recyclage de processus, la protection rapide contre les pannes et le système de configuration commun) qui étaient réservées exclusivement aux applications basées sur HTTP.

 Cette option d'hébergement requiert que les services WAS soient configurés correctement, mais n'exige pas l'écriture d'un code d'hébergement dans le cadre de l'application. Pour plus d’informations sur la configuration de l’hébergement WAS, consultez [Comment : héberger un service WCF dans was](./feature-details/how-to-host-a-wcf-service-in-was.md).

## <a name="choose-a-hosting-environment"></a>Choisir un environnement d’hébergement
 Le tableau suivant résume certains avantages et scénarios clés associés à chacune des options d'hébergement.

|Environnement d'hébergement|Scénarios courants|Avantages et limitations clés|
|-------------------------|----------------------|----------------------------------|
|Application managée (« auto-hébergée »)|-Applications de console utilisées pendant le développement.<br />-Riches applications clientes WinForm et WPF accédant aux services.|Fixes.<br />-Facile à déployer.<br />-N’est pas une solution d’entreprise pour les services.|
|Services Windows (autrefois appelés services NT)|-Un service WCF de longue durée hébergé en dehors d’IIS.|-Durée de vie du processus de service contrôlé par le système d’exploitation, et non activée par message.<br />-Prise en charge par toutes les versions de Windows.<br />-Environnement sécurisé.|
|IIS 5,1, IIS 6,0|-Exécution d’un service WCF côte à côte avec le contenu ASP.NET sur Internet à l’aide du protocole HTTP.|: Recyclage de processus.<br />-Arrêt inactif.<br />-Analyse de l’intégrité des processus.<br />-Activation basée sur les messages.<br />-HTTP uniquement.|
|Windows Process Activation Service (WAS)|-Exécution d’un service WCF sans installer IIS sur Internet à l’aide de différents protocoles de transport.|-IIS n’est pas requis.<br />: Recyclage de processus.<br />-Arrêt inactif.<br />-Analyse de l’intégrité des processus.<br />-Activation basée sur les messages.<br />-Fonctionne avec les protocoles HTTP, TCP, les canaux nommés et MSMQ.|
|IIS 7.0|-Exécution d’un service WCF avec le contenu ASP.NET.<br />-Exécution d’un service WCF sur Internet à l’aide de différents protocoles de transport.|-Avantages.<br />-Intégré avec ASP.NET et le contenu IIS.|

 Le choix d'un environnement d'hébergement dépend de la version de Windows sur lequel il est déployé, des transports requis pour envoyer les messages et du type de recyclage de processus et de domaine d'application requis. Le tableau suivant résume les données liées à ces spécifications.

|Environnement d'hébergement|Disponibilité de plateforme|Transports pris en charge|Recyclage de processus et AppDomain|
|-------------------------|---------------------------|--------------------------|-------------------------------------|
|Applications managées (« auto-hébergées »)|Windows XP, Windows Server 2003, Windows Vista,<br /><br /> Windows Server 2008|HTTP,<br /><br /> net.tcp,<br /><br /> net.pipe,<br /><br /> net.msmq|No|
|Services Windows (autrefois appelés services NT)|Windows XP, Windows Server 2003, Windows Vista,<br /><br /> Windows Server 2008|HTTP,<br /><br /> net.tcp,<br /><br /> net.pipe,<br /><br /> net.msmq|No|
|IIS 5,1|Windows XP|HTTP|Yes|
|IIS 6.0|Windows Server 2003|HTTP|Yes|
|Windows Process Activation Service (WAS)|Windows Vista, Windows Server 2008|HTTP,<br /><br /> net.tcp,<br /><br /> net.pipe,<br /><br /> net.msmq|Yes|

 Il est important de noter que l'exécution d'un service ou d'une extension à partir d'un hôte non fiable compromet la sécurité. En outre, lors de l’ouverture d’un <xref:System.ServiceModel.ServiceHost> sous emprunt d’identité, une application doit s’assurer que l’utilisateur n’est pas déconnecté, par exemple en mettant en cache le <xref:System.Security.Principal.WindowsIdentity> de l’utilisateur.

## <a name="see-also"></a>Voir aussi

- [Cycle de vie de la programmation de base](basic-programming-lifecycle.md)
- [Implémentation de contrats de service](implementing-service-contracts.md)
- [Comment : héberger un service WCF dans IIS](./feature-details/how-to-host-a-wcf-service-in-iis.md)
- [Comment : héberger un service WCF dans WAS](./feature-details/how-to-host-a-wcf-service-in-was.md)
- [Comment : héberger un service WCF dans un service Windows managé](./feature-details/how-to-host-a-wcf-service-in-a-managed-windows-service.md)
- [Comment : héberger un service WCF dans une application managée](how-to-host-a-wcf-service-in-a-managed-application.md)

---
title: Introduction aux applications de service Windows
description: Lisez une introduction aux applications de service Windows. Les services vous permettent de créer des applications exécutables à long terme qui s’exécutent dans leurs propres sessions Windows.
ms.date: 03/30/2017
f1_keywords:
- ServiceController
helpviewer_keywords:
- Windows Service applications, deploying
- OnStop method
- OnPause method
- services, about services
- Service class, Windows Service applications
- framework services, creating services
- ServiceController components, about Windows services
- Win32OwnProcess service type
- services, lifetime
- OnContinue method
- Windows Service applications, about Windows Service applications
- services, states
- service states
- WaitForStatus method
- Win32ShareProcess service type
- Windows Service applications, lifetime
ms.assetid: 1b1b5e67-3ff3-40c0-8154-322cfd6ef0ae
ms.openlocfilehash: fd69ca11d42a229b861bafd642383e89f0119815
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96270469"
---
# <a name="introduction-to-windows-service-applications"></a>Introduction aux applications de service Windows

Les services Microsoft Windows, anciennement « services NT », vous permettent de créer des applications exécutables longue durée qui s’exécutent au sein de leurs propres sessions Windows. Ces services peuvent être lancés automatiquement au démarrage de l’ordinateur, et peuvent être suspendus et redémarrés. Ils n’affichent aucune interface utilisateur. Les services sont donc parfaitement adaptés à une utilisation sur un serveur ou chaque fois que vous avez besoin de fonctionnalités longue durée qui n’interfèrent pas avec d’autres utilisateurs travaillant sur le même ordinateur. Vous pouvez également exécuter des services dans le contexte de sécurité d’un compte d’utilisateur spécifique (différent de l’utilisateur connecté ou du compte d’ordinateur par défaut). Pour plus d’informations sur les services et sessions Windows, consultez la documentation du kit SDK Windows.  
  
 Vous pouvez facilement créer des services en créant une application qui est installée comme service. Par exemple, supposons que vous souhaitiez monitorer les données d’un compteur de performances et réagir à des valeurs de seuil. Vous pouvez écrire une application de service Windows qui écoute les données du compteur de performances, déployer l’application, puis lancer la collecte et l’analyse des données.  
  
 Créez votre service en tant que projet Microsoft Visual Studio. Dans celui-ci, définissez du code qui contrôle les commandes pouvant être envoyées au service et les actions à effectuer quand ces commandes sont reçues. Parmi les commandes que vous pouvez envoyer à un service, citons le démarrage, la suspension, la reprise et l’arrêt. Vous pouvez également exécuter des commandes personnalisées.  
  
 Après avoir créé et généré l’application, vous pouvez l’installer en exécutant l’utilitaire de ligne de commande InstallUtil.exe et en passant le chemin au fichier exécutable du service. Vous pouvez ensuite utiliser le **Gestionnaire de contrôle des services** pour démarrer, arrêter, suspendre, reprendre et configurer votre service. Vous pouvez également accomplir la plupart de ces tâches dans le nœud **Services** de **l’Explorateur de serveurs** ou à l’aide de la classe <xref:System.ServiceProcess.ServiceController>.  
  
## <a name="service-applications-vs-other-visual-studio-applications"></a>Applications de service et autres applications Visual Studio  

 Le fonctionnement des applications de service diffère de celui d’autres types de projets à plusieurs égards :  
  
- Le fichier exécutable compilé créé par un projet d’application de service doit d’abord être installé sur le serveur pour que le projet puisse fonctionner de manière utile. Vous ne pouvez pas appuyer sur F5 ou F11 pour déboguer ou exécuter une application de service. Par ailleurs, vous ne pouvez ni exécuter immédiatement un service ni effectuer un pas à pas détaillé dans son code. Vous devez installer et démarrer votre service, puis attacher un débogueur au processus du service. Pour plus d’informations, consultez [Guide pratique pour déboguer les applications de service Windows](how-to-debug-windows-service-applications.md).  
  
- Contrairement à certains types de projets, vous devez créer des composants d’installation pour les applications de service. Les composants d’installation installent le service sur le serveur et l’inscrivent auprès de celui-ci. Ils créent également une entrée pour votre service dans le **Gestionnaire de contrôle des services** Windows. Pour plus d’informations, consultez [Guide pratique pour ajouter des programmes d’installation à votre application de service](how-to-add-installers-to-your-service-application.md).  
  
- La méthode `Main` de votre application de service doit émettre la commande Run pour les services contenus dans votre projet. La méthode `Run` charge les services dans le **Gestionnaire de contrôle des services** sur le serveur approprié. Si vous utilisez le modèle de projet **Services Windows**, cette méthode est automatiquement écrite pour vous. Notez que le chargement et le démarrage d’un service sont deux choses différentes. Pour plus d’informations, consultez « Durée de vie du service » ci-dessous.  
  
- Les applications de service Windows s’exécutent dans une station de fenêtre différente de la station interactive de l’utilisateur connecté. Une station de fenêtre est un objet sécurisé contenant un Presse-papiers, un ensemble d’atomes globaux et un groupe d’objets de bureau. Étant donné que la station du service Windows n’est pas une station interactive, les boîtes de dialogue déclenchées à partir d’une application de service Windows ne sont pas visibles et peuvent provoquer le blocage de votre programme. De la même façon, les messages d’erreur doivent être journalisés dans le journal des événements Windows au lieu d’être déclenchés dans l’interface utilisateur.  
  
     Les classes de service Windows prises en charge par le .NET Framework ne prennent pas en charge l’interaction avec des stations interactives, c’est-à-dire l’utilisateur connecté. Le .NET Framework n’inclut pas non plus les classes qui représentent des stations et des bureaux. Si votre service Windows doit interagir avec d’autres stations, vous devez accéder à l’API Windows non managée. Pour plus d’informations, consultez la documentation du SDK Windows.  
  
     Prenez soin de concevoir l’interaction du service Windows avec l’utilisateur ou d’autres stations pour faire face à divers scénarios, notamment l’absence d’un utilisateur connecté ou la présence d’un ensemble inattendu d’objets sur le Bureau d’un utilisateur. Dans certains cas, il peut être plus opportun d’écrire une application Windows qui s’exécute sous le contrôle de l’utilisateur.  
  
- Les applications de service Windows s’exécutent dans leur propre contexte de sécurité et sont démarrées avant que l’utilisateur ne se connecte à l’ordinateur Windows sur lequel elles sont installées. Réfléchissez bien au compte d’utilisateur sous lequel vous souhaitez que le service s’exécute. En effet, un compte système confère au service davantage de droits et de privilèges qu’un compte d’utilisateur.  
  
## <a name="service-lifetime"></a>Durée de vie d’un service  

 Un service passe par plusieurs états internes au cours de sa vie. Le service est d’abord installé sur le système sur lequel il doit s’exécuter. Ce processus exécute les programmes d’installation du projet de service et charge le service dans le **Gestionnaire de contrôle des services** de cet ordinateur. Le **Gestionnaire de contrôle des services** est l’utilitaire central fourni par Windows pour administrer les services.  
  
 Une fois le service chargé, il doit être démarré. Un service qui n’est pas démarré ne fonctionne pas. Vous pouvez démarrer un service à partir du **Gestionnaire de contrôle des services**, à partir de **l’Explorateur de serveurs** ou à partir du code en appelant la méthode <xref:System.ServiceProcess.ServiceController.Start%2A>. La méthode <xref:System.ServiceProcess.ServiceController.Start%2A> passe le traitement à la méthode <xref:System.ServiceProcess.ServiceBase.OnStart%2A> de l’application et traite le code que vous avez défini à cet emplacement.  
  
 Un service en cours d’exécution peut être dans cet état indéfiniment, jusqu’à son arrêt ou sa suspension ou jusqu’à l’arrêt de l’ordinateur. Un service peut être dans l’un des trois états de base suivants : <xref:System.ServiceProcess.ServiceControllerStatus.Running>, <xref:System.ServiceProcess.ServiceControllerStatus.Paused> ou <xref:System.ServiceProcess.ServiceControllerStatus.Stopped>. Le service peut également signaler l’état d’une commande en attente : <xref:System.ServiceProcess.ServiceControllerStatus.ContinuePending>, <xref:System.ServiceProcess.ServiceControllerStatus.PausePending>, <xref:System.ServiceProcess.ServiceControllerStatus.StartPending> ou <xref:System.ServiceProcess.ServiceControllerStatus.StopPending>. Ces états indiquent qu’une commande a été émise, par exemple pour suspendre un service en cours d’exécution, mais qu’elle n’a pas encore été exécutée. Vous pouvez interroger <xref:System.ServiceProcess.ServiceController.Status%2A> pour déterminer l’état d’un service, ou utiliser <xref:System.ServiceProcess.ServiceController.WaitForStatus%2A> pour effectuer une action quand l’un de ces états se produit.  
  
 Vous pouvez suspendre, arrêter ou reprendre un service à partir du **Gestionnaire de contrôle des services**, à partir de **l’Explorateur de serveurs** ou en appelant des méthodes dans le code. Chacune de ces actions peut appeler une procédure associée dans le service (<xref:System.ServiceProcess.ServiceBase.OnStop%2A>, <xref:System.ServiceProcess.ServiceBase.OnPause%2A> ou <xref:System.ServiceProcess.ServiceBase.OnContinue%2A>), où vous pouvez définir un traitement supplémentaire à effectuer quand le service change d’état.  
  
## <a name="types-of-services"></a>Types de services  

 Dans Visual Studio, vous pouvez créer deux types de services à l’aide du .NET Framework. Un service unique dans un processus se voit affecter le type <xref:System.ServiceProcess.ServiceType.Win32OwnProcess>. Un service qui partage un processus avec un autre service se voit affecter le type <xref:System.ServiceProcess.ServiceType.Win32ShareProcess>. Pour récupérer le type d’un service, interrogez la propriété <xref:System.ServiceProcess.ServiceController.ServiceType%2A>.  
  
 Il est possible que vous obteniez d’autres types de services si vous interrogez des services existants qui n’ont pas été créés dans Visual Studio. Pour plus d’informations sur ceux-ci, consultez <xref:System.ServiceProcess.ServiceType>.  
  
## <a name="services-and-the-servicecontroller-component"></a>Services et composant ServiceController  

 Le composant <xref:System.ServiceProcess.ServiceController> permet d’établir une connexion à un service installé et de manipuler son état. À l’aide d’un composant <xref:System.ServiceProcess.ServiceController>, vous pouvez démarrer et arrêter un service, suspendre et poursuivre son exécution, et envoyer des commandes personnalisées à un service. Toutefois, il est inutile de recourir à un composant <xref:System.ServiceProcess.ServiceController> quand vous créez une application de service. En fait, dans la plupart des cas, votre composant <xref:System.ServiceProcess.ServiceController> doit se trouver dans une application séparée de l’application de service Windows qui définit votre service.  
  
 Pour plus d’informations, consultez <xref:System.ServiceProcess.ServiceController>.  
  
## <a name="requirements"></a>Spécifications  
  
- Les services doivent être créés dans un projet d’application **Service Windows** ou un autre projet compatible .NET Framework qui crée un fichier .exe au moment de la génération et qui hérite de la classe <xref:System.ServiceProcess.ServiceBase>.  
  
- Les projets contenant des services Windows doivent avoir des composants d’installation pour le projet et ses services. Pour y parvenir facilement, utilisez la fenêtre **Propriétés**. Pour plus d’informations, consultez [Guide pratique pour ajouter des programmes d’installation à votre application de service](how-to-add-installers-to-your-service-application.md).  
  
## <a name="see-also"></a>Voir aussi

- [Applications de service Windows](index.md)
- [Architecture de programmation d'une application de service](service-application-programming-architecture.md)
- [Procédure : créer des services Windows](how-to-create-windows-services.md)
- [Procédure : Installer et désinstaller des services](how-to-install-and-uninstall-services.md)
- [Procédure : démarrer des services](how-to-start-services.md)
- [Procédure : déboguer les applications de service Windows](how-to-debug-windows-service-applications.md)
- [Procédure pas à pas : création d’une application de service Windows dans le Concepteur de composants](walkthrough-creating-a-windows-service-application-in-the-component-designer.md)
- [Procédure : ajouter des programmes d’installation à votre application de service](how-to-add-installers-to-your-service-application.md)

---
title: 'Comment : démarrer des services'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, starting
- services, starting
ms.assetid: 9ea77955-2d96-4c3d-913c-14db7604cdad
author: ghogen
ms.openlocfilehash: 75fd3aba88bdffbe536ad5dab14996913d0a9d22
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053568"
---
# <a name="how-to-start-services"></a>Comment : démarrer des services

Une fois qu’un service est installé, il doit être démarré. Le démarrage appelle la méthode <xref:System.ServiceProcess.ServiceBase.OnStart%2A> sur la classe de service. En règle générale, la méthode <xref:System.ServiceProcess.ServiceBase.OnStart%2A> définit le travail utile effectué par le service. Une fois un service démarré, il reste actif jusqu’à ce qu’il soit suspendu ou arrêté.

Vous pouvez configurer un service pour qu’il démarre automatiquement ou manuellement. Un service à démarrage automatique démarre quand l’ordinateur sur lequel il est installé est mis en marche pour la première fois ou redémarré. Un service à démarrage manuel doit être démarré par un utilisateur.

> [!NOTE]
> Par défaut, les services créés avec Visual Studio sont définis pour démarrer manuellement.

Vous pouvez démarrer manuellement un service de plusieurs façons : à partir de **l’Explorateur de serveurs**, à partir du **Gestionnaire de contrôle des services** ou à partir du code à l’aide d’un composant appelé <xref:System.ServiceProcess.ServiceController>.

Pour indiquer si un service doit être démarré manuellement ou automatiquement, définissez la propriété <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> sur la classe <xref:System.ServiceProcess.ServiceInstaller>.

### <a name="to-specify-how-a-service-should-start"></a>Pour spécifier comment un service doit démarrer

1. Après avoir créé votre service, ajoutez les programmes d’installation nécessaires à celui-ci. Pour plus d’informations, consultez [Guide pratique pour ajouter des programmes d’installation à votre application de service](how-to-add-installers-to-your-service-application.md).

2. Dans le concepteur, cliquez sur le programme d’installation du service que vous utilisez.

3. Dans la fenêtre **Propriétés**, définissez la propriété <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> avec l’une des valeurs suivantes :

    |Pour que votre service s’installe|Définissez cette valeur|
    |----------------------------------|--------------------|
    |Quand l’ordinateur redémarre|**Automatique**|
    |Quand une action explicite de l’utilisateur démarre le service|**Manuel**|

    > [!TIP]
    > Pour que votre service ne démarre pas, définissez la propriété <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> avec la valeur **Disabled**. Procédez de la sorte si vous prévoyez de redémarrer un serveur plusieurs fois. Le fait de ne pas démarrer les services habituels vous fera gagner du temps.

    > [!NOTE]
    > Ces propriétés, ainsi que d’autres, peuvent être modifiées après l’installation du service.

    Vous pouvez démarrer un service dont le processus <xref:System.ServiceProcess.ServiceInstaller.StartType%2A>a la valeur **Manual** de plusieurs façons : à partir de **l’Explorateur de serveurs**, à partir du **Gestionnaire de contrôle des services Windows** ou à partir du code. Il est important de noter que ces méthodes ne démarrent pas toutes le service dans le contexte du **Gestionnaire de contrôle des services**. En effet, **l’Explorateur de serveurs** et les méthodes de démarrage du service par programmation manipulent le contrôleur.

### <a name="to-manually-start-a-service-from-server-explorer"></a>Pour démarrer manuellement un service à partir de l’Explorateur de serveurs

1. Dans **l’Explorateur de serveurs**, ajoutez le serveur désiré s’il n’est pas déjà répertorié. Pour plus d’informations, consultez Guide pratique pour accéder à l’Explorateur de serveurs/bases de données et l’initialiser.

2. Développez le nœud **Services**, puis recherchez le service à démarrer.

3. Cliquez avec le bouton droit sur le nom du service, puis cliquez sur **Démarrer**.

### <a name="to-manually-start-a-service-from-services-control-manager"></a>Pour démarrer manuellement un service à partir du Gestionnaire de contrôle des services

1. Effectuez l’une des procédures suivantes pour ouvrir le **Gestionnaire de contrôle des services** :

    - Dans Windows XP et Windows 2000 Professionnel, cliquez avec le bouton droit sur **Poste de travail** sur le Bureau, puis cliquez sur **Gérer**. Dans la boîte de dialogue qui s’affiche, développez le nœud **Services et applications**.

      \- ou -

    - Dans Windows Server 2003 et Windows 2000 Server, cliquez sur **Démarrer**, pointez sur **Programmes**, puis cliquez sur **Outils d’administration** et sur **Services**.

      > [!NOTE]
      > Dans Windows NT version 4.0, vous pouvez ouvrir cette boîte de dialogue à partir du **Panneau de configuration**.

    Votre service doit maintenant être répertorié dans la section **Services** de la fenêtre.

2. Sélectionnez votre service dans la liste, cliquez dessus avec le bouton droit, puis cliquez sur **Démarrer**.

### <a name="to-manually-start-a-service-from-code"></a>Pour démarrer manuellement un service à partir du code

1. Créez une instance de la classe <xref:System.ServiceProcess.ServiceController> et configurez-la pour interagir avec le service à administrer.

2. Appelez la méthode <xref:System.ServiceProcess.ServiceController.Start%2A> pour démarrer le service.

## <a name="see-also"></a>Voir aussi

- [Présentation des applications de service Windows](introduction-to-windows-service-applications.md)
- [Guide pratique pour créer des services Windows](how-to-create-windows-services.md)
- [Comment : ajouter des programmes d'installation à votre application de service](how-to-add-installers-to-your-service-application.md)

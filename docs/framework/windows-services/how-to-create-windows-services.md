---
title: 'Procédure : créer des services Windows'
description: Utilisez le modèle de projet de service Windows pour créer un service. Définissez la propriété ServiceName, créez des programmes d’installation et remplacez les méthodes OnStart et OnStop.
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, creating
- templates, Windows Service
ms.assetid: 0f5e2cbb-d95d-477c-b2b5-4b990e6b86ff
ms.openlocfilehash: 35d78acd4fae7bf98a2b3f4ce6ac8a32393c35d4
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91608593"
---
# <a name="how-to-create-windows-services"></a>Procédure : créer des services Windows
Quand vous créez un service, vous pouvez utiliser un modèle de projet Visual Studio appelé **Service Windows**. Ce modèle accomplit automatiquement pour vous une grande part du travail : il référence les classes et les espaces de noms appropriés, définit l'héritage à partir de la classe de base des services et substitue les méthodes que vous êtes le plus susceptible de vouloir substituer.  
  
> [!WARNING]
> Le modèle de projet Services Windows n'est pas disponible dans l'édition Express de Visual Studio.  
  
 Pour créer un service fonctionnel, vous devez, au minimum :  
  
- définir la propriété <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> ;  
  
- ajouter les programmes d'installation nécessaires à votre application de service ;  
  
- substituer et spécifier le code des méthodes <xref:System.ServiceProcess.ServiceBase.OnStart%2A> et <xref:System.ServiceProcess.ServiceBase.OnStop%2A> pour personnaliser le comportement de votre service.  
  
### <a name="to-create-a-windows-service-application"></a>Pour créer une application de service Windows  
  
1. Créez un projet **Service Windows**.  
  
    > [!NOTE]
    > Pour savoir comment écrire un service sans avoir recours au modèle, consultez [Guide pratique pour écrire des services par programmation](how-to-write-services-programmatically.md).  
  
2. Dans la fenêtre **Propriétés**, définissez la propriété <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> pour votre service.  
  
     ![Définissez la propriété ServiceName.](./media/windowsservice-servicename.PNG "WindowsService_ServiceName")  
  
    > [!NOTE]
    > La valeur de la propriété <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> doit toujours correspondre au nom enregistré dans les classes Installer. Si vous modifiez cette propriété, vous devez également mettre à jour la propriété <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> des classes Installer.  
  
3. Définissez le fonctionnement de votre service à l'aide des propriétés suivantes.  
  
    |Property|Paramètre|  
    |--------------|-------------|  
    |<xref:System.ServiceProcess.ServiceBase.CanStop%2A>|`True` pour indiquer que le service acceptera des demandes d'arrêt ; `false` pour empêcher tout arrêt du service.|  
    |<xref:System.ServiceProcess.ServiceBase.CanShutdown%2A>|`True` pour indiquer que le service doit recevoir une notification en cas d'arrêt de l'ordinateur sur lequel il s'exécute, ce qui lui permet d'appeler la procédure <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A>.|  
    |<xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A>|`True` pour indiquer que le service acceptera les demandes de suspension ou de redémarrage ; `false` pour empêcher une suspension et un redémarrage du service.|  
    |<xref:System.ServiceProcess.ServiceBase.CanHandlePowerEvent%2A>|`True` pour indiquer que le service peut gérer la notification des changements apportés à l’état d’alimentation de l’ordinateur ; `false` pour empêcher le service d’être notifié de ces changements.|  
    |<xref:System.ServiceProcess.ServiceBase.AutoLog%2A>|`True` pour écrire des entrées à caractère informatif dans le journal des événements de l'application lorsque votre service effectue une action ; `false` pour désactiver cette fonctionnalité. Pour plus d’informations, consultez [Guide pratique pour enregistrer des informations relatives aux services](how-to-log-information-about-services.md). **Remarque :** Par défaut, <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> a la valeur `true`.|  
  
    > [!NOTE]
    > Quand <xref:System.ServiceProcess.ServiceBase.CanStop%2A> ou <xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A> a la valeur `false`, le **Gestionnaire de contrôle des services** désactive les options de menu correspondantes pour arrêter, suspendre ou poursuivre le service.  
  
4. Accédez à l'éditeur de code et indiquez le traitement souhaité pour les procédures <xref:System.ServiceProcess.ServiceBase.OnStart%2A> et <xref:System.ServiceProcess.ServiceBase.OnStop%2A>.  
  
5. Substituez toutes les autres méthodes pour lesquelles vous voulez définir des fonctionnalités.  
  
6. Ajoutez les programmes d'installation nécessaires à votre application de service. Pour plus d’informations, consultez [Guide pratique pour ajouter des programmes d’installation à votre application de service](how-to-add-installers-to-your-service-application.md).  
  
7. Générez votre projet en sélectionnant **Générer la solution** dans le menu **Générer**.  
  
    > [!NOTE]
    > N'appuyez pas sur la touche F5 pour exécuter votre projet : vous ne pouvez pas exécuter un projet de service de cette manière.  
  
8. Installez le service. Pour plus d'informations, consultez [How to: Install and Uninstall Services](how-to-install-and-uninstall-services.md).  
  
## <a name="see-also"></a>Voir aussi

- [Introduction aux applications de service Windows](introduction-to-windows-service-applications.md)
- [Procédure : écrire les services par programmation](how-to-write-services-programmatically.md)
- [Procédure : ajouter des programmes d’installation à votre application de service](how-to-add-installers-to-your-service-application.md)
- [Procédure : enregistrer des informations relatives aux services](how-to-log-information-about-services.md)
- [Procédure : démarrer des services](how-to-start-services.md)
- [Procédure : spécifier le contexte de sécurité des services](how-to-specify-the-security-context-for-services.md)
- [Procédure : Installer et désinstaller des services](how-to-install-and-uninstall-services.md)
- [Procédure pas à pas : création d’une application de service Windows dans le Concepteur de composants](walkthrough-creating-a-windows-service-application-in-the-component-designer.md)

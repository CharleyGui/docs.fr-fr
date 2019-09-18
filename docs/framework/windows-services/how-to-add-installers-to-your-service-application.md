---
title: 'Procédure : ajouter des programmes d’installation à votre application de service'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, deploying
- installation components, adding to services
- installers, adding to services
- Windows Service applications, adding installers
- services, adding installers
- ServiceInstaller class, adding installers to services
- ServiceProcessInstaller class, adding installers to services
ms.assetid: 8b698e9a-b88e-4f44-ae45-e0c5ea0ae5a8
author: ghogen
ms.openlocfilehash: 99e2376c50f0b47cc21002b2926818707188805e
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053650"
---
# <a name="how-to-add-installers-to-your-service-application"></a>Procédure : ajouter des programmes d’installation à votre application de service
Visual Studio est fourni avec des composants d’installation qui peuvent installer des ressources associées à vos applications de service. Les composants d’installation inscrivent un service auprès du système sur lequel il est installé et informent le Gestionnaire de contrôle des services de l’existence du service. Quand vous travaillez avec une application de service, vous pouvez sélectionner un lien dans la fenêtre Propriétés pour ajouter automatiquement les programmes d’installation appropriés à votre projet.  
  
> [!NOTE]
> Les valeurs des propriétés de votre service sont copiées de la classe de service dans la classe du programme d’installation. Si vous modifiez les valeurs des propriétés sur la classe de service, vos modifications ne sont pas automatiquement répercutées dans le programme d’installation.  
  
 Quand vous ajoutez un programme d’installation à votre projet, une nouvelle classe (nommée par défaut `ProjectInstaller`) est créée dans le projet, et des instances des composants d’installation appropriés sont créées dans celui-ci. Cette classe sert de point central à tous les composants d’installation dont votre projet a besoin. Par exemple, le fait d’ajouter un deuxième service à votre application et de cliquer sur le lien Ajouter le programme d’installation n’entraîne pas l’ajout d’une deuxième classe dans le programme d’installation. Au lieu de cela, le composant d’installation nécessaire pour le deuxième service est ajouté à la classe existante.  
  
 Les programmes d’installation ne nécessitent aucun codage spécial pour que vos services s’installent correctement. Toutefois, vous devrez parfois modifier le contenu des programmes d’installation pour ajouter des fonctionnalités spéciales au processus d’installation.  
  
> [!NOTE]
> Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-add-installers-to-your-service-application"></a>Pour ajouter des programmes d’installation à votre application de service  
  
1. Dans **l’Explorateur de solutions**, accédez au **mode Création** du service auquel vous souhaitez ajouter un composant d’installation.  
  
2. Cliquez sur l’arrière-plan du concepteur pour sélectionner le service lui-même et non son contenu.  
  
3. Quand le concepteur a le focus, cliquez dessus avec le bouton droit, puis cliquez sur **Ajouter le programme d’installation**.  
  
     Une nouvelle classe, `ProjectInstaller`, et deux composants d’installation, <xref:System.ServiceProcess.ServiceProcessInstaller> et <xref:System.ServiceProcess.ServiceInstaller>, sont ajoutés à votre projet, et les valeurs des propriétés du service sont copiées dans les composants.  
  
4. Cliquez sur le composant <xref:System.ServiceProcess.ServiceInstaller> et vérifiez que la valeur de la propriété <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> est identique à celle de la propriété <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> sur le service.  
  
5. Pour déterminer le mode de démarrage de votre service, cliquez sur le composant <xref:System.ServiceProcess.ServiceInstaller> et définissez la propriété <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> avec la valeur appropriée.  
  
    |Valeur|Résultat|  
    |-----------|------------|  
    |<xref:System.ServiceProcess.ServiceStartMode.Manual>|Vous devez démarrer manuellement le service après l’installation. Pour plus d’informations, consultez [Guide pratique pour démarrer des services](how-to-start-services.md).|  
    |<xref:System.ServiceProcess.ServiceStartMode.Automatic>|Le service démarre automatiquement à chaque redémarrage de l’ordinateur.|  
    |<xref:System.ServiceProcess.ServiceStartMode.Disabled>|Le service ne peut pas être démarré.|  
  
6. Pour déterminer le contexte de sécurité dans lequel votre service va s’exécuter, cliquez sur le composant <xref:System.ServiceProcess.ServiceProcessInstaller> et définissez les valeurs de propriété appropriées. Pour plus d'informations, voir [Procédure : spécifier le contexte de sécurité des services](how-to-specify-the-security-context-for-services.md).  
  
7. Substituez les méthodes qui doivent faire l’objet d’un traitement personnalisé.  
  
8. Effectuez les étapes 1 à 7 pour chaque service supplémentaire dans votre projet.  
  
    > [!NOTE]
    > Pour chaque service supplémentaire dans votre projet, ajoutez un composant <xref:System.ServiceProcess.ServiceInstaller> à la classe `ProjectInstaller` du projet. Le composant <xref:System.ServiceProcess.ServiceProcessInstaller> ajouté à la troisième étape fonctionne avec tous les programmes d’installation de service dans le projet.  
  
## <a name="see-also"></a>Voir aussi

- [Introduction aux applications de service Windows](introduction-to-windows-service-applications.md)
- [Guide pratique pour Installer et désinstaller des services](how-to-install-and-uninstall-services.md)
- [Guide pratique : démarrer des services](how-to-start-services.md)
- [Guide pratique pour spécifier le contexte de sécurité des services](how-to-specify-the-security-context-for-services.md)

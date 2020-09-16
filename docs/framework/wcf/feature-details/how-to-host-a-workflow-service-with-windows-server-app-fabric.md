---
title: 'Procédure : héberger un service de workflow avec Windows Server App Fabric'
ms.date: 03/30/2017
ms.assetid: 83b62cce-5fc2-4c6d-b27c-5742ba3bac73
ms.openlocfilehash: 2cf77753a0540e75ae6778065f7fa006729f8d6a
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555983"
---
# <a name="how-to-host-a-workflow-service-with-windows-server-app-fabric"></a>Procédure : héberger un service de workflow avec Windows Server App Fabric

L'hébergement de services de workflow dans App Fabric est similaire à l'hébergement sous IIS/WAS. La seule différence réside dans les outils que propose App Fabric pour déployer, surveiller et gérer les services de workflow. Cette rubrique utilise le service de workflow créé dans la [création d’un service de flux de travail de longue durée](creating-a-long-running-workflow-service.md). Celle-ci vous guide dans la création d'un service de workflow. La présente rubrique explique comment héberger le service de workflow à l'aide d'App Fabric. Pour plus d’informations sur Windows Server App fabric, consultez [la documentation de Windows Server App Fabric](/previous-versions/appfabric/ff384253(v=azure.10)). Avant de réaliser les étapes suivantes, vérifiez que Windows Server App Fabric est installé.  Pour ce faire, ouvrez le Internet Information Services (inetmgr.exe), cliquez sur le nom de votre serveur dans la vue **connexions** , cliquez sur sites, puis cliquez sur **site Web par défaut**. Dans la partie droite de l’écran, vous devriez voir une section nommée **app Fabric**. Si cette section ne s'affiche pas (en haut du volet droit), AppFabric n'est pas installé. Pour plus d’informations sur l’installation de Windows Server App fabric, consultez [installation de Windows Server App Fabric](/previous-versions/appfabric/ee790960(v=azure.10)).  
  
### <a name="creating-a-simple-workflow-service"></a>Création d'un service de workflow simple  
  
1. Ouvrez Visual Studio 2012 et chargez la solution OrderProcessing que vous avez créée dans la rubrique [création d’un service de flux de travail de longue durée](creating-a-long-running-workflow-service.md) .  
  
2. Cliquez avec le bouton droit sur le projet **OrderService** et sélectionnez **Propriétés** , puis sélectionnez l’onglet **Web** .  
  
3. Dans la section **action de démarrage** de la page de propriétés, sélectionnez **page spécifique** et tapez Service1. xamlx dans la zone d’édition.  
  
4. Dans la section **serveurs** de la page de propriétés, sélectionnez **utiliser le serveur Web IIS local** et tapez l’URL suivante : `http://localhost/OrderService` .  
  
5. Cliquez sur le bouton **créer un répertoire virtuel** . Cette opération crée un répertoire virtuel et configure le projet de sorte que les fichiers nécessaires soient copiés dans ce répertoire virtuel lorsque le projet est généré.  Vous avez toutefois la possibilité de copier manuellement les fichiers .xamlx, web.config et les DLL requises dans le répertoire virtuel.  
  
### <a name="configuring-a-workflow-service-hosted-in-windows-server-app-fabric"></a>Configuration d'un service de workflow hébergé dans Windows Server App Fabric  
  
1. Ouvrez le Gestionnaire des services IIS (inetmgr.exe).  
  
2. Accédez au répertoire virtuel OrderService dans le volet **connexions** .  
  
3. Cliquez avec le bouton droit sur OrderService, puis sélectionnez **gérer les services WCF et WF**, **configurer...**. La boîte **de dialogue Configurer WCF et WF pour l’application** s’affiche.  
  
4. Sélectionnez l’onglet **général** pour afficher des informations générales sur l’application, comme illustré dans la capture d’écran suivante.  
  
     ![Onglet Général de la boîte de dialogue de configuration AppFabric](media/appfabricconfiguration-general.gif "AppFabricConfiguration-général")  
  
5. Sélectionnez l’onglet **analyse** . Cela montre différents paramètres de surveillance, comme indiqué dans la capture d’écran suivante.  
  
     ![Onglet Analyse de la boîte de dialogue de configuration AppFabric](media/appfabricconfiguration-monitoring.gif "AppFabricConfiguration-surveillance")  
  
     Pour plus d’informations sur la configuration de l’analyse du service de workflow dans App fabric, consultez Configuration de l' [analyse avec application Fabric](/previous-versions/appfabric/ee677384(v=azure.10)).  
  
6. Sélectionnez l’onglet **persistance du flux de travail** . Cela vous permet de configurer votre application pour utiliser le fournisseur de persistance par défaut d’App Fabric comme indiqué dans la capture d’écran suivante.  
  
     ![Configuration de l’infrastructure d’application &#45; la persistance](media/appfabricconfiguration-persistence.gif "AppFabricConfiguration-persistance")  
  
     Pour plus d’informations sur la configuration de la persistance des workflows dans Windows Server App fabric, consultez [configuration de la persistance des flux de travail dans l’application Fabric](/previous-versions/appfabric/ee677353(v=azure.10)).  
  
7. Sélectionnez l’onglet gestion de l' **hôte de flux de travail** . Cela vous permet de spécifier le moment où les instances de service de workflow inactives doivent être déchargées et rendues persistantes, comme indiqué dans la capture d’écran suivante.  
  
     ![Configuration App Fabric gestion des hôtes de flux de travail](media/appfabricconfiguration-management.gif "AppFabricConfiguration-gestion")  
  
     Pour plus d’informations sur la configuration de la gestion [des hôtes de workflow, consultez Configuration de la gestion des hôtes de workflow dans App Fabric](/previous-versions/appfabric/ff383424(v=azure.10)).  
  
8. Sélectionnez l’onglet **démarrage automatique** . Cela vous permet de spécifier les paramètres de démarrage automatique pour les services de flux de travail dans l’application, comme illustré dans la capture d’écran suivante.  
  
     ![Capture d’écran montrant la configuration du démarrage automatique de l'&#45;App fabric.](./media/how-to-host-a-workflow-service-with-windows-server-app-fabric/app-fabric-auto-start-configuration.gif)  
  
     Pour plus d’informations sur la configuration du démarrage automatique, consultez [configuration du démarrage automatique avec App Fabric](/previous-versions/appfabric/ee677261(v=azure.10)).  
  
9. Sélectionnez l’onglet **limitation** . Cela vous permet de configurer des paramètres de limitation pour le service de workflow, comme illustré dans la capture d’écran suivante.  
  
     ![Capture d’écran montrant la configuration de la limitation d’application fabric.](./media/how-to-host-a-workflow-service-with-windows-server-app-fabric/app-fabric-throttling-configuration.gif)  
  
     Pour plus d’informations sur la configuration de la limitation, consultez [configuration de la limitation avec App Fabric](/previous-versions/appfabric/ee677261(v=azure.10)).  
  
10. Sélectionnez l’onglet **sécurité** . Cela vous permet de configurer les paramètres de sécurité de l’application, comme illustré dans la capture d’écran suivante.  
  
     ![Configuration de la sécurité AppFabric](media/appfabricconfiguration-security.gif "AppFabricConfiguration-sécurité")  
  
     Pour plus d’informations sur la configuration de la sécurité avec Windows Server App fabric, consultez [configuration de la sécurité avec App Fabric](/previous-versions/appfabric/ee677278(v=azure.10)).  
  
### <a name="using-windows-server-app-fabric"></a>Utilisation de Windows Server App Fabric  
  
1. Générez la solution pour copier les fichiers nécessaires dans le répertoire virtuel.  
  
2. Cliquez avec le bouton droit sur le projet OrderClient et sélectionnez **Déboguer**, **Démarrer une nouvelle instance** pour lancer l’application cliente.  
  
3. Le client s’exécute et Visual Studio affiche une boîte de dialogue **attacher un avertissement de sécurité** , puis clique sur le bouton **ne pas attacher** . Cela indique à Visual Studio de ne pas attacher le débogueur au processus IIS pour le débogage.  
  
4. L'application cliente appelle immédiatement le service de workflow, puis attend. Le service de workflow devient inactif, puis est rendu persistant. Vous pouvez le vérifier en démarrant Internet Information Services (inetmgr.exe), en accédant à OrderService dans le volet Connexions, puis en le sélectionnant. Ensuite, cliquez sur l'icône Tableau de bord d'AppFabric dans le volet droit. Sous Instances WF persistantes, vous verrez qu’il existe une instance de service de workflow persistante, comme illustré dans la capture d’écran suivante.  
  
     ![Capture d’écran montrant le tableau de bord App fabric.](./media/how-to-host-a-workflow-service-with-windows-server-app-fabric/app-fabric-dashboard.gif)  
  
     L' **historique de l’instance WF** répertorie des informations sur le service de workflow, telles que le nombre d’activations du service de workflow, le nombre de saisies semi-automatiques de l’instance du service de workflow et le nombre d’instances de workflow avec échecs. Sous instances actives ou inactives, un lien s’affiche, cliquez sur le lien pour afficher plus d’informations sur les instances de workflow inactives, comme indiqué dans la capture d’écran suivante.  
  
     ![Capture d’écran qui affiche les détails de l’instance de flux de travail persistante.](./media/how-to-host-a-workflow-service-with-windows-server-app-fabric/persisted-workflow-instance-detail.gif)  
  
     Pour plus d’informations sur les fonctionnalités de Windows Server App fabric et la façon de les utiliser, consultez [fonctionnalités d’hébergement de Windows Server App Fabric](/previous-versions/appfabric/ee677189(v=azure.10))  
  
## <a name="see-also"></a>Voir aussi

- [Création d'un service de workflow de longue durée](creating-a-long-running-workflow-service.md)
- [Fonctionnalités d’hébergement de Windows Server AppFabric](/previous-versions/appfabric/ee677189(v=azure.10))
- [Installation de Windows Server App Fabric](/previous-versions/appfabric/ee790960(v=azure.10))
- [Documentation Windows Server App Fabric](/previous-versions/appfabric/ff384253(v=azure.10))

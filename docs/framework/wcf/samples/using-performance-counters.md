---
title: Using Performance Counters
ms.date: 03/30/2017
ms.assetid: 00a787af-1876-473c-a48d-f52b51e28a3f
ms.openlocfilehash: 7ffd9f5de5efb4be22968958246839e804daf23d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143575"
---
# <a name="using-performance-counters"></a>Using Performance Counters
Cet exemple montre comment accéder aux compteurs de performances de la Windows Communication Foundation (WCF) et comment créer des compteurs de performances définis par l’utilisateur. Cet échantillon est basé sur le [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
> [!NOTE]
> La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
 Dans cet exemple, le client appelle les quatre méthodes du service `ICalculator`. Le client continue jusqu'à ce qu'il soit interrompu par l'utilisateur. Le service reste inchangé.  
  
 Les compteurs de performance sont activés dans la section de diagnostic du fichier Web.config pour le service, comme le montre l'exemple de configuration suivant.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <diagnostics performanceCounters="All" />
  </system.serviceModel>  
</configuration>  
```  
  
 Cette tâche peut également être effectuée à l’aide de [l’outil d’éditeur de configuration (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).  
  
 Lorsque les compteurs de performance sont activés, toute la suite de compteurs de performances WCF est activée pour le service. Le .NET Framework assure automatiquement la maintenance des données de performance à trois niveaux : `ServiceModelService`, `ServiceModelEndpoint` et `ServiceModelOperation`. Chacun de ces niveaux comporte des compteurs de performance tels que « Appels », « Appels par seconde », et « Appels de sécurité non autorisés ».  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les échantillons de la Fondation De communication Windows.](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)  
  
2. Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Pour exécuter l’échantillon dans une configuration mono-ou cross-computer, suivez les instructions dans [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
### <a name="to-view-performance-data"></a>Pour afficher les données de performances  
  
1. Démarrer l’outil de moniteur de performance `perfmon` en cliquant sur **Démarrer,** **Exécuter...**, entrez et cliquez **sur OK,** ou à partir du panneau de contrôle, sélectionnez **des outils administratifs** et **des performances**en double clic.  
  
    > [!NOTE]
    > Vous ne pouvez pas ajouter de compteurs tant que l'exemple de code est en cours d'exécution.  
  
2. Supprimez les compteurs de performance répertoriés en les sélectionnant et en appuyant sur la touche Suppr.  
  
3. Ajoutez des compteurs WCF en cliquant à droite sur le volet graphique et en sélectionnant **add Counters**. Dans la boîte de dialogue **Add Counters,** sélectionnez **ServiceModelOperation 3.0.0.0, ServiceModelEndpoint 3.0.0.0, ou ServiceModelService 3.0.0.0** dans la boîte de liste de chute de l’objet Performance. Sélectionnez les compteurs que vous souhaitez afficher dans la liste.  
  
    > [!NOTE]
    > Il n’y a pas de compteurs de performance WCF pour un service s’il n’y a pas de services WCF en cours d’exécution sur l’ordinateur.  
  
### <a name="to-use-the-configuration-editor-to-enable-counters"></a>Pour utiliser l'Éditeur de configuration afin d'activer des compteurs  
  
1. Ouvrez une instance de SvcConfigEditor.exe.  
  
2. Sur le menu Du fichier, cliquez sur **Open** puis cliquez sur **le fichier Config...**.  
  
3. Naviguez jusqu'au dossier de service de l'exemple d'application et ouvrez le fichier Web.config.  
  
4. Cliquez sur **Diagnostics** sur l’arbre Configuration.  
  
5. **Basculez le compteur de performance** dans la fenêtre **Diagnostics** pour montrer 'All'.  
  
6. Enregistrez le fichier de configuration et quittez l'éditeur.  
  
> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, rendez-vous sur [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) Samples pour .NET Framework 4 pour](https://www.microsoft.com/download/details.aspx?id=21459) télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] des échantillons. Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\PerfCounters`  
  
## <a name="see-also"></a>Voir aussi

- [Exemples d'analyse AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))

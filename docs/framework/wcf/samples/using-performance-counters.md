---
title: Using Performance Counters
ms.date: 03/30/2017
ms.assetid: 00a787af-1876-473c-a48d-f52b51e28a3f
ms.openlocfilehash: 0b63cdc145ff8806c26b255500bcb2a132e9ef9f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596498"
---
# <a name="using-performance-counters"></a>Using Performance Counters
Cet exemple montre comment accéder aux compteurs de performance Windows Communication Foundation (WCF) et comment créer des compteurs de performances définis par l’utilisateur. Cet exemple est basé sur le [prise en main](getting-started-sample.md).  
  
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
  
 Cette tâche peut également être effectuée à l’aide de l' [outil Éditeur de configuration (SvcConfigEditor. exe)](../configuration-editor-tool-svcconfigeditor-exe.md).  
  
 Lorsque les compteurs de performance sont activés, la suite entière des compteurs de performance WCF est activée pour le service. Le .NET Framework assure automatiquement la maintenance des données de performance à trois niveaux : `ServiceModelService`, `ServiceModelEndpoint` et `ServiceModelOperation`. Chacun de ces niveaux comporte des compteurs de performance tels que « Appels », « Appels par seconde », et « Appels de sécurité non autorisés ».  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](building-the-samples.md).  
  
3. Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](running-the-samples.md).  
  
### <a name="to-view-performance-data"></a>Pour afficher les données de performances  
  
1. Démarrez l’outil Analyseur de performances en cliquant sur **Démarrer**, **exécuter...**, entrez `perfmon` et cliquez sur **OK,** ou dans le panneau de configuration, sélectionnez **Outils d’administration** et double-cliquez sur **performances**.  
  
    > [!NOTE]
    > Vous ne pouvez pas ajouter de compteurs tant que l'exemple de code est en cours d'exécution.  
  
2. Supprimez les compteurs de performance répertoriés en les sélectionnant et en appuyant sur la touche Suppr.  
  
3. Pour ajouter des compteurs WCF, cliquez avec le bouton droit sur le volet graphique et sélectionnez **Ajouter des compteurs**. Dans la boîte de dialogue **Ajouter des compteurs** , sélectionnez **ServiceModelOperation 3.0.0.0, ServiceModelEndpoint 3.0.0.0 ou ServiceModelService 3.0.0.0** dans la zone de liste déroulante objet de performance. Sélectionnez les compteurs que vous souhaitez afficher dans la liste.  
  
    > [!NOTE]
    > Il n’y a aucun compteur de performance WCF pour un service s’il n’y a aucun service WCF en cours d’exécution sur l’ordinateur.  
  
### <a name="to-use-the-configuration-editor-to-enable-counters"></a>Pour utiliser l'Éditeur de configuration afin d'activer des compteurs  
  
1. Ouvrez une instance de SvcConfigEditor.exe.  
  
2. Dans le menu fichier, cliquez sur **ouvrir** , puis sur **fichier de configuration...**.  
  
3. Naviguez jusqu'au dossier de service de l'exemple d'application et ouvrez le fichier Web.config.  
  
4. Cliquez sur **Diagnostics** dans l’arborescence de configuration.  
  
5. Activez/désactivez le **compteur de performances** dans la fenêtre **Diagnostics** pour afficher « tout ».  
  
6. Enregistrez le fichier de configuration et quittez l'éditeur.  
  
> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\PerfCounters`  
  
## <a name="see-also"></a>Voir aussi

- [Exemples d'analyse AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))

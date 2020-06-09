---
title: ETW Tracing
ms.date: 03/30/2017
ms.assetid: ac99a063-e2d2-40cc-b659-d23c2f783f92
ms.openlocfilehash: 0bdbf6699a0cfa3dce58abda4c989fb25d764459
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600556"
---
# <a name="etw-tracing"></a>ETW Tracing
Cet exemple montre comment implémenter le suivi de bout en bout (E2E) à l'aide du suivi d'événements pour Windows (ETW, Event Tracing for Windows) et du `ETWTraceListener` fourni dans cet exemple. L’exemple est basé sur le [prise en main](getting-started-sample.md) et comprend le suivi ETW.  
  
> [!NOTE]
> La procédure d'installation ainsi que les instructions de génération correspondant à cet exemple figurent en fin de rubrique.  
  
 Cet exemple suppose que vous êtes familiarisé avec [le suivi et la journalisation des messages](tracing-and-message-logging.md).  
  
 Chaque source de suivi du modèle de suivi <xref:System.Diagnostics> peut disposer de plusieurs écouteurs de suivi qui déterminent où et comment les données sont suivies. Le type de ces écouteurs définit le format auquel les données de suivi sont enregistrées. L'exemple de code suivant indique comment ajouter un écouteur à la configuration.  
  
```xml  
<system.diagnostics>  
    <sources>  
        <source name="System.ServiceModel"
             switchValue="Verbose,ActivityTracing"  
             propagateActivity="true">  
            <listeners>  
                <add type=  
                   "System.Diagnostics.DefaultTraceListener"  
                   name="Default">  
                   <filter type="" />  
                </add>  
                <add name="ETW">  
                    <filter type="" />  
                </add>  
            </listeners>  
        </source>  
    </sources>  
    <sharedListeners>  
        <add type=  
            "Microsoft.ServiceModel.Samples.EtwTraceListener, ETWTraceListener"  
            name="ETW" traceOutputOptions="Timestamp">  
            <filter type="" />  
       </add>  
    </sharedListeners>  
</system.diagnostics>  
```  
  
 Avant d'utiliser cet écouteur, une session de suivi ETW doit être démarrée. Pour ce faire, Logman.exe ou Tracelog.exe peut être utilisé. Cet exemple contient un fichier SetupETW.bat vous permettant de configurer une session de suivi ETW ainsi qu'un fichier CleanupETW.bat vous permettant de fermer la session et de compléter le fichier journal.  
  
> [!NOTE]
> La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique. Pour plus d’informations sur ces outils, consultez.<https://go.microsoft.com/fwlink/?LinkId=56580>  
  
 Lorsque l'écouteur ETWTraceListener est utilisé, les suivis sont enregistrés dans des fichiers .etl binaires. Si le suivi ServiceModel est activé, tous les suivis générés apparaissent dans le même fichier. Utilisez l' [outil Service Trace Viewer (SvcTraceViewer. exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) pour afficher les fichiers journaux. etl et. svclog. La visionneuse affiche une vue de bout en bout du système, ce qui permet de suivre un message de sa source à ses destination et point de consommation.  
  
 L'écouteur de suivi ETW prend en charge l'enregistrement circulaire. Pour activer cette fonctionnalité, accédez à **Démarrer**, **exécuter** et tapez `cmd` pour démarrer une console de commandes. Dans la commande suivante, remplacez le paramètre `<logfilename>` par le nom de votre fichier journal.  
  
```console  
logman create trace Wcf -o <logfilename> -p "{411a0819-c24b-428c-83e2-26b41091702e}" -f bincirc -max 1000  
```  
  
 Les commutateurs `-f` et `-max` sont facultatifs. Ils spécifient respectivement le format circulaire binaire et la taille maximale du journal, à savoir 1 000 Mo. Le commutateur `-p` est utilisé pour spécifier le fournisseur du suivi. Dans notre exemple, `"{411a0819-c24b-428c-83e2-26b41091702e}"` correspond au GUID du fournisseur d'exemples ETW XML.  
  
 Pour démarrer la session, tapez la commande suivante.  
  
```console  
logman start Wcf  
```  
  
 L'enregistrement terminé, vous pouvez arrêter la session à l'aide de la commande suivante.  
  
```console  
logman stop Wcf  
```  
  
 Ce processus génère des journaux circulaires binaires que vous pouvez traiter avec l’outil de votre choix, y compris l' [outil Service Trace Viewer (SvcTraceViewer. exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) ou tracerpt.  
  
 Vous pouvez également consulter l’exemple de [traçage circulaire](circular-tracing.md) pour plus d’informations sur un autre écouteur afin d’effectuer une journalisation circulaire.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pour générer la solution, suivez les instructions de [la création des exemples de Windows Communication Foundation](building-the-samples.md).  
  
    > [!NOTE]
    > Pour exécuter les commandes RegisterProvider.bat, SetupETW.bat et CleanupETW.bat, vous devez utiliser un compte d'administrateur local. Si vous utilisez Windows Vista ou une version ultérieure, vous devez également exécuter l’invite de commandes avec des privilèges élevés. Pour ce faire, cliquez avec le bouton droit sur l’icône de l’invite de commandes, puis cliquez sur **exécuter en tant qu’administrateur**.  
  
3. Avant d'exécuter l'exemple, exécutez RegisterProvider.bat sur le client et le serveur. Cette opération installe le fichier ETWTracingSampleLog.etl qui permet de générer les suivis que vous pourrez ensuite afficher dans Service Trace Viewer. Ce fichier se trouve dans le dossier C:\logs. Si ce dossier n'existe pas, il doit être créé. Si vous ne respectez pas cette consigne, aucun suivi ne pourra être généré. Exécutez ensuite SetupETW.bat sur le client et le serveur pour démarrer la session de suivi ETW. Le fichier SetupETW.bat se trouve sous le dossier CS\Client.  
  
4. Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](running-the-samples.md).  
  
5. L'exécution de l'exemple terminée, exécutez CleanupETW.bat pour compléter la création du fichier ETWTracingSampleLog.etl.  
  
6. Ouvrez le fichier ETWTracingSampleLog.etl dans Service Trace Viewer. Vous serez alors invité à enregistrer ce fichier au format binaire comme fichier .svclog.  
  
7. Ouvrez ce nouveau fichier .svclog dans Service Trace Viewer pour afficher les suivis ETW et ServiceModel.  
  
> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\AnalyticTrace`  
  
## <a name="see-also"></a>Voir aussi

- [Exemples d'analyse AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))

---
title: ETW Tracing
ms.date: 03/30/2017
ms.assetid: ac99a063-e2d2-40cc-b659-d23c2f783f92
ms.openlocfilehash: 07379a464e6635a3de10c08647dbc769a5885e4e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183700"
---
# <a name="etw-tracing"></a>ETW Tracing
Cet exemple montre comment implémenter le suivi de bout en bout (E2E) à l'aide du suivi d'événements pour Windows (ETW, Event Tracing for Windows) et du `ETWTraceListener` fourni dans cet exemple. L’échantillon est basé sur le [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) et comprend le traçage ETW.  
  
> [!NOTE]
> La procédure d'installation ainsi que les instructions de génération correspondant à cet exemple figurent en fin de rubrique.  
  
 Cet exemple suppose que vous êtes familier avec [tracing et l’enregistrement des messages](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).  
  
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
> La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique. Pour plus d’informations sur ces outils, voir<https://go.microsoft.com/fwlink/?LinkId=56580>  
  
 Lorsque l'écouteur ETWTraceListener est utilisé, les suivis sont enregistrés dans des fichiers .etl binaires. Si le suivi ServiceModel est activé, tous les suivis générés apparaissent dans le même fichier. Utilisez [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) pour visionner les fichiers journal .etl et .svclog. La visionneuse affiche une vue de bout en bout du système, ce qui permet de suivre un message de sa source à ses destination et point de consommation.  
  
 L'écouteur de suivi ETW prend en charge l'enregistrement circulaire. Pour activer cette fonctionnalité, **Run** allez `cmd` **démarrer,** exécuter et tapez pour démarrer une console de commande. Dans la commande suivante, remplacez le paramètre `<logfilename>` par le nom de votre fichier journal.  
  
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
  
 Ce processus génère des journaux circulaires binaires que vous pouvez traiter avec votre outil de choix, y compris [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) ou Tracerpt.  
  
 Vous pouvez également consulter l’échantillon [Circular Tracing](../../../../docs/framework/wcf/samples/circular-tracing.md) pour plus d’informations sur un auditeur alternatif pour effectuer l’enregistrement circulaire.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les échantillons de la Fondation De communication Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pour construire la solution, suivez les instructions dans [la construction des échantillons de la Fondation De communication Windows](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
    > [!NOTE]
    > Pour exécuter les commandes RegisterProvider.bat, SetupETW.bat et CleanupETW.bat, vous devez utiliser un compte d'administrateur local. Si vous utilisez Windows Vista ou plus tard, vous devez également exécuter l’invite de commande avec des privilèges élevés. Pour ce faire, cliquez à droite sur l’icône d’invite de commande, puis cliquez sur **Run en tant qu’administrateur**.  
  
3. Avant d'exécuter l'exemple, exécutez RegisterProvider.bat sur le client et le serveur. Cette opération installe le fichier ETWTracingSampleLog.etl qui permet de générer les suivis que vous pourrez ensuite afficher dans Service Trace Viewer. Ce fichier se trouve dans le dossier C:\logs. Si ce dossier n'existe pas, il doit être créé. Si vous ne respectez pas cette consigne, aucun suivi ne pourra être généré. Exécutez ensuite SetupETW.bat sur le client et le serveur pour démarrer la session de suivi ETW. Le fichier SetupETW.bat se trouve sous le dossier CS\Client.  
  
4. Pour exécuter l’échantillon dans une configuration mono-ou cross-computer, suivez les instructions dans [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
5. L'exécution de l'exemple terminée, exécutez CleanupETW.bat pour compléter la création du fichier ETWTracingSampleLog.etl.  
  
6. Ouvrez le fichier ETWTracingSampleLog.etl dans Service Trace Viewer. Vous serez alors invité à enregistrer ce fichier au format binaire comme fichier .svclog.  
  
7. Ouvrez ce nouveau fichier .svclog dans Service Trace Viewer pour afficher les suivis ETW et ServiceModel.  
  
> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, rendez-vous sur [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) Samples pour .NET Framework 4 pour](https://www.microsoft.com/download/details.aspx?id=21459) télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] des échantillons. Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\AnalyticTrace`  
  
## <a name="see-also"></a>Voir aussi

- [Exemples d'analyse AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))

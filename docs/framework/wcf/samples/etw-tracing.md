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
# <a name="etw-tracing"></a><span data-ttu-id="51a13-102">ETW Tracing</span><span class="sxs-lookup"><span data-stu-id="51a13-102">ETW Tracing</span></span>
<span data-ttu-id="51a13-103">Cet exemple montre comment implémenter le suivi de bout en bout (E2E) à l'aide du suivi d'événements pour Windows (ETW, Event Tracing for Windows) et du `ETWTraceListener` fourni dans cet exemple.</span><span class="sxs-lookup"><span data-stu-id="51a13-103">This sample demonstrates how to implement End-to-End (E2E) tracing using Event Tracing for Windows (ETW) and the `ETWTraceListener` that is provided with this sample.</span></span> <span data-ttu-id="51a13-104">L’échantillon est basé sur le [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) et comprend le traçage ETW.</span><span class="sxs-lookup"><span data-stu-id="51a13-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) and includes ETW tracing.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="51a13-105">La procédure d'installation ainsi que les instructions de génération correspondant à cet exemple figurent en fin de rubrique.</span><span class="sxs-lookup"><span data-stu-id="51a13-105">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="51a13-106">Cet exemple suppose que vous êtes familier avec [tracing et l’enregistrement des messages](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).</span><span class="sxs-lookup"><span data-stu-id="51a13-106">This sample assumes that you are familiar with [Tracing and Message Logging](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).</span></span>  
  
 <span data-ttu-id="51a13-107">Chaque source de suivi du modèle de suivi <xref:System.Diagnostics> peut disposer de plusieurs écouteurs de suivi qui déterminent où et comment les données sont suivies.</span><span class="sxs-lookup"><span data-stu-id="51a13-107">Each trace source in the <xref:System.Diagnostics> tracing model can have multiple trace listeners that determine where and how the data is traced.</span></span> <span data-ttu-id="51a13-108">Le type de ces écouteurs définit le format auquel les données de suivi sont enregistrées.</span><span class="sxs-lookup"><span data-stu-id="51a13-108">The type of listener defines the format in which trace data is logged.</span></span> <span data-ttu-id="51a13-109">L'exemple de code suivant indique comment ajouter un écouteur à la configuration.</span><span class="sxs-lookup"><span data-stu-id="51a13-109">The following code sample shows how to add the listener to configuration.</span></span>  
  
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
  
 <span data-ttu-id="51a13-110">Avant d'utiliser cet écouteur, une session de suivi ETW doit être démarrée.</span><span class="sxs-lookup"><span data-stu-id="51a13-110">Before using this listener, an ETW Trace Session must be started.</span></span> <span data-ttu-id="51a13-111">Pour ce faire, Logman.exe ou Tracelog.exe peut être utilisé.</span><span class="sxs-lookup"><span data-stu-id="51a13-111">This session can be started by using Logman.exe or Tracelog.exe.</span></span> <span data-ttu-id="51a13-112">Cet exemple contient un fichier SetupETW.bat vous permettant de configurer une session de suivi ETW ainsi qu'un fichier CleanupETW.bat vous permettant de fermer la session et de compléter le fichier journal.</span><span class="sxs-lookup"><span data-stu-id="51a13-112">A SetupETW.bat file is included with this sample so that you can set up the ETW Trace Session along with a CleanupETW.bat file for closing the session and completing the log file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="51a13-113">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="51a13-113">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span> <span data-ttu-id="51a13-114">Pour plus d’informations sur ces outils, voir<https://go.microsoft.com/fwlink/?LinkId=56580></span><span class="sxs-lookup"><span data-stu-id="51a13-114">For more information about these tools, see <https://go.microsoft.com/fwlink/?LinkId=56580></span></span>  
  
 <span data-ttu-id="51a13-115">Lorsque l'écouteur ETWTraceListener est utilisé, les suivis sont enregistrés dans des fichiers .etl binaires.</span><span class="sxs-lookup"><span data-stu-id="51a13-115">When using the ETWTraceListener, traces are logged in binary .etl files.</span></span> <span data-ttu-id="51a13-116">Si le suivi ServiceModel est activé, tous les suivis générés apparaissent dans le même fichier.</span><span class="sxs-lookup"><span data-stu-id="51a13-116">With ServiceModel tracing turned on, all generated traces appear in the same file.</span></span> <span data-ttu-id="51a13-117">Utilisez [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) pour visionner les fichiers journal .etl et .svclog.</span><span class="sxs-lookup"><span data-stu-id="51a13-117">Use [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) for viewing .etl and .svclog log files.</span></span> <span data-ttu-id="51a13-118">La visionneuse affiche une vue de bout en bout du système, ce qui permet de suivre un message de sa source à ses destination et point de consommation.</span><span class="sxs-lookup"><span data-stu-id="51a13-118">The viewer creates an end-to-end view of the system that makes it possible to trace a message from its source to its destination and point of consumption.</span></span>  
  
 <span data-ttu-id="51a13-119">L'écouteur de suivi ETW prend en charge l'enregistrement circulaire.</span><span class="sxs-lookup"><span data-stu-id="51a13-119">The ETW Trace Listener supports circular logging.</span></span> <span data-ttu-id="51a13-120">Pour activer cette fonctionnalité, **Run** allez `cmd` **démarrer,** exécuter et tapez pour démarrer une console de commande.</span><span class="sxs-lookup"><span data-stu-id="51a13-120">To enable this feature, go to **Start**, **Run** and type `cmd` to start a command console.</span></span> <span data-ttu-id="51a13-121">Dans la commande suivante, remplacez le paramètre `<logfilename>` par le nom de votre fichier journal.</span><span class="sxs-lookup"><span data-stu-id="51a13-121">In the following command, replace the `<logfilename>` parameter with the name of your log file.</span></span>  
  
```console  
logman create trace Wcf -o <logfilename> -p "{411a0819-c24b-428c-83e2-26b41091702e}" -f bincirc -max 1000  
```  
  
 <span data-ttu-id="51a13-122">Les commutateurs `-f` et `-max` sont facultatifs.</span><span class="sxs-lookup"><span data-stu-id="51a13-122">The `-f` and `-max` switches are optional.</span></span> <span data-ttu-id="51a13-123">Ils spécifient respectivement le format circulaire binaire et la taille maximale du journal, à savoir 1 000 Mo.</span><span class="sxs-lookup"><span data-stu-id="51a13-123">They specify the binary circular format and max log size of 1000MB respectively.</span></span> <span data-ttu-id="51a13-124">Le commutateur `-p` est utilisé pour spécifier le fournisseur du suivi.</span><span class="sxs-lookup"><span data-stu-id="51a13-124">The `-p` switch is used to specify the trace provider.</span></span> <span data-ttu-id="51a13-125">Dans notre exemple, `"{411a0819-c24b-428c-83e2-26b41091702e}"` correspond au GUID du fournisseur d'exemples ETW XML.</span><span class="sxs-lookup"><span data-stu-id="51a13-125">In our example, `"{411a0819-c24b-428c-83e2-26b41091702e}"` is the GUID for "XML ETW Sample Provider".</span></span>  
  
 <span data-ttu-id="51a13-126">Pour démarrer la session, tapez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="51a13-126">To start the session, type in the following command.</span></span>  
  
```console  
logman start Wcf  
```  
  
 <span data-ttu-id="51a13-127">L'enregistrement terminé, vous pouvez arrêter la session à l'aide de la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="51a13-127">After you have finished logging, you can stop the session with the following command.</span></span>  
  
```console  
logman stop Wcf  
```  
  
 <span data-ttu-id="51a13-128">Ce processus génère des journaux circulaires binaires que vous pouvez traiter avec votre outil de choix, y compris [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) ou Tracerpt.</span><span class="sxs-lookup"><span data-stu-id="51a13-128">This process generates binary circular logs that you can process with your tool of choice, including [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) or Tracerpt.</span></span>  
  
 <span data-ttu-id="51a13-129">Vous pouvez également consulter l’échantillon [Circular Tracing](../../../../docs/framework/wcf/samples/circular-tracing.md) pour plus d’informations sur un auditeur alternatif pour effectuer l’enregistrement circulaire.</span><span class="sxs-lookup"><span data-stu-id="51a13-129">You can also review the [Circular Tracing](../../../../docs/framework/wcf/samples/circular-tracing.md) sample for more information on an alternative listener to perform circular logging.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="51a13-130">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="51a13-130">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="51a13-131">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les échantillons de la Fondation De communication Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="51a13-131">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="51a13-132">Pour construire la solution, suivez les instructions dans [la construction des échantillons de la Fondation De communication Windows](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="51a13-132">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="51a13-133">Pour exécuter les commandes RegisterProvider.bat, SetupETW.bat et CleanupETW.bat, vous devez utiliser un compte d'administrateur local.</span><span class="sxs-lookup"><span data-stu-id="51a13-133">To use the RegisterProvider.bat, SetupETW.bat and CleanupETW.bat commands, you must run under a local administrator account.</span></span> <span data-ttu-id="51a13-134">Si vous utilisez Windows Vista ou plus tard, vous devez également exécuter l’invite de commande avec des privilèges élevés.</span><span class="sxs-lookup"><span data-stu-id="51a13-134">If you are using Windows Vista or later, you must also run the command prompt with elevated privileges.</span></span> <span data-ttu-id="51a13-135">Pour ce faire, cliquez à droite sur l’icône d’invite de commande, puis cliquez sur **Run en tant qu’administrateur**.</span><span class="sxs-lookup"><span data-stu-id="51a13-135">To do so, right-click the command prompt icon, then click **Run as administrator**.</span></span>  
  
3. <span data-ttu-id="51a13-136">Avant d'exécuter l'exemple, exécutez RegisterProvider.bat sur le client et le serveur.</span><span class="sxs-lookup"><span data-stu-id="51a13-136">Before running the sample, run RegisterProvider.bat on the client and server.</span></span> <span data-ttu-id="51a13-137">Cette opération installe le fichier ETWTracingSampleLog.etl qui permet de générer les suivis que vous pourrez ensuite afficher dans Service Trace Viewer.</span><span class="sxs-lookup"><span data-stu-id="51a13-137">This sets up the resulting ETWTracingSampleLog.etl file to generate traces that can be read by the Service Trace Viewer.</span></span> <span data-ttu-id="51a13-138">Ce fichier se trouve dans le dossier C:\logs.</span><span class="sxs-lookup"><span data-stu-id="51a13-138">This file can be found in the C:\logs folder.</span></span> <span data-ttu-id="51a13-139">Si ce dossier n'existe pas, il doit être créé. Si vous ne respectez pas cette consigne, aucun suivi ne pourra être généré.</span><span class="sxs-lookup"><span data-stu-id="51a13-139">If this folder does not exist, it must be created or no traces are generated.</span></span> <span data-ttu-id="51a13-140">Exécutez ensuite SetupETW.bat sur le client et le serveur pour démarrer la session de suivi ETW.</span><span class="sxs-lookup"><span data-stu-id="51a13-140">Then, run SetupETW.bat on the client and server computers to begin the ETW Trace Session.</span></span> <span data-ttu-id="51a13-141">Le fichier SetupETW.bat se trouve sous le dossier CS\Client.</span><span class="sxs-lookup"><span data-stu-id="51a13-141">The SetupETW.bat file can be found under the CS\Client folder.</span></span>  
  
4. <span data-ttu-id="51a13-142">Pour exécuter l’échantillon dans une configuration mono-ou cross-computer, suivez les instructions dans [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="51a13-142">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
5. <span data-ttu-id="51a13-143">L'exécution de l'exemple terminée, exécutez CleanupETW.bat pour compléter la création du fichier ETWTracingSampleLog.etl.</span><span class="sxs-lookup"><span data-stu-id="51a13-143">When the sample is completed, run CleanupETW.bat to complete the creation of the ETWTracingSampleLog.etl file.</span></span>  
  
6. <span data-ttu-id="51a13-144">Ouvrez le fichier ETWTracingSampleLog.etl dans Service Trace Viewer.</span><span class="sxs-lookup"><span data-stu-id="51a13-144">Open the ETWTracingSampleLog.etl file from within the Service Trace Viewer.</span></span> <span data-ttu-id="51a13-145">Vous serez alors invité à enregistrer ce fichier au format binaire comme fichier .svclog.</span><span class="sxs-lookup"><span data-stu-id="51a13-145">You will be prompted to save the binary formatted file as a .svclog file.</span></span>  
  
7. <span data-ttu-id="51a13-146">Ouvrez ce nouveau fichier .svclog dans Service Trace Viewer pour afficher les suivis ETW et ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="51a13-146">Open the newly created .svclog file from within the Service Trace Viewer to view the ETW and ServiceModel traces.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="51a13-147">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="51a13-147">The samples may already be installed on your computer.</span></span> <span data-ttu-id="51a13-148">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="51a13-148">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="51a13-149">Si ce répertoire n’existe pas, rendez-vous sur [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) Samples pour .NET Framework 4 pour](https://www.microsoft.com/download/details.aspx?id=21459) télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] des échantillons.</span><span class="sxs-lookup"><span data-stu-id="51a13-149">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="51a13-150">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="51a13-150">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\AnalyticTrace`  
  
## <a name="see-also"></a><span data-ttu-id="51a13-151">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="51a13-151">See also</span></span>

- <span data-ttu-id="51a13-152">[Exemples d'analyse AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="51a13-152">[AppFabric Monitoring Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span></span>

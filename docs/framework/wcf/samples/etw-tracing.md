---
title: ETW Tracing
description: Cet exemple montre comment implémenter le suivi de bout en bout (E2E) à l’aide de Suivi d’v nements pour Windows (ETW) et du ETWTraceListener.
ms.date: 03/30/2017
ms.assetid: ac99a063-e2d2-40cc-b659-d23c2f783f92
ms.openlocfilehash: 210186285ed749a5d1567becd6738939b0bd9d03
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244424"
---
# <a name="etw-tracing"></a><span data-ttu-id="ed403-103">ETW Tracing</span><span class="sxs-lookup"><span data-stu-id="ed403-103">ETW Tracing</span></span>
<span data-ttu-id="ed403-104">Cet exemple montre comment implémenter le suivi de bout en bout (E2E) à l'aide du suivi d'événements pour Windows (ETW, Event Tracing for Windows) et du `ETWTraceListener` fourni dans cet exemple.</span><span class="sxs-lookup"><span data-stu-id="ed403-104">This sample demonstrates how to implement End-to-End (E2E) tracing using Event Tracing for Windows (ETW) and the `ETWTraceListener` that is provided with this sample.</span></span> <span data-ttu-id="ed403-105">L’exemple est basé sur le [prise en main](getting-started-sample.md) et comprend le suivi ETW.</span><span class="sxs-lookup"><span data-stu-id="ed403-105">The sample is based on the [Getting Started](getting-started-sample.md) and includes ETW tracing.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ed403-106">La procédure d'installation ainsi que les instructions de génération correspondant à cet exemple figurent en fin de rubrique.</span><span class="sxs-lookup"><span data-stu-id="ed403-106">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="ed403-107">Cet exemple suppose que vous êtes familiarisé avec [le suivi et la journalisation des messages](tracing-and-message-logging.md).</span><span class="sxs-lookup"><span data-stu-id="ed403-107">This sample assumes that you are familiar with [Tracing and Message Logging](tracing-and-message-logging.md).</span></span>  
  
 <span data-ttu-id="ed403-108">Chaque source de suivi du modèle de suivi <xref:System.Diagnostics> peut disposer de plusieurs écouteurs de suivi qui déterminent où et comment les données sont suivies.</span><span class="sxs-lookup"><span data-stu-id="ed403-108">Each trace source in the <xref:System.Diagnostics> tracing model can have multiple trace listeners that determine where and how the data is traced.</span></span> <span data-ttu-id="ed403-109">Le type de ces écouteurs définit le format auquel les données de suivi sont enregistrées.</span><span class="sxs-lookup"><span data-stu-id="ed403-109">The type of listener defines the format in which trace data is logged.</span></span> <span data-ttu-id="ed403-110">L'exemple de code suivant indique comment ajouter un écouteur à la configuration.</span><span class="sxs-lookup"><span data-stu-id="ed403-110">The following code sample shows how to add the listener to configuration.</span></span>  
  
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
  
 <span data-ttu-id="ed403-111">Avant d'utiliser cet écouteur, une session de suivi ETW doit être démarrée.</span><span class="sxs-lookup"><span data-stu-id="ed403-111">Before using this listener, an ETW Trace Session must be started.</span></span> <span data-ttu-id="ed403-112">Pour ce faire, Logman.exe ou Tracelog.exe peut être utilisé.</span><span class="sxs-lookup"><span data-stu-id="ed403-112">This session can be started by using Logman.exe or Tracelog.exe.</span></span> <span data-ttu-id="ed403-113">Cet exemple contient un fichier SetupETW.bat vous permettant de configurer une session de suivi ETW ainsi qu'un fichier CleanupETW.bat vous permettant de fermer la session et de compléter le fichier journal.</span><span class="sxs-lookup"><span data-stu-id="ed403-113">A SetupETW.bat file is included with this sample so that you can set up the ETW Trace Session along with a CleanupETW.bat file for closing the session and completing the log file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ed403-114">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="ed403-114">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span> <span data-ttu-id="ed403-115">Pour plus d’informations sur ces outils, consultez.<https://go.microsoft.com/fwlink/?LinkId=56580></span><span class="sxs-lookup"><span data-stu-id="ed403-115">For more information about these tools, see <https://go.microsoft.com/fwlink/?LinkId=56580></span></span>  
  
 <span data-ttu-id="ed403-116">Lorsque l'écouteur ETWTraceListener est utilisé, les suivis sont enregistrés dans des fichiers .etl binaires.</span><span class="sxs-lookup"><span data-stu-id="ed403-116">When using the ETWTraceListener, traces are logged in binary .etl files.</span></span> <span data-ttu-id="ed403-117">Si le suivi ServiceModel est activé, tous les suivis générés apparaissent dans le même fichier.</span><span class="sxs-lookup"><span data-stu-id="ed403-117">With ServiceModel tracing turned on, all generated traces appear in the same file.</span></span> <span data-ttu-id="ed403-118">Utilisez l' [outil Service Trace Viewer (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) pour afficher les fichiers journaux. etl et. svclog.</span><span class="sxs-lookup"><span data-stu-id="ed403-118">Use [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) for viewing .etl and .svclog log files.</span></span> <span data-ttu-id="ed403-119">La visionneuse affiche une vue de bout en bout du système, ce qui permet de suivre un message de sa source à ses destination et point de consommation.</span><span class="sxs-lookup"><span data-stu-id="ed403-119">The viewer creates an end-to-end view of the system that makes it possible to trace a message from its source to its destination and point of consumption.</span></span>  
  
 <span data-ttu-id="ed403-120">L'écouteur de suivi ETW prend en charge l'enregistrement circulaire.</span><span class="sxs-lookup"><span data-stu-id="ed403-120">The ETW Trace Listener supports circular logging.</span></span> <span data-ttu-id="ed403-121">Pour activer cette fonctionnalité, accédez à **Démarrer**, **exécuter** et tapez `cmd` pour démarrer une console de commandes.</span><span class="sxs-lookup"><span data-stu-id="ed403-121">To enable this feature, go to **Start**, **Run** and type `cmd` to start a command console.</span></span> <span data-ttu-id="ed403-122">Dans la commande suivante, remplacez le paramètre `<logfilename>` par le nom de votre fichier journal.</span><span class="sxs-lookup"><span data-stu-id="ed403-122">In the following command, replace the `<logfilename>` parameter with the name of your log file.</span></span>  
  
```console  
logman create trace Wcf -o <logfilename> -p "{411a0819-c24b-428c-83e2-26b41091702e}" -f bincirc -max 1000  
```  
  
 <span data-ttu-id="ed403-123">Les commutateurs `-f` et `-max` sont facultatifs.</span><span class="sxs-lookup"><span data-stu-id="ed403-123">The `-f` and `-max` switches are optional.</span></span> <span data-ttu-id="ed403-124">Ils spécifient respectivement le format circulaire binaire et la taille maximale du journal, à savoir 1 000 Mo.</span><span class="sxs-lookup"><span data-stu-id="ed403-124">They specify the binary circular format and max log size of 1000MB respectively.</span></span> <span data-ttu-id="ed403-125">Le commutateur `-p` est utilisé pour spécifier le fournisseur du suivi.</span><span class="sxs-lookup"><span data-stu-id="ed403-125">The `-p` switch is used to specify the trace provider.</span></span> <span data-ttu-id="ed403-126">Dans notre exemple, `"{411a0819-c24b-428c-83e2-26b41091702e}"` correspond au GUID du fournisseur d'exemples ETW XML.</span><span class="sxs-lookup"><span data-stu-id="ed403-126">In our example, `"{411a0819-c24b-428c-83e2-26b41091702e}"` is the GUID for "XML ETW Sample Provider".</span></span>  
  
 <span data-ttu-id="ed403-127">Pour démarrer la session, tapez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="ed403-127">To start the session, type in the following command.</span></span>  
  
```console  
logman start Wcf  
```  
  
 <span data-ttu-id="ed403-128">L'enregistrement terminé, vous pouvez arrêter la session à l'aide de la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="ed403-128">After you have finished logging, you can stop the session with the following command.</span></span>  
  
```console  
logman stop Wcf  
```  
  
 <span data-ttu-id="ed403-129">Ce processus génère des journaux circulaires binaires que vous pouvez traiter avec l’outil de votre choix, y compris l' [outil Service Trace Viewer (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) ou tracerpt.</span><span class="sxs-lookup"><span data-stu-id="ed403-129">This process generates binary circular logs that you can process with your tool of choice, including [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) or Tracerpt.</span></span>  
  
 <span data-ttu-id="ed403-130">Vous pouvez également consulter l’exemple de [traçage circulaire](circular-tracing.md) pour plus d’informations sur un autre écouteur afin d’effectuer une journalisation circulaire.</span><span class="sxs-lookup"><span data-stu-id="ed403-130">You can also review the [Circular Tracing](circular-tracing.md) sample for more information on an alternative listener to perform circular logging.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ed403-131">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="ed403-131">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="ed403-132">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ed403-132">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="ed403-133">Pour générer la solution, suivez les instructions de [la création des exemples de Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ed403-133">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="ed403-134">Pour exécuter les commandes RegisterProvider.bat, SetupETW.bat et CleanupETW.bat, vous devez utiliser un compte d'administrateur local.</span><span class="sxs-lookup"><span data-stu-id="ed403-134">To use the RegisterProvider.bat, SetupETW.bat and CleanupETW.bat commands, you must run under a local administrator account.</span></span> <span data-ttu-id="ed403-135">Si vous utilisez Windows Vista ou une version ultérieure, vous devez également exécuter l’invite de commandes avec des privilèges élevés.</span><span class="sxs-lookup"><span data-stu-id="ed403-135">If you are using Windows Vista or later, you must also run the command prompt with elevated privileges.</span></span> <span data-ttu-id="ed403-136">Pour ce faire, cliquez avec le bouton droit sur l’icône de l’invite de commandes, puis cliquez sur **exécuter en tant qu’administrateur**.</span><span class="sxs-lookup"><span data-stu-id="ed403-136">To do so, right-click the command prompt icon, then click **Run as administrator**.</span></span>  
  
3. <span data-ttu-id="ed403-137">Avant d'exécuter l'exemple, exécutez RegisterProvider.bat sur le client et le serveur.</span><span class="sxs-lookup"><span data-stu-id="ed403-137">Before running the sample, run RegisterProvider.bat on the client and server.</span></span> <span data-ttu-id="ed403-138">Cette opération installe le fichier ETWTracingSampleLog.etl qui permet de générer les suivis que vous pourrez ensuite afficher dans Service Trace Viewer.</span><span class="sxs-lookup"><span data-stu-id="ed403-138">This sets up the resulting ETWTracingSampleLog.etl file to generate traces that can be read by the Service Trace Viewer.</span></span> <span data-ttu-id="ed403-139">Ce fichier se trouve dans le dossier C:\logs.</span><span class="sxs-lookup"><span data-stu-id="ed403-139">This file can be found in the C:\logs folder.</span></span> <span data-ttu-id="ed403-140">Si ce dossier n'existe pas, il doit être créé. Si vous ne respectez pas cette consigne, aucun suivi ne pourra être généré.</span><span class="sxs-lookup"><span data-stu-id="ed403-140">If this folder does not exist, it must be created or no traces are generated.</span></span> <span data-ttu-id="ed403-141">Exécutez ensuite SetupETW.bat sur le client et le serveur pour démarrer la session de suivi ETW.</span><span class="sxs-lookup"><span data-stu-id="ed403-141">Then, run SetupETW.bat on the client and server computers to begin the ETW Trace Session.</span></span> <span data-ttu-id="ed403-142">Le fichier SetupETW.bat se trouve sous le dossier CS\Client.</span><span class="sxs-lookup"><span data-stu-id="ed403-142">The SetupETW.bat file can be found under the CS\Client folder.</span></span>  
  
4. <span data-ttu-id="ed403-143">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ed403-143">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
5. <span data-ttu-id="ed403-144">L'exécution de l'exemple terminée, exécutez CleanupETW.bat pour compléter la création du fichier ETWTracingSampleLog.etl.</span><span class="sxs-lookup"><span data-stu-id="ed403-144">When the sample is completed, run CleanupETW.bat to complete the creation of the ETWTracingSampleLog.etl file.</span></span>  
  
6. <span data-ttu-id="ed403-145">Ouvrez le fichier ETWTracingSampleLog.etl dans Service Trace Viewer.</span><span class="sxs-lookup"><span data-stu-id="ed403-145">Open the ETWTracingSampleLog.etl file from within the Service Trace Viewer.</span></span> <span data-ttu-id="ed403-146">Vous serez alors invité à enregistrer ce fichier au format binaire comme fichier .svclog.</span><span class="sxs-lookup"><span data-stu-id="ed403-146">You will be prompted to save the binary formatted file as a .svclog file.</span></span>  
  
7. <span data-ttu-id="ed403-147">Ouvrez ce nouveau fichier .svclog dans Service Trace Viewer pour afficher les suivis ETW et ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="ed403-147">Open the newly created .svclog file from within the Service Trace Viewer to view the ETW and ServiceModel traces.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ed403-148">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="ed403-148">The samples may already be installed on your computer.</span></span> <span data-ttu-id="ed403-149">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="ed403-149">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="ed403-150">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="ed403-150">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ed403-151">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="ed403-151">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\AnalyticTrace`  
  
## <a name="see-also"></a><span data-ttu-id="ed403-152">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ed403-152">See also</span></span>

- <span data-ttu-id="ed403-153">[Exemples d'analyse AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="ed403-153">[AppFabric Monitoring Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span></span>

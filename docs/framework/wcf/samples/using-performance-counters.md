---
title: Using Performance Counters
ms.date: 03/30/2017
ms.assetid: 00a787af-1876-473c-a48d-f52b51e28a3f
ms.openlocfilehash: 3e0a0199e93abe1218f7d9c052807cb94e911140
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716710"
---
# <a name="using-performance-counters"></a><span data-ttu-id="ae804-102">Using Performance Counters</span><span class="sxs-lookup"><span data-stu-id="ae804-102">Using Performance Counters</span></span>
<span data-ttu-id="ae804-103">Cet exemple montre comment accéder aux compteurs de performance Windows Communication Foundation (WCF) et comment créer des compteurs de performances définis par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="ae804-103">This sample demonstrates how to access Windows Communication Foundation (WCF) performance counters and how to create user-defined performance counters.</span></span> <span data-ttu-id="ae804-104">Cet exemple est basé sur le [prise en main](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="ae804-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ae804-105">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="ae804-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="ae804-106">Dans cet exemple, le client appelle les quatre méthodes du service `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="ae804-106">In this sample, the client calls the four methods of the `ICalculator` service.</span></span> <span data-ttu-id="ae804-107">Le client continue jusqu'à ce qu'il soit interrompu par l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="ae804-107">The client continues to do this until it is interrupted by the user.</span></span> <span data-ttu-id="ae804-108">Le service reste inchangé.</span><span class="sxs-lookup"><span data-stu-id="ae804-108">The service remains unchanged.</span></span>  
  
 <span data-ttu-id="ae804-109">Les compteurs de performance sont activés dans la section de diagnostic du fichier Web.config pour le service, comme le montre l'exemple de configuration suivant.</span><span class="sxs-lookup"><span data-stu-id="ae804-109">Performance counters are enabled in the diagnostics section of the Web.config file for the service, as shown in the following sample configuration.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <diagnostics performanceCounters="All" />   
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="ae804-110">Cette tâche peut également être effectuée à l’aide de l' [outil Éditeur de configuration (SvcConfigEditor. exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span><span class="sxs-lookup"><span data-stu-id="ae804-110">This task can also be done using the [Configuration Editor Tool (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
 <span data-ttu-id="ae804-111">Lorsque les compteurs de performance sont activés, la suite entière des compteurs de performance WCF est activée pour le service.</span><span class="sxs-lookup"><span data-stu-id="ae804-111">When performance counters are enabled, the entire suite of WCF performance counters is enabled for the service.</span></span> <span data-ttu-id="ae804-112">Le .NET Framework assure automatiquement la maintenance des données de performance à trois niveaux : `ServiceModelService`, `ServiceModelEndpoint` et `ServiceModelOperation`.</span><span class="sxs-lookup"><span data-stu-id="ae804-112">The .NET Framework automatically maintains performance data at three levels: `ServiceModelService`, `ServiceModelEndpoint` and `ServiceModelOperation`.</span></span> <span data-ttu-id="ae804-113">Chacun de ces niveaux comporte des compteurs de performance tels que « Appels », « Appels par seconde », et « Appels de sécurité non autorisés ».</span><span class="sxs-lookup"><span data-stu-id="ae804-113">Each of these levels has performance counters such as "Calls", "Calls per Second", and "Security Calls Not Authorized".</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ae804-114">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="ae804-114">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="ae804-115">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ae804-115">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="ae804-116">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ae804-116">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="ae804-117">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ae804-117">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-view-performance-data"></a><span data-ttu-id="ae804-118">Pour afficher les données de performances</span><span class="sxs-lookup"><span data-stu-id="ae804-118">To view performance data</span></span>  
  
1. <span data-ttu-id="ae804-119">Démarrez l’outil Analyseur de performances en cliquant sur **Démarrer**, **exécuter...** , entrez `perfmon`, cliquez sur **OK ou,** dans le panneau de configuration, sélectionnez **Outils d’administration** et double-cliquez sur **performances**.</span><span class="sxs-lookup"><span data-stu-id="ae804-119">Start the Performance Monitor Tool by clicking **Start**, **Run…**, enter `perfmon` and click **OK,** or from Control Panel, select **Administrative Tools** and double-click **Performance**.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="ae804-120">Vous ne pouvez pas ajouter de compteurs tant que l'exemple de code est en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="ae804-120">You cannot add counters until the sample code is running.</span></span>  
  
2. <span data-ttu-id="ae804-121">Supprimez les compteurs de performance répertoriés en les sélectionnant et en appuyant sur la touche Suppr.</span><span class="sxs-lookup"><span data-stu-id="ae804-121">Remove the performance counters that are listed by selecting them and pressing the Delete key.</span></span>  
  
3. <span data-ttu-id="ae804-122">Pour ajouter des compteurs WCF, cliquez avec le bouton droit sur le volet graphique et sélectionnez **Ajouter des compteurs**.</span><span class="sxs-lookup"><span data-stu-id="ae804-122">Add WCF counters by right-clicking the graph pane and selecting **Add Counters**.</span></span> <span data-ttu-id="ae804-123">Dans la boîte de dialogue **Ajouter des compteurs** , sélectionnez **ServiceModelOperation 3.0.0.0, ServiceModelEndpoint 3.0.0.0 ou ServiceModelService 3.0.0.0** dans la zone de liste déroulante objet de performance.</span><span class="sxs-lookup"><span data-stu-id="ae804-123">In the **Add Counters** dialog box, select **ServiceModelOperation 3.0.0.0, ServiceModelEndpoint 3.0.0.0, or ServiceModelService 3.0.0.0** in the Performance object drop down list box.</span></span> <span data-ttu-id="ae804-124">Sélectionnez les compteurs que vous souhaitez afficher dans la liste.</span><span class="sxs-lookup"><span data-stu-id="ae804-124">Select the counters you want to view from the list.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="ae804-125">Il n’y a aucun compteur de performance WCF pour un service s’il n’y a aucun service WCF en cours d’exécution sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="ae804-125">There are no WCF performance counters for a service if there are no WCF services running on the computer.</span></span>  
  
### <a name="to-use-the-configuration-editor-to-enable-counters"></a><span data-ttu-id="ae804-126">Pour utiliser l'Éditeur de configuration afin d'activer des compteurs</span><span class="sxs-lookup"><span data-stu-id="ae804-126">To use the Configuration Editor to enable counters</span></span>  
  
1. <span data-ttu-id="ae804-127">Ouvrez une instance de SvcConfigEditor.exe.</span><span class="sxs-lookup"><span data-stu-id="ae804-127">Open an instance of the SvcConfigEditor.exe.</span></span>  
  
2. <span data-ttu-id="ae804-128">Dans le menu fichier, cliquez sur **ouvrir** , puis sur **fichier de configuration...** .</span><span class="sxs-lookup"><span data-stu-id="ae804-128">On the File menu, click **Open** and then click **Config file…**.</span></span>  
  
3. <span data-ttu-id="ae804-129">Naviguez jusqu'au dossier de service de l'exemple d'application et ouvrez le fichier Web.config.</span><span class="sxs-lookup"><span data-stu-id="ae804-129">Navigate to the sample application's service folder and open the Web.config file.</span></span>  
  
4. <span data-ttu-id="ae804-130">Cliquez sur **Diagnostics** dans l’arborescence de configuration.</span><span class="sxs-lookup"><span data-stu-id="ae804-130">Click **Diagnostics** on the Configuration tree.</span></span>  
  
5. <span data-ttu-id="ae804-131">Activez/désactivez le **compteur de performances** dans la fenêtre **Diagnostics** pour afficher « tout ».</span><span class="sxs-lookup"><span data-stu-id="ae804-131">Toggle **Performance Counter** in the **Diagnostics** window to show 'All'.</span></span>  
  
6. <span data-ttu-id="ae804-132">Enregistrez le fichier de configuration et quittez l'éditeur.</span><span class="sxs-lookup"><span data-stu-id="ae804-132">Save the configuration file and exit the editor.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ae804-133">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="ae804-133">The samples may already be installed on your computer.</span></span> <span data-ttu-id="ae804-134">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="ae804-134">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="ae804-135">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ae804-135">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ae804-136">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="ae804-136">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\PerfCounters`  
  
## <a name="see-also"></a><span data-ttu-id="ae804-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ae804-137">See also</span></span>

- [<span data-ttu-id="ae804-138">Exemples de surveillance AppFabric</span><span class="sxs-lookup"><span data-stu-id="ae804-138">AppFabric Monitoring Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193959)

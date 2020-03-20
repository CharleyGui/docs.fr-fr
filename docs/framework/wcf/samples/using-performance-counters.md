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
# <a name="using-performance-counters"></a><span data-ttu-id="cff69-102">Using Performance Counters</span><span class="sxs-lookup"><span data-stu-id="cff69-102">Using Performance Counters</span></span>
<span data-ttu-id="cff69-103">Cet exemple montre comment accéder aux compteurs de performances de la Windows Communication Foundation (WCF) et comment créer des compteurs de performances définis par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="cff69-103">This sample demonstrates how to access Windows Communication Foundation (WCF) performance counters and how to create user-defined performance counters.</span></span> <span data-ttu-id="cff69-104">Cet échantillon est basé sur le [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="cff69-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cff69-105">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="cff69-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="cff69-106">Dans cet exemple, le client appelle les quatre méthodes du service `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="cff69-106">In this sample, the client calls the four methods of the `ICalculator` service.</span></span> <span data-ttu-id="cff69-107">Le client continue jusqu'à ce qu'il soit interrompu par l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="cff69-107">The client continues to do this until it is interrupted by the user.</span></span> <span data-ttu-id="cff69-108">Le service reste inchangé.</span><span class="sxs-lookup"><span data-stu-id="cff69-108">The service remains unchanged.</span></span>  
  
 <span data-ttu-id="cff69-109">Les compteurs de performance sont activés dans la section de diagnostic du fichier Web.config pour le service, comme le montre l'exemple de configuration suivant.</span><span class="sxs-lookup"><span data-stu-id="cff69-109">Performance counters are enabled in the diagnostics section of the Web.config file for the service, as shown in the following sample configuration.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <diagnostics performanceCounters="All" />
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="cff69-110">Cette tâche peut également être effectuée à l’aide de [l’outil d’éditeur de configuration (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span><span class="sxs-lookup"><span data-stu-id="cff69-110">This task can also be done using the [Configuration Editor Tool (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
 <span data-ttu-id="cff69-111">Lorsque les compteurs de performance sont activés, toute la suite de compteurs de performances WCF est activée pour le service.</span><span class="sxs-lookup"><span data-stu-id="cff69-111">When performance counters are enabled, the entire suite of WCF performance counters is enabled for the service.</span></span> <span data-ttu-id="cff69-112">Le .NET Framework assure automatiquement la maintenance des données de performance à trois niveaux : `ServiceModelService`, `ServiceModelEndpoint` et `ServiceModelOperation`.</span><span class="sxs-lookup"><span data-stu-id="cff69-112">The .NET Framework automatically maintains performance data at three levels: `ServiceModelService`, `ServiceModelEndpoint` and `ServiceModelOperation`.</span></span> <span data-ttu-id="cff69-113">Chacun de ces niveaux comporte des compteurs de performance tels que « Appels », « Appels par seconde », et « Appels de sécurité non autorisés ».</span><span class="sxs-lookup"><span data-stu-id="cff69-113">Each of these levels has performance counters such as "Calls", "Calls per Second", and "Security Calls Not Authorized".</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="cff69-114">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="cff69-114">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="cff69-115">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les échantillons de la Fondation De communication Windows.](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)</span><span class="sxs-lookup"><span data-stu-id="cff69-115">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="cff69-116">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cff69-116">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="cff69-117">Pour exécuter l’échantillon dans une configuration mono-ou cross-computer, suivez les instructions dans [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cff69-117">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-view-performance-data"></a><span data-ttu-id="cff69-118">Pour afficher les données de performances</span><span class="sxs-lookup"><span data-stu-id="cff69-118">To view performance data</span></span>  
  
1. <span data-ttu-id="cff69-119">Démarrer l’outil de moniteur de performance `perfmon` en cliquant sur **Démarrer,** **Exécuter...**, entrez et cliquez **sur OK,** ou à partir du panneau de contrôle, sélectionnez **des outils administratifs** et **des performances**en double clic.</span><span class="sxs-lookup"><span data-stu-id="cff69-119">Start the Performance Monitor Tool by clicking **Start**, **Run…**, enter `perfmon` and click **OK,** or from Control Panel, select **Administrative Tools** and double-click **Performance**.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="cff69-120">Vous ne pouvez pas ajouter de compteurs tant que l'exemple de code est en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="cff69-120">You cannot add counters until the sample code is running.</span></span>  
  
2. <span data-ttu-id="cff69-121">Supprimez les compteurs de performance répertoriés en les sélectionnant et en appuyant sur la touche Suppr.</span><span class="sxs-lookup"><span data-stu-id="cff69-121">Remove the performance counters that are listed by selecting them and pressing the Delete key.</span></span>  
  
3. <span data-ttu-id="cff69-122">Ajoutez des compteurs WCF en cliquant à droite sur le volet graphique et en sélectionnant **add Counters**.</span><span class="sxs-lookup"><span data-stu-id="cff69-122">Add WCF counters by right-clicking the graph pane and selecting **Add Counters**.</span></span> <span data-ttu-id="cff69-123">Dans la boîte de dialogue **Add Counters,** sélectionnez **ServiceModelOperation 3.0.0.0, ServiceModelEndpoint 3.0.0.0, ou ServiceModelService 3.0.0.0** dans la boîte de liste de chute de l’objet Performance.</span><span class="sxs-lookup"><span data-stu-id="cff69-123">In the **Add Counters** dialog box, select **ServiceModelOperation 3.0.0.0, ServiceModelEndpoint 3.0.0.0, or ServiceModelService 3.0.0.0** in the Performance object drop down list box.</span></span> <span data-ttu-id="cff69-124">Sélectionnez les compteurs que vous souhaitez afficher dans la liste.</span><span class="sxs-lookup"><span data-stu-id="cff69-124">Select the counters you want to view from the list.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="cff69-125">Il n’y a pas de compteurs de performance WCF pour un service s’il n’y a pas de services WCF en cours d’exécution sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="cff69-125">There are no WCF performance counters for a service if there are no WCF services running on the computer.</span></span>  
  
### <a name="to-use-the-configuration-editor-to-enable-counters"></a><span data-ttu-id="cff69-126">Pour utiliser l'Éditeur de configuration afin d'activer des compteurs</span><span class="sxs-lookup"><span data-stu-id="cff69-126">To use the Configuration Editor to enable counters</span></span>  
  
1. <span data-ttu-id="cff69-127">Ouvrez une instance de SvcConfigEditor.exe.</span><span class="sxs-lookup"><span data-stu-id="cff69-127">Open an instance of the SvcConfigEditor.exe.</span></span>  
  
2. <span data-ttu-id="cff69-128">Sur le menu Du fichier, cliquez sur **Open** puis cliquez sur **le fichier Config...**.</span><span class="sxs-lookup"><span data-stu-id="cff69-128">On the File menu, click **Open** and then click **Config file…**.</span></span>  
  
3. <span data-ttu-id="cff69-129">Naviguez jusqu'au dossier de service de l'exemple d'application et ouvrez le fichier Web.config.</span><span class="sxs-lookup"><span data-stu-id="cff69-129">Navigate to the sample application's service folder and open the Web.config file.</span></span>  
  
4. <span data-ttu-id="cff69-130">Cliquez sur **Diagnostics** sur l’arbre Configuration.</span><span class="sxs-lookup"><span data-stu-id="cff69-130">Click **Diagnostics** on the Configuration tree.</span></span>  
  
5. <span data-ttu-id="cff69-131">**Basculez le compteur de performance** dans la fenêtre **Diagnostics** pour montrer 'All'.</span><span class="sxs-lookup"><span data-stu-id="cff69-131">Toggle **Performance Counter** in the **Diagnostics** window to show 'All'.</span></span>  
  
6. <span data-ttu-id="cff69-132">Enregistrez le fichier de configuration et quittez l'éditeur.</span><span class="sxs-lookup"><span data-stu-id="cff69-132">Save the configuration file and exit the editor.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="cff69-133">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="cff69-133">The samples may already be installed on your computer.</span></span> <span data-ttu-id="cff69-134">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="cff69-134">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="cff69-135">Si ce répertoire n’existe pas, rendez-vous sur [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) Samples pour .NET Framework 4 pour](https://www.microsoft.com/download/details.aspx?id=21459) télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] des échantillons.</span><span class="sxs-lookup"><span data-stu-id="cff69-135">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="cff69-136">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="cff69-136">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\PerfCounters`  
  
## <a name="see-also"></a><span data-ttu-id="cff69-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cff69-137">See also</span></span>

- <span data-ttu-id="cff69-138">[Exemples d'analyse AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="cff69-138">[AppFabric Monitoring Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span></span>

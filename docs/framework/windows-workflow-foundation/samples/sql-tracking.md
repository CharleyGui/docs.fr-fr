---
title: Suivi SQL
ms.date: 03/30/2017
ms.assetid: bcaebeb1-b9e5-49e8-881b-e49af66fd341
ms.openlocfilehash: 24cc484bf11d7cedab949d61c63f805a28a9f849
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70038053"
---
# <a name="sql-tracking"></a><span data-ttu-id="5ad95-102">Suivi SQL</span><span class="sxs-lookup"><span data-stu-id="5ad95-102">SQL Tracking</span></span>
<span data-ttu-id="5ad95-103">Cet exemple montre comment écrire un participant de suivi SQL personnalisé, qui écrit des enregistrements de suivi dans une base de données SQL.</span><span class="sxs-lookup"><span data-stu-id="5ad95-103">This sample demonstrates how to write a custom SQL tracking participant, that writes tracking records to a SQL database.</span></span> <span data-ttu-id="5ad95-104">Windows Workflow Foundation (WF) fournit le suivi de workflow pour obtenir une visibilité sur l’exécution d’une instance de Workflow.</span><span class="sxs-lookup"><span data-stu-id="5ad95-104">Windows Workflow Foundation (WF) provides workflow tracking to gain visibility into the execution of a workflow instance.</span></span> <span data-ttu-id="5ad95-105">Le runtime de suivi émet des enregistrements de suivi de workflow lors de l'exécution du workflow.</span><span class="sxs-lookup"><span data-stu-id="5ad95-105">The tracking runtime emits workflow tracking records during the execution of the workflow.</span></span> <span data-ttu-id="5ad95-106">Pour plus d’informations sur le suivi de workflow, consultez [suivi et traçage de workflow](../workflow-tracking-and-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="5ad95-106">For more information about workflow tracking, see [Workflow Tracking and Tracing](../workflow-tracking-and-tracing.md).</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="5ad95-107">Pour utiliser cet exemple</span><span class="sxs-lookup"><span data-stu-id="5ad95-107">To use this sample</span></span>

1. <span data-ttu-id="5ad95-108">Vérifiez que vous disposez de SQL Server 2008, SQL Server 2008 Express ou version plus récente.</span><span class="sxs-lookup"><span data-stu-id="5ad95-108">Verify you have SQL Server 2008, SQL Server 2008 Express or newer installed.</span></span> <span data-ttu-id="5ad95-109">Les scripts fournis avec l'exemple supposent l'utilisation d'une instance SQL Express sur votre ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="5ad95-109">The scripts packaged with the sample assume the use of a SQL Express instance on your local computer.</span></span> <span data-ttu-id="5ad95-110">Si vous avez une instance différente, modifiez les scripts liés à la base de données avant d'exécuter l'exemple.</span><span class="sxs-lookup"><span data-stu-id="5ad95-110">If you have a different instance please modify the database-related scripts before running the sample.</span></span>

2. <span data-ttu-id="5ad95-111">Créez la base de données de suivi SQL Server en exécutant Trackingsetup.cmd dans le répertoire de scripts (\WF\Basic\Tracking\SqlTracking\CS\Scripts).</span><span class="sxs-lookup"><span data-stu-id="5ad95-111">Create the SQL Server tracking database by running Trackingsetup.cmd in the scripts directory (\WF\Basic\Tracking\SqlTracking\CS\Scripts).</span></span> <span data-ttu-id="5ad95-112">Cela crée une base de données appelée TrackingSample.</span><span class="sxs-lookup"><span data-stu-id="5ad95-112">This creates a database called TrackingSample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="5ad95-113">Le script crée la base de données sur l'instance par défaut de SQL Express.</span><span class="sxs-lookup"><span data-stu-id="5ad95-113">The script creates the database on the default instance of SQL Express.</span></span> <span data-ttu-id="5ad95-114">Si vous souhaitez l'installer sur une instance de base de données différente, modifiez le script Trackingsetup.cmd.</span><span class="sxs-lookup"><span data-stu-id="5ad95-114">If you want to install it on a different database instance, edit the Trackingsetup.cmd script.</span></span>  
  
3. <span data-ttu-id="5ad95-115">Ouvrez SqlTrackingSample. sln dans Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="5ad95-115">Open SqlTrackingSample.sln in Visual Studio 2010.</span></span>  
  
4. <span data-ttu-id="5ad95-116">Appuyez sur Ctrl+Maj+B pour générer la solution.</span><span class="sxs-lookup"><span data-stu-id="5ad95-116">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
5. <span data-ttu-id="5ad95-117">Appuyez sur F5 pour exécuter l'application.</span><span class="sxs-lookup"><span data-stu-id="5ad95-117">Press F5 to run the application.</span></span>  
  
     <span data-ttu-id="5ad95-118">La fenêtre du navigateur s'ouvre et affiche la liste des répertoires pour l'application.</span><span class="sxs-lookup"><span data-stu-id="5ad95-118">The browser window opens and shows the directory listing for the application.</span></span>  
  
6. <span data-ttu-id="5ad95-119">Dans le navigateur, cliquez sur StockPriceService.xamlx.</span><span class="sxs-lookup"><span data-stu-id="5ad95-119">In the browser, click StockPriceService.xamlx.</span></span>  
  
7. <span data-ttu-id="5ad95-120">Le navigateur affiche la page StockPriceService, laquelle contient l'adresse WSDL du service local.</span><span class="sxs-lookup"><span data-stu-id="5ad95-120">The browser displays the StockPriceService page, which contains the local service WSDL address.</span></span> <span data-ttu-id="5ad95-121">Copiez cette adresse.</span><span class="sxs-lookup"><span data-stu-id="5ad95-121">Copy this address.</span></span>  
  
     <span data-ttu-id="5ad95-122">Un exemple de l’adresse WSDL du service local `http://localhost:65193/StockPriceService.xamlx?wsdl`est.</span><span class="sxs-lookup"><span data-stu-id="5ad95-122">An example of the local service WSDL address is `http://localhost:65193/StockPriceService.xamlx?wsdl`.</span></span>  
  
8. <span data-ttu-id="5ad95-123">À l’aide de l’Explorateur de fichiers, exécutez le client test WCF (WcfTestClient. exe).</span><span class="sxs-lookup"><span data-stu-id="5ad95-123">Using File Explorer, run the WCF test client (WcfTestClient.exe).</span></span> <span data-ttu-id="5ad95-124">Il se trouve dans le répertoire Microsoft Visual Studio 10.0\Common7\IDE.</span><span class="sxs-lookup"><span data-stu-id="5ad95-124">It is located in the Microsoft Visual Studio 10.0\Common7\IDE directory.</span></span>  
  
9. <span data-ttu-id="5ad95-125">Dans le client test WCF, cliquez sur le menu **fichier** et sélectionnez **Ajouter un service**.</span><span class="sxs-lookup"><span data-stu-id="5ad95-125">In the WCF test client, click the **File** menu and select **Add Service**.</span></span> <span data-ttu-id="5ad95-126">Collez l'adresse du service local dans la zone de texte.</span><span class="sxs-lookup"><span data-stu-id="5ad95-126">Paste the local service address in the textbox.</span></span> <span data-ttu-id="5ad95-127">Cliquez sur **OK** pour fermer la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="5ad95-127">Click **OK** to close the dialog.</span></span>  
  
10. <span data-ttu-id="5ad95-128">Dans le client test WCF, double-cliquez sur **GetStockPrice**.</span><span class="sxs-lookup"><span data-stu-id="5ad95-128">In the WCF test client, double click **GetStockPrice**.</span></span> <span data-ttu-id="5ad95-129">Cela ouvre l' `GetStockPrice` opération qui accepte un paramètre, tapez la valeur `Contoso` et cliquez sur **appeler**.</span><span class="sxs-lookup"><span data-stu-id="5ad95-129">This opens the `GetStockPrice` operation that takes one parameter, type in the value `Contoso` and click **Invoke**.</span></span>  
  
11. <span data-ttu-id="5ad95-130">Les enregistrements de suivi émis sont écrits dans une base de données SQL.</span><span class="sxs-lookup"><span data-stu-id="5ad95-130">The emitted tracking records are written to a SQL database.</span></span> <span data-ttu-id="5ad95-131">Pour afficher les enregistrements de suivi, ouvrez la base de données TrackingSample dans SQL Management Studio et naviguez jusqu'aux tables.</span><span class="sxs-lookup"><span data-stu-id="5ad95-131">To view the tracking records, open the TrackingSample database in SQL Management Studio and navigate to the tables.</span></span> <span data-ttu-id="5ad95-132">Pour plus d’informations sur la SQL Server Management Studio, consultez [Présentation des SQL Server Management Studio](https://go.microsoft.com/fwlink/?LinkId=165645).</span><span class="sxs-lookup"><span data-stu-id="5ad95-132">For more information about SQL Server Management Studio, see [Introducing SQL Server Management Studio](https://go.microsoft.com/fwlink/?LinkId=165645).</span></span> <span data-ttu-id="5ad95-133">SQL Server 2008 Management Studio Express peut être téléchargé [ici](https://go.microsoft.com/fwlink/?LinkId=180520).</span><span class="sxs-lookup"><span data-stu-id="5ad95-133">SQL Server 2008 Management Studio Express can be downloaded [here](https://go.microsoft.com/fwlink/?LinkId=180520).</span></span> <span data-ttu-id="5ad95-134">L'exécution d'une requête Sélection dans les tables affiche les données dans les enregistrements de suivi stockés dans les tables respectives.</span><span class="sxs-lookup"><span data-stu-id="5ad95-134">Running a select query on the tables displays the data within the tracking records stored in the respective tables.</span></span>  
  
#### <a name="to-uninstall-the-sample"></a><span data-ttu-id="5ad95-135">Pour désinstaller l'exemple</span><span class="sxs-lookup"><span data-stu-id="5ad95-135">To uninstall the sample</span></span>  
  
1. <span data-ttu-id="5ad95-136">Exécutez le script Trackingcleanup.cmd dans le répertoire de l'exemple (\WF\Basic\Tracking\SqlTracking).</span><span class="sxs-lookup"><span data-stu-id="5ad95-136">Run theTrackingcleanup.cmd script in the sample directory (\WF\Basic\Tracking\SqlTracking).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="5ad95-137">Trackingcleanup.cmd essaie de supprimer la base de données de votre ordinateur local SQL Express.</span><span class="sxs-lookup"><span data-stu-id="5ad95-137">The Trackingcleanup.cmd attempts to delete the database in your local computer SQL Express.</span></span> <span data-ttu-id="5ad95-138">Si vous utilisez une autre instance SQL Server, modifiez Trackingcleanup.cmd.</span><span class="sxs-lookup"><span data-stu-id="5ad95-138">If you are using another SQL server instance, edit Trackingcleanup.cmd.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5ad95-139">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="5ad95-139">The samples may already be installed on your computer.</span></span> <span data-ttu-id="5ad95-140">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="5ad95-140">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="5ad95-141">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples Windows Communication Foundation (WCF [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ) et.</span><span class="sxs-lookup"><span data-stu-id="5ad95-141">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5ad95-142">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="5ad95-142">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\SqlTracking`  
  
## <a name="see-also"></a><span data-ttu-id="5ad95-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5ad95-143">See also</span></span>

- [<span data-ttu-id="5ad95-144">Exemples de surveillance AppFabric</span><span class="sxs-lookup"><span data-stu-id="5ad95-144">AppFabric Monitoring Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193959)

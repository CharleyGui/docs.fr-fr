---
title: Téléchargement d'exemples de base de données (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: eb42a7af-d410-4b7f-b4a8-13c72ce6fd09
ms.openlocfilehash: 340ccd1e0e2d415fe60721775bd39acf9db00f85
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67504500"
---
# <a name="downloading-sample-databases-linq-to-dataset"></a><span data-ttu-id="f956e-102">Téléchargement d'exemples de base de données (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="f956e-102">Downloading Sample Databases (LINQ to DataSet)</span></span>
<span data-ttu-id="f956e-103">Les procédures pas à pas dans le LINQ to DataSet documentation et les exemples utilisent la base de données AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="f956e-103">The samples and walkthroughs in the LINQ to DataSet documentation use the AdventureWorks sample database.</span></span> <span data-ttu-id="f956e-104">Vous pouvez télécharger ce produit gratuitement à partir du site de téléchargement Microsoft.</span><span class="sxs-lookup"><span data-stu-id="f956e-104">You can download this product free of charge from the Microsoft download site.</span></span> <span data-ttu-id="f956e-105">Les exemples et les procédures pas à pas dans le LINQ to DataSet documentation utilisent SQL Server comme magasin de données.</span><span class="sxs-lookup"><span data-stu-id="f956e-105">The samples and walkthroughs in the LINQ to DataSet documentation use SQL Server as the data store.</span></span> <span data-ttu-id="f956e-106">SQL Server Express Edition, disponible gratuitement, peut également être utilisé comme magasin de données à la place de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="f956e-106">SQL Server Express Edition, which is available without charge, can also be used as the data store instead of SQL Server.</span></span>  
  
## <a name="downloading-and-installing-the-adventureworks-database"></a><span data-ttu-id="f956e-107">Téléchargement et installation de la base de données AdventureWorks</span><span class="sxs-lookup"><span data-stu-id="f956e-107">Downloading and Installing the AdventureWorks Database</span></span>  
  
#### <a name="to-download-and-install-the-adventureworks-sample-database-for-sql-server"></a><span data-ttu-id="f956e-108">Pour télécharger et installer l'exemple de base de données AdventureWorks pour SQL Server</span><span class="sxs-lookup"><span data-stu-id="f956e-108">To download and install the AdventureWorks sample database for SQL Server</span></span>  
  
1. <span data-ttu-id="f956e-109">Ouvrez Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="f956e-109">Open Internet Explorer.</span></span>  
  
2. <span data-ttu-id="f956e-110">Accédez à la [exemples SQL Server 2005 et les bases de données exemple](https://go.microsoft.com/fwlink/?linkid=31046) site Web.</span><span class="sxs-lookup"><span data-stu-id="f956e-110">Go to the [SQL Server 2005 Samples and Sample Databases](https://go.microsoft.com/fwlink/?linkid=31046) Web site.</span></span>  
  
3. <span data-ttu-id="f956e-111">Suivez les instructions pour télécharger l'exemple de base de données AdventureWorks pour votre type de processeur (AdventureWorksDB.msi par exemple), et enregistrez le fichier .MSI sur votre ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="f956e-111">Follow the instructions for downloading the AdventureWorks sample database for your processor type (such as AdventureWorksDB.msi), and save the .MSI file to your local computer.</span></span>  
  
4. <span data-ttu-id="f956e-112">Si vous disposez d'une version précédente de la base de données AdventureWorks installée à partir du téléchargement ou pendant la configuration de SQL Server, vous devez la supprimer avant d'exécuter AdventureWorks.msi.</span><span class="sxs-lookup"><span data-stu-id="f956e-112">If you have a previous version of AdventureWorks installed from the download or during the SQL Server setup, you must remove it before running AdventureWorks.msi.</span></span>  
  
#### <a name="to-remove-a-previous-download-of-an-adventureworks-sample-database"></a><span data-ttu-id="f956e-113">Pour supprimer un téléchargement précédent d'un exemple de base de données AdventureWorks</span><span class="sxs-lookup"><span data-stu-id="f956e-113">To remove a previous download of an AdventureWorks sample database</span></span>  
  
1. <span data-ttu-id="f956e-114">Abandonnez la base de données AdventureWorks ou AdventureWorksDW.</span><span class="sxs-lookup"><span data-stu-id="f956e-114">Drop the AdventureWorks or AdventureWorksDW database.</span></span>  
  
2. <span data-ttu-id="f956e-115">À partir de **Ajout / Suppression de programmes**, sélectionnez **AdventureWorksDB** ou **AdventureWorksBI** et cliquez sur **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="f956e-115">From **Add or Remove Programs**, select **AdventureWorksDB** or **AdventureWorksBI** and click **Remove**.</span></span>  
  
#### <a name="to-remove-an-adventureworks-sample-database-previously-installed-using-setup"></a><span data-ttu-id="f956e-116">Pour supprimer un exemple de base de données AdventureWorks précédemment installé à l'aide du programme d'installation</span><span class="sxs-lookup"><span data-stu-id="f956e-116">To remove an AdventureWorks sample database previously installed using Setup</span></span>  
  
1. <span data-ttu-id="f956e-117">Abandonnez la base de données AdventureWorks ou AdventureWorksDW.</span><span class="sxs-lookup"><span data-stu-id="f956e-117">Drop the AdventureWorks or AdventureWorksDW database.</span></span>  
  
2. <span data-ttu-id="f956e-118">À partir de **Ajout / Suppression de programmes**, sélectionnez **Microsoft SQL Server 2005** et cliquez sur **modification**.</span><span class="sxs-lookup"><span data-stu-id="f956e-118">From **Add or Remove Programs**, select **Microsoft SQL Server 2005** and click **Change**.</span></span>  
  
3. <span data-ttu-id="f956e-119">À partir de **sélection des composants**, sélectionnez **composants de station de travail** puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="f956e-119">From **Component Selection**, select **Workstation Components** and then click **Next**.</span></span>  
  
4. <span data-ttu-id="f956e-120">À partir de **Bienvenue dans l’Assistant Installation de SQL Server**, cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="f956e-120">From **Welcome to the SQL Server Installation Wizard**, click **Next**.</span></span>  
  
5. <span data-ttu-id="f956e-121">À partir de **System Configuration Check**, cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="f956e-121">From **System Configuration Check**, click **Next**.</span></span>  
  
6. <span data-ttu-id="f956e-122">À partir de **changer ou supprimer l’Instance**, cliquez sur **changer les composants installés**.</span><span class="sxs-lookup"><span data-stu-id="f956e-122">From **Change or Remove Instance**, click **Change Installed Components**.</span></span>  
  
7. <span data-ttu-id="f956e-123">À partir de **sélection des fonctionnalités**, développez le **Documentation, exemples et exemples de bases de données** nœud.</span><span class="sxs-lookup"><span data-stu-id="f956e-123">From **Feature Selection**, expand the **Documentation, Samples, and Sample Databases** node.</span></span>  
  
8. <span data-ttu-id="f956e-124">Sélectionnez **exemple de Code et des Applications**.</span><span class="sxs-lookup"><span data-stu-id="f956e-124">Select **Sample Code and Applications**.</span></span> <span data-ttu-id="f956e-125">Développez **Sample Databases**, sélectionnez la base de données à supprimer, puis sélectionnez **totalité de cette fonctionnalité n’est pas disponible**.</span><span class="sxs-lookup"><span data-stu-id="f956e-125">Expand **Sample Databases**, select the sample database to be removed, and select **Entire feature will be unavailable**.</span></span> <span data-ttu-id="f956e-126">Cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="f956e-126">Click **Next**.</span></span>  
  
9. <span data-ttu-id="f956e-127">Cliquez sur **installer** et terminez l’Assistant installation.</span><span class="sxs-lookup"><span data-stu-id="f956e-127">Click **Install** and finish the installation wizard.</span></span>  
  
#### <a name="to-attach-the-adventureworks-sample-database-files-to-an-instance-of-sql-server"></a><span data-ttu-id="f956e-128">Pour attacher les fichiers de l'exemple de base de données AdventureWorks à une instance de SQL Server</span><span class="sxs-lookup"><span data-stu-id="f956e-128">To attach the AdventureWorks sample database files to an instance of SQL Server</span></span>  
  
1. <span data-ttu-id="f956e-129">Une fois le fichier de programme d’installation de base de données exemple fichier téléchargé, double-cliquez sur le **AdventureWorksDB.msi** fichier (ou le fichier que vous avez téléchargé) pour installer la base de données.</span><span class="sxs-lookup"><span data-stu-id="f956e-129">After the file sample database installer file has downloaded, double-click the **AdventureWorksDB.msi** file (or the file you downloaded) to install the database.</span></span> <span data-ttu-id="f956e-130">Par défaut, la base de données est installée dans c:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data.</span><span class="sxs-lookup"><span data-stu-id="f956e-130">By default, the database is installed at c:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data.</span></span>  
  
2. <span data-ttu-id="f956e-131">Attachez les fichiers de la base de données AdventureWorks à une instance de SQL Server en exécutant le script suivant à l'aide de SQLCMD ou SQL Server Management Studio :</span><span class="sxs-lookup"><span data-stu-id="f956e-131">Attach the AdventureWorks database files to an instance of SQL Server by executing the following script SQLCMD or SQL Server Management Studio:</span></span>  
  
    ```sql
    exec sp_attach_db @dbname=N'AdventureWorks', @filename1=N'C:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data\AdventureWorks_Data.mdf', @filename2=N'C:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data\AdventureWorks_log.ldf'  
    ```  
  
     <span data-ttu-id="f956e-132">Si vous avez installé ces fichiers dans un lecteur ou un répertoire différent, vous devez modifier les chemins en conséquence avant d’exécuter la procédure stockée `sp_attach_db`.</span><span class="sxs-lookup"><span data-stu-id="f956e-132">If you have installed these files to a different drive or directory, you must revise the paths appropriately before you execute the `sp_attach_db` stored procedure.</span></span>  
  
## <a name="downloading-sql-server-express-edition"></a><span data-ttu-id="f956e-133">Téléchargement de SQL Server Express Edition</span><span class="sxs-lookup"><span data-stu-id="f956e-133">Downloading SQL Server Express Edition</span></span>  
 <span data-ttu-id="f956e-134">Les exemples et les procédures pas à pas dans le LINQ to DataSet section utiliser SQL Server 2005 comme magasin de données, mais peut être modifié pour utiliser SQL Server Express Edition, à la place.</span><span class="sxs-lookup"><span data-stu-id="f956e-134">The samples and walkthroughs in the LINQ to DataSet section use SQL Server 2005 as the data store but can be modified to use SQL Server Express Edition, instead.</span></span> <span data-ttu-id="f956e-135">SQL Server Express Edition est disponible gratuitement et vous pouvez le redistribuer avec les applications.</span><span class="sxs-lookup"><span data-stu-id="f956e-135">SQL Server Express Edition is available without charge, and you can redistribute it with applications.</span></span> <span data-ttu-id="f956e-136">Si vous utilisez Visual Studio, SQL Server Express Edition est incluse dans les éditions professionnelles et ultérieures.</span><span class="sxs-lookup"><span data-stu-id="f956e-136">If you are using Visual Studio, SQL Server Express Edition is included in the Pro and higher editions.</span></span>  
  
#### <a name="to-download-and-install-sql-server-express-edition"></a><span data-ttu-id="f956e-137">Pour télécharger et installer SQL Server Express Edition</span><span class="sxs-lookup"><span data-stu-id="f956e-137">To download and install SQL Server Express Edition</span></span>  
  
1. <span data-ttu-id="f956e-138">Démarrez Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="f956e-138">Start Internet Explorer.</span></span>  
  
2. <span data-ttu-id="f956e-139">Accédez à la [Microsoft SQL Server 2005 Express Edition](https://go.microsoft.com/fwlink/?LinkID=31070) page de téléchargement.</span><span class="sxs-lookup"><span data-stu-id="f956e-139">Go to the  [Microsoft SQL Server 2005 Express Edition](https://go.microsoft.com/fwlink/?LinkID=31070) download page.</span></span>  
  
3. <span data-ttu-id="f956e-140">Suivez les instructions d’installation indiquées sur le site web.</span><span class="sxs-lookup"><span data-stu-id="f956e-140">Follow the installation instructions on the Web site.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f956e-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f956e-141">See also</span></span>

- [<span data-ttu-id="f956e-142">Prise en main</span><span class="sxs-lookup"><span data-stu-id="f956e-142">Getting Started</span></span>](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)

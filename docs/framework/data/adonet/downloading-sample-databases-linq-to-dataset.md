---
title: Téléchargement d'exemples de base de données (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: eb42a7af-d410-4b7f-b4a8-13c72ce6fd09
ms.openlocfilehash: c67ee699cf594f476a728c7345b47b0c32dea7ff
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795181"
---
# <a name="downloading-sample-databases-linq-to-dataset"></a><span data-ttu-id="27bc2-102">Téléchargement d'exemples de base de données (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="27bc2-102">Downloading Sample Databases (LINQ to DataSet)</span></span>
<span data-ttu-id="27bc2-103">Les exemples et les procédures pas à pas de la documentation LINQ to DataSet utilisent l’exemple de base de données AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="27bc2-103">The samples and walkthroughs in the LINQ to DataSet documentation use the AdventureWorks sample database.</span></span> <span data-ttu-id="27bc2-104">Vous pouvez télécharger ce produit gratuitement à partir du site de téléchargement Microsoft.</span><span class="sxs-lookup"><span data-stu-id="27bc2-104">You can download this product free of charge from the Microsoft download site.</span></span> <span data-ttu-id="27bc2-105">Les exemples et les procédures pas à pas de la documentation LINQ to DataSet utilisent SQL Server comme magasin de données.</span><span class="sxs-lookup"><span data-stu-id="27bc2-105">The samples and walkthroughs in the LINQ to DataSet documentation use SQL Server as the data store.</span></span> <span data-ttu-id="27bc2-106">SQL Server Express Edition, disponible gratuitement, peut également être utilisé comme magasin de données à la place de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="27bc2-106">SQL Server Express Edition, which is available without charge, can also be used as the data store instead of SQL Server.</span></span>  
  
## <a name="downloading-and-installing-the-adventureworks-database"></a><span data-ttu-id="27bc2-107">Téléchargement et installation de la base de données AdventureWorks</span><span class="sxs-lookup"><span data-stu-id="27bc2-107">Downloading and Installing the AdventureWorks Database</span></span>  
  
#### <a name="to-download-and-install-the-adventureworks-sample-database-for-sql-server"></a><span data-ttu-id="27bc2-108">Pour télécharger et installer l'exemple de base de données AdventureWorks pour SQL Server</span><span class="sxs-lookup"><span data-stu-id="27bc2-108">To download and install the AdventureWorks sample database for SQL Server</span></span>  
  
1. <span data-ttu-id="27bc2-109">Ouvrez Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="27bc2-109">Open Internet Explorer.</span></span>  
  
2. <span data-ttu-id="27bc2-110">Accédez au site Web des [exemples SQL Server 2005 et des exemples de bases de données](https://go.microsoft.com/fwlink/?linkid=31046) .</span><span class="sxs-lookup"><span data-stu-id="27bc2-110">Go to the [SQL Server 2005 Samples and Sample Databases](https://go.microsoft.com/fwlink/?linkid=31046) Web site.</span></span>  
  
3. <span data-ttu-id="27bc2-111">Suivez les instructions pour télécharger l'exemple de base de données AdventureWorks pour votre type de processeur (AdventureWorksDB.msi par exemple), et enregistrez le fichier .MSI sur votre ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="27bc2-111">Follow the instructions for downloading the AdventureWorks sample database for your processor type (such as AdventureWorksDB.msi), and save the .MSI file to your local computer.</span></span>  
  
4. <span data-ttu-id="27bc2-112">Si vous disposez d'une version précédente de la base de données AdventureWorks installée à partir du téléchargement ou pendant la configuration de SQL Server, vous devez la supprimer avant d'exécuter AdventureWorks.msi.</span><span class="sxs-lookup"><span data-stu-id="27bc2-112">If you have a previous version of AdventureWorks installed from the download or during the SQL Server setup, you must remove it before running AdventureWorks.msi.</span></span>  
  
#### <a name="to-remove-a-previous-download-of-an-adventureworks-sample-database"></a><span data-ttu-id="27bc2-113">Pour supprimer un téléchargement précédent d'un exemple de base de données AdventureWorks</span><span class="sxs-lookup"><span data-stu-id="27bc2-113">To remove a previous download of an AdventureWorks sample database</span></span>  
  
1. <span data-ttu-id="27bc2-114">Abandonnez la base de données AdventureWorks ou AdventureWorksDW.</span><span class="sxs-lookup"><span data-stu-id="27bc2-114">Drop the AdventureWorks or AdventureWorksDW database.</span></span>  
  
2. <span data-ttu-id="27bc2-115">Dans **Ajout/suppression de programmes**, sélectionnez **AdventureWorksDB** ou **AdventureWorksBI** , puis cliquez sur **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="27bc2-115">From **Add or Remove Programs**, select **AdventureWorksDB** or **AdventureWorksBI** and click **Remove**.</span></span>  
  
#### <a name="to-remove-an-adventureworks-sample-database-previously-installed-using-setup"></a><span data-ttu-id="27bc2-116">Pour supprimer un exemple de base de données AdventureWorks précédemment installé à l'aide du programme d'installation</span><span class="sxs-lookup"><span data-stu-id="27bc2-116">To remove an AdventureWorks sample database previously installed using Setup</span></span>  
  
1. <span data-ttu-id="27bc2-117">Abandonnez la base de données AdventureWorks ou AdventureWorksDW.</span><span class="sxs-lookup"><span data-stu-id="27bc2-117">Drop the AdventureWorks or AdventureWorksDW database.</span></span>  
  
2. <span data-ttu-id="27bc2-118">Dans **Ajout/suppression de programmes**, sélectionnez **Microsoft SQL Server 2005** , puis cliquez sur **modifier**.</span><span class="sxs-lookup"><span data-stu-id="27bc2-118">From **Add or Remove Programs**, select **Microsoft SQL Server 2005** and click **Change**.</span></span>  
  
3. <span data-ttu-id="27bc2-119">Dans **sélection du composant**, sélectionnez composants de la **station de travail** , puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="27bc2-119">From **Component Selection**, select **Workstation Components** and then click **Next**.</span></span>  
  
4. <span data-ttu-id="27bc2-120">Dans **la page Bienvenue dans l’Assistant Installation de SQL Server**, cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="27bc2-120">From **Welcome to the SQL Server Installation Wizard**, click **Next**.</span></span>  
  
5. <span data-ttu-id="27bc2-121">Dans **vérification de la configuration système**, cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="27bc2-121">From **System Configuration Check**, click **Next**.</span></span>  
  
6. <span data-ttu-id="27bc2-122">Dans **modifier ou supprimer l’instance**, cliquez sur **modifier les composants installés**.</span><span class="sxs-lookup"><span data-stu-id="27bc2-122">From **Change or Remove Instance**, click **Change Installed Components**.</span></span>  
  
7. <span data-ttu-id="27bc2-123">Dans **sélection de fonctionnalités**, développez le nœud **documentation, exemples et exemples de bases de données** .</span><span class="sxs-lookup"><span data-stu-id="27bc2-123">From **Feature Selection**, expand the **Documentation, Samples, and Sample Databases** node.</span></span>  
  
8. <span data-ttu-id="27bc2-124">Sélectionnez **exemple de code et d’applications**.</span><span class="sxs-lookup"><span data-stu-id="27bc2-124">Select **Sample Code and Applications**.</span></span> <span data-ttu-id="27bc2-125">Développez **exemples de bases de données**, sélectionnez l’exemple de base de données à supprimer, puis sélectionnez la **fonctionnalité tout entière n’est pas disponible**.</span><span class="sxs-lookup"><span data-stu-id="27bc2-125">Expand **Sample Databases**, select the sample database to be removed, and select **Entire feature will be unavailable**.</span></span> <span data-ttu-id="27bc2-126">Cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="27bc2-126">Click **Next**.</span></span>  
  
9. <span data-ttu-id="27bc2-127">Cliquez sur **installer** , puis terminez l’Assistant installation.</span><span class="sxs-lookup"><span data-stu-id="27bc2-127">Click **Install** and finish the installation wizard.</span></span>  
  
#### <a name="to-attach-the-adventureworks-sample-database-files-to-an-instance-of-sql-server"></a><span data-ttu-id="27bc2-128">Pour attacher les fichiers de l'exemple de base de données AdventureWorks à une instance de SQL Server</span><span class="sxs-lookup"><span data-stu-id="27bc2-128">To attach the AdventureWorks sample database files to an instance of SQL Server</span></span>  
  
1. <span data-ttu-id="27bc2-129">Une fois le fichier d’installation de la base de données exemple téléchargé, double-cliquez sur le fichier **AdventureWorksDB. msi** (ou le fichier que vous avez téléchargé) pour installer la base de données.</span><span class="sxs-lookup"><span data-stu-id="27bc2-129">After the file sample database installer file has downloaded, double-click the **AdventureWorksDB.msi** file (or the file you downloaded) to install the database.</span></span> <span data-ttu-id="27bc2-130">Par défaut, la base de données est installée dans c:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data.</span><span class="sxs-lookup"><span data-stu-id="27bc2-130">By default, the database is installed at c:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data.</span></span>  
  
2. <span data-ttu-id="27bc2-131">Attachez les fichiers de la base de données AdventureWorks à une instance de SQL Server en exécutant le script suivant à l'aide de SQLCMD ou SQL Server Management Studio :</span><span class="sxs-lookup"><span data-stu-id="27bc2-131">Attach the AdventureWorks database files to an instance of SQL Server by executing the following script SQLCMD or SQL Server Management Studio:</span></span>  
  
    ```sql
    exec sp_attach_db @dbname=N'AdventureWorks', @filename1=N'C:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data\AdventureWorks_Data.mdf', @filename2=N'C:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data\AdventureWorks_log.ldf'  
    ```  
  
     <span data-ttu-id="27bc2-132">Si vous avez installé ces fichiers dans un lecteur ou un répertoire différent, vous devez modifier les chemins en conséquence avant d’exécuter la procédure stockée `sp_attach_db`.</span><span class="sxs-lookup"><span data-stu-id="27bc2-132">If you have installed these files to a different drive or directory, you must revise the paths appropriately before you execute the `sp_attach_db` stored procedure.</span></span>  
  
## <a name="downloading-sql-server-express-edition"></a><span data-ttu-id="27bc2-133">Téléchargement de SQL Server Express Edition</span><span class="sxs-lookup"><span data-stu-id="27bc2-133">Downloading SQL Server Express Edition</span></span>  
 <span data-ttu-id="27bc2-134">Les exemples et les procédures pas à pas de la section LINQ to DataSet utilisent SQL Server 2005 comme magasin de données, mais ils peuvent être modifiés pour utiliser SQL Server Express Edition, à la place.</span><span class="sxs-lookup"><span data-stu-id="27bc2-134">The samples and walkthroughs in the LINQ to DataSet section use SQL Server 2005 as the data store but can be modified to use SQL Server Express Edition, instead.</span></span> <span data-ttu-id="27bc2-135">SQL Server Express Edition est disponible gratuitement et vous pouvez le redistribuer avec les applications.</span><span class="sxs-lookup"><span data-stu-id="27bc2-135">SQL Server Express Edition is available without charge, and you can redistribute it with applications.</span></span> <span data-ttu-id="27bc2-136">Si vous utilisez Visual Studio, SQL Server Express édition est incluse dans les éditions professionnel et ultérieure.</span><span class="sxs-lookup"><span data-stu-id="27bc2-136">If you are using Visual Studio, SQL Server Express Edition is included in the Pro and higher editions.</span></span>  
  
#### <a name="to-download-and-install-sql-server-express-edition"></a><span data-ttu-id="27bc2-137">Pour télécharger et installer SQL Server Express Edition</span><span class="sxs-lookup"><span data-stu-id="27bc2-137">To download and install SQL Server Express Edition</span></span>  
  
1. <span data-ttu-id="27bc2-138">Démarrez Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="27bc2-138">Start Internet Explorer.</span></span>  
  
2. <span data-ttu-id="27bc2-139">Accédez à la page de téléchargement [Microsoft SQL Server 2005 Express Edition](https://go.microsoft.com/fwlink/?LinkID=31070) .</span><span class="sxs-lookup"><span data-stu-id="27bc2-139">Go to the  [Microsoft SQL Server 2005 Express Edition](https://go.microsoft.com/fwlink/?LinkID=31070) download page.</span></span>  
  
3. <span data-ttu-id="27bc2-140">Suivez les instructions d’installation indiquées sur le site web.</span><span class="sxs-lookup"><span data-stu-id="27bc2-140">Follow the installation instructions on the Web site.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27bc2-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="27bc2-141">See also</span></span>

- [<span data-ttu-id="27bc2-142">Prise en main</span><span class="sxs-lookup"><span data-stu-id="27bc2-142">Getting Started</span></span>](getting-started-linq-to-dataset.md)

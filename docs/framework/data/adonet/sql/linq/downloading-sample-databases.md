---
title: Obtenir l’exemple de base de données SQL Server pour les exemples de code ADO.NET
description: Téléchargez l’exemple de bases de données SQL Server utilisées dans les exemples de code dans la documentation ADO.NET, ainsi que les SQL Server et les outils de gestion
ms.date: 01/11/2019
ms.assetid: ef9d69a1-9461-43fe-94bb-7c836754bcb5
ms.openlocfilehash: 60566041ff4f99e96c9aee052dbcc17b5e5da9e5
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794031"
---
# <a name="get-the-sample-databases-for-adonet-code-samples"></a><span data-ttu-id="59d2b-103">Obtenir les exemples de bases de données pour les exemples de code ADO.NET</span><span class="sxs-lookup"><span data-stu-id="59d2b-103">Get the sample databases for ADO.NET code samples</span></span>

<span data-ttu-id="59d2b-104">Un certain nombre d’exemples et de procédures pas [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] à pas de la documentation utilisent des exemples SQL Server des bases de données et des SQL Server Express.</span><span class="sxs-lookup"><span data-stu-id="59d2b-104">A number of examples and walkthroughs in the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentation use sample SQL Server databases and SQL Server Express.</span></span> <span data-ttu-id="59d2b-105">Vous pouvez télécharger ces produits gratuitement auprès de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="59d2b-105">You can download these products free of charge from Microsoft.</span></span>

## <a name="get-the-northwind-sample-database-for-sql-server"></a><span data-ttu-id="59d2b-106">Obtenir l’exemple de base de données Northwind pour SQL Server</span><span class="sxs-lookup"><span data-stu-id="59d2b-106">Get the Northwind sample database for SQL Server</span></span>

<span data-ttu-id="59d2b-107">Téléchargez le script `instnwnd.sql` à partir du référentiel GitHub suivant pour créer et charger l’exemple de base de données Northwind pour SQL Server :</span><span class="sxs-lookup"><span data-stu-id="59d2b-107">Download the script `instnwnd.sql` from the following GitHub repository to create and load the Northwind sample database for SQL Server:</span></span>

[<span data-ttu-id="59d2b-108">Exemples de bases de données Northwind et pubs pour Microsoft SQL Server</span><span class="sxs-lookup"><span data-stu-id="59d2b-108">Northwind and pubs sample databases for Microsoft SQL Server</span></span>](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs)

<span data-ttu-id="59d2b-109">Avant de pouvoir utiliser la base de données Northwind, vous devez exécuter le `instnwnd.sql` fichier de script téléchargé pour recréer la base de données sur une instance de SQL Server à l’aide de [SQL Server Management Studio](#get_ssms) ou d’un outil similaire.</span><span class="sxs-lookup"><span data-stu-id="59d2b-109">Before you can use the Northwind database, you have to run the downloaded `instnwnd.sql` script file to recreate the database on an instance of SQL Server by using [SQL Server Management Studio](#get_ssms) or a similar tool.</span></span> <span data-ttu-id="59d2b-110">Suivez les instructions du fichier Lisez-moi dans le référentiel.</span><span class="sxs-lookup"><span data-stu-id="59d2b-110">Follow the instructions in the Readme file in the repository.</span></span>

> [!TIP]
> <span data-ttu-id="59d2b-111">Si vous recherchez la base de données Northwind pour Microsoft Access, consultez [installer l’exemple de base de données Northwind pour Microsoft Access](#northwind_access).</span><span class="sxs-lookup"><span data-stu-id="59d2b-111">If you're looking for the Northwind database for Microsoft Access, see [Install the Northwind sample database for Microsoft Access](#northwind_access).</span></span>

## <a name="northwind_access"></a><span data-ttu-id="59d2b-112">Obtenir l’exemple de base de données Northwind pour Microsoft Access</span><span class="sxs-lookup"><span data-stu-id="59d2b-112">Get the Northwind sample database for Microsoft Access</span></span>

<span data-ttu-id="59d2b-113">L’exemple de base de données Northwind pour Microsoft Access n’est pas disponible dans le centre de téléchargement Microsoft.</span><span class="sxs-lookup"><span data-stu-id="59d2b-113">The Northwind sample database for Microsoft Access is not available on the Microsoft Download Center.</span></span> <span data-ttu-id="59d2b-114">Pour installer Northwind directement à partir d’Access, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="59d2b-114">To install Northwind directly from within Access, do the following things:</span></span>

1. <span data-ttu-id="59d2b-115">Ouvrez Access.</span><span class="sxs-lookup"><span data-stu-id="59d2b-115">Open Access.</span></span>

1. <span data-ttu-id="59d2b-116">Entrez **Northwind** dans la zone **Rechercher des modèles en ligne** , puis sélectionnez **entrée**.</span><span class="sxs-lookup"><span data-stu-id="59d2b-116">Enter **Northwind** in the **Search for Online Templates** box, and then select **Enter**.</span></span>

1. <span data-ttu-id="59d2b-117">Dans l’écran résultats, sélectionnez **Northwind**.</span><span class="sxs-lookup"><span data-stu-id="59d2b-117">On the results screen, select **Northwind**.</span></span> <span data-ttu-id="59d2b-118">Une nouvelle fenêtre s’ouvre avec une description de la base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="59d2b-118">A new window opens with a description of the Northwind database.</span></span>

1. <span data-ttu-id="59d2b-119">Dans la nouvelle fenêtre, dans la zone de texte **nom de fichier** , fournissez un nom de fichier pour votre copie de la base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="59d2b-119">In the new window, in the **File Name** text box, provide a filename for your copy of the Northwind database.</span></span>

1. <span data-ttu-id="59d2b-120">Sélectionnez **Créer**.</span><span class="sxs-lookup"><span data-stu-id="59d2b-120">Select **Create**.</span></span> <span data-ttu-id="59d2b-121">Access télécharge la base de données Northwind et prépare le fichier.</span><span class="sxs-lookup"><span data-stu-id="59d2b-121">Access downloads the Northwind database and prepares the file.</span></span>

1. <span data-ttu-id="59d2b-122">Une fois ce processus terminé, la base de données s’ouvre avec un écran d’accueil.</span><span class="sxs-lookup"><span data-stu-id="59d2b-122">When this process is complete, the database opens with a Welcome screen.</span></span>

## <a name="get-the-adventureworks-sample-database-for-sql-server"></a><span data-ttu-id="59d2b-123">Obtenir l’exemple de base de données AdventureWorks pour SQL Server</span><span class="sxs-lookup"><span data-stu-id="59d2b-123">Get the AdventureWorks sample database for SQL Server</span></span>

<span data-ttu-id="59d2b-124">Téléchargez l’exemple de base de données AdventureWorks pour SQL Server à partir du dépôt GitHub suivant :</span><span class="sxs-lookup"><span data-stu-id="59d2b-124">Download the AdventureWorks sample database for SQL Server from the following GitHub repository:</span></span>

[<span data-ttu-id="59d2b-125">Exemples de bases de données AdventureWorks</span><span class="sxs-lookup"><span data-stu-id="59d2b-125">AdventureWorks sample databases</span></span>](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)

<span data-ttu-id="59d2b-126">Après avoir téléchargé l’un des fichiers de sauvegarde\*de base de données (. bak), restaurez la sauvegarde sur une instance de SQL Server à l’aide de SQL Server Management Studio (SSMS).</span><span class="sxs-lookup"><span data-stu-id="59d2b-126">After you download one of the database backup (\*.bak) files, restore the backup to an instance of SQL Server by using SQL Server Management Studio (SSMS).</span></span> <span data-ttu-id="59d2b-127">Consultez [obtenir des SQL Server Management Studio](#get_ssms).</span><span class="sxs-lookup"><span data-stu-id="59d2b-127">See [Get SQL Server Management Studio](#get_ssms).</span></span>

## <a name="get_ssms"></a><span data-ttu-id="59d2b-128">Recevoir SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="59d2b-128">Get SQL Server Management Studio</span></span>
<span data-ttu-id="59d2b-129">Si vous souhaitez afficher ou modifier une base de données que vous avez téléchargée, vous pouvez utiliser SQL Server Management Studio (SSMS).</span><span class="sxs-lookup"><span data-stu-id="59d2b-129">If you want to view or modify a database that you've downloaded, you can use SQL Server Management Studio (SSMS).</span></span> <span data-ttu-id="59d2b-130">Téléchargez SSMS à partir de la page suivante :</span><span class="sxs-lookup"><span data-stu-id="59d2b-130">Download SSMS from the following page:</span></span>

[<span data-ttu-id="59d2b-131">Télécharger SQL Server Management Studio (SSMS)</span><span class="sxs-lookup"><span data-stu-id="59d2b-131">Download SQL Server Management Studio (SSMS)</span></span>](/sql/ssms/download-sql-server-management-studio-ssms) 

<span data-ttu-id="59d2b-132">Vous pouvez également afficher et gérer des bases de données dans l’environnement de développement intégré (IDE) de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="59d2b-132">You can also view and manage databases in the Visual Studio integrated development environment (IDE).</span></span> <span data-ttu-id="59d2b-133">Dans [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), connectez-vous à la base de données à partir de **Explorateur d’objets SQL Server**ou créez une connexion de données à la base de données dans **Explorateur de serveurs**.</span><span class="sxs-lookup"><span data-stu-id="59d2b-133">In [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), connect to the database from **SQL Server Object Explorer**, or create a Data Connection to the database in **Server Explorer**.</span></span> <span data-ttu-id="59d2b-134">Ouvrez ces volets Explorateur dans le menu **affichage** .</span><span class="sxs-lookup"><span data-stu-id="59d2b-134">Open these explorer panes from the **View** menu.</span></span>

## <a name="get_sql"></a><span data-ttu-id="59d2b-135">Recevoir SQL Server Express</span><span class="sxs-lookup"><span data-stu-id="59d2b-135">Get SQL Server Express</span></span>

<span data-ttu-id="59d2b-136">SQL Server Express est une édition gratuite de SQL Server que vous pouvez redistribuer avec les applications.</span><span class="sxs-lookup"><span data-stu-id="59d2b-136">SQL Server Express is a free, entry-level edition of SQL Server that you can redistribute with applications.</span></span> <span data-ttu-id="59d2b-137">Téléchargez SQL Server Express à partir de la page suivante :</span><span class="sxs-lookup"><span data-stu-id="59d2b-137">Download SQL Server Express from the following page:</span></span>
  
[<span data-ttu-id="59d2b-138">Édition SQL Server Express</span><span class="sxs-lookup"><span data-stu-id="59d2b-138">SQL Server Express Edition</span></span>](https://www.microsoft.com/sql-server/sql-server-editions-express)

<span data-ttu-id="59d2b-139">Si vous utilisez [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), SQL Server Express la base de données locale est incluse dans l’édition Community gratuite de Visual Studio, ainsi que dans les éditions Professional et supérieures.</span><span class="sxs-lookup"><span data-stu-id="59d2b-139">If you're using [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), SQL Server Express LocalDB is included in the free Community edition of Visual Studio, as well as the Professional and higher editions.</span></span>  

## <a name="see-also"></a><span data-ttu-id="59d2b-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="59d2b-140">See also</span></span>

- [<span data-ttu-id="59d2b-141">Prise en main</span><span class="sxs-lookup"><span data-stu-id="59d2b-141">Getting Started</span></span>](getting-started.md)

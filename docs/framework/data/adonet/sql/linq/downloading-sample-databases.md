---
title: Obtenez les bases de données SQL Server pour ADO.NET échantillons de code
description: Téléchargez les données de données SQL Server utilisées dans les échantillons de code dans la documentation ADO.NET, ainsi que le serveur SQL et les outils de gestion
ms.date: 01/11/2019
ms.assetid: ef9d69a1-9461-43fe-94bb-7c836754bcb5
ms.openlocfilehash: 19d659cbe8f39d27b71dc59c738355f12fce92a0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148385"
---
# <a name="get-the-sample-databases-for-adonet-code-samples"></a><span data-ttu-id="db063-103">Obtenez les bases de données d’échantillons pour les échantillons de code ADO.NET</span><span class="sxs-lookup"><span data-stu-id="db063-103">Get the sample databases for ADO.NET code samples</span></span>

<span data-ttu-id="db063-104">Un certain nombre d’exemples et [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] de procédures pas à pas dans la documentation utilisent des bases de données SQL Server et SQL Server Express.</span><span class="sxs-lookup"><span data-stu-id="db063-104">A number of examples and walkthroughs in the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentation use sample SQL Server databases and SQL Server Express.</span></span> <span data-ttu-id="db063-105">Vous pouvez télécharger ces produits gratuitement à partir de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="db063-105">You can download these products free of charge from Microsoft.</span></span>

## <a name="get-the-northwind-sample-database-for-sql-server"></a><span data-ttu-id="db063-106">Obtenez la base de données de l’échantillon Northwind pour SQL Server</span><span class="sxs-lookup"><span data-stu-id="db063-106">Get the Northwind sample database for SQL Server</span></span>

<span data-ttu-id="db063-107">Téléchargez `instnwnd.sql` le script à partir du référentiel GitHub suivant pour créer et charger la base de données de l’échantillon Northwind pour SQL Server :</span><span class="sxs-lookup"><span data-stu-id="db063-107">Download the script `instnwnd.sql` from the following GitHub repository to create and load the Northwind sample database for SQL Server:</span></span>

[<span data-ttu-id="db063-108">Northwind et pubs échantillonnent des bases de données pour Microsoft SQL Server</span><span class="sxs-lookup"><span data-stu-id="db063-108">Northwind and pubs sample databases for Microsoft SQL Server</span></span>](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs)

<span data-ttu-id="db063-109">Avant de pouvoir utiliser la base de données `instnwnd.sql` Northwind, vous devez exécuter le fichier de script téléchargé pour recréer la base de données sur une instance de SQL Server en utilisant [SQL Server Management Studio](#get_ssms) ou un outil similaire.</span><span class="sxs-lookup"><span data-stu-id="db063-109">Before you can use the Northwind database, you have to run the downloaded `instnwnd.sql` script file to recreate the database on an instance of SQL Server by using [SQL Server Management Studio](#get_ssms) or a similar tool.</span></span> <span data-ttu-id="db063-110">Suivez les instructions dans le fichier Readme dans le référentiel.</span><span class="sxs-lookup"><span data-stu-id="db063-110">Follow the instructions in the Readme file in the repository.</span></span>

> [!TIP]
> <span data-ttu-id="db063-111">Si vous êtes à la recherche de la base de données Northwind pour Microsoft Access, consultez [la base de données de l’échantillon Northwind pour Microsoft Access](#northwind_access).</span><span class="sxs-lookup"><span data-stu-id="db063-111">If you're looking for the Northwind database for Microsoft Access, see [Install the Northwind sample database for Microsoft Access](#northwind_access).</span></span>

## <a name="get-the-northwind-sample-database-for-microsoft-access"></a><a name="northwind_access"></a><span data-ttu-id="db063-112">Obtenez la base de données de l’échantillon Northwind pour Microsoft Access</span><span class="sxs-lookup"><span data-stu-id="db063-112">Get the Northwind sample database for Microsoft Access</span></span>

<span data-ttu-id="db063-113">La base de données d’échantillons Northwind pour Microsoft Access n’est pas disponible sur le Microsoft Download Center.</span><span class="sxs-lookup"><span data-stu-id="db063-113">The Northwind sample database for Microsoft Access is not available on the Microsoft Download Center.</span></span> <span data-ttu-id="db063-114">Pour installer Northwind directement à partir de l’intérieur d’Access, faites les choses suivantes :</span><span class="sxs-lookup"><span data-stu-id="db063-114">To install Northwind directly from within Access, do the following things:</span></span>

1. <span data-ttu-id="db063-115">Accès libre.</span><span class="sxs-lookup"><span data-stu-id="db063-115">Open Access.</span></span>

1. <span data-ttu-id="db063-116">Entrez **Northwind** dans la **boîte De modèles en ligne,** puis **sélectionnez Entrez**.</span><span class="sxs-lookup"><span data-stu-id="db063-116">Enter **Northwind** in the **Search for Online Templates** box, and then select **Enter**.</span></span>

1. <span data-ttu-id="db063-117">Sur l’écran des résultats, sélectionnez **Northwind**.</span><span class="sxs-lookup"><span data-stu-id="db063-117">On the results screen, select **Northwind**.</span></span> <span data-ttu-id="db063-118">Une nouvelle fenêtre s’ouvre sur une description de la base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="db063-118">A new window opens with a description of the Northwind database.</span></span>

1. <span data-ttu-id="db063-119">Dans la nouvelle fenêtre, dans la boîte de texte **Nom de fichier,** fournissez un nom de fichier pour votre copie de la base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="db063-119">In the new window, in the **File Name** text box, provide a filename for your copy of the Northwind database.</span></span>

1. <span data-ttu-id="db063-120">Sélectionnez **Créer**.</span><span class="sxs-lookup"><span data-stu-id="db063-120">Select **Create**.</span></span> <span data-ttu-id="db063-121">Access télécharge la base de données Northwind et prépare le fichier.</span><span class="sxs-lookup"><span data-stu-id="db063-121">Access downloads the Northwind database and prepares the file.</span></span>

1. <span data-ttu-id="db063-122">Lorsque ce processus est terminé, la base de données s’ouvre avec un écran Bienvenue.</span><span class="sxs-lookup"><span data-stu-id="db063-122">When this process is complete, the database opens with a Welcome screen.</span></span>

## <a name="get-the-adventureworks-sample-database-for-sql-server"></a><span data-ttu-id="db063-123">Obtenez la base de données d’échantillons AdventureWorks pour SQL Server</span><span class="sxs-lookup"><span data-stu-id="db063-123">Get the AdventureWorks sample database for SQL Server</span></span>

<span data-ttu-id="db063-124">Téléchargez la base de données de l’échantillon AdventureWorks pour SQL Server à partir du référentiel GitHub suivant :</span><span class="sxs-lookup"><span data-stu-id="db063-124">Download the AdventureWorks sample database for SQL Server from the following GitHub repository:</span></span>

[<span data-ttu-id="db063-125">Exemples de bases de données AdventureWorks</span><span class="sxs-lookup"><span data-stu-id="db063-125">AdventureWorks sample databases</span></span>](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)

<span data-ttu-id="db063-126">Après avoir téléchargé l’un\*des fichiers de sauvegarde de base de données (.bak), redérez la sauvegarde à une instance de SQL Server en utilisant SQL Server Management Studio (SSMS).</span><span class="sxs-lookup"><span data-stu-id="db063-126">After you download one of the database backup (\*.bak) files, restore the backup to an instance of SQL Server by using SQL Server Management Studio (SSMS).</span></span> <span data-ttu-id="db063-127">Voir [Get SQL Server Management Studio](#get_ssms).</span><span class="sxs-lookup"><span data-stu-id="db063-127">See [Get SQL Server Management Studio](#get_ssms).</span></span>

## <a name="get-sql-server-management-studio"></a><a name="get_ssms"></a><span data-ttu-id="db063-128">Obtenez SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="db063-128">Get SQL Server Management Studio</span></span>
<span data-ttu-id="db063-129">Si vous souhaitez afficher ou modifier une base de données que vous avez téléchargée, vous pouvez utiliser SQL Server Management Studio (SSMS).</span><span class="sxs-lookup"><span data-stu-id="db063-129">If you want to view or modify a database that you've downloaded, you can use SQL Server Management Studio (SSMS).</span></span> <span data-ttu-id="db063-130">Télécharger SSMS à partir de la page suivante:</span><span class="sxs-lookup"><span data-stu-id="db063-130">Download SSMS from the following page:</span></span>

[<span data-ttu-id="db063-131">Télécharger SQL Server Management Studio (SSMS)</span><span class="sxs-lookup"><span data-stu-id="db063-131">Download SQL Server Management Studio (SSMS)</span></span>](/sql/ssms/download-sql-server-management-studio-ssms)

<span data-ttu-id="db063-132">Vous pouvez également afficher et gérer des bases de données dans l’environnement de développement intégré Visual Studio (IDE).</span><span class="sxs-lookup"><span data-stu-id="db063-132">You can also view and manage databases in the Visual Studio integrated development environment (IDE).</span></span> <span data-ttu-id="db063-133">Dans [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), connectez-vous à la base de données de **SQL Server Object Explorer**, ou créez une connexion de données à la base de données dans Server **Explorer**.</span><span class="sxs-lookup"><span data-stu-id="db063-133">In [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), connect to the database from **SQL Server Object Explorer**, or create a Data Connection to the database in **Server Explorer**.</span></span> <span data-ttu-id="db063-134">Ouvrez ces volets explorateurs à partir du menu **View.**</span><span class="sxs-lookup"><span data-stu-id="db063-134">Open these explorer panes from the **View** menu.</span></span>

## <a name="get-sql-server-express"></a><a name="get_sql"></a><span data-ttu-id="db063-135">Obtenez SQL Server Express</span><span class="sxs-lookup"><span data-stu-id="db063-135">Get SQL Server Express</span></span>

<span data-ttu-id="db063-136">SQL Server Express est une édition gratuite d’entrée de gamme de SQL Server que vous pouvez redistribuer avec des applications.</span><span class="sxs-lookup"><span data-stu-id="db063-136">SQL Server Express is a free, entry-level edition of SQL Server that you can redistribute with applications.</span></span> <span data-ttu-id="db063-137">Télécharger SQL Server Express à partir de la page suivante:</span><span class="sxs-lookup"><span data-stu-id="db063-137">Download SQL Server Express from the following page:</span></span>
  
[<span data-ttu-id="db063-138">SQL Server Express</span><span class="sxs-lookup"><span data-stu-id="db063-138">SQL Server Express Edition</span></span>](https://www.microsoft.com/sql-server/sql-server-editions-express)

<span data-ttu-id="db063-139">Si vous utilisez [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), SQL Server Express LocalDB est inclus dans l’édition communautaire gratuite de Visual Studio, ainsi que les éditions Professionnelles et Supérieures.</span><span class="sxs-lookup"><span data-stu-id="db063-139">If you're using [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), SQL Server Express LocalDB is included in the free Community edition of Visual Studio, as well as the Professional and higher editions.</span></span>  

## <a name="see-also"></a><span data-ttu-id="db063-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="db063-140">See also</span></span>

- [<span data-ttu-id="db063-141">Prise en main</span><span class="sxs-lookup"><span data-stu-id="db063-141">Getting Started</span></span>](getting-started.md)

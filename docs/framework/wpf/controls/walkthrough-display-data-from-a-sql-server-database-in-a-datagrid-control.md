---
title: 'Procédure pas à pas : afficher des données à partir d’une base de données SQL Server dans un contrôle DataGrid'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid [WPF], displaying data from SQL Server
- controls [WPF], DataGrid
ms.assetid: 6810b048-0a23-4f86-bfa5-97f92b3cfab4
ms.openlocfilehash: 1398d8408a0b85d6603d638312e92ba35c5e77d3
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84591031"
---
# <a name="walkthrough-display-data-from-a-sql-server-database-in-a-datagrid-control"></a><span data-ttu-id="90dea-102">Procédure pas à pas : affichage de données d’une base de données SQL Server dans un contrôle DataGrid</span><span class="sxs-lookup"><span data-stu-id="90dea-102">Walkthrough: Display data from a SQL Server database in a DataGrid control</span></span>

<span data-ttu-id="90dea-103">Dans cette procédure pas à pas, vous extrayez des données d’une base de données SQL Server et affichez ces données dans un <xref:System.Windows.Controls.DataGrid> contrôle.</span><span class="sxs-lookup"><span data-stu-id="90dea-103">In this walkthrough, you retrieve data from a SQL Server database and display that data in a <xref:System.Windows.Controls.DataGrid> control.</span></span> <span data-ttu-id="90dea-104">Vous utilisez la Entity Framework ADO.NET pour créer les classes d’entité qui représentent les données, et utilisez LINQ pour écrire une requête qui récupère les données spécifiées à partir d’une classe d’entité.</span><span class="sxs-lookup"><span data-stu-id="90dea-104">You use the ADO.NET Entity Framework to create the entity classes that represent the data, and use LINQ to write a query that retrieves the specified data from an entity class.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="90dea-105">Prérequis</span><span class="sxs-lookup"><span data-stu-id="90dea-105">Prerequisites</span></span>

<span data-ttu-id="90dea-106">Vous devez disposer des éléments suivants pour exécuter cette procédure pas à pas :</span><span class="sxs-lookup"><span data-stu-id="90dea-106">You need the following components to complete this walkthrough:</span></span>

- <span data-ttu-id="90dea-107">Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="90dea-107">Visual Studio.</span></span>

- <span data-ttu-id="90dea-108">Accès à une instance en cours d’exécution de SQL Server ou SQL Server Express à laquelle l’exemple de base de données AdventureWorks est attaché.</span><span class="sxs-lookup"><span data-stu-id="90dea-108">Access to a running instance of SQL Server or SQL Server Express that has the AdventureWorks sample database attached to it.</span></span> <span data-ttu-id="90dea-109">Vous pouvez télécharger la base de données AdventureWorks à partir du [GitHub](https://github.com/Microsoft/sql-server-samples/releases).</span><span class="sxs-lookup"><span data-stu-id="90dea-109">You can download the AdventureWorks database from the [GitHub](https://github.com/Microsoft/sql-server-samples/releases).</span></span>

## <a name="create-entity-classes"></a><span data-ttu-id="90dea-110">Créer des classes d’entité</span><span class="sxs-lookup"><span data-stu-id="90dea-110">Create entity classes</span></span>

1. <span data-ttu-id="90dea-111">Créez un projet d’application WPF dans Visual Basic ou C#, puis nommez-le `DataGridSQLExample` .</span><span class="sxs-lookup"><span data-stu-id="90dea-111">Create a new WPF Application project in Visual Basic or C#, and name it `DataGridSQLExample`.</span></span>

2. <span data-ttu-id="90dea-112">Dans Explorateur de solutions, cliquez avec le bouton droit sur votre projet, pointez sur **Ajouter**, puis sélectionnez **nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="90dea-112">In Solution Explorer, right-click your project, point to **Add**, and then select **New Item**.</span></span>

     <span data-ttu-id="90dea-113">La boîte de dialogue Ajouter un nouvel élément s'affiche.</span><span class="sxs-lookup"><span data-stu-id="90dea-113">The Add New Item dialog box appears.</span></span>

3. <span data-ttu-id="90dea-114">Dans le volet Modèles installés, sélectionnez **données** et dans la liste des modèles, sélectionnez **ADO.NET Entity Data Model**.</span><span class="sxs-lookup"><span data-stu-id="90dea-114">In the Installed Templates pane, select **Data** and in the list of templates, select **ADO.NET Entity Data Model**.</span></span>

     ![Modèle d’élément de Entity Data Model ADO.NET](../../wcf/feature-details/media/ado-net-entity-data-model-item-template.png)

4. <span data-ttu-id="90dea-116">Nommez le fichier `AdventureWorksModel.edmx` , puis cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="90dea-116">Name the file `AdventureWorksModel.edmx` and then click **Add**.</span></span>

     <span data-ttu-id="90dea-117">L'Assistant Entity Data Model s'affiche.</span><span class="sxs-lookup"><span data-stu-id="90dea-117">The Entity Data Model Wizard appears.</span></span>

5. <span data-ttu-id="90dea-118">Dans l’écran choisir le contenu du modèle, sélectionnez le **Concepteur EF à partir de la base de données** , puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="90dea-118">In the Choose Model Contents screen, select **EF Designer from database** and then click **Next**.</span></span>

6. <span data-ttu-id="90dea-119">Dans l’écran choisir votre connexion de données, fournissez la connexion à votre base de données AdventureWorksLT2008.</span><span class="sxs-lookup"><span data-stu-id="90dea-119">In the Choose Your Data Connection screen, provide the connection to your AdventureWorksLT2008 database.</span></span> <span data-ttu-id="90dea-120">Pour plus d’informations, consultez [boîte de dialogue choisir votre connexion de données](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399244(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="90dea-120">For more information, see [Choose Your Data Connection Dialog Box](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399244(v=vs.100)).</span></span>

    <span data-ttu-id="90dea-121">Assurez-vous que le nom est `AdventureWorksLT2008Entities` et que la case à cocher **enregistrer les paramètres de connexion de l’entité dans App. config en tant que** est activée, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="90dea-121">Make sure that the name is `AdventureWorksLT2008Entities` and that the **Save entity connection settings in App.Config as** check box is selected, and then click **Next**.</span></span>

7. <span data-ttu-id="90dea-122">Dans l’écran choisir vos objets de base de données, développez le nœud tables, puis sélectionnez les tables **Product** et **ProductCategory** .</span><span class="sxs-lookup"><span data-stu-id="90dea-122">In the Choose Your Database Objects screen, expand the Tables node, and select the **Product** and **ProductCategory** tables.</span></span>

     <span data-ttu-id="90dea-123">Vous pouvez générer des classes d’entité pour toutes les tables ; Toutefois, dans cet exemple, vous récupérez uniquement les données de ces deux tables.</span><span class="sxs-lookup"><span data-stu-id="90dea-123">You can generate entity classes for all of the tables; however, in this example you only retrieve data from those two tables.</span></span>

     <span data-ttu-id="90dea-124">![Sélectionner Product et ProductCategory dans les tables](./media/datagrid-sql-ef-step4.png "DataGrid_SQL_EF_Step4")</span><span class="sxs-lookup"><span data-stu-id="90dea-124">![Select Product and ProductCategory from tables](./media/datagrid-sql-ef-step4.png "DataGrid_SQL_EF_Step4")</span></span>

8. <span data-ttu-id="90dea-125">Cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="90dea-125">Click **Finish**.</span></span>

     <span data-ttu-id="90dea-126">Les entités Product et ProductCategory sont affichées dans la Entity Designer.</span><span class="sxs-lookup"><span data-stu-id="90dea-126">The Product and ProductCategory entities are displayed in the Entity Designer.</span></span>

     <span data-ttu-id="90dea-127">![Modèles d'entité Product et ProductCategory](./media/datagrid-sql-ef-step5.png "DataGrid_SQL_EF_Step5")</span><span class="sxs-lookup"><span data-stu-id="90dea-127">![Product and ProductCategory entity models](./media/datagrid-sql-ef-step5.png "DataGrid_SQL_EF_Step5")</span></span>

## <a name="retrieve-and-present-the-data"></a><span data-ttu-id="90dea-128">Récupérer et présenter les données</span><span class="sxs-lookup"><span data-stu-id="90dea-128">Retrieve and present the data</span></span>

1. <span data-ttu-id="90dea-129">Ouvrez le fichier MainWindow. Xaml.</span><span class="sxs-lookup"><span data-stu-id="90dea-129">Open the MainWindow.xaml file.</span></span>

2. <span data-ttu-id="90dea-130">Affectez <xref:System.Windows.FrameworkElement.Width%2A> à la propriété de la valeur <xref:System.Windows.Window> 450.</span><span class="sxs-lookup"><span data-stu-id="90dea-130">Set the <xref:System.Windows.FrameworkElement.Width%2A> property on the <xref:System.Windows.Window> to 450.</span></span>

3. <span data-ttu-id="90dea-131">Dans l’éditeur XAML, ajoutez la <xref:System.Windows.Controls.DataGrid> balise suivante entre `<Grid>` les `</Grid>` balises et pour ajouter un <xref:System.Windows.Controls.DataGrid> nommé `dataGrid1` .</span><span class="sxs-lookup"><span data-stu-id="90dea-131">In the XAML editor, add the following <xref:System.Windows.Controls.DataGrid> tag between the `<Grid>` and `</Grid>` tags to add a <xref:System.Windows.Controls.DataGrid> named `dataGrid1`.</span></span>

     [!code-xaml[DataGrid_SQL_EF_Walkthrough#3](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml#3)]

     <span data-ttu-id="90dea-132">![Fenêtre avec DataGrid](./media/datagrid-sql-ef-step6.png "DataGrid_SQL_EF_Step6")</span><span class="sxs-lookup"><span data-stu-id="90dea-132">![Window with DataGrid](./media/datagrid-sql-ef-step6.png "DataGrid_SQL_EF_Step6")</span></span>

4. <span data-ttu-id="90dea-133">Sélectionnez <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="90dea-133">Select the <xref:System.Windows.Window>.</span></span>

5. <span data-ttu-id="90dea-134">À l’aide de l’Fenêtre Propriétés ou de l’éditeur XAML, créez un gestionnaire d’événements pour le <xref:System.Windows.Window> nommé `Window_Loaded` pour l' <xref:System.Windows.FrameworkElement.Loaded> événement.</span><span class="sxs-lookup"><span data-stu-id="90dea-134">Using the Properties window or XAML editor, create an event handler for the <xref:System.Windows.Window> named `Window_Loaded` for the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span> <span data-ttu-id="90dea-135">Pour plus d’informations, consultez [Comment : créer un gestionnaire d’événements simple](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="90dea-135">For more information, see [How to: Create a Simple Event Handler](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100)).</span></span>

     <span data-ttu-id="90dea-136">L’exemple suivant montre le code XAML pour MainWindow. Xaml.</span><span class="sxs-lookup"><span data-stu-id="90dea-136">The following shows the XAML for MainWindow.xaml.</span></span>

    > [!NOTE]
    > <span data-ttu-id="90dea-137">Si vous utilisez Visual Basic, dans la première ligne de MainWindow. xaml, remplacez `x:Class="DataGridSQLExample.MainWindow"` par `x:Class="MainWindow"` .</span><span class="sxs-lookup"><span data-stu-id="90dea-137">If you are using Visual Basic, in the first line of MainWindow.xaml, replace `x:Class="DataGridSQLExample.MainWindow"` with `x:Class="MainWindow"`.</span></span>

     [!code-xaml[DataGrid_SQL_EF_Walkthrough#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml#1)]

6. <span data-ttu-id="90dea-138">Ouvrez le fichier code-behind (MainWindow. Xaml. vb ou MainWindow.xaml.cs) pour le <xref:System.Windows.Window> .</span><span class="sxs-lookup"><span data-stu-id="90dea-138">Open the code-behind file (MainWindow.xaml.vb or MainWindow.xaml.cs) for the <xref:System.Windows.Window>.</span></span>

7. <span data-ttu-id="90dea-139">Ajoutez le code suivant pour récupérer uniquement des valeurs spécifiques des tables jointes et définissez la <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> propriété de <xref:System.Windows.Controls.DataGrid> sur les résultats de la requête.</span><span class="sxs-lookup"><span data-stu-id="90dea-139">Add the following code to retrieve only specific values from the joined tables and set the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property of the <xref:System.Windows.Controls.DataGrid> to the results of the query.</span></span>

     [!code-csharp[DataGrid_SQL_EF_Walkthrough#2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml.cs#2)]
     [!code-vb[DataGrid_SQL_EF_Walkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/VB/MainWindow.xaml.vb#2)]

8. <span data-ttu-id="90dea-140">Exécutez l'exemple.</span><span class="sxs-lookup"><span data-stu-id="90dea-140">Run the example.</span></span>

     <span data-ttu-id="90dea-141">Vous devez voir un <xref:System.Windows.Controls.DataGrid> qui affiche des données.</span><span class="sxs-lookup"><span data-stu-id="90dea-141">You should see a <xref:System.Windows.Controls.DataGrid> that displays data.</span></span>

     <span data-ttu-id="90dea-142">![DataGrid avec des données de la base de données SQL](./media/datagrid-sql-ef-step7.png "DataGrid_SQL_EF_Step7")</span><span class="sxs-lookup"><span data-stu-id="90dea-142">![DataGrid with data from SQL database](./media/datagrid-sql-ef-step7.png "DataGrid_SQL_EF_Step7")</span></span>

## <a name="see-also"></a><span data-ttu-id="90dea-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="90dea-143">See also</span></span>

- <xref:System.Windows.Controls.DataGrid>

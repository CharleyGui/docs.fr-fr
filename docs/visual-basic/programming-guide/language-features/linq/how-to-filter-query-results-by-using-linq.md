---
title: 'Guide pratique : filtrer les résultats d’une requête à l’aide de LINQ'
ms.date: 07/20/2015
helpviewer_keywords:
- filtering [Visual Basic]
- filtering data [LINQ in Visual Basic]
- filtering [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], filtering results
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
- filtering data [Visual Basic]
ms.assetid: ef103092-9bed-4134-97f4-2db696e83c12
ms.openlocfilehash: 4d91783429f24abfe4149217542f8f7a6073bfef
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404989"
---
# <a name="how-to-filter-query-results-by-using-linq-visual-basic"></a><span data-ttu-id="200bf-102">Comment : filtrer les résultats d'une requête à l'aide de LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="200bf-102">How to: Filter Query Results by Using LINQ (Visual Basic)</span></span>

<span data-ttu-id="200bf-103">LINQ (Language-Integrated Query) facilite l’accès aux informations de la base de données et à l’exécution des requêtes.</span><span class="sxs-lookup"><span data-stu-id="200bf-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span>

<span data-ttu-id="200bf-104">L’exemple suivant montre comment créer une application qui exécute des requêtes sur une base de données SQL Server et filtre les résultats en fonction d’une valeur particulière à l’aide de la `Where` clause.</span><span class="sxs-lookup"><span data-stu-id="200bf-104">The following example shows how to create a new application that performs queries against a SQL Server database and filters the results by a particular value by using the `Where` clause.</span></span> <span data-ttu-id="200bf-105">Pour plus d’informations, consultez [Where, clause](../../../language-reference/queries/where-clause.md).</span><span class="sxs-lookup"><span data-stu-id="200bf-105">For more information, see [Where Clause](../../../language-reference/queries/where-clause.md).</span></span>

<span data-ttu-id="200bf-106">Les exemples de cette rubrique utilisent l’exemple de base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="200bf-106">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="200bf-107">Si cette base de données n’est pas disponible sur votre ordinateur de développement, vous pouvez la télécharger à partir du Centre de téléchargement Microsoft.</span><span class="sxs-lookup"><span data-stu-id="200bf-107">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="200bf-108">Pour obtenir des instructions, consultez [téléchargement d’exemples de bases de données](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="200bf-108">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="200bf-109">Pour créer une connexion à une base de données</span><span class="sxs-lookup"><span data-stu-id="200bf-109">To create a connection to a database</span></span>

1. <span data-ttu-id="200bf-110">Dans Visual Studio, ouvrez **Explorateur de serveurs** / **Explorateur de base de données** en cliquant sur **Explorateur de serveurs** / **Explorateur de base de données** dans le menu **affichage** .</span><span class="sxs-lookup"><span data-stu-id="200bf-110">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>

2. <span data-ttu-id="200bf-111">Cliquez avec le bouton droit sur **connexions de données** dans **Explorateur de serveurs** / **Explorateur de base de données** puis cliquez sur **Ajouter une connexion**.</span><span class="sxs-lookup"><span data-stu-id="200bf-111">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>

3. <span data-ttu-id="200bf-112">Spécifiez une connexion valide à l’exemple de base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="200bf-112">Specify a valid connection to the Northwind sample database.</span></span>

## <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="200bf-113">Pour ajouter un projet qui contient un fichier LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="200bf-113">To add a project that contains a LINQ to SQL file</span></span>

1. <span data-ttu-id="200bf-114">Dans Visual Studio, dans le menu **fichier** , pointez sur **nouveau** , puis cliquez sur **projet**.</span><span class="sxs-lookup"><span data-stu-id="200bf-114">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="200bf-115">Sélectionnez Visual Basic **Application Windows Forms** comme type de projet.</span><span class="sxs-lookup"><span data-stu-id="200bf-115">Select Visual Basic **Windows Forms Application** as the project type.</span></span>

2. <span data-ttu-id="200bf-116">Dans le menu **Projet** , cliquez sur **Ajouter un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="200bf-116">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="200bf-117">Sélectionnez le modèle d’élément **Classes LINQ to SQL** .</span><span class="sxs-lookup"><span data-stu-id="200bf-117">Select the **LINQ to SQL Classes** item template.</span></span>

3. <span data-ttu-id="200bf-118">Nommez le fichier `northwind.dbml`.</span><span class="sxs-lookup"><span data-stu-id="200bf-118">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="200bf-119">Cliquez sur **Add**.</span><span class="sxs-lookup"><span data-stu-id="200bf-119">Click **Add**.</span></span> <span data-ttu-id="200bf-120">Le Concepteur Objet Relationnel (Concepteur O/R) s’ouvre pour le fichier Northwind. dbml.</span><span class="sxs-lookup"><span data-stu-id="200bf-120">The Object Relational Designer (O/R Designer) opens for the northwind.dbml file.</span></span>

## <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="200bf-121">Pour ajouter des tables à interroger dans le Concepteur O/R</span><span class="sxs-lookup"><span data-stu-id="200bf-121">To add tables to query to the O/R Designer</span></span>

1. <span data-ttu-id="200bf-122">Dans **Explorateur de serveurs** / **Explorateur de base de données**, développez la connexion à la base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="200bf-122">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="200bf-123">Développez le dossier **Tables** .</span><span class="sxs-lookup"><span data-stu-id="200bf-123">Expand the **Tables** folder.</span></span>

     <span data-ttu-id="200bf-124">Si vous avez fermé le Concepteur O/R, vous pouvez le rouvrir en double-cliquant sur le fichier Northwind. dbml que vous avez ajouté précédemment.</span><span class="sxs-lookup"><span data-stu-id="200bf-124">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>

2. <span data-ttu-id="200bf-125">Cliquez sur la table Customers et faites-la glisser vers le volet gauche du concepteur.</span><span class="sxs-lookup"><span data-stu-id="200bf-125">Click the Customers table and drag it to the left pane of the designer.</span></span> <span data-ttu-id="200bf-126">Cliquez sur la table Orders et faites-la glisser vers le volet gauche du concepteur.</span><span class="sxs-lookup"><span data-stu-id="200bf-126">Click the Orders table and drag it to the left pane of the designer.</span></span>

     <span data-ttu-id="200bf-127">Le concepteur crée `Customer` de nouveaux `Order` objets et pour votre projet.</span><span class="sxs-lookup"><span data-stu-id="200bf-127">The designer creates new `Customer` and `Order` objects for your project.</span></span> <span data-ttu-id="200bf-128">Notez que le concepteur détecte automatiquement les relations entre les tables et crée des propriétés enfants pour les objets connexes.</span><span class="sxs-lookup"><span data-stu-id="200bf-128">Notice that the designer automatically detects relationships between the tables and creates child properties for related objects.</span></span> <span data-ttu-id="200bf-129">Par exemple, IntelliSense indique que l' `Customer` objet a une `Orders` propriété pour toutes les commandes associées à ce client.</span><span class="sxs-lookup"><span data-stu-id="200bf-129">For example, IntelliSense will show that the `Customer` object has an `Orders` property for all orders related to that customer.</span></span>

3. <span data-ttu-id="200bf-130">Enregistrez vos modifications et fermez le concepteur.</span><span class="sxs-lookup"><span data-stu-id="200bf-130">Save your changes and close the designer.</span></span>

4. <span data-ttu-id="200bf-131">Enregistrez votre projet.</span><span class="sxs-lookup"><span data-stu-id="200bf-131">Save your project.</span></span>

## <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="200bf-132">Pour ajouter du code pour interroger la base de données et afficher les résultats</span><span class="sxs-lookup"><span data-stu-id="200bf-132">To add code to query the database and display the results</span></span>

1. <span data-ttu-id="200bf-133">À partir de la **boîte à outils**, faites glisser un <xref:System.Windows.Forms.DataGridView> contrôle sur le Windows Form par défaut de votre projet, Form1.</span><span class="sxs-lookup"><span data-stu-id="200bf-133">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>

2. <span data-ttu-id="200bf-134">Double-cliquez sur Form1 pour ajouter du code à l' `Load` événement du formulaire.</span><span class="sxs-lookup"><span data-stu-id="200bf-134">Double-click Form1 to add code to the `Load` event of the form.</span></span>

3. <span data-ttu-id="200bf-135">Quand vous avez ajouté des tables au Concepteur O/R, le concepteur a ajouté un <xref:System.Data.Linq.DataContext> objet pour votre projet.</span><span class="sxs-lookup"><span data-stu-id="200bf-135">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="200bf-136">Cet objet contient le code dont vous devez disposer pour accéder à ces tables, en plus des objets et des collections individuels pour chaque table.</span><span class="sxs-lookup"><span data-stu-id="200bf-136">This object contains the code that you must have to access those tables, in addition to individual objects and collections for each table.</span></span> <span data-ttu-id="200bf-137">L' <xref:System.Data.Linq.DataContext> objet de votre projet est nommé en fonction du nom de votre fichier. dbml.</span><span class="sxs-lookup"><span data-stu-id="200bf-137">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="200bf-138">Pour ce projet, l' <xref:System.Data.Linq.DataContext> objet est nommé `northwindDataContext` .</span><span class="sxs-lookup"><span data-stu-id="200bf-138">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>

    <span data-ttu-id="200bf-139">Vous pouvez créer une instance de <xref:System.Data.Linq.DataContext> dans votre code et interroger les tables spécifiées par le Concepteur O/R.</span><span class="sxs-lookup"><span data-stu-id="200bf-139">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>

    <span data-ttu-id="200bf-140">Ajoutez le code suivant à l' `Load` événement pour interroger les tables qui sont exposées en tant que propriétés de votre contexte de données.</span><span class="sxs-lookup"><span data-stu-id="200bf-140">Add the following code to the `Load` event to query the tables that are exposed as properties of your data context.</span></span> <span data-ttu-id="200bf-141">La requête filtre les résultats et retourne uniquement les clients qui se trouvent dans `London` .</span><span class="sxs-lookup"><span data-stu-id="200bf-141">The query filters the results and returns only customers that are located in `London`.</span></span>

    [!code-vb[VbLINQToSQLHowTos#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form5.vb#11)]

4. <span data-ttu-id="200bf-142">Appuyez sur F5 pour exécuter votre projet et afficher les résultats.</span><span class="sxs-lookup"><span data-stu-id="200bf-142">Press F5 to run your project and view the results.</span></span>

5. <span data-ttu-id="200bf-143">Voici d’autres filtres que vous pouvez essayer.</span><span class="sxs-lookup"><span data-stu-id="200bf-143">Following are some other filters that you can try.</span></span>

    [!code-vb[VbLINQToSQLHowTos#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form5.vb#12)]

## <a name="see-also"></a><span data-ttu-id="200bf-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="200bf-144">See also</span></span>

- [<span data-ttu-id="200bf-145">LINQ</span><span class="sxs-lookup"><span data-stu-id="200bf-145">LINQ</span></span>](index.md)
- [<span data-ttu-id="200bf-146">Requêtes</span><span class="sxs-lookup"><span data-stu-id="200bf-146">Queries</span></span>](../../../language-reference/queries/index.md)
- [<span data-ttu-id="200bf-147">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="200bf-147">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="200bf-148">Méthode DataContext (Concepteur O/R)</span><span class="sxs-lookup"><span data-stu-id="200bf-148">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)

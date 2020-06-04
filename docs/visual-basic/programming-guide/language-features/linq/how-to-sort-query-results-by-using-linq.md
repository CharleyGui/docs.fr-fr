---
title: 'Guide pratique : trier les résultats d’une requête à l’aide de LINQ'
ms.date: 07/20/2015
helpviewer_keywords:
- sorting query results, multiple columns
- sorting data [Visual Basic]
- sorting data [LINQ in Visual Basic]
- sorting query results [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], sorting results
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
ms.assetid: 07a4584d-9fd8-4a1d-b7d9-ccf2efa5c84e
ms.openlocfilehash: c1bc6ab863f9de118d59e102d3d5d251d326f497
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404937"
---
# <a name="how-to-sort-query-results-by-using-linq-visual-basic"></a><span data-ttu-id="41939-102">Comment : trier les résultats d'une requête à l'aide de LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="41939-102">How to: Sort Query Results by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="41939-103">LINQ (Language-Integrated Query) facilite l’accès aux informations de la base de données et à l’exécution des requêtes.</span><span class="sxs-lookup"><span data-stu-id="41939-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span>  
  
 <span data-ttu-id="41939-104">L’exemple suivant montre comment créer une application qui exécute des requêtes sur une base de données SQL Server et trie les résultats en fonction de plusieurs champs à l’aide de la `Order By` clause.</span><span class="sxs-lookup"><span data-stu-id="41939-104">The following example shows how to create a new application that performs queries against a SQL Server database and sorts the results by multiple fields by using the `Order By` clause.</span></span> <span data-ttu-id="41939-105">L’ordre de tri de chaque champ peut être ordre croissant ou décroissant.</span><span class="sxs-lookup"><span data-stu-id="41939-105">The sort order for each field can be ascending order or descending order.</span></span> <span data-ttu-id="41939-106">Pour plus d’informations, consultez [clause ORDER BY](../../../language-reference/queries/order-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="41939-106">For more information, see [Order By Clause](../../../language-reference/queries/order-by-clause.md).</span></span>  
  
 <span data-ttu-id="41939-107">Les exemples de cette rubrique utilisent l’exemple de base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="41939-107">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="41939-108">Si cette base de données n’est pas disponible sur votre ordinateur de développement, vous pouvez la télécharger à partir du Centre de téléchargement Microsoft.</span><span class="sxs-lookup"><span data-stu-id="41939-108">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="41939-109">Pour obtenir des instructions, consultez [téléchargement d’exemples de bases de données](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="41939-109">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="41939-110">Pour créer une connexion à une base de données</span><span class="sxs-lookup"><span data-stu-id="41939-110">To create a connection to a database</span></span>  
  
1. <span data-ttu-id="41939-111">Dans Visual Studio, ouvrez **Explorateur de serveurs** / **Explorateur de base de données** en cliquant sur **Explorateur de serveurs** / **Explorateur de base de données** dans le menu **affichage** .</span><span class="sxs-lookup"><span data-stu-id="41939-111">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2. <span data-ttu-id="41939-112">Cliquez avec le bouton droit sur **connexions de données** dans **Explorateur de serveurs** / **Explorateur de base de données** puis cliquez sur **Ajouter une connexion**.</span><span class="sxs-lookup"><span data-stu-id="41939-112">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3. <span data-ttu-id="41939-113">Spécifiez une connexion valide à l’exemple de base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="41939-113">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="41939-114">Pour ajouter un projet qui contient un fichier LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="41939-114">To add a project that contains a LINQ to SQL file</span></span>  
  
1. <span data-ttu-id="41939-115">Dans Visual Studio, dans le menu **fichier** , pointez sur **nouveau** , puis cliquez sur **projet**.</span><span class="sxs-lookup"><span data-stu-id="41939-115">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="41939-116">Sélectionnez Visual Basic **Application Windows Forms** comme type de projet.</span><span class="sxs-lookup"><span data-stu-id="41939-116">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2. <span data-ttu-id="41939-117">Dans le menu **Projet** , cliquez sur **Ajouter un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="41939-117">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="41939-118">Sélectionnez le modèle d’élément **Classes LINQ to SQL** .</span><span class="sxs-lookup"><span data-stu-id="41939-118">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3. <span data-ttu-id="41939-119">Nommez le fichier `northwind.dbml`.</span><span class="sxs-lookup"><span data-stu-id="41939-119">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="41939-120">Cliquez sur **Add**.</span><span class="sxs-lookup"><span data-stu-id="41939-120">Click **Add**.</span></span> <span data-ttu-id="41939-121">Le Concepteur Objet Relationnel (Concepteur O/R) est ouvert pour le fichier Northwind. dbml.</span><span class="sxs-lookup"><span data-stu-id="41939-121">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="41939-122">Pour ajouter des tables à interroger dans le Concepteur O/R</span><span class="sxs-lookup"><span data-stu-id="41939-122">To add tables to query to the O/R Designer</span></span>  
  
1. <span data-ttu-id="41939-123">Dans **Explorateur de serveurs** / **Explorateur de base de données**, développez la connexion à la base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="41939-123">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="41939-124">Développez le dossier **Tables** .</span><span class="sxs-lookup"><span data-stu-id="41939-124">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="41939-125">Si vous avez fermé le Concepteur O/R, vous pouvez le rouvrir en double-cliquant sur le fichier Northwind. dbml que vous avez ajouté précédemment.</span><span class="sxs-lookup"><span data-stu-id="41939-125">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2. <span data-ttu-id="41939-126">Cliquez sur la table Customers et faites-la glisser vers le volet gauche du concepteur.</span><span class="sxs-lookup"><span data-stu-id="41939-126">Click the Customers table and drag it to the left pane of the designer.</span></span> <span data-ttu-id="41939-127">Cliquez sur la table Orders et faites-la glisser vers le volet gauche du concepteur.</span><span class="sxs-lookup"><span data-stu-id="41939-127">Click the Orders table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="41939-128">Le concepteur crée `Customer` de nouveaux `Order` objets et pour votre projet.</span><span class="sxs-lookup"><span data-stu-id="41939-128">The designer creates new `Customer` and `Order` objects for your project.</span></span> <span data-ttu-id="41939-129">Notez que le concepteur détecte automatiquement les relations entre les tables et crée des propriétés enfants pour les objets connexes.</span><span class="sxs-lookup"><span data-stu-id="41939-129">Notice that the designer automatically detects relationships between the tables and creates child properties for related objects.</span></span> <span data-ttu-id="41939-130">Par exemple, IntelliSense indique que l' `Customer` objet a une `Orders` propriété pour toutes les commandes associées à ce client.</span><span class="sxs-lookup"><span data-stu-id="41939-130">For example, IntelliSense will show that the `Customer` object has an `Orders` property for all orders related to that customer.</span></span>  
  
3. <span data-ttu-id="41939-131">Enregistrez vos modifications et fermez le concepteur.</span><span class="sxs-lookup"><span data-stu-id="41939-131">Save your changes and close the designer.</span></span>  
  
4. <span data-ttu-id="41939-132">Enregistrez votre projet.</span><span class="sxs-lookup"><span data-stu-id="41939-132">Save your project.</span></span>  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="41939-133">Pour ajouter du code pour interroger la base de données et afficher les résultats</span><span class="sxs-lookup"><span data-stu-id="41939-133">To add code to query the database and display the results</span></span>  
  
1. <span data-ttu-id="41939-134">À partir de la **boîte à outils**, faites glisser un <xref:System.Windows.Forms.DataGridView> contrôle sur le Windows Form par défaut de votre projet, Form1.</span><span class="sxs-lookup"><span data-stu-id="41939-134">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2. <span data-ttu-id="41939-135">Double-cliquez sur Form1 pour ajouter du code à l' `Load` événement du formulaire.</span><span class="sxs-lookup"><span data-stu-id="41939-135">Double-click Form1 to add code to the `Load` event of the form.</span></span>  
  
3. <span data-ttu-id="41939-136">Quand vous avez ajouté des tables au Concepteur O/R, le concepteur a ajouté un <xref:System.Data.Linq.DataContext> objet à votre projet.</span><span class="sxs-lookup"><span data-stu-id="41939-136">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object to your project.</span></span> <span data-ttu-id="41939-137">Cet objet contient le code dont vous devez disposer pour accéder à ces tables et pour accéder à des objets et des collections individuels pour chaque table.</span><span class="sxs-lookup"><span data-stu-id="41939-137">This object contains the code that you must have to access those tables, and to access individual objects and collections for each table.</span></span> <span data-ttu-id="41939-138">L' <xref:System.Data.Linq.DataContext> objet de votre projet est nommé en fonction du nom de votre fichier. dbml.</span><span class="sxs-lookup"><span data-stu-id="41939-138">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="41939-139">Pour ce projet, l' <xref:System.Data.Linq.DataContext> objet est nommé `northwindDataContext` .</span><span class="sxs-lookup"><span data-stu-id="41939-139">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="41939-140">Vous pouvez créer une instance de <xref:System.Data.Linq.DataContext> dans votre code et interroger les tables spécifiées par le Concepteur O/R.</span><span class="sxs-lookup"><span data-stu-id="41939-140">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="41939-141">Ajoutez le code suivant à l' `Load` événement pour interroger les tables qui sont exposées en tant que propriétés de votre contexte de données et trier les résultats.</span><span class="sxs-lookup"><span data-stu-id="41939-141">Add the following code to the `Load` event to query the tables that are exposed as properties of your data context and sort the results.</span></span> <span data-ttu-id="41939-142">La requête trie les résultats selon le nombre de commandes client, dans l’ordre décroissant.</span><span class="sxs-lookup"><span data-stu-id="41939-142">The query sorts the results by the number of customer orders, in descending order.</span></span> <span data-ttu-id="41939-143">Les clients qui ont le même nombre de commandes sont classés par nom de société dans l’ordre croissant (valeur par défaut).</span><span class="sxs-lookup"><span data-stu-id="41939-143">Customers that have the same number of orders are ordered by company name in ascending order (the default).</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form4.vb#10)]  
  
4. <span data-ttu-id="41939-144">Appuyez sur F5 pour exécuter votre projet et afficher les résultats.</span><span class="sxs-lookup"><span data-stu-id="41939-144">Press F5 to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41939-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="41939-145">See also</span></span>

- [<span data-ttu-id="41939-146">LINQ</span><span class="sxs-lookup"><span data-stu-id="41939-146">LINQ</span></span>](index.md)
- [<span data-ttu-id="41939-147">Requêtes</span><span class="sxs-lookup"><span data-stu-id="41939-147">Queries</span></span>](../../../language-reference/queries/index.md)
- [<span data-ttu-id="41939-148">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="41939-148">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="41939-149">Méthode DataContext (Concepteur O/R)</span><span class="sxs-lookup"><span data-stu-id="41939-149">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)

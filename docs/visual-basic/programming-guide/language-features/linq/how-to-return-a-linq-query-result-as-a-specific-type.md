---
title: 'Comment : retourner un résultat de requête LINQ en tant que type spécifique'
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], specific type returned
- projection [LINQ in Visual Basic]
- anonymous types [Visual Basic]
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
ms.assetid: 621bb10a-e5d7-44fb-a025-317964b19d92
ms.openlocfilehash: 249c3eebaeec3d09a297fead07ab056caff1b618
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071805"
---
# <a name="how-to-return-a-linq-query-result-as-a-specific-type-visual-basic"></a><span data-ttu-id="4b626-102">Comment : retourner un résultat de requête LINQ en tant que type spécifique (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4b626-102">How to: Return a LINQ Query Result as a Specific Type (Visual Basic)</span></span>

<span data-ttu-id="4b626-103">LINQ (Language-Integrated Query) facilite l’accès aux informations de la base de données et à l’exécution des requêtes.</span><span class="sxs-lookup"><span data-stu-id="4b626-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span> <span data-ttu-id="4b626-104">Par défaut, les requêtes LINQ retournent une liste d’objets en tant que type anonyme.</span><span class="sxs-lookup"><span data-stu-id="4b626-104">By default, LINQ queries return a list of objects as an anonymous type.</span></span> <span data-ttu-id="4b626-105">Vous pouvez également spécifier qu’une requête retourne une liste d’un type spécifique à l’aide de la `Select` clause.</span><span class="sxs-lookup"><span data-stu-id="4b626-105">You can also specify that a query return a list of a specific type by using the `Select` clause.</span></span>  
  
 <span data-ttu-id="4b626-106">L’exemple suivant montre comment créer une application qui exécute des requêtes sur une base de données SQL Server et projette les résultats sous la forme d’un type nommé spécifique.</span><span class="sxs-lookup"><span data-stu-id="4b626-106">The following example shows how to create a new application that performs queries against a SQL Server database and projects the results as a specific named type.</span></span> <span data-ttu-id="4b626-107">Pour plus d’informations, consultez [types anonymes](../objects-and-classes/anonymous-types.md) et [clause SELECT](../../../language-reference/queries/select-clause.md).</span><span class="sxs-lookup"><span data-stu-id="4b626-107">For more information, see [Anonymous Types](../objects-and-classes/anonymous-types.md) and [Select Clause](../../../language-reference/queries/select-clause.md).</span></span>  
  
 <span data-ttu-id="4b626-108">Les exemples de cette rubrique utilisent l’exemple de base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="4b626-108">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="4b626-109">Si cette base de données n’est pas disponible sur votre ordinateur de développement, vous pouvez la télécharger à partir du Centre de téléchargement Microsoft.</span><span class="sxs-lookup"><span data-stu-id="4b626-109">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="4b626-110">Pour obtenir des instructions, consultez [téléchargement d’exemples de bases de données](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="4b626-110">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="4b626-111">Pour créer une connexion à une base de données</span><span class="sxs-lookup"><span data-stu-id="4b626-111">To create a connection to a database</span></span>  
  
1. <span data-ttu-id="4b626-112">Dans Visual Studio, ouvrez **Explorateur de serveurs** / **Explorateur de base de données** en cliquant sur **Explorateur de serveurs** / **Explorateur de base de données** dans le menu **affichage** .</span><span class="sxs-lookup"><span data-stu-id="4b626-112">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2. <span data-ttu-id="4b626-113">Cliquez avec le bouton droit sur **connexions de données** dans **Explorateur de serveurs** / **Explorateur de base de données** puis cliquez sur **Ajouter une connexion**.</span><span class="sxs-lookup"><span data-stu-id="4b626-113">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3. <span data-ttu-id="4b626-114">Spécifiez une connexion valide à l’exemple de base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="4b626-114">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="4b626-115">Pour ajouter un projet qui contient un fichier LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="4b626-115">To add a project that contains a LINQ to SQL file</span></span>  
  
1. <span data-ttu-id="4b626-116">Dans Visual Studio, dans le menu **fichier** , pointez sur **nouveau** , puis cliquez sur **projet**.</span><span class="sxs-lookup"><span data-stu-id="4b626-116">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="4b626-117">Sélectionnez Visual Basic **Application Windows Forms** comme type de projet.</span><span class="sxs-lookup"><span data-stu-id="4b626-117">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2. <span data-ttu-id="4b626-118">Dans le menu **Projet** , cliquez sur **Ajouter un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="4b626-118">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="4b626-119">Sélectionnez le modèle d’élément **Classes LINQ to SQL** .</span><span class="sxs-lookup"><span data-stu-id="4b626-119">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3. <span data-ttu-id="4b626-120">Nommez le fichier `northwind.dbml`.</span><span class="sxs-lookup"><span data-stu-id="4b626-120">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="4b626-121">Cliquez sur **Add**.</span><span class="sxs-lookup"><span data-stu-id="4b626-121">Click **Add**.</span></span> <span data-ttu-id="4b626-122">Le Concepteur Objet Relationnel (Concepteur O/R) est ouvert pour le fichier Northwind. dbml.</span><span class="sxs-lookup"><span data-stu-id="4b626-122">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="4b626-123">Pour ajouter des tables à interroger dans le Concepteur O/R</span><span class="sxs-lookup"><span data-stu-id="4b626-123">To add tables to query to the O/R Designer</span></span>  
  
1. <span data-ttu-id="4b626-124">Dans **Explorateur de serveurs** / **Explorateur de base de données**, développez la connexion à la base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="4b626-124">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="4b626-125">Développez le dossier **Tables** .</span><span class="sxs-lookup"><span data-stu-id="4b626-125">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="4b626-126">Si vous avez fermé le Concepteur O/R, vous pouvez le rouvrir en double-cliquant sur le fichier Northwind. dbml que vous avez ajouté précédemment.</span><span class="sxs-lookup"><span data-stu-id="4b626-126">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2. <span data-ttu-id="4b626-127">Cliquez sur la table Customers et faites-la glisser vers le volet gauche du concepteur.</span><span class="sxs-lookup"><span data-stu-id="4b626-127">Click the Customers table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="4b626-128">Le concepteur crée un nouvel `Customer` objet pour votre projet.</span><span class="sxs-lookup"><span data-stu-id="4b626-128">The designer creates a new `Customer` object for your project.</span></span> <span data-ttu-id="4b626-129">Vous pouvez projeter un résultat de requête en tant que `Customer` type ou en tant que type que vous créez.</span><span class="sxs-lookup"><span data-stu-id="4b626-129">You can project a query result as the `Customer` type or as a type that you create.</span></span> <span data-ttu-id="4b626-130">Cet exemple crée un nouveau type dans une procédure ultérieure et projette un résultat de requête comme ce type.</span><span class="sxs-lookup"><span data-stu-id="4b626-130">This sample will create a new type in a later procedure and project a query result as that type.</span></span>  
  
3. <span data-ttu-id="4b626-131">Enregistrez vos modifications et fermez le concepteur.</span><span class="sxs-lookup"><span data-stu-id="4b626-131">Save your changes and close the designer.</span></span>  
  
4. <span data-ttu-id="4b626-132">Enregistrez votre projet.</span><span class="sxs-lookup"><span data-stu-id="4b626-132">Save your project.</span></span>  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="4b626-133">Pour ajouter du code pour interroger la base de données et afficher les résultats</span><span class="sxs-lookup"><span data-stu-id="4b626-133">To add code to query the database and display the results</span></span>  
  
1. <span data-ttu-id="4b626-134">À partir de la **boîte à outils**, faites glisser un <xref:System.Windows.Forms.DataGridView> contrôle sur le Windows Form par défaut de votre projet, Form1.</span><span class="sxs-lookup"><span data-stu-id="4b626-134">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2. <span data-ttu-id="4b626-135">Double-cliquez sur Form1 pour modifier la classe Form1.</span><span class="sxs-lookup"><span data-stu-id="4b626-135">Double-click Form1 to modify the Form1 class.</span></span>  
  
3. <span data-ttu-id="4b626-136">Après l' `End Class` instruction de la classe Form1, ajoutez le code suivant pour créer un `CustomerInfo` type destiné à contenir les résultats de la requête pour cet exemple.</span><span class="sxs-lookup"><span data-stu-id="4b626-136">After the `End Class` statement of the Form1 class, add the following code to create a `CustomerInfo` type to hold the query results for this sample.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form8.vb#16)]  
  
4. <span data-ttu-id="4b626-137">Quand vous avez ajouté des tables au Concepteur O/R, le concepteur a ajouté un <xref:System.Data.Linq.DataContext> objet à votre projet.</span><span class="sxs-lookup"><span data-stu-id="4b626-137">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object to your project.</span></span> <span data-ttu-id="4b626-138">Cet objet contient le code dont vous devez disposer pour accéder à ces tables et pour accéder à des objets et des collections individuels pour chaque table.</span><span class="sxs-lookup"><span data-stu-id="4b626-138">This object contains the code that you must have to access those tables, and to access individual objects and collections for each table.</span></span> <span data-ttu-id="4b626-139">L' <xref:System.Data.Linq.DataContext> objet de votre projet est nommé en fonction du nom de votre fichier. dbml.</span><span class="sxs-lookup"><span data-stu-id="4b626-139">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="4b626-140">Pour ce projet, l' <xref:System.Data.Linq.DataContext> objet est nommé `northwindDataContext` .</span><span class="sxs-lookup"><span data-stu-id="4b626-140">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="4b626-141">Vous pouvez créer une instance de <xref:System.Data.Linq.DataContext> dans votre code et interroger les tables spécifiées par le Concepteur O/R.</span><span class="sxs-lookup"><span data-stu-id="4b626-141">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="4b626-142">Dans l' `Load` événement de la classe Form1, ajoutez le code suivant pour interroger les tables qui sont exposées en tant que propriétés de votre contexte de données.</span><span class="sxs-lookup"><span data-stu-id="4b626-142">In the `Load` event of the Form1 class, add the following code to query the tables that are exposed as properties of your data context.</span></span> <span data-ttu-id="4b626-143">La `Select` clause de la requête créera un nouveau `CustomerInfo` type au lieu d’un type anonyme pour chaque élément du résultat de la requête.</span><span class="sxs-lookup"><span data-stu-id="4b626-143">The `Select` clause of the query will create a new `CustomerInfo` type instead of an anonymous type for each item of the query result.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form8.vb#15)]  
  
5. <span data-ttu-id="4b626-144">Appuyez sur F5 pour exécuter votre projet et afficher les résultats.</span><span class="sxs-lookup"><span data-stu-id="4b626-144">Press F5 to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b626-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4b626-145">See also</span></span>

- [<span data-ttu-id="4b626-146">LINQ</span><span class="sxs-lookup"><span data-stu-id="4b626-146">LINQ</span></span>](index.md)
- [<span data-ttu-id="4b626-147">Requêtes</span><span class="sxs-lookup"><span data-stu-id="4b626-147">Queries</span></span>](../../../language-reference/queries/index.md)
- [<span data-ttu-id="4b626-148">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="4b626-148">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="4b626-149">DataContext, méthodes (Concepteur O/R)</span><span class="sxs-lookup"><span data-stu-id="4b626-149">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)

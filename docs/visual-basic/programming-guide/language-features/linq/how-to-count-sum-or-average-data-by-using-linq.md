---
title: 'How to: Count, Sum, or Average Data by Using LINQ'
ms.date: 07/20/2015
helpviewer_keywords:
- average operator [LINQ in Visual Basic]
- aggregate operator [LINQ in Visual Basic]
- aggregate queries
- queries [LINQ in Visual Basic], sum results
- Aggregate clause [Visual Basic]
- sum operator [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], aggregate queries
- queries [LINQ in Visual Basic], counting results
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
- count operator [LINQ in Visual Basic]
ms.assetid: 51ca1f59-7770-4884-8b76-113002e54fc0
ms.openlocfilehash: 7e105c75653f979f53567ef49f1f4cdeafaa4d0f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345011"
---
# <a name="how-to-count-sum-or-average-data-by-using-linq-visual-basic"></a><span data-ttu-id="c4078-102">Comment : compter, additionner ou faire la moyenne de données à l'aide de LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c4078-102">How to: Count, Sum, or Average Data by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="c4078-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span><span class="sxs-lookup"><span data-stu-id="c4078-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span>  
  
 <span data-ttu-id="c4078-104">The following example shows how to create a new application that performs queries against a SQL Server database.</span><span class="sxs-lookup"><span data-stu-id="c4078-104">The following example shows how to create a new application that performs queries against a SQL Server database.</span></span> <span data-ttu-id="c4078-105">The sample counts, sums, and averages the results by using the `Aggregate` and `Group By` clauses.</span><span class="sxs-lookup"><span data-stu-id="c4078-105">The sample counts, sums, and averages the results by using the `Aggregate` and `Group By` clauses.</span></span> <span data-ttu-id="c4078-106">For more information, see [Aggregate Clause](../../../../visual-basic/language-reference/queries/aggregate-clause.md) and [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="c4078-106">For more information, see [Aggregate Clause](../../../../visual-basic/language-reference/queries/aggregate-clause.md) and [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span></span>  
  
 <span data-ttu-id="c4078-107">The examples in this topic use the Northwind sample database.</span><span class="sxs-lookup"><span data-stu-id="c4078-107">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="c4078-108">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span><span class="sxs-lookup"><span data-stu-id="c4078-108">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="c4078-109">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="c4078-109">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="c4078-110">To create a connection to a database</span><span class="sxs-lookup"><span data-stu-id="c4078-110">To create a connection to a database</span></span>  
  
1. <span data-ttu-id="c4078-111">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span><span class="sxs-lookup"><span data-stu-id="c4078-111">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2. <span data-ttu-id="c4078-112">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span><span class="sxs-lookup"><span data-stu-id="c4078-112">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3. <span data-ttu-id="c4078-113">Specify a valid connection to the Northwind sample database.</span><span class="sxs-lookup"><span data-stu-id="c4078-113">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="c4078-114">To add a project that contains a LINQ to SQL file</span><span class="sxs-lookup"><span data-stu-id="c4078-114">To add a project that contains a LINQ to SQL file</span></span>  
  
1. <span data-ttu-id="c4078-115">Dans Visual Studio, dans le menu **Fichier**,pointez sur **Nouveau**, puis cliquez sur **Projet**.</span><span class="sxs-lookup"><span data-stu-id="c4078-115">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="c4078-116">Select Visual Basic **Windows Forms Application** as the project type.</span><span class="sxs-lookup"><span data-stu-id="c4078-116">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2. <span data-ttu-id="c4078-117">Dans le menu **Projet** , cliquez sur **Ajouter un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="c4078-117">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="c4078-118">Select the **LINQ to SQL Classes** item template.</span><span class="sxs-lookup"><span data-stu-id="c4078-118">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3. <span data-ttu-id="c4078-119">Nommez le fichier `northwind.dbml`.</span><span class="sxs-lookup"><span data-stu-id="c4078-119">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="c4078-120">Cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="c4078-120">Click **Add**.</span></span> <span data-ttu-id="c4078-121">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span><span class="sxs-lookup"><span data-stu-id="c4078-121">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="c4078-122">To add tables to query to the O/R Designer</span><span class="sxs-lookup"><span data-stu-id="c4078-122">To add tables to query to the O/R Designer</span></span>  
  
1. <span data-ttu-id="c4078-123">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span><span class="sxs-lookup"><span data-stu-id="c4078-123">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="c4078-124">Expand the **Tables** folder.</span><span class="sxs-lookup"><span data-stu-id="c4078-124">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="c4078-125">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span><span class="sxs-lookup"><span data-stu-id="c4078-125">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2. <span data-ttu-id="c4078-126">Click the Customers table and drag it to the left pane of the designer.</span><span class="sxs-lookup"><span data-stu-id="c4078-126">Click the Customers table and drag it to the left pane of the designer.</span></span> <span data-ttu-id="c4078-127">Click the Orders table and drag it to the left pane of the designer.</span><span class="sxs-lookup"><span data-stu-id="c4078-127">Click the Orders table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="c4078-128">The designer creates new `Customer` and `Order` objects for your project.</span><span class="sxs-lookup"><span data-stu-id="c4078-128">The designer creates new `Customer` and `Order` objects for your project.</span></span> <span data-ttu-id="c4078-129">Notice that the designer automatically detects relationships between the tables and creates child properties for related objects.</span><span class="sxs-lookup"><span data-stu-id="c4078-129">Notice that the designer automatically detects relationships between the tables and creates child properties for related objects.</span></span> <span data-ttu-id="c4078-130">For example, IntelliSense will show that the `Customer` object has an `Orders` property for all orders related to that customer.</span><span class="sxs-lookup"><span data-stu-id="c4078-130">For example, IntelliSense will show that the `Customer` object has an `Orders` property for all orders related to that customer.</span></span>  
  
3. <span data-ttu-id="c4078-131">Save your changes and close the designer.</span><span class="sxs-lookup"><span data-stu-id="c4078-131">Save your changes and close the designer.</span></span>  
  
4. <span data-ttu-id="c4078-132">Enregistrez votre projet.</span><span class="sxs-lookup"><span data-stu-id="c4078-132">Save your project.</span></span>  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="c4078-133">To add code to query the database and display the results</span><span class="sxs-lookup"><span data-stu-id="c4078-133">To add code to query the database and display the results</span></span>  
  
1. <span data-ttu-id="c4078-134">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span><span class="sxs-lookup"><span data-stu-id="c4078-134">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2. <span data-ttu-id="c4078-135">Double-click Form1 to add code to the `Load` event of the form.</span><span class="sxs-lookup"><span data-stu-id="c4078-135">Double-click Form1 to add code to the `Load` event of the form.</span></span>  
  
3. <span data-ttu-id="c4078-136">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span><span class="sxs-lookup"><span data-stu-id="c4078-136">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="c4078-137">This object contains the code that you must have to access those tables, and to access individual objects and collections for each table.</span><span class="sxs-lookup"><span data-stu-id="c4078-137">This object contains the code that you must have to access those tables, and to access individual objects and collections for each table.</span></span> <span data-ttu-id="c4078-138">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span><span class="sxs-lookup"><span data-stu-id="c4078-138">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="c4078-139">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="c4078-139">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="c4078-140">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span><span class="sxs-lookup"><span data-stu-id="c4078-140">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="c4078-141">Add the following code to the `Load` event to query the tables that are exposed as properties of your <xref:System.Data.Linq.DataContext> and count, sum, and average the results.</span><span class="sxs-lookup"><span data-stu-id="c4078-141">Add the following code to the `Load` event to query the tables that are exposed as properties of your <xref:System.Data.Linq.DataContext> and count, sum, and average the results.</span></span> <span data-ttu-id="c4078-142">The sample uses the `Aggregate` clause to query for a single result, and the `Group By` clause to show an average for grouped results.</span><span class="sxs-lookup"><span data-stu-id="c4078-142">The sample uses the `Aggregate` clause to query for a single result, and the `Group By` clause to show an average for grouped results.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form6.vb#13)]  
  
4. <span data-ttu-id="c4078-143">Press F5 to run your project and view the results.</span><span class="sxs-lookup"><span data-stu-id="c4078-143">Press F5 to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4078-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c4078-144">See also</span></span>

- [<span data-ttu-id="c4078-145">LINQ</span><span class="sxs-lookup"><span data-stu-id="c4078-145">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="c4078-146">Requêtes</span><span class="sxs-lookup"><span data-stu-id="c4078-146">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="c4078-147">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="c4078-147">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="c4078-148">DataContext, méthodes (Concepteur O/R)</span><span class="sxs-lookup"><span data-stu-id="c4078-148">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [<span data-ttu-id="c4078-149">Aggregate (clause)</span><span class="sxs-lookup"><span data-stu-id="c4078-149">Aggregate Clause</span></span>](../../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [<span data-ttu-id="c4078-150">Group By (clause)</span><span class="sxs-lookup"><span data-stu-id="c4078-150">Group By Clause</span></span>](../../../../visual-basic/language-reference/queries/group-by-clause.md)

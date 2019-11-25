---
title: 'How to: Sort Query Results by Using LINQ'
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
ms.openlocfilehash: 020e4a3800515329b29e2941baf50d3d8add4605
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354163"
---
# <a name="how-to-sort-query-results-by-using-linq-visual-basic"></a><span data-ttu-id="dea61-102">Comment : trier les résultats d'une requête à l'aide de LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dea61-102">How to: Sort Query Results by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="dea61-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span><span class="sxs-lookup"><span data-stu-id="dea61-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span>  
  
 <span data-ttu-id="dea61-104">The following example shows how to create a new application that performs queries against a SQL Server database and sorts the results by multiple fields by using the `Order By` clause.</span><span class="sxs-lookup"><span data-stu-id="dea61-104">The following example shows how to create a new application that performs queries against a SQL Server database and sorts the results by multiple fields by using the `Order By` clause.</span></span> <span data-ttu-id="dea61-105">The sort order for each field can be ascending order or descending order.</span><span class="sxs-lookup"><span data-stu-id="dea61-105">The sort order for each field can be ascending order or descending order.</span></span> <span data-ttu-id="dea61-106">For more information, see [Order By Clause](../../../../visual-basic/language-reference/queries/order-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="dea61-106">For more information, see [Order By Clause](../../../../visual-basic/language-reference/queries/order-by-clause.md).</span></span>  
  
 <span data-ttu-id="dea61-107">The examples in this topic use the Northwind sample database.</span><span class="sxs-lookup"><span data-stu-id="dea61-107">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="dea61-108">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span><span class="sxs-lookup"><span data-stu-id="dea61-108">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="dea61-109">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="dea61-109">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="dea61-110">To create a connection to a database</span><span class="sxs-lookup"><span data-stu-id="dea61-110">To create a connection to a database</span></span>  
  
1. <span data-ttu-id="dea61-111">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span><span class="sxs-lookup"><span data-stu-id="dea61-111">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2. <span data-ttu-id="dea61-112">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span><span class="sxs-lookup"><span data-stu-id="dea61-112">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3. <span data-ttu-id="dea61-113">Specify a valid connection to the Northwind sample database.</span><span class="sxs-lookup"><span data-stu-id="dea61-113">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="dea61-114">To add a project that contains a LINQ to SQL file</span><span class="sxs-lookup"><span data-stu-id="dea61-114">To add a project that contains a LINQ to SQL file</span></span>  
  
1. <span data-ttu-id="dea61-115">Dans Visual Studio, dans le menu **Fichier**,pointez sur **Nouveau**, puis cliquez sur **Projet**.</span><span class="sxs-lookup"><span data-stu-id="dea61-115">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="dea61-116">Select Visual Basic **Windows Forms Application** as the project type.</span><span class="sxs-lookup"><span data-stu-id="dea61-116">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2. <span data-ttu-id="dea61-117">Dans le menu **Projet** , cliquez sur **Ajouter un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="dea61-117">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="dea61-118">Select the **LINQ to SQL Classes** item template.</span><span class="sxs-lookup"><span data-stu-id="dea61-118">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3. <span data-ttu-id="dea61-119">Nommez le fichier `northwind.dbml`.</span><span class="sxs-lookup"><span data-stu-id="dea61-119">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="dea61-120">Cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="dea61-120">Click **Add**.</span></span> <span data-ttu-id="dea61-121">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span><span class="sxs-lookup"><span data-stu-id="dea61-121">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="dea61-122">To add tables to query to the O/R Designer</span><span class="sxs-lookup"><span data-stu-id="dea61-122">To add tables to query to the O/R Designer</span></span>  
  
1. <span data-ttu-id="dea61-123">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span><span class="sxs-lookup"><span data-stu-id="dea61-123">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="dea61-124">Expand the **Tables** folder.</span><span class="sxs-lookup"><span data-stu-id="dea61-124">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="dea61-125">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span><span class="sxs-lookup"><span data-stu-id="dea61-125">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2. <span data-ttu-id="dea61-126">Click the Customers table and drag it to the left pane of the designer.</span><span class="sxs-lookup"><span data-stu-id="dea61-126">Click the Customers table and drag it to the left pane of the designer.</span></span> <span data-ttu-id="dea61-127">Click the Orders table and drag it to the left pane of the designer.</span><span class="sxs-lookup"><span data-stu-id="dea61-127">Click the Orders table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="dea61-128">The designer creates new `Customer` and `Order` objects for your project.</span><span class="sxs-lookup"><span data-stu-id="dea61-128">The designer creates new `Customer` and `Order` objects for your project.</span></span> <span data-ttu-id="dea61-129">Notice that the designer automatically detects relationships between the tables and creates child properties for related objects.</span><span class="sxs-lookup"><span data-stu-id="dea61-129">Notice that the designer automatically detects relationships between the tables and creates child properties for related objects.</span></span> <span data-ttu-id="dea61-130">For example, IntelliSense will show that the `Customer` object has an `Orders` property for all orders related to that customer.</span><span class="sxs-lookup"><span data-stu-id="dea61-130">For example, IntelliSense will show that the `Customer` object has an `Orders` property for all orders related to that customer.</span></span>  
  
3. <span data-ttu-id="dea61-131">Save your changes and close the designer.</span><span class="sxs-lookup"><span data-stu-id="dea61-131">Save your changes and close the designer.</span></span>  
  
4. <span data-ttu-id="dea61-132">Enregistrez votre projet.</span><span class="sxs-lookup"><span data-stu-id="dea61-132">Save your project.</span></span>  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="dea61-133">To add code to query the database and display the results</span><span class="sxs-lookup"><span data-stu-id="dea61-133">To add code to query the database and display the results</span></span>  
  
1. <span data-ttu-id="dea61-134">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span><span class="sxs-lookup"><span data-stu-id="dea61-134">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2. <span data-ttu-id="dea61-135">Double-click Form1 to add code to the `Load` event of the form.</span><span class="sxs-lookup"><span data-stu-id="dea61-135">Double-click Form1 to add code to the `Load` event of the form.</span></span>  
  
3. <span data-ttu-id="dea61-136">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object to your project.</span><span class="sxs-lookup"><span data-stu-id="dea61-136">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object to your project.</span></span> <span data-ttu-id="dea61-137">This object contains the code that you must have to access those tables, and to access individual objects and collections for each table.</span><span class="sxs-lookup"><span data-stu-id="dea61-137">This object contains the code that you must have to access those tables, and to access individual objects and collections for each table.</span></span> <span data-ttu-id="dea61-138">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span><span class="sxs-lookup"><span data-stu-id="dea61-138">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="dea61-139">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="dea61-139">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="dea61-140">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span><span class="sxs-lookup"><span data-stu-id="dea61-140">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="dea61-141">Add the following code to the `Load` event to query the tables that are exposed as properties of your data context and sort the results.</span><span class="sxs-lookup"><span data-stu-id="dea61-141">Add the following code to the `Load` event to query the tables that are exposed as properties of your data context and sort the results.</span></span> <span data-ttu-id="dea61-142">The query sorts the results by the number of customer orders, in descending order.</span><span class="sxs-lookup"><span data-stu-id="dea61-142">The query sorts the results by the number of customer orders, in descending order.</span></span> <span data-ttu-id="dea61-143">Customers that have the same number of orders are ordered by company name in ascending order (the default).</span><span class="sxs-lookup"><span data-stu-id="dea61-143">Customers that have the same number of orders are ordered by company name in ascending order (the default).</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form4.vb#10)]  
  
4. <span data-ttu-id="dea61-144">Press F5 to run your project and view the results.</span><span class="sxs-lookup"><span data-stu-id="dea61-144">Press F5 to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dea61-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dea61-145">See also</span></span>

- [<span data-ttu-id="dea61-146">LINQ</span><span class="sxs-lookup"><span data-stu-id="dea61-146">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="dea61-147">Requêtes</span><span class="sxs-lookup"><span data-stu-id="dea61-147">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="dea61-148">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="dea61-148">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="dea61-149">DataContext, méthodes (Concepteur O/R)</span><span class="sxs-lookup"><span data-stu-id="dea61-149">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)

---
title: 'How to: Filter Query Results by Using LINQ'
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
ms.openlocfilehash: 2ea8a852a2f012ddb25ec1198c66e09df880ff47
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344986"
---
# <a name="how-to-filter-query-results-by-using-linq-visual-basic"></a><span data-ttu-id="a97a1-102">Comment : filtrer les résultats d'une requête à l'aide de LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a97a1-102">How to: Filter Query Results by Using LINQ (Visual Basic)</span></span>

<span data-ttu-id="a97a1-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span><span class="sxs-lookup"><span data-stu-id="a97a1-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span>

<span data-ttu-id="a97a1-104">The following example shows how to create a new application that performs queries against a SQL Server database and filters the results by a particular value by using the `Where` clause.</span><span class="sxs-lookup"><span data-stu-id="a97a1-104">The following example shows how to create a new application that performs queries against a SQL Server database and filters the results by a particular value by using the `Where` clause.</span></span> <span data-ttu-id="a97a1-105">For more information, see [Where Clause](../../../../visual-basic/language-reference/queries/where-clause.md).</span><span class="sxs-lookup"><span data-stu-id="a97a1-105">For more information, see [Where Clause](../../../../visual-basic/language-reference/queries/where-clause.md).</span></span>

<span data-ttu-id="a97a1-106">The examples in this topic use the Northwind sample database.</span><span class="sxs-lookup"><span data-stu-id="a97a1-106">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="a97a1-107">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span><span class="sxs-lookup"><span data-stu-id="a97a1-107">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="a97a1-108">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="a97a1-108">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="a97a1-109">To create a connection to a database</span><span class="sxs-lookup"><span data-stu-id="a97a1-109">To create a connection to a database</span></span>

1. <span data-ttu-id="a97a1-110">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span><span class="sxs-lookup"><span data-stu-id="a97a1-110">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>

2. <span data-ttu-id="a97a1-111">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span><span class="sxs-lookup"><span data-stu-id="a97a1-111">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>

3. <span data-ttu-id="a97a1-112">Specify a valid connection to the Northwind sample database.</span><span class="sxs-lookup"><span data-stu-id="a97a1-112">Specify a valid connection to the Northwind sample database.</span></span>

## <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="a97a1-113">To add a project that contains a LINQ to SQL file</span><span class="sxs-lookup"><span data-stu-id="a97a1-113">To add a project that contains a LINQ to SQL file</span></span>

1. <span data-ttu-id="a97a1-114">Dans Visual Studio, dans le menu **Fichier**,pointez sur **Nouveau**, puis cliquez sur **Projet**.</span><span class="sxs-lookup"><span data-stu-id="a97a1-114">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="a97a1-115">Select Visual Basic **Windows Forms Application** as the project type.</span><span class="sxs-lookup"><span data-stu-id="a97a1-115">Select Visual Basic **Windows Forms Application** as the project type.</span></span>

2. <span data-ttu-id="a97a1-116">Dans le menu **Projet** , cliquez sur **Ajouter un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="a97a1-116">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="a97a1-117">Select the **LINQ to SQL Classes** item template.</span><span class="sxs-lookup"><span data-stu-id="a97a1-117">Select the **LINQ to SQL Classes** item template.</span></span>

3. <span data-ttu-id="a97a1-118">Nommez le fichier `northwind.dbml`.</span><span class="sxs-lookup"><span data-stu-id="a97a1-118">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="a97a1-119">Cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="a97a1-119">Click **Add**.</span></span> <span data-ttu-id="a97a1-120">The Object Relational Designer (O/R Designer) opens for the northwind.dbml file.</span><span class="sxs-lookup"><span data-stu-id="a97a1-120">The Object Relational Designer (O/R Designer) opens for the northwind.dbml file.</span></span>

## <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="a97a1-121">To add tables to query to the O/R Designer</span><span class="sxs-lookup"><span data-stu-id="a97a1-121">To add tables to query to the O/R Designer</span></span>

1. <span data-ttu-id="a97a1-122">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span><span class="sxs-lookup"><span data-stu-id="a97a1-122">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="a97a1-123">Expand the **Tables** folder.</span><span class="sxs-lookup"><span data-stu-id="a97a1-123">Expand the **Tables** folder.</span></span>

     <span data-ttu-id="a97a1-124">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span><span class="sxs-lookup"><span data-stu-id="a97a1-124">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>

2. <span data-ttu-id="a97a1-125">Click the Customers table and drag it to the left pane of the designer.</span><span class="sxs-lookup"><span data-stu-id="a97a1-125">Click the Customers table and drag it to the left pane of the designer.</span></span> <span data-ttu-id="a97a1-126">Click the Orders table and drag it to the left pane of the designer.</span><span class="sxs-lookup"><span data-stu-id="a97a1-126">Click the Orders table and drag it to the left pane of the designer.</span></span>

     <span data-ttu-id="a97a1-127">The designer creates new `Customer` and `Order` objects for your project.</span><span class="sxs-lookup"><span data-stu-id="a97a1-127">The designer creates new `Customer` and `Order` objects for your project.</span></span> <span data-ttu-id="a97a1-128">Notice that the designer automatically detects relationships between the tables and creates child properties for related objects.</span><span class="sxs-lookup"><span data-stu-id="a97a1-128">Notice that the designer automatically detects relationships between the tables and creates child properties for related objects.</span></span> <span data-ttu-id="a97a1-129">For example, IntelliSense will show that the `Customer` object has an `Orders` property for all orders related to that customer.</span><span class="sxs-lookup"><span data-stu-id="a97a1-129">For example, IntelliSense will show that the `Customer` object has an `Orders` property for all orders related to that customer.</span></span>

3. <span data-ttu-id="a97a1-130">Save your changes and close the designer.</span><span class="sxs-lookup"><span data-stu-id="a97a1-130">Save your changes and close the designer.</span></span>

4. <span data-ttu-id="a97a1-131">Enregistrez votre projet.</span><span class="sxs-lookup"><span data-stu-id="a97a1-131">Save your project.</span></span>

## <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="a97a1-132">To add code to query the database and display the results</span><span class="sxs-lookup"><span data-stu-id="a97a1-132">To add code to query the database and display the results</span></span>

1. <span data-ttu-id="a97a1-133">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span><span class="sxs-lookup"><span data-stu-id="a97a1-133">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>

2. <span data-ttu-id="a97a1-134">Double-click Form1 to add code to the `Load` event of the form.</span><span class="sxs-lookup"><span data-stu-id="a97a1-134">Double-click Form1 to add code to the `Load` event of the form.</span></span>

3. <span data-ttu-id="a97a1-135">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span><span class="sxs-lookup"><span data-stu-id="a97a1-135">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="a97a1-136">This object contains the code that you must have to access those tables, in addition to individual objects and collections for each table.</span><span class="sxs-lookup"><span data-stu-id="a97a1-136">This object contains the code that you must have to access those tables, in addition to individual objects and collections for each table.</span></span> <span data-ttu-id="a97a1-137">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span><span class="sxs-lookup"><span data-stu-id="a97a1-137">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="a97a1-138">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="a97a1-138">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>

    <span data-ttu-id="a97a1-139">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span><span class="sxs-lookup"><span data-stu-id="a97a1-139">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>

    <span data-ttu-id="a97a1-140">Add the following code to the `Load` event to query the tables that are exposed as properties of your data context.</span><span class="sxs-lookup"><span data-stu-id="a97a1-140">Add the following code to the `Load` event to query the tables that are exposed as properties of your data context.</span></span> <span data-ttu-id="a97a1-141">The query filters the results and returns only customers that are located in `London`.</span><span class="sxs-lookup"><span data-stu-id="a97a1-141">The query filters the results and returns only customers that are located in `London`.</span></span>

    [!code-vb[VbLINQToSQLHowTos#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form5.vb#11)]

4. <span data-ttu-id="a97a1-142">Press F5 to run your project and view the results.</span><span class="sxs-lookup"><span data-stu-id="a97a1-142">Press F5 to run your project and view the results.</span></span>

5. <span data-ttu-id="a97a1-143">Following are some other filters that you can try.</span><span class="sxs-lookup"><span data-stu-id="a97a1-143">Following are some other filters that you can try.</span></span>

    [!code-vb[VbLINQToSQLHowTos#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form5.vb#12)]

## <a name="see-also"></a><span data-ttu-id="a97a1-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a97a1-144">See also</span></span>

- [<span data-ttu-id="a97a1-145">LINQ</span><span class="sxs-lookup"><span data-stu-id="a97a1-145">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="a97a1-146">Requêtes</span><span class="sxs-lookup"><span data-stu-id="a97a1-146">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="a97a1-147">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="a97a1-147">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="a97a1-148">DataContext, méthodes (Concepteur O/R)</span><span class="sxs-lookup"><span data-stu-id="a97a1-148">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)

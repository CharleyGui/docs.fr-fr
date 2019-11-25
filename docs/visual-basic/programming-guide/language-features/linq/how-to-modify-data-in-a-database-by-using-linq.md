---
title: 'How to: Modify Data in a Database by Using LINQ'
ms.date: 07/20/2015
helpviewer_keywords:
- inserting rows [LINQ to SQL]
- deleting rows [LINQ to SQL]
- updating rows [LINQ to SQL]
- inserting data [Visual Basic]
- deleting data
- data [Visual Basic], updating
- updating data [LINQ]
- queries [LINQ in Visual Basic], data changes in database
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: cf52635f-0c1b-46c3-aff1-bdf181cf19b1
ms.openlocfilehash: 9a10efef5ae92dd21888594ae80a3fc07869a8c0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344942"
---
# <a name="how-to-modify-data-in-a-database-by-using-linq-visual-basic"></a><span data-ttu-id="1b4df-102">Comment : modifier des données dans une base de données à l'aide de LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1b4df-102">How to: Modify Data in a Database by Using LINQ (Visual Basic)</span></span>

<span data-ttu-id="1b4df-103">Language-Integrated Query (LINQ) queries make it easy to access database information and modify values in the database.</span><span class="sxs-lookup"><span data-stu-id="1b4df-103">Language-Integrated Query (LINQ) queries make it easy to access database information and modify values in the database.</span></span>

<span data-ttu-id="1b4df-104">The following example shows how to create a new application that retrieves and updates information in a SQL Server database.</span><span class="sxs-lookup"><span data-stu-id="1b4df-104">The following example shows how to create a new application that retrieves and updates information in a SQL Server database.</span></span>

<span data-ttu-id="1b4df-105">The examples in this topic use the Northwind sample database.</span><span class="sxs-lookup"><span data-stu-id="1b4df-105">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="1b4df-106">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span><span class="sxs-lookup"><span data-stu-id="1b4df-106">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="1b4df-107">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="1b4df-107">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>

### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="1b4df-108">To create a connection to a database</span><span class="sxs-lookup"><span data-stu-id="1b4df-108">To create a connection to a database</span></span>

1. <span data-ttu-id="1b4df-109">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking the **View** menu, and then select **Server Explorer**/**Database Explorer**.</span><span class="sxs-lookup"><span data-stu-id="1b4df-109">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking the **View** menu, and then select **Server Explorer**/**Database Explorer**.</span></span>

2. <span data-ttu-id="1b4df-110">Right-click **Data Connections** in **Server Explorer**/**Database Explorer**, and click **Add Connection**.</span><span class="sxs-lookup"><span data-stu-id="1b4df-110">Right-click **Data Connections** in **Server Explorer**/**Database Explorer**, and click **Add Connection**.</span></span>

3. <span data-ttu-id="1b4df-111">Specify a valid connection to the Northwind sample database.</span><span class="sxs-lookup"><span data-stu-id="1b4df-111">Specify a valid connection to the Northwind sample database.</span></span>

### <a name="to-add-a-project-with-a-linq-to-sql-file"></a><span data-ttu-id="1b4df-112">To add a Project with a LINQ to SQL file</span><span class="sxs-lookup"><span data-stu-id="1b4df-112">To add a Project with a LINQ to SQL file</span></span>

1. <span data-ttu-id="1b4df-113">Dans Visual Studio, dans le menu **Fichier**,pointez sur **Nouveau**, puis cliquez sur **Projet**.</span><span class="sxs-lookup"><span data-stu-id="1b4df-113">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="1b4df-114">Select Visual Basic **Windows Forms Application** as the project type.</span><span class="sxs-lookup"><span data-stu-id="1b4df-114">Select Visual Basic **Windows Forms Application** as the project type.</span></span>

2. <span data-ttu-id="1b4df-115">Dans le menu **Projet** , cliquez sur **Ajouter un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="1b4df-115">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="1b4df-116">Select the **LINQ to SQL Classes** item template.</span><span class="sxs-lookup"><span data-stu-id="1b4df-116">Select the **LINQ to SQL Classes** item template.</span></span>

3. <span data-ttu-id="1b4df-117">Nommez le fichier `northwind.dbml`.</span><span class="sxs-lookup"><span data-stu-id="1b4df-117">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="1b4df-118">Cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="1b4df-118">Click **Add**.</span></span> <span data-ttu-id="1b4df-119">The Object Relational Designer (O/R Designer) is opened for the `northwind.dbml` file.</span><span class="sxs-lookup"><span data-stu-id="1b4df-119">The Object Relational Designer (O/R Designer) is opened for the `northwind.dbml` file.</span></span>

### <a name="to-add-tables-to-query-and-modify-to-the-designer"></a><span data-ttu-id="1b4df-120">To add tables to query and modify to the designer</span><span class="sxs-lookup"><span data-stu-id="1b4df-120">To add tables to query and modify to the designer</span></span>

1. <span data-ttu-id="1b4df-121">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span><span class="sxs-lookup"><span data-stu-id="1b4df-121">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="1b4df-122">Expand the **Tables** folder.</span><span class="sxs-lookup"><span data-stu-id="1b4df-122">Expand the **Tables** folder.</span></span>

     <span data-ttu-id="1b4df-123">If you have closed the O/R Designer, you can reopen it by double-clicking the `northwind.dbml` file that you added earlier.</span><span class="sxs-lookup"><span data-stu-id="1b4df-123">If you have closed the O/R Designer, you can reopen it by double-clicking the `northwind.dbml` file that you added earlier.</span></span>

2. <span data-ttu-id="1b4df-124">Click the Customers table and drag it to the left pane of the designer.</span><span class="sxs-lookup"><span data-stu-id="1b4df-124">Click the Customers table and drag it to the left pane of the designer.</span></span>

     <span data-ttu-id="1b4df-125">The designer creates a new Customer object for your project.</span><span class="sxs-lookup"><span data-stu-id="1b4df-125">The designer creates a new Customer object for your project.</span></span>

3. <span data-ttu-id="1b4df-126">Save your changes and close the designer.</span><span class="sxs-lookup"><span data-stu-id="1b4df-126">Save your changes and close the designer.</span></span>

4. <span data-ttu-id="1b4df-127">Enregistrez votre projet.</span><span class="sxs-lookup"><span data-stu-id="1b4df-127">Save your project.</span></span>

### <a name="to-add-code-to-modify-the-database-and-display-the-results"></a><span data-ttu-id="1b4df-128">To add code to modify the database and display the results</span><span class="sxs-lookup"><span data-stu-id="1b4df-128">To add code to modify the database and display the results</span></span>

1. <span data-ttu-id="1b4df-129">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span><span class="sxs-lookup"><span data-stu-id="1b4df-129">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>

2. <span data-ttu-id="1b4df-130">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object to your project.</span><span class="sxs-lookup"><span data-stu-id="1b4df-130">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object to your project.</span></span> <span data-ttu-id="1b4df-131">This object contains code that you can use to access the Customers table.</span><span class="sxs-lookup"><span data-stu-id="1b4df-131">This object contains code that you can use to access the Customers table.</span></span> <span data-ttu-id="1b4df-132">It also contains code that defines  a local Customer object and a Customers collection for the table.</span><span class="sxs-lookup"><span data-stu-id="1b4df-132">It also contains code that defines  a local Customer object and a Customers collection for the table.</span></span> <span data-ttu-id="1b4df-133">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span><span class="sxs-lookup"><span data-stu-id="1b4df-133">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="1b4df-134">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="1b4df-134">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>

     <span data-ttu-id="1b4df-135">You can create an instance of the <xref:System.Data.Linq.DataContext> object in your code and query and modify the Customers collection specified by the O/R Designer.</span><span class="sxs-lookup"><span data-stu-id="1b4df-135">You can create an instance of the <xref:System.Data.Linq.DataContext> object in your code and query and modify the Customers collection specified by the O/R Designer.</span></span> <span data-ttu-id="1b4df-136">Changes that you make to the Customers collection are not reflected in the database until you submit them by calling the <xref:System.Data.Linq.DataContext.SubmitChanges%2A> method of the <xref:System.Data.Linq.DataContext> object.</span><span class="sxs-lookup"><span data-stu-id="1b4df-136">Changes that you make to the Customers collection are not reflected in the database until you submit them by calling the <xref:System.Data.Linq.DataContext.SubmitChanges%2A> method of the <xref:System.Data.Linq.DataContext> object.</span></span>

     <span data-ttu-id="1b4df-137">Double-click the Windows Form, Form1, to add code to the <xref:System.Windows.Forms.Form.Load> event to query the Customers table that is exposed as a property of your <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="1b4df-137">Double-click the Windows Form, Form1, to add code to the <xref:System.Windows.Forms.Form.Load> event to query the Customers table that is exposed as a property of your <xref:System.Data.Linq.DataContext>.</span></span> <span data-ttu-id="1b4df-138">Ajoutez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="1b4df-138">Add the following code:</span></span>

    ```vb
    Private db As northwindDataContext

    Private Sub Form1_Load(ByVal sender As System.Object,
                           ByVal e As System.EventArgs
                          ) Handles MyBase.Load
      db = New northwindDataContext()

      RefreshData()
    End Sub

    Private Sub RefreshData()
      Dim customers = From cust In db.Customers
                      Where cust.City(0) = "W"
                      Select cust

      DataGridView1.DataSource = customers
    End Sub
    ```

3. <span data-ttu-id="1b4df-139">From the **Toolbox**, drag three <xref:System.Windows.Forms.Button> controls onto the form.</span><span class="sxs-lookup"><span data-stu-id="1b4df-139">From the **Toolbox**, drag three <xref:System.Windows.Forms.Button> controls onto the form.</span></span> <span data-ttu-id="1b4df-140">Select the first `Button` control.</span><span class="sxs-lookup"><span data-stu-id="1b4df-140">Select the first `Button` control.</span></span> <span data-ttu-id="1b4df-141">In the **Properties** window, set the `Name` of the `Button` control to `AddButton` and the `Text` to `Add`.</span><span class="sxs-lookup"><span data-stu-id="1b4df-141">In the **Properties** window, set the `Name` of the `Button` control to `AddButton` and the `Text` to `Add`.</span></span> <span data-ttu-id="1b4df-142">Select the second button and set the `Name` property to `UpdateButton` and the `Text` property to `Update`.</span><span class="sxs-lookup"><span data-stu-id="1b4df-142">Select the second button and set the `Name` property to `UpdateButton` and the `Text` property to `Update`.</span></span> <span data-ttu-id="1b4df-143">Select the third button and set the `Name` property to `DeleteButton` and the `Text` property to `Delete`.</span><span class="sxs-lookup"><span data-stu-id="1b4df-143">Select the third button and set the `Name` property to `DeleteButton` and the `Text` property to `Delete`.</span></span>

4. <span data-ttu-id="1b4df-144">Double-click the **Add** button to add code to its `Click` event.</span><span class="sxs-lookup"><span data-stu-id="1b4df-144">Double-click the **Add** button to add code to its `Click` event.</span></span> <span data-ttu-id="1b4df-145">Ajoutez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="1b4df-145">Add the following code:</span></span>

    ```vb
    Private Sub AddButton_Click(ByVal sender As System.Object,
                                ByVal e As System.EventArgs
                               ) Handles AddButton.Click
      Dim cust As New Customer With {
        .City = "Wellington",
        .CompanyName = "Blue Yonder Airlines",
        .ContactName = "Jill Frank",
        .Country = "New Zealand",
        .CustomerID = "JILLF"}

      db.Customers.InsertOnSubmit(cust)

      Try
        db.SubmitChanges()
      Catch
        ' Handle exception.
      End Try

      RefreshData()
    End Sub
    ```

5. <span data-ttu-id="1b4df-146">Double-click the **Update** button to add code to its `Click` event.</span><span class="sxs-lookup"><span data-stu-id="1b4df-146">Double-click the **Update** button to add code to its `Click` event.</span></span> <span data-ttu-id="1b4df-147">Ajoutez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="1b4df-147">Add the following code:</span></span>

    ```vb
    Private Sub UpdateButton_Click(ByVal sender As System.Object, _
                                   ByVal e As System.EventArgs
                                  ) Handles UpdateButton.Click
      Dim updateCust = (From cust In db.Customers
                        Where cust.CustomerID = "JILLF").ToList()(0)

      updateCust.ContactName = "Jill Shrader"
      updateCust.Country = "Wales"
      updateCust.CompanyName = "Red Yonder Airlines"
      updateCust.City = "Cardiff"

      Try
        db.SubmitChanges()
      Catch
        ' Handle exception.
      End Try

      RefreshData()
    End Sub
    ```

6. <span data-ttu-id="1b4df-148">Double-click the **Delete** button to add code to its `Click` event.</span><span class="sxs-lookup"><span data-stu-id="1b4df-148">Double-click the **Delete** button to add code to its `Click` event.</span></span> <span data-ttu-id="1b4df-149">Ajoutez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="1b4df-149">Add the following code:</span></span>

    ```vb
    Private Sub DeleteButton_Click(ByVal sender As System.Object, _
                                   ByVal e As System.EventArgs
                                  ) Handles DeleteButton.Click
      Dim deleteCust = (From cust In db.Customers
                        Where cust.CustomerID = "JILLF").ToList()(0)

      db.Customers.DeleteOnSubmit(deleteCust)

      Try
        db.SubmitChanges()
      Catch
        ' Handle exception.
      End Try

      RefreshData()
    End Sub
    ```

7. <span data-ttu-id="1b4df-150">Appuyez sur F5 pour exécuter votre projet.</span><span class="sxs-lookup"><span data-stu-id="1b4df-150">Press F5 to run your project.</span></span> <span data-ttu-id="1b4df-151">Click **Add** to add a new record.</span><span class="sxs-lookup"><span data-stu-id="1b4df-151">Click **Add** to add a new record.</span></span> <span data-ttu-id="1b4df-152">Click **Update** to modify the new record.</span><span class="sxs-lookup"><span data-stu-id="1b4df-152">Click **Update** to modify the new record.</span></span> <span data-ttu-id="1b4df-153">Click **Delete** to delete the new record.</span><span class="sxs-lookup"><span data-stu-id="1b4df-153">Click **Delete** to delete the new record.</span></span>

## <a name="see-also"></a><span data-ttu-id="1b4df-154">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1b4df-154">See also</span></span>

- [<span data-ttu-id="1b4df-155">LINQ</span><span class="sxs-lookup"><span data-stu-id="1b4df-155">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="1b4df-156">Requêtes</span><span class="sxs-lookup"><span data-stu-id="1b4df-156">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="1b4df-157">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="1b4df-157">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="1b4df-158">DataContext, méthodes (Concepteur O/R)</span><span class="sxs-lookup"><span data-stu-id="1b4df-158">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [<span data-ttu-id="1b4df-159">Guide pratique pour affecter des procédures stockées pour effectuer des mises à jour, des insertions et des suppressions (Concepteur O/R)</span><span class="sxs-lookup"><span data-stu-id="1b4df-159">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)

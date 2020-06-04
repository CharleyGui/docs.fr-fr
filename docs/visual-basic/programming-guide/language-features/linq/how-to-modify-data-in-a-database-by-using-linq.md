---
title: 'Guide pratique : modifier des données dans une base de données à l’aide de LINQ'
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
ms.openlocfilehash: eb076d9156fa66858f2e560422eef0dc61ba22b5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403483"
---
# <a name="how-to-modify-data-in-a-database-by-using-linq-visual-basic"></a><span data-ttu-id="01c29-102">Comment : modifier des données dans une base de données à l'aide de LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="01c29-102">How to: Modify Data in a Database by Using LINQ (Visual Basic)</span></span>

<span data-ttu-id="01c29-103">Les requêtes LINQ (Language-Integrated Query) facilitent l’accès aux informations de la base de données et la modification des valeurs dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="01c29-103">Language-Integrated Query (LINQ) queries make it easy to access database information and modify values in the database.</span></span>

<span data-ttu-id="01c29-104">L’exemple suivant montre comment créer une nouvelle application qui récupère et met à jour des informations dans une base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="01c29-104">The following example shows how to create a new application that retrieves and updates information in a SQL Server database.</span></span>

<span data-ttu-id="01c29-105">Les exemples de cette rubrique utilisent l’exemple de base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="01c29-105">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="01c29-106">Si cette base de données n’est pas disponible sur votre ordinateur de développement, vous pouvez la télécharger à partir du Centre de téléchargement Microsoft.</span><span class="sxs-lookup"><span data-stu-id="01c29-106">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="01c29-107">Pour obtenir des instructions, consultez [téléchargement d’exemples de bases de données](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="01c29-107">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>

### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="01c29-108">Pour créer une connexion à une base de données</span><span class="sxs-lookup"><span data-stu-id="01c29-108">To create a connection to a database</span></span>

1. <span data-ttu-id="01c29-109">Dans Visual Studio, ouvrez **Explorateur de serveurs** / **Explorateur de base de données** en cliquant sur le menu **affichage** , puis sélectionnez **Explorateur de serveurs** / **Explorateur de base de données**.</span><span class="sxs-lookup"><span data-stu-id="01c29-109">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking the **View** menu, and then select **Server Explorer**/**Database Explorer**.</span></span>

2. <span data-ttu-id="01c29-110">Cliquez avec le bouton droit sur **connexions de données** dans **Explorateur de serveurs** / **Explorateur de base de données**, puis cliquez sur **Ajouter une connexion**.</span><span class="sxs-lookup"><span data-stu-id="01c29-110">Right-click **Data Connections** in **Server Explorer**/**Database Explorer**, and click **Add Connection**.</span></span>

3. <span data-ttu-id="01c29-111">Spécifiez une connexion valide à l’exemple de base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="01c29-111">Specify a valid connection to the Northwind sample database.</span></span>

### <a name="to-add-a-project-with-a-linq-to-sql-file"></a><span data-ttu-id="01c29-112">Pour ajouter un projet avec un fichier LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="01c29-112">To add a Project with a LINQ to SQL file</span></span>

1. <span data-ttu-id="01c29-113">Dans Visual Studio, dans le menu **fichier** , pointez sur **nouveau** , puis cliquez sur **projet**.</span><span class="sxs-lookup"><span data-stu-id="01c29-113">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="01c29-114">Sélectionnez Visual Basic **Application Windows Forms** comme type de projet.</span><span class="sxs-lookup"><span data-stu-id="01c29-114">Select Visual Basic **Windows Forms Application** as the project type.</span></span>

2. <span data-ttu-id="01c29-115">Dans le menu **Projet** , cliquez sur **Ajouter un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="01c29-115">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="01c29-116">Sélectionnez le modèle d’élément **Classes LINQ to SQL** .</span><span class="sxs-lookup"><span data-stu-id="01c29-116">Select the **LINQ to SQL Classes** item template.</span></span>

3. <span data-ttu-id="01c29-117">Nommez le fichier `northwind.dbml`.</span><span class="sxs-lookup"><span data-stu-id="01c29-117">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="01c29-118">Cliquez sur **Add**.</span><span class="sxs-lookup"><span data-stu-id="01c29-118">Click **Add**.</span></span> <span data-ttu-id="01c29-119">Le Concepteur Objet Relationnel (Concepteur O/R) est ouvert pour le `northwind.dbml` fichier.</span><span class="sxs-lookup"><span data-stu-id="01c29-119">The Object Relational Designer (O/R Designer) is opened for the `northwind.dbml` file.</span></span>

### <a name="to-add-tables-to-query-and-modify-to-the-designer"></a><span data-ttu-id="01c29-120">Pour ajouter des tables à interroger et à modifier dans le concepteur</span><span class="sxs-lookup"><span data-stu-id="01c29-120">To add tables to query and modify to the designer</span></span>

1. <span data-ttu-id="01c29-121">Dans **Explorateur de serveurs** / **Explorateur de base de données**, développez la connexion à la base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="01c29-121">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="01c29-122">Développez le dossier **Tables** .</span><span class="sxs-lookup"><span data-stu-id="01c29-122">Expand the **Tables** folder.</span></span>

     <span data-ttu-id="01c29-123">Si vous avez fermé le Concepteur O/R, vous pouvez le rouvrir en double-cliquant sur le `northwind.dbml` fichier que vous avez ajouté précédemment.</span><span class="sxs-lookup"><span data-stu-id="01c29-123">If you have closed the O/R Designer, you can reopen it by double-clicking the `northwind.dbml` file that you added earlier.</span></span>

2. <span data-ttu-id="01c29-124">Cliquez sur la table Customers et faites-la glisser vers le volet gauche du concepteur.</span><span class="sxs-lookup"><span data-stu-id="01c29-124">Click the Customers table and drag it to the left pane of the designer.</span></span>

     <span data-ttu-id="01c29-125">Le concepteur crée un nouvel objet client pour votre projet.</span><span class="sxs-lookup"><span data-stu-id="01c29-125">The designer creates a new Customer object for your project.</span></span>

3. <span data-ttu-id="01c29-126">Enregistrez vos modifications et fermez le concepteur.</span><span class="sxs-lookup"><span data-stu-id="01c29-126">Save your changes and close the designer.</span></span>

4. <span data-ttu-id="01c29-127">Enregistrez votre projet.</span><span class="sxs-lookup"><span data-stu-id="01c29-127">Save your project.</span></span>

### <a name="to-add-code-to-modify-the-database-and-display-the-results"></a><span data-ttu-id="01c29-128">Pour ajouter du code afin de modifier la base de données et d’afficher les résultats</span><span class="sxs-lookup"><span data-stu-id="01c29-128">To add code to modify the database and display the results</span></span>

1. <span data-ttu-id="01c29-129">À partir de la **boîte à outils**, faites glisser un <xref:System.Windows.Forms.DataGridView> contrôle sur le Windows Form par défaut de votre projet, Form1.</span><span class="sxs-lookup"><span data-stu-id="01c29-129">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>

2. <span data-ttu-id="01c29-130">Quand vous avez ajouté des tables au Concepteur O/R, le concepteur a ajouté un <xref:System.Data.Linq.DataContext> objet à votre projet.</span><span class="sxs-lookup"><span data-stu-id="01c29-130">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object to your project.</span></span> <span data-ttu-id="01c29-131">Cet objet contient du code que vous pouvez utiliser pour accéder à la table Customers.</span><span class="sxs-lookup"><span data-stu-id="01c29-131">This object contains code that you can use to access the Customers table.</span></span> <span data-ttu-id="01c29-132">Il contient également du code qui définit un objet Customer local et une collection Customers pour la table.</span><span class="sxs-lookup"><span data-stu-id="01c29-132">It also contains code that defines  a local Customer object and a Customers collection for the table.</span></span> <span data-ttu-id="01c29-133">L' <xref:System.Data.Linq.DataContext> objet de votre projet est nommé en fonction du nom de votre fichier. dbml.</span><span class="sxs-lookup"><span data-stu-id="01c29-133">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="01c29-134">Pour ce projet, l' <xref:System.Data.Linq.DataContext> objet est nommé `northwindDataContext` .</span><span class="sxs-lookup"><span data-stu-id="01c29-134">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>

     <span data-ttu-id="01c29-135">Vous pouvez créer une instance de l' <xref:System.Data.Linq.DataContext> objet dans votre code et interroger et modifier la collection Customers spécifiée par le Concepteur O/R.</span><span class="sxs-lookup"><span data-stu-id="01c29-135">You can create an instance of the <xref:System.Data.Linq.DataContext> object in your code and query and modify the Customers collection specified by the O/R Designer.</span></span> <span data-ttu-id="01c29-136">Les modifications que vous apportez à la collection Customers ne sont pas reflétées dans la base de données tant que vous ne les avez pas envoyées en appelant la <xref:System.Data.Linq.DataContext.SubmitChanges%2A> méthode de l' <xref:System.Data.Linq.DataContext> objet.</span><span class="sxs-lookup"><span data-stu-id="01c29-136">Changes that you make to the Customers collection are not reflected in the database until you submit them by calling the <xref:System.Data.Linq.DataContext.SubmitChanges%2A> method of the <xref:System.Data.Linq.DataContext> object.</span></span>

     <span data-ttu-id="01c29-137">Double-cliquez sur le Windows Form, Form1, pour ajouter du code à l' <xref:System.Windows.Forms.Form.Load> événement afin d’interroger la table Customers exposée en tant que propriété de votre <xref:System.Data.Linq.DataContext> .</span><span class="sxs-lookup"><span data-stu-id="01c29-137">Double-click the Windows Form, Form1, to add code to the <xref:System.Windows.Forms.Form.Load> event to query the Customers table that is exposed as a property of your <xref:System.Data.Linq.DataContext>.</span></span> <span data-ttu-id="01c29-138">Ajoutez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="01c29-138">Add the following code:</span></span>

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

3. <span data-ttu-id="01c29-139">À partir de la **boîte à outils**, faites glisser trois <xref:System.Windows.Forms.Button> contrôles sur le formulaire.</span><span class="sxs-lookup"><span data-stu-id="01c29-139">From the **Toolbox**, drag three <xref:System.Windows.Forms.Button> controls onto the form.</span></span> <span data-ttu-id="01c29-140">Sélectionnez le premier `Button` contrôle.</span><span class="sxs-lookup"><span data-stu-id="01c29-140">Select the first `Button` control.</span></span> <span data-ttu-id="01c29-141">Dans la fenêtre Propriétés, affectez à la **propriété** du contrôle la valeur `Name` `Button` `AddButton` et `Text` à `Add` .</span><span class="sxs-lookup"><span data-stu-id="01c29-141">In the **Properties** window, set the `Name` of the `Button` control to `AddButton` and the `Text` to `Add`.</span></span> <span data-ttu-id="01c29-142">Sélectionnez le deuxième bouton et affectez à la propriété la valeur `Name` `UpdateButton` et `Text` à la propriété `Update` .</span><span class="sxs-lookup"><span data-stu-id="01c29-142">Select the second button and set the `Name` property to `UpdateButton` and the `Text` property to `Update`.</span></span> <span data-ttu-id="01c29-143">Sélectionnez le troisième bouton et affectez à la propriété la valeur `Name` `DeleteButton` et `Text` à la propriété `Delete` .</span><span class="sxs-lookup"><span data-stu-id="01c29-143">Select the third button and set the `Name` property to `DeleteButton` and the `Text` property to `Delete`.</span></span>

4. <span data-ttu-id="01c29-144">Double-cliquez sur le bouton **Ajouter** pour ajouter du code à l' `Click` événement.</span><span class="sxs-lookup"><span data-stu-id="01c29-144">Double-click the **Add** button to add code to its `Click` event.</span></span> <span data-ttu-id="01c29-145">Ajoutez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="01c29-145">Add the following code:</span></span>

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

5. <span data-ttu-id="01c29-146">Double-cliquez sur le bouton **mettre à jour** pour ajouter du code à l' `Click` événement.</span><span class="sxs-lookup"><span data-stu-id="01c29-146">Double-click the **Update** button to add code to its `Click` event.</span></span> <span data-ttu-id="01c29-147">Ajoutez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="01c29-147">Add the following code:</span></span>

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

6. <span data-ttu-id="01c29-148">Double-cliquez sur le bouton **supprimer** pour ajouter du code à l' `Click` événement.</span><span class="sxs-lookup"><span data-stu-id="01c29-148">Double-click the **Delete** button to add code to its `Click` event.</span></span> <span data-ttu-id="01c29-149">Ajoutez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="01c29-149">Add the following code:</span></span>

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

7. <span data-ttu-id="01c29-150">Appuyez sur F5 pour exécuter votre projet.</span><span class="sxs-lookup"><span data-stu-id="01c29-150">Press F5 to run your project.</span></span> <span data-ttu-id="01c29-151">Cliquez sur **Ajouter** pour ajouter un nouvel enregistrement.</span><span class="sxs-lookup"><span data-stu-id="01c29-151">Click **Add** to add a new record.</span></span> <span data-ttu-id="01c29-152">Cliquez sur **mettre à jour** pour modifier le nouvel enregistrement.</span><span class="sxs-lookup"><span data-stu-id="01c29-152">Click **Update** to modify the new record.</span></span> <span data-ttu-id="01c29-153">Cliquez sur **supprimer** pour supprimer le nouvel enregistrement.</span><span class="sxs-lookup"><span data-stu-id="01c29-153">Click **Delete** to delete the new record.</span></span>

## <a name="see-also"></a><span data-ttu-id="01c29-154">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="01c29-154">See also</span></span>

- [<span data-ttu-id="01c29-155">LINQ</span><span class="sxs-lookup"><span data-stu-id="01c29-155">LINQ</span></span>](index.md)
- [<span data-ttu-id="01c29-156">Requêtes</span><span class="sxs-lookup"><span data-stu-id="01c29-156">Queries</span></span>](../../../language-reference/queries/index.md)
- [<span data-ttu-id="01c29-157">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="01c29-157">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="01c29-158">Méthode DataContext (Concepteur O/R)</span><span class="sxs-lookup"><span data-stu-id="01c29-158">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [<span data-ttu-id="01c29-159">Guide pratique pour affecter des procédures stockées pour effectuer des mises à jour, des insertions et des suppressions (Concepteur O/R)</span><span class="sxs-lookup"><span data-stu-id="01c29-159">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)

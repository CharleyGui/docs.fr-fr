---
title: 'Comment : appeler une procédure stockée à l’aide de LINQ'
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], stored procedure calls
- stored procedures sample [Visual Basic]
- stored procedures [LINQ to SQL]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 6436d384-d1e0-40aa-8afd-451007477260
ms.openlocfilehash: f91ccda1842887b3785ce304fd41bdd020a55479
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345026"
---
# <a name="how-to-call-a-stored-procedure-by-using-linq-visual-basic"></a><span data-ttu-id="d0fa4-102">Comment : appeler une procédure stockée à l'aide de LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d0fa4-102">How to: Call a Stored Procedure by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="d0fa4-103">LINQ (Language-Integrated Query) facilite l’accès aux informations de la base de données, notamment les objets de base de données tels que les procédures stockées.</span><span class="sxs-lookup"><span data-stu-id="d0fa4-103">Language-Integrated Query (LINQ) makes it easy to access database information, including database objects such as stored procedures.</span></span>  
  
 <span data-ttu-id="d0fa4-104">L’exemple suivant montre comment créer une application qui appelle une procédure stockée dans une base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d0fa4-104">The following example shows how to create an application that calls a stored procedure in a SQL Server database.</span></span> <span data-ttu-id="d0fa4-105">L’exemple montre comment appeler deux procédures stockées différentes dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="d0fa4-105">The sample shows how to call two different stored procedures in the database.</span></span> <span data-ttu-id="d0fa4-106">Chaque procédure retourne les résultats d’une requête.</span><span class="sxs-lookup"><span data-stu-id="d0fa4-106">Each procedure returns the results of a query.</span></span> <span data-ttu-id="d0fa4-107">Une procédure accepte les paramètres d’entrée, et l’autre procédure n’accepte pas de paramètres.</span><span class="sxs-lookup"><span data-stu-id="d0fa4-107">One procedure takes input parameters, and the other procedure does not take parameters.</span></span>  
  
 <span data-ttu-id="d0fa4-108">Les exemples de cette rubrique utilisent l’exemple de base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="d0fa4-108">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="d0fa4-109">Si cette base de données n'est pas disponible sur votre ordinateur de développement, vous pouvez la télécharger à partir du centre de téléchargement Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d0fa4-109">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="d0fa4-110">Pour obtenir des instructions, consultez [téléchargement d’exemples de bases de données](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="d0fa4-110">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="d0fa4-111">Pour créer une connexion à une base de données</span><span class="sxs-lookup"><span data-stu-id="d0fa4-111">To create a connection to a database</span></span>  
  
1. <span data-ttu-id="d0fa4-112">Dans Visual Studio, ouvrez **Explorateur de serveurs**/**Explorateur de base de données** en cliquant sur Explorateur de serveurs **/Explorateur de base de données dans le** menu **affichage** .</span><span class="sxs-lookup"><span data-stu-id="d0fa4-112">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2. <span data-ttu-id="d0fa4-113">Cliquez avec le bouton droit sur **connexions de données** dans **Explorateur de serveurs**/**Explorateur de base de données** puis cliquez sur **Ajouter une connexion**.</span><span class="sxs-lookup"><span data-stu-id="d0fa4-113">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3. <span data-ttu-id="d0fa4-114">Spécifiez une connexion valide à l’exemple de base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="d0fa4-114">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="d0fa4-115">Pour ajouter un projet qui contient un fichier LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="d0fa4-115">To add a project that contains a LINQ to SQL file</span></span>  
  
1. <span data-ttu-id="d0fa4-116">Dans Visual Studio, dans le menu **Fichier**,pointez sur **Nouveau**, puis cliquez sur **Projet**.</span><span class="sxs-lookup"><span data-stu-id="d0fa4-116">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="d0fa4-117">Sélectionnez Visual Basic **Application Windows Forms** comme type de projet.</span><span class="sxs-lookup"><span data-stu-id="d0fa4-117">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2. <span data-ttu-id="d0fa4-118">Dans le menu **Projet** , cliquez sur **Ajouter un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="d0fa4-118">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="d0fa4-119">Sélectionnez le modèle d’élément **Classes LINQ to SQL** .</span><span class="sxs-lookup"><span data-stu-id="d0fa4-119">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3. <span data-ttu-id="d0fa4-120">Nommez le fichier `northwind.dbml`.</span><span class="sxs-lookup"><span data-stu-id="d0fa4-120">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="d0fa4-121">Cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="d0fa4-121">Click **Add**.</span></span> <span data-ttu-id="d0fa4-122">Le Concepteur Objet Relationnel (Concepteur O/R) est ouvert pour le fichier Northwind. dbml.</span><span class="sxs-lookup"><span data-stu-id="d0fa4-122">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
### <a name="to-add-stored-procedures-to-the-or-designer"></a><span data-ttu-id="d0fa4-123">Pour ajouter des procédures stockées au Concepteur O/R</span><span class="sxs-lookup"><span data-stu-id="d0fa4-123">To add stored procedures to the O/R Designer</span></span>  
  
1. <span data-ttu-id="d0fa4-124">Dans **Explorateur de serveurs**/**Explorateur de base de données**, développez la connexion à la base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="d0fa4-124">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="d0fa4-125">Développez le dossier **procédures stockées** .</span><span class="sxs-lookup"><span data-stu-id="d0fa4-125">Expand the **Stored Procedures** folder.</span></span>  
  
     <span data-ttu-id="d0fa4-126">Si vous avez fermé le Concepteur O/R, vous pouvez le rouvrir en double-cliquant sur le fichier Northwind. dbml que vous avez ajouté précédemment.</span><span class="sxs-lookup"><span data-stu-id="d0fa4-126">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2. <span data-ttu-id="d0fa4-127">Cliquez sur la procédure stockée **ventes par année** et faites-la glisser vers le volet droit du concepteur.</span><span class="sxs-lookup"><span data-stu-id="d0fa4-127">Click the **Sales by Year** stored procedure and drag it to the right pane of the designer.</span></span> <span data-ttu-id="d0fa4-128">Cliquez sur la procédure stockée **10 produits les plus chers** , puis faites-la glisser vers le volet droit du concepteur.</span><span class="sxs-lookup"><span data-stu-id="d0fa4-128">Click the **Ten Most Expensive Products** stored procedure drag it to the right pane of the designer.</span></span>  
  
3. <span data-ttu-id="d0fa4-129">Enregistrez vos modifications et fermez le concepteur.</span><span class="sxs-lookup"><span data-stu-id="d0fa4-129">Save your changes and close the designer.</span></span>  
  
4. <span data-ttu-id="d0fa4-130">Enregistrez votre projet.</span><span class="sxs-lookup"><span data-stu-id="d0fa4-130">Save your project.</span></span>  
  
### <a name="to-add-code-to-display-the-results-of-the-stored-procedures"></a><span data-ttu-id="d0fa4-131">Pour ajouter du code afin d’afficher les résultats des procédures stockées</span><span class="sxs-lookup"><span data-stu-id="d0fa4-131">To add code to display the results of the stored procedures</span></span>  
  
1. <span data-ttu-id="d0fa4-132">À partir de la **boîte à outils**, faites glisser un contrôle <xref:System.Windows.Forms.DataGridView> sur le Windows Form par défaut de votre projet, Form1.</span><span class="sxs-lookup"><span data-stu-id="d0fa4-132">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2. <span data-ttu-id="d0fa4-133">Double-cliquez sur Form1 pour ajouter du code à son événement `Load`.</span><span class="sxs-lookup"><span data-stu-id="d0fa4-133">Double-click Form1 to add code to its `Load` event.</span></span>  
  
3. <span data-ttu-id="d0fa4-134">Quand vous avez ajouté des procédures stockées au Concepteur O/R, le concepteur a ajouté un objet <xref:System.Data.Linq.DataContext> pour votre projet.</span><span class="sxs-lookup"><span data-stu-id="d0fa4-134">When you added stored procedures to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="d0fa4-135">Cet objet contient le code dont vous devez disposer pour accéder à ces procédures.</span><span class="sxs-lookup"><span data-stu-id="d0fa4-135">This object contains the code that you must have to access those procedures.</span></span> <span data-ttu-id="d0fa4-136">L’objet <xref:System.Data.Linq.DataContext> pour le projet est nommé en fonction du nom du fichier. dbml.</span><span class="sxs-lookup"><span data-stu-id="d0fa4-136">The <xref:System.Data.Linq.DataContext> object for the project is named based on the name of the .dbml file.</span></span> <span data-ttu-id="d0fa4-137">Pour ce projet, l’objet <xref:System.Data.Linq.DataContext> est nommé `northwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="d0fa4-137">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="d0fa4-138">Vous pouvez créer une instance du <xref:System.Data.Linq.DataContext> dans votre code et appeler les méthodes de procédure stockée spécifiées par le Concepteur O/R.</span><span class="sxs-lookup"><span data-stu-id="d0fa4-138">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and call the stored procedure methods specified by the O/R Designer.</span></span> <span data-ttu-id="d0fa4-139">Pour effectuer une liaison à l’objet <xref:System.Windows.Forms.DataGridView>, vous devrez peut-être forcer la requête à s’exécuter immédiatement en appelant la méthode <xref:System.Linq.Enumerable.ToList%2A> sur les résultats de la procédure stockée.</span><span class="sxs-lookup"><span data-stu-id="d0fa4-139">To bind to the <xref:System.Windows.Forms.DataGridView> object, you may have to force the query to execute immediately by calling the <xref:System.Linq.Enumerable.ToList%2A> method on the results of the stored procedure.</span></span>  
  
     <span data-ttu-id="d0fa4-140">Ajoutez le code suivant à l’événement `Load` pour appeler l’une des procédures stockées exposées comme méthodes pour votre contexte de données.</span><span class="sxs-lookup"><span data-stu-id="d0fa4-140">Add the following code to the `Load` event to call either of the stored procedures exposed as methods for your data context.</span></span>  
  
     [!code-vb[VbLINQtoSQLHowTos#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form3.vb#1)]  
    [!code-vb[VbLINQtoSQLHowTos#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form3.vb#2)]  
  
4. <span data-ttu-id="d0fa4-141">Appuyez sur F5 pour exécuter votre projet et afficher les résultats.</span><span class="sxs-lookup"><span data-stu-id="d0fa4-141">Press F5 to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0fa4-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d0fa4-142">See also</span></span>

- [<span data-ttu-id="d0fa4-143">LINQ</span><span class="sxs-lookup"><span data-stu-id="d0fa4-143">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="d0fa4-144">Requêtes</span><span class="sxs-lookup"><span data-stu-id="d0fa4-144">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="d0fa4-145">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="d0fa4-145">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="d0fa4-146">DataContext, méthodes (Concepteur O/R)</span><span class="sxs-lookup"><span data-stu-id="d0fa4-146">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [<span data-ttu-id="d0fa4-147">Guide pratique pour affecter des procédures stockées pour effectuer des mises à jour, des insertions et des suppressions (Concepteur O/R)</span><span class="sxs-lookup"><span data-stu-id="d0fa4-147">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)

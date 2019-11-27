---
title: 'Comment : Rechercher la valeur minimale ou maximale dans un résultat de requête à l’aide de LINQ'
ms.date: 07/20/2015
helpviewer_keywords:
- max operator [LINQ in Visual Basic]
- aggregate operator [LINQ in Visual Basic]
- aggregate queries
- minimum values [LINQ in Visual Basic]
- min operator [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], minimum and maximum values
- Max property
- maximum values [LINQ in Visual Basic]
- Aggregate clause [Visual Basic]
- queries [LINQ in Visual Basic], aggregate queries
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 238b763b-7dcd-4b14-8050-b65500a4f71c
ms.openlocfilehash: bddb90baa0b01fd9d724583b472af9f9fa7569e5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344976"
---
# <a name="how-to-find-the-minimum-or-maximum-value-in-a-query-result-by-using-linq-visual-basic"></a><span data-ttu-id="4ae1d-102">Comment : rechercher la valeur minimale ou maximale dans un résultat de requête à l'aide de LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4ae1d-102">How to: Find the Minimum or Maximum Value in a Query Result by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="4ae1d-103">LINQ (Language-Integrated Query) facilite l’accès aux informations de la base de données et à l’exécution des requêtes.</span><span class="sxs-lookup"><span data-stu-id="4ae1d-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span>  
  
 <span data-ttu-id="4ae1d-104">L’exemple suivant montre comment créer une application qui exécute des requêtes sur une base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="4ae1d-104">The following example shows how to create a new application that performs queries against a SQL Server database.</span></span> <span data-ttu-id="4ae1d-105">L’exemple détermine les valeurs minimale et maximale des résultats à l’aide des clauses `Aggregate` et `Group By`.</span><span class="sxs-lookup"><span data-stu-id="4ae1d-105">The sample determines the minimum and maximum values for the results by using the `Aggregate` and `Group By` clauses.</span></span> <span data-ttu-id="4ae1d-106">Pour plus d’informations, consultez clause [Aggregate](../../../../visual-basic/language-reference/queries/aggregate-clause.md) et [clause Group by](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="4ae1d-106">For more information, see [Aggregate Clause](../../../../visual-basic/language-reference/queries/aggregate-clause.md) and [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span></span>  
  
 <span data-ttu-id="4ae1d-107">Les exemples de cette rubrique utilisent l’exemple de base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="4ae1d-107">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="4ae1d-108">Si cette base de données n'est pas disponible sur votre ordinateur de développement, vous pouvez la télécharger à partir du centre de téléchargement Microsoft.</span><span class="sxs-lookup"><span data-stu-id="4ae1d-108">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="4ae1d-109">Pour obtenir des instructions, consultez [téléchargement d’exemples de bases de données](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="4ae1d-109">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="4ae1d-110">Pour créer une connexion à une base de données</span><span class="sxs-lookup"><span data-stu-id="4ae1d-110">To create a connection to a database</span></span>  
  
1. <span data-ttu-id="4ae1d-111">Dans Visual Studio, ouvrez **Explorateur de serveurs**/**Explorateur de base de données** en cliquant sur Explorateur de serveurs **/Explorateur de base de données dans le** menu **affichage** .</span><span class="sxs-lookup"><span data-stu-id="4ae1d-111">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2. <span data-ttu-id="4ae1d-112">Cliquez avec le bouton droit sur **connexions de données** dans **Explorateur de serveurs**/**Explorateur de base de données** puis cliquez sur **Ajouter une connexion**.</span><span class="sxs-lookup"><span data-stu-id="4ae1d-112">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3. <span data-ttu-id="4ae1d-113">Spécifiez une connexion valide à l’exemple de base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="4ae1d-113">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="4ae1d-114">Pour ajouter un projet qui contient un fichier LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="4ae1d-114">To add a project that contains a LINQ to SQL file</span></span>  
  
1. <span data-ttu-id="4ae1d-115">Dans Visual Studio, dans le menu **Fichier**,pointez sur **Nouveau**, puis cliquez sur **Projet**.</span><span class="sxs-lookup"><span data-stu-id="4ae1d-115">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="4ae1d-116">Sélectionnez Visual Basic **Application Windows Forms** comme type de projet.</span><span class="sxs-lookup"><span data-stu-id="4ae1d-116">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2. <span data-ttu-id="4ae1d-117">Dans le menu **Projet** , cliquez sur **Ajouter un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="4ae1d-117">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="4ae1d-118">Sélectionnez le modèle d’élément **Classes LINQ to SQL** .</span><span class="sxs-lookup"><span data-stu-id="4ae1d-118">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3. <span data-ttu-id="4ae1d-119">Nommez le fichier `northwind.dbml`.</span><span class="sxs-lookup"><span data-stu-id="4ae1d-119">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="4ae1d-120">Cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="4ae1d-120">Click **Add**.</span></span> <span data-ttu-id="4ae1d-121">Le Concepteur Objet Relationnel (Concepteur O/R) est ouvert pour le fichier Northwind. dbml.</span><span class="sxs-lookup"><span data-stu-id="4ae1d-121">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="4ae1d-122">Pour ajouter des tables à interroger dans le Concepteur O/R</span><span class="sxs-lookup"><span data-stu-id="4ae1d-122">To add tables to query to the O/R Designer</span></span>  
  
1. <span data-ttu-id="4ae1d-123">Dans **Explorateur de serveurs**/**Explorateur de base de données**, développez la connexion à la base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="4ae1d-123">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="4ae1d-124">Développez le dossier **tables** .</span><span class="sxs-lookup"><span data-stu-id="4ae1d-124">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="4ae1d-125">Si vous avez fermé le Concepteur O/R, vous pouvez le rouvrir en double-cliquant sur le fichier Northwind. dbml que vous avez ajouté précédemment.</span><span class="sxs-lookup"><span data-stu-id="4ae1d-125">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2. <span data-ttu-id="4ae1d-126">Cliquez sur la table Customers et faites-la glisser vers le volet gauche du concepteur.</span><span class="sxs-lookup"><span data-stu-id="4ae1d-126">Click the Customers table and drag it to the left pane of the designer.</span></span> <span data-ttu-id="4ae1d-127">Cliquez sur la table Orders et faites-la glisser vers le volet gauche du concepteur.</span><span class="sxs-lookup"><span data-stu-id="4ae1d-127">Click the Orders table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="4ae1d-128">Le concepteur crée de nouveaux `Customer` et `Order` objets pour votre projet.</span><span class="sxs-lookup"><span data-stu-id="4ae1d-128">The designer creates new `Customer` and `Order` objects for your project.</span></span> <span data-ttu-id="4ae1d-129">Notez que le concepteur détecte automatiquement les relations entre les tables et crée des propriétés enfants pour les objets connexes.</span><span class="sxs-lookup"><span data-stu-id="4ae1d-129">Notice that the designer automatically detects relationships between the tables and creates child properties for related objects.</span></span> <span data-ttu-id="4ae1d-130">Par exemple, IntelliSense indique que l’objet `Customer` a une propriété `Orders` pour toutes les commandes associées à ce client.</span><span class="sxs-lookup"><span data-stu-id="4ae1d-130">For example, IntelliSense will show that the `Customer` object has an `Orders` property for all orders related to that customer.</span></span>  
  
3. <span data-ttu-id="4ae1d-131">Enregistrez vos modifications et fermez le concepteur.</span><span class="sxs-lookup"><span data-stu-id="4ae1d-131">Save your changes and close the designer.</span></span>  
  
4. <span data-ttu-id="4ae1d-132">Enregistrez votre projet.</span><span class="sxs-lookup"><span data-stu-id="4ae1d-132">Save your project.</span></span>  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="4ae1d-133">Pour ajouter du code pour interroger la base de données et afficher les résultats</span><span class="sxs-lookup"><span data-stu-id="4ae1d-133">To add code to query the database and display the results</span></span>  
  
1. <span data-ttu-id="4ae1d-134">À partir de la **boîte à outils**, faites glisser un contrôle <xref:System.Windows.Forms.DataGridView> sur le Windows Form par défaut de votre projet, Form1.</span><span class="sxs-lookup"><span data-stu-id="4ae1d-134">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2. <span data-ttu-id="4ae1d-135">Double-cliquez sur Form1 pour ajouter du code à l’événement `Load` du formulaire.</span><span class="sxs-lookup"><span data-stu-id="4ae1d-135">Double-click Form1 to add code to the `Load` event of the form.</span></span>  
  
3. <span data-ttu-id="4ae1d-136">Quand vous avez ajouté des tables au Concepteur O/R, le concepteur a ajouté un objet <xref:System.Data.Linq.DataContext> pour votre projet.</span><span class="sxs-lookup"><span data-stu-id="4ae1d-136">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="4ae1d-137">Cet objet contient le code dont vous devez disposer pour accéder à ces tables, en plus des objets et des collections individuels pour chaque table.</span><span class="sxs-lookup"><span data-stu-id="4ae1d-137">This object contains the code that you must have to access those tables, in addition to individual objects and collections for each table.</span></span> <span data-ttu-id="4ae1d-138">L’objet <xref:System.Data.Linq.DataContext> de votre projet est nommé en fonction du nom de votre fichier. dbml.</span><span class="sxs-lookup"><span data-stu-id="4ae1d-138">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="4ae1d-139">Pour ce projet, l’objet <xref:System.Data.Linq.DataContext> est nommé `northwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="4ae1d-139">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="4ae1d-140">Vous pouvez créer une instance du <xref:System.Data.Linq.DataContext> dans votre code et interroger les tables spécifiées par le Concepteur O/R.</span><span class="sxs-lookup"><span data-stu-id="4ae1d-140">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="4ae1d-141">Ajoutez le code suivant à l’événement `Load`.</span><span class="sxs-lookup"><span data-stu-id="4ae1d-141">Add the following code to the `Load` event.</span></span> <span data-ttu-id="4ae1d-142">Ce code interroge les tables qui sont exposées en tant que propriétés de votre contexte de données et détermine les valeurs minimales et maximales pour les résultats.</span><span class="sxs-lookup"><span data-stu-id="4ae1d-142">This code queries the tables that are exposed as properties of your data context and determines the minimum and maximum values for the results.</span></span> <span data-ttu-id="4ae1d-143">L’exemple utilise la clause `Aggregate` pour interroger un résultat unique et la clause `Group By` pour afficher une moyenne pour les résultats groupés.</span><span class="sxs-lookup"><span data-stu-id="4ae1d-143">The sample uses he `Aggregate` clause to query for a single result, and the `Group By` clause to show an average for grouped results.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form7.vb#14)]  
  
4. <span data-ttu-id="4ae1d-144">Appuyez sur F5 pour exécuter votre projet et afficher les résultats.</span><span class="sxs-lookup"><span data-stu-id="4ae1d-144">Press F5 to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ae1d-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4ae1d-145">See also</span></span>

- [<span data-ttu-id="4ae1d-146">LINQ</span><span class="sxs-lookup"><span data-stu-id="4ae1d-146">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="4ae1d-147">Requêtes</span><span class="sxs-lookup"><span data-stu-id="4ae1d-147">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="4ae1d-148">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="4ae1d-148">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="4ae1d-149">DataContext, méthodes (Concepteur O/R)</span><span class="sxs-lookup"><span data-stu-id="4ae1d-149">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)

---
title: 'Guide pratique : rechercher la valeur minimale ou maximale dans un résultat de requête à l’aide de LINQ'
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
ms.openlocfilehash: ef5f218cdcc7275f616486110825ad0b9df11cc3
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112360"
---
# <a name="how-to-find-the-minimum-or-maximum-value-in-a-query-result-by-using-linq-visual-basic"></a><span data-ttu-id="08ed5-102">Comment : rechercher la valeur minimale ou maximale dans un résultat de requête à l'aide de LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="08ed5-102">How to: Find the Minimum or Maximum Value in a Query Result by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="08ed5-103">La requête intégrée en langue (LINQ) facilite l’accès aux informations de base de données et exécute des requêtes.</span><span class="sxs-lookup"><span data-stu-id="08ed5-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span>  
  
 <span data-ttu-id="08ed5-104">L’exemple suivant montre comment créer une nouvelle application qui effectue des requêtes contre une base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="08ed5-104">The following example shows how to create a new application that performs queries against a SQL Server database.</span></span> <span data-ttu-id="08ed5-105">L’échantillon détermine les valeurs minimales et `Aggregate` maximales pour les résultats en utilisant les et `Group By` les clauses.</span><span class="sxs-lookup"><span data-stu-id="08ed5-105">The sample determines the minimum and maximum values for the results by using the `Aggregate` and `Group By` clauses.</span></span> <span data-ttu-id="08ed5-106">Pour plus d’informations, voir [Clause globale](../../../../visual-basic/language-reference/queries/aggregate-clause.md) et [Groupe par clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="08ed5-106">For more information, see [Aggregate Clause](../../../../visual-basic/language-reference/queries/aggregate-clause.md) and [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span></span>  
  
 <span data-ttu-id="08ed5-107">Les exemples dans ce sujet utilisent la base de données de l’échantillon Northwind.</span><span class="sxs-lookup"><span data-stu-id="08ed5-107">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="08ed5-108">Si cette base de données n’est pas disponible sur votre ordinateur de développement, vous pouvez la télécharger à partir du Centre de téléchargement Microsoft.</span><span class="sxs-lookup"><span data-stu-id="08ed5-108">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="08ed5-109">Pour obtenir des instructions, voir [Télécharger des bases de données d’échantillons](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="08ed5-109">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="create-a-connection-to-a-database"></a><span data-ttu-id="08ed5-110">Créer une connexion à une base de données</span><span class="sxs-lookup"><span data-stu-id="08ed5-110">Create a connection to a database</span></span>  
  
1. <span data-ttu-id="08ed5-111">Dans Visual Studio, ouvrez **Server Explorer**/**Database Explorer** en cliquant sur Server **Explorer**/**Database Explorer** sur le menu **View.**</span><span class="sxs-lookup"><span data-stu-id="08ed5-111">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2. <span data-ttu-id="08ed5-112">Cliquez à droite **Data Connections** dans **Server Explorer**/**Database Explorer,** puis cliquez sur **Add Connection**.</span><span class="sxs-lookup"><span data-stu-id="08ed5-112">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3. <span data-ttu-id="08ed5-113">Spécifier une connexion valide à la base de données de l’échantillon Northwind.</span><span class="sxs-lookup"><span data-stu-id="08ed5-113">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="08ed5-114">Pour ajouter un projet qui contient un LINQ au fichier SQL</span><span class="sxs-lookup"><span data-stu-id="08ed5-114">To add a project that contains a LINQ to SQL file</span></span>  
  
1. <span data-ttu-id="08ed5-115">Dans Visual Studio, sur le menu **Du fichier,** pointez vers **New** puis cliquez sur **Project**.</span><span class="sxs-lookup"><span data-stu-id="08ed5-115">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="08ed5-116">Sélectionnez Visual Basic **Windows Forms Application** comme type de projet.</span><span class="sxs-lookup"><span data-stu-id="08ed5-116">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2. <span data-ttu-id="08ed5-117">Dans le menu **Projet** , cliquez sur **Ajouter un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="08ed5-117">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="08ed5-118">Sélectionnez le modèle **d’article LINQ à SQL Classes.**</span><span class="sxs-lookup"><span data-stu-id="08ed5-118">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3. <span data-ttu-id="08ed5-119">Nommez le fichier `northwind.dbml`.</span><span class="sxs-lookup"><span data-stu-id="08ed5-119">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="08ed5-120">Cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="08ed5-120">Click **Add**.</span></span> <span data-ttu-id="08ed5-121">L’Object Relational Designer (O/R Designer) est ouvert pour le fichier northwind.dbml.</span><span class="sxs-lookup"><span data-stu-id="08ed5-121">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
## <a name="add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="08ed5-122">Ajouter des tables à la requête au concepteur O/R</span><span class="sxs-lookup"><span data-stu-id="08ed5-122">Add tables to query to the O/R Designer</span></span>  
  
1. <span data-ttu-id="08ed5-123">Dans **Server Explorer**/**Database Explorer**, étendre la connexion à la base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="08ed5-123">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="08ed5-124">Développez le dossier **Tables** .</span><span class="sxs-lookup"><span data-stu-id="08ed5-124">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="08ed5-125">Si vous avez fermé le concepteur O/R, vous pouvez le rouvrir en cliquant à deux fois sur le fichier northwind.dbml que vous avez ajouté plus tôt.</span><span class="sxs-lookup"><span data-stu-id="08ed5-125">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2. <span data-ttu-id="08ed5-126">Cliquez sur la table des clients et faites-la glisser sur la vitre gauche du concepteur.</span><span class="sxs-lookup"><span data-stu-id="08ed5-126">Click the Customers table and drag it to the left pane of the designer.</span></span> <span data-ttu-id="08ed5-127">Cliquez sur la table des commandes et faites-la glisser sur la vitre gauche du concepteur.</span><span class="sxs-lookup"><span data-stu-id="08ed5-127">Click the Orders table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="08ed5-128">Le designer `Customer` crée `Order` de nouveaux objets pour votre projet.</span><span class="sxs-lookup"><span data-stu-id="08ed5-128">The designer creates new `Customer` and `Order` objects for your project.</span></span> <span data-ttu-id="08ed5-129">Notez que le concepteur détecte automatiquement les relations entre les tables et crée des propriétés pour enfants pour les objets connexes.</span><span class="sxs-lookup"><span data-stu-id="08ed5-129">Notice that the designer automatically detects relationships between the tables and creates child properties for related objects.</span></span> <span data-ttu-id="08ed5-130">Par exemple, IntelliSense montrera que l’objet `Customer` a une `Orders` propriété pour toutes les commandes liées à ce client.</span><span class="sxs-lookup"><span data-stu-id="08ed5-130">For example, IntelliSense will show that the `Customer` object has an `Orders` property for all orders related to that customer.</span></span>  
  
3. <span data-ttu-id="08ed5-131">Enregistrez vos modifications et fermez le concepteur.</span><span class="sxs-lookup"><span data-stu-id="08ed5-131">Save your changes and close the designer.</span></span>  
  
4. <span data-ttu-id="08ed5-132">Enregistrez votre projet.</span><span class="sxs-lookup"><span data-stu-id="08ed5-132">Save your project.</span></span>  
  
## <a name="add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="08ed5-133">Ajouter du code pour interroger la base de données et afficher les résultats</span><span class="sxs-lookup"><span data-stu-id="08ed5-133">Add code to query the database and display the results</span></span>  
  
1. <span data-ttu-id="08ed5-134">Depuis la boîte à <xref:System.Windows.Forms.DataGridView> **outils,** faites glisser un contrôle sur le formulaire Windows par défaut pour votre projet, Form1.</span><span class="sxs-lookup"><span data-stu-id="08ed5-134">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2. <span data-ttu-id="08ed5-135">Double clic Form1 pour ajouter `Load` du code à l’événement du formulaire.</span><span class="sxs-lookup"><span data-stu-id="08ed5-135">Double-click Form1 to add code to the `Load` event of the form.</span></span>  
  
3. <span data-ttu-id="08ed5-136">Lorsque vous avez ajouté des tables au concepteur <xref:System.Data.Linq.DataContext> O/R, le concepteur a ajouté un objet pour votre projet.</span><span class="sxs-lookup"><span data-stu-id="08ed5-136">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="08ed5-137">Cet objet contient le code que vous devez avoir pour accéder à ces tables, en plus des objets individuels et des collections pour chaque table.</span><span class="sxs-lookup"><span data-stu-id="08ed5-137">This object contains the code that you must have to access those tables, in addition to individual objects and collections for each table.</span></span> <span data-ttu-id="08ed5-138">L’objet <xref:System.Data.Linq.DataContext> de votre projet est nommé en fonction du nom de votre fichier .dbml.</span><span class="sxs-lookup"><span data-stu-id="08ed5-138">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="08ed5-139">Pour ce projet, l’objet <xref:System.Data.Linq.DataContext> est nommé `northwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="08ed5-139">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="08ed5-140">Vous pouvez créer une <xref:System.Data.Linq.DataContext> instance de l’in votre code et interroger les tables spécifiées par le concepteur O/R.</span><span class="sxs-lookup"><span data-stu-id="08ed5-140">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="08ed5-141">Ajoutez le code `Load` suivant à l’événement.</span><span class="sxs-lookup"><span data-stu-id="08ed5-141">Add the following code to the `Load` event.</span></span> <span data-ttu-id="08ed5-142">Ce code interroge les tableaux qui sont exposés comme propriétés de votre contexte de données et détermine les valeurs minimales et maximales pour les résultats.</span><span class="sxs-lookup"><span data-stu-id="08ed5-142">This code queries the tables that are exposed as properties of your data context and determines the minimum and maximum values for the results.</span></span> <span data-ttu-id="08ed5-143">L’échantillon `Aggregate` utilise la clause pour demander un `Group By` seul résultat, et la clause pour afficher une moyenne pour les résultats groupés.</span><span class="sxs-lookup"><span data-stu-id="08ed5-143">The sample uses the `Aggregate` clause to query for a single result, and the `Group By` clause to show an average for grouped results.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form7.vb#14)]  
  
4. <span data-ttu-id="08ed5-144">Appuyez sur **F5** pour exécuter votre projet et voir les résultats.</span><span class="sxs-lookup"><span data-stu-id="08ed5-144">Press **F5** to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08ed5-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="08ed5-145">See also</span></span>

- [<span data-ttu-id="08ed5-146">LINQ</span><span class="sxs-lookup"><span data-stu-id="08ed5-146">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="08ed5-147">Requêtes</span><span class="sxs-lookup"><span data-stu-id="08ed5-147">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="08ed5-148">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="08ed5-148">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="08ed5-149">Méthodes DataContext (O/R Designer)</span><span class="sxs-lookup"><span data-stu-id="08ed5-149">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)

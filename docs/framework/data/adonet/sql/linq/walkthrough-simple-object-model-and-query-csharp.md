---
title: 'Procédure pas à pas : Requête et modèle objet simples (C#)'
ms.date: 03/30/2017
ms.assetid: 419961cc-92d6-45f5-ae8a-d485bdde3a37
ms.openlocfilehash: a9b3b57e37331cd13f2cd30b8a7663f2fb39d8c1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792130"
---
# <a name="walkthrough-simple-object-model-and-query-c"></a><span data-ttu-id="24bd3-102">Procédure pas à pas : Requête et modèle objet simples (C#)</span><span class="sxs-lookup"><span data-stu-id="24bd3-102">Walkthrough: Simple Object Model and Query (C#)</span></span>

<span data-ttu-id="24bd3-103">Cette procédure pas à pas fournit un scénario [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] complet essentiel de complexité minimale.</span><span class="sxs-lookup"><span data-stu-id="24bd3-103">This walkthrough provides a fundamental end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario with minimal complexities.</span></span> <span data-ttu-id="24bd3-104">Vous allez créer une classe d'entité qui modélise la table Customers dans l'exemple de base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="24bd3-104">You will create an entity class that models the Customers table in the sample Northwind database.</span></span> <span data-ttu-id="24bd3-105">Vous créerez ensuite une requête simple pour répertorier les clients localisés à Londres.</span><span class="sxs-lookup"><span data-stu-id="24bd3-105">You will then create a simple query to list customers who are located in London.</span></span>

<span data-ttu-id="24bd3-106">Cette procédure pas à pas est orientée code en termes de conception pour permettre l'affichage des concepts [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="24bd3-106">This walkthrough is code-oriented by design to help show [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] concepts.</span></span> <span data-ttu-id="24bd3-107">En règle générale, vous utilisez la Concepteur Objet Relationnel pour créer votre modèle objet.</span><span class="sxs-lookup"><span data-stu-id="24bd3-107">Normally speaking, you would use the Object Relational Designer to create your object model.</span></span>

[!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]

<span data-ttu-id="24bd3-108">Cette procédure pas à pas a été écrite à l'aide des paramètres de développement Visual C#.</span><span class="sxs-lookup"><span data-stu-id="24bd3-108">This walkthrough was written by using Visual C# Development Settings.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="24bd3-109">Prérequis</span><span class="sxs-lookup"><span data-stu-id="24bd3-109">Prerequisites</span></span>

- <span data-ttu-id="24bd3-110">Les fichiers sont stockés dans un dossier dédié, c:\linqtest5.</span><span class="sxs-lookup"><span data-stu-id="24bd3-110">This walkthrough uses a dedicated folder ("c:\linqtest5") to hold files.</span></span> <span data-ttu-id="24bd3-111">Vous devez créer ce dossier avant de commencer la procédure pas à pas.</span><span class="sxs-lookup"><span data-stu-id="24bd3-111">Create this folder before you begin the walkthrough.</span></span>

- <span data-ttu-id="24bd3-112">Cette procédure pas à pas requiert l'exemple de base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="24bd3-112">This walkthrough requires the Northwind sample database.</span></span> <span data-ttu-id="24bd3-113">Si cette base de données n'est pas disponible sur votre ordinateur de développement, vous pouvez la télécharger à partir du site de téléchargement Microsoft.</span><span class="sxs-lookup"><span data-stu-id="24bd3-113">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="24bd3-114">Pour obtenir des instructions, consultez [téléchargement d’exemples de bases de données](downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="24bd3-114">For instructions, see [Downloading Sample Databases](downloading-sample-databases.md).</span></span> <span data-ttu-id="24bd3-115">Après avoir téléchargé la base de données, copiez le fichier dans le dossier c:\linqtest5.</span><span class="sxs-lookup"><span data-stu-id="24bd3-115">After you have downloaded the database, copy the file to the c:\linqtest5 folder.</span></span>

## <a name="overview"></a><span data-ttu-id="24bd3-116">Présentation</span><span class="sxs-lookup"><span data-stu-id="24bd3-116">Overview</span></span>

<span data-ttu-id="24bd3-117">Cette procédure pas à pas se compose de six tâches principales :</span><span class="sxs-lookup"><span data-stu-id="24bd3-117">This walkthrough consists of six main tasks:</span></span>

- <span data-ttu-id="24bd3-118">Création d' [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] une solution dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="24bd3-118">Creating a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in Visual Studio.</span></span>

- <span data-ttu-id="24bd3-119">Mappage d'une classe à une table de base de données.</span><span class="sxs-lookup"><span data-stu-id="24bd3-119">Mapping a class to a database table.</span></span>

- <span data-ttu-id="24bd3-120">Désignation de propriétés sur la classe pour représenter des colonnes de base de données.</span><span class="sxs-lookup"><span data-stu-id="24bd3-120">Designating properties on the class to represent database columns.</span></span>

- <span data-ttu-id="24bd3-121">Spécification de la connexion à la base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="24bd3-121">Specifying the connection to the Northwind database.</span></span>

- <span data-ttu-id="24bd3-122">Création d'une requête simple à exécuter sur la base de données.</span><span class="sxs-lookup"><span data-stu-id="24bd3-122">Creating a simple query to run against the database.</span></span>

- <span data-ttu-id="24bd3-123">Exécution de la requête et observation des résultats.</span><span class="sxs-lookup"><span data-stu-id="24bd3-123">Executing the query and observing the results.</span></span>

## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="24bd3-124">Création d'une solution LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="24bd3-124">Creating a LINQ to SQL Solution</span></span>

<span data-ttu-id="24bd3-125">Dans cette première tâche, vous allez créer une solution Visual Studio qui contient les références nécessaires pour générer et exécuter [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] un projet.</span><span class="sxs-lookup"><span data-stu-id="24bd3-125">In this first task, you create a Visual Studio solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>

### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="24bd3-126">Pour créer une solution LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="24bd3-126">To create a LINQ to SQL solution</span></span>

1. <span data-ttu-id="24bd3-127">Dans le menu **fichier** de Visual Studio, pointez sur **nouveau**, puis cliquez sur **projet**.</span><span class="sxs-lookup"><span data-stu-id="24bd3-127">On the Visual Studio **File** menu, point to **New**, and then click **Project**.</span></span>

2. <span data-ttu-id="24bd3-128">Dans le volet **types de projets** de la boîte de dialogue **nouveau projet** , cliquez sur **visuel C#** .</span><span class="sxs-lookup"><span data-stu-id="24bd3-128">In the **Project types** pane of the **New Project** dialog box, click **Visual C#**.</span></span>

3. <span data-ttu-id="24bd3-129">Dans le volet **Modèles**, cliquez sur **Application console**.</span><span class="sxs-lookup"><span data-stu-id="24bd3-129">In the **Templates** pane, click **Console Application**.</span></span>

4. <span data-ttu-id="24bd3-130">Dans la zone **nom** , tapez **LinqConsoleApp**.</span><span class="sxs-lookup"><span data-stu-id="24bd3-130">In the **Name** box, type **LinqConsoleApp**.</span></span>

5. <span data-ttu-id="24bd3-131">Dans la zone **emplacement** , vérifiez l’emplacement où vous souhaitez stocker vos fichiers projet.</span><span class="sxs-lookup"><span data-stu-id="24bd3-131">In the **Location** box, verify where you want to store your project files.</span></span>

6. <span data-ttu-id="24bd3-132">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="24bd3-132">Click **OK**.</span></span>

## <a name="adding-linq-references-and-directives"></a><span data-ttu-id="24bd3-133">Ajout de références et de directives LINQ</span><span class="sxs-lookup"><span data-stu-id="24bd3-133">Adding LINQ References and Directives</span></span>

<span data-ttu-id="24bd3-134">Cette procédure pas à pas utilise des assemblys qui ne sont pas nécessairement installés par défaut dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="24bd3-134">This walkthrough uses assemblies that might not be installed by default in your project.</span></span> <span data-ttu-id="24bd3-135">Si System. Data. Linq n’est pas listé comme une référence dans votre projet (développez le nœud **références** dans **Explorateur de solutions**), ajoutez-le, comme expliqué dans les étapes suivantes.</span><span class="sxs-lookup"><span data-stu-id="24bd3-135">If System.Data.Linq is not listed as a reference in your project (expand the **References** node in **Solution Explorer**), add it, as explained in the following steps.</span></span>

### <a name="to-add-systemdatalinq"></a><span data-ttu-id="24bd3-136">Pour ajouter System.Data.Linq</span><span class="sxs-lookup"><span data-stu-id="24bd3-136">To add System.Data.Linq</span></span>

1. <span data-ttu-id="24bd3-137">Dans **Explorateur de solutions**, cliquez avec le bouton droit sur **références**, puis cliquez sur **Ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="24bd3-137">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>

2. <span data-ttu-id="24bd3-138">Dans la boîte de dialogue **Ajouter une référence** , cliquez sur **.net**, sur l’assembly System. Data. Linq, puis sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="24bd3-138">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>

     <span data-ttu-id="24bd3-139">L'assembly est ajouté au projet.</span><span class="sxs-lookup"><span data-stu-id="24bd3-139">The assembly is added to the project.</span></span>

3. <span data-ttu-id="24bd3-140">Ajoutez les directives suivantes en haut de **Program.cs**:</span><span class="sxs-lookup"><span data-stu-id="24bd3-140">Add the following directives at the top of **Program.cs**:</span></span>

     [!code-csharp[DLinqWalk1CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#1)]

## <a name="mapping-a-class-to-a-database-table"></a><span data-ttu-id="24bd3-141">Mappage d'une classe à une table de base de données</span><span class="sxs-lookup"><span data-stu-id="24bd3-141">Mapping a Class to a Database Table</span></span>

<span data-ttu-id="24bd3-142">Au cours de cette étape, vous allez créer une classe et la mapper à une table de base de données.</span><span class="sxs-lookup"><span data-stu-id="24bd3-142">In this step, you create a class and map it to a database table.</span></span> <span data-ttu-id="24bd3-143">Une telle classe est appelée classe d' *entité*.</span><span class="sxs-lookup"><span data-stu-id="24bd3-143">Such a class is termed an *entity class*.</span></span> <span data-ttu-id="24bd3-144">Notez que le mappage s'effectue simplement en ajoutant l'attribut <xref:System.Data.Linq.Mapping.TableAttribute>.</span><span class="sxs-lookup"><span data-stu-id="24bd3-144">Note that the mapping is accomplished by just adding the <xref:System.Data.Linq.Mapping.TableAttribute> attribute.</span></span> <span data-ttu-id="24bd3-145">La propriété <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> spécifie le nom de la table dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="24bd3-145">The <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> property specifies the name of the table in the database.</span></span>

### <a name="to-create-an-entity-class-and-map-it-to-a-database-table"></a><span data-ttu-id="24bd3-146">Pour créer une classe d'entité et la mapper à une table de base de données</span><span class="sxs-lookup"><span data-stu-id="24bd3-146">To create an entity class and map it to a database table</span></span>

- <span data-ttu-id="24bd3-147">Tapez ou collez le code suivant dans Program.cs juste au-dessus de la déclaration de classe `Program` :</span><span class="sxs-lookup"><span data-stu-id="24bd3-147">Type or paste the following code into Program.cs immediately above the `Program` class declaration:</span></span>

     [!code-csharp[DLinqWalk1CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#2)]

## <a name="designating-properties-on-the-class-to-represent-database-columns"></a><span data-ttu-id="24bd3-148">Désignation de propriétés sur la classe pour représenter des colonnes de base de données</span><span class="sxs-lookup"><span data-stu-id="24bd3-148">Designating Properties on the Class to Represent Database Columns</span></span>

<span data-ttu-id="24bd3-149">Au cours de cette étape, vous allez effectuer plusieurs tâches.</span><span class="sxs-lookup"><span data-stu-id="24bd3-149">In this step, you accomplish several tasks.</span></span>

- <span data-ttu-id="24bd3-150">Utilisez l'attribut <xref:System.Data.Linq.Mapping.ColumnAttribute> pour désigner les propriétés `CustomerID` et `City` sur la classe d'entité comme représentant des colonnes de la table de base de données.</span><span class="sxs-lookup"><span data-stu-id="24bd3-150">You use the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate `CustomerID` and `City` properties on the entity class as representing columns in the database table.</span></span>

- <span data-ttu-id="24bd3-151">Désignez la propriété `CustomerID` comme représentant une colonne de clé primaire dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="24bd3-151">You designate the `CustomerID` property as representing a primary key column in the database.</span></span>

- <span data-ttu-id="24bd3-152">Désignez les champs `_CustomerID` et `_City` pour le stockage privé.</span><span class="sxs-lookup"><span data-stu-id="24bd3-152">You designate `_CustomerID` and `_City` fields for private storage.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="24bd3-153">peut ensuite stocker et récupérer directement des valeurs, au lieu d'utiliser des accesseurs publics qui peuvent inclure la logique métier.</span><span class="sxs-lookup"><span data-stu-id="24bd3-153">can then store and retrieve values directly, instead of using public accessors that might include business logic.</span></span>

### <a name="to-represent-characteristics-of-two-database-columns"></a><span data-ttu-id="24bd3-154">Pour représenter les caractéristiques de deux colonnes de base de données</span><span class="sxs-lookup"><span data-stu-id="24bd3-154">To represent characteristics of two database columns</span></span>

- <span data-ttu-id="24bd3-155">Tapez ou collez le code suivant dans Program.cs à l'intérieur des accolades pour la classe `Customer`.</span><span class="sxs-lookup"><span data-stu-id="24bd3-155">Type or paste the following code into Program.cs inside the curly braces for the `Customer` class.</span></span>

     [!code-csharp[DLinqWalk1CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#3)]

## <a name="specifying-the-connection-to-the-northwind-database"></a><span data-ttu-id="24bd3-156">Spécification de la connexion à la base de données Northwind</span><span class="sxs-lookup"><span data-stu-id="24bd3-156">Specifying the Connection to the Northwind Database</span></span>

<span data-ttu-id="24bd3-157">Au cours de cette étape, vous allez utiliser un objet <xref:System.Data.Linq.DataContext> pour établir une connexion entre vos structures de données basées sur du code et la base de données elle-même.</span><span class="sxs-lookup"><span data-stu-id="24bd3-157">In this step you use a <xref:System.Data.Linq.DataContext> object to establish a connection between your code-based data structures and the database itself.</span></span> <span data-ttu-id="24bd3-158">Le <xref:System.Data.Linq.DataContext> est le canal principal par le biais duquel vous récupérez des objets de la base de données et soumettez des modifications.</span><span class="sxs-lookup"><span data-stu-id="24bd3-158">The <xref:System.Data.Linq.DataContext> is the main channel through which you retrieve objects from the database and submit changes.</span></span>

<span data-ttu-id="24bd3-159">Déclarez également un `Table<Customer>` comme jouant le rôle de table typée logique pour vos requêtes sur la table Customers dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="24bd3-159">You also declare a `Table<Customer>` to act as the logical, typed table for your queries against the Customers table in the database.</span></span> <span data-ttu-id="24bd3-160">La création et l'exécution de ces requêtes s'effectueront dans des étapes ultérieures.</span><span class="sxs-lookup"><span data-stu-id="24bd3-160">You will create and execute these queries in later steps.</span></span>

### <a name="to-specify-the-database-connection"></a><span data-ttu-id="24bd3-161">Pour spécifier la connexion de base de données</span><span class="sxs-lookup"><span data-stu-id="24bd3-161">To specify the database connection</span></span>

- <span data-ttu-id="24bd3-162">Tapez ou collez le code suivant dans la méthode `Main` :</span><span class="sxs-lookup"><span data-stu-id="24bd3-162">Type or paste the following code into the `Main` method.</span></span>

     <span data-ttu-id="24bd3-163">Notez que le fichier `northwnd.mdf` est censé se trouver dans le dossier linqtest5.</span><span class="sxs-lookup"><span data-stu-id="24bd3-163">Note that the `northwnd.mdf` file is assumed to be in the linqtest5 folder.</span></span> <span data-ttu-id="24bd3-164">Pour plus d'informations, consultez la section Composants requis au début de cette procédure pas à pas.</span><span class="sxs-lookup"><span data-stu-id="24bd3-164">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>

     [!code-csharp[DLinqWalk1CS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#4)]

## <a name="creating-a-simple-query"></a><span data-ttu-id="24bd3-165">Création d'une requête simple</span><span class="sxs-lookup"><span data-stu-id="24bd3-165">Creating a Simple Query</span></span>

<span data-ttu-id="24bd3-166">Au cours de cette étape, vous allez créer une requête pour rechercher les clients localisés à Londres dans la table Customers de la base de données.</span><span class="sxs-lookup"><span data-stu-id="24bd3-166">In this step, you create a query to find which customers in the database Customers table are located in London.</span></span> <span data-ttu-id="24bd3-167">Le code de requête de cette étape décrit simplement la requête.</span><span class="sxs-lookup"><span data-stu-id="24bd3-167">The query code in this step just describes the query.</span></span> <span data-ttu-id="24bd3-168">Il ne l'exécute pas.</span><span class="sxs-lookup"><span data-stu-id="24bd3-168">It does not execute it.</span></span> <span data-ttu-id="24bd3-169">Cette approche est appelée *exécution différée*.</span><span class="sxs-lookup"><span data-stu-id="24bd3-169">This approach is known as *deferred execution*.</span></span> <span data-ttu-id="24bd3-170">Pour plus d’informations, consultez [Introduction aux requêtes LINQ (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="24bd3-170">For more information, see [Introduction to LINQ Queries (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>

<span data-ttu-id="24bd3-171">Vous produirez également une sortie de journal pour afficher les commandes SQL générées par [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="24bd3-171">You will also produce a log output to show the SQL commands that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates.</span></span> <span data-ttu-id="24bd3-172">Cette fonctionnalité d’enregistrement (qui utilise <xref:System.Data.Linq.DataContext.Log%2A>) est utile pour le débogage et pour déterminer que les commandes envoyées à la base de données représentent précisément votre requête.</span><span class="sxs-lookup"><span data-stu-id="24bd3-172">This logging feature (which uses <xref:System.Data.Linq.DataContext.Log%2A>) is helpful in debugging, and in determining that the commands being sent to the database accurately represent your query.</span></span>

### <a name="to-create-a-simple-query"></a><span data-ttu-id="24bd3-173">Pour créer une requête simple</span><span class="sxs-lookup"><span data-stu-id="24bd3-173">To create a simple query</span></span>

- <span data-ttu-id="24bd3-174">Tapez ou collez le code suivant dans la méthode `Main` après la déclaration `Table<Customer>` :</span><span class="sxs-lookup"><span data-stu-id="24bd3-174">Type or paste the following code into the `Main` method after the `Table<Customer>` declaration.</span></span>

     [!code-csharp[DLinqWalk1ACS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1ACS/cs/Program.cs#5)]

## <a name="executing-the-query"></a><span data-ttu-id="24bd3-175">Exécution de la requête</span><span class="sxs-lookup"><span data-stu-id="24bd3-175">Executing the Query</span></span>

<span data-ttu-id="24bd3-176">Dans cette étape, vous allez exécuter la requête.</span><span class="sxs-lookup"><span data-stu-id="24bd3-176">In this step, you actually execute the query.</span></span> <span data-ttu-id="24bd3-177">Les expressions de requête créées au cours des étapes précédentes ne sont pas évaluées tant que les résultats ne sont pas nécessaires.</span><span class="sxs-lookup"><span data-stu-id="24bd3-177">The query expressions you created in the previous steps are not evaluated until the results are needed.</span></span> <span data-ttu-id="24bd3-178">Lorsque vous commencez l'itération `foreach`, une commande SQL est exécutée sur la base de données et les objets sont matérialisés.</span><span class="sxs-lookup"><span data-stu-id="24bd3-178">When you begin the `foreach` iteration, a SQL command is executed against the database and objects are materialized.</span></span>

### <a name="to-execute-the-query"></a><span data-ttu-id="24bd3-179">Pour exécuter la requête</span><span class="sxs-lookup"><span data-stu-id="24bd3-179">To execute the query</span></span>

1. <span data-ttu-id="24bd3-180">Tapez ou collez le code suivant à la fin de la méthode `Main` (après la description de la requête).</span><span class="sxs-lookup"><span data-stu-id="24bd3-180">Type or paste the following code at the end of the `Main` method (after the query description).</span></span>

     [!code-csharp[DLinqWalk1ACS#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1ACS/cs/Program.cs#6)]

2. <span data-ttu-id="24bd3-181">Appuyez sur F5 pour déboguer l'application.</span><span class="sxs-lookup"><span data-stu-id="24bd3-181">Press F5 to debug the application.</span></span>

    > [!NOTE]
    > <span data-ttu-id="24bd3-182">Si votre application génère une erreur d’exécution, consultez la section résolution des problèmes d' [apprentissage par les procédures pas à pas](learning-by-walkthroughs.md).</span><span class="sxs-lookup"><span data-stu-id="24bd3-182">If your application generates a run-time error, see the Troubleshooting section of [Learning by Walkthroughs](learning-by-walkthroughs.md).</span></span>

     <span data-ttu-id="24bd3-183">Les résultats de la requête dans la fenêtre de console doivent apparaître comme suit :</span><span class="sxs-lookup"><span data-stu-id="24bd3-183">The query results in the console window should appear as follows:</span></span>

     `ID=AROUT, City=London`

     `ID=BSBEV, City=London`

     `ID=CONSH, City=London`

     `ID=EASTC, City=London`

     `ID=NORTS, City=London`

     `ID=SEVES, City=London`

3. <span data-ttu-id="24bd3-184">Appuyez sur Entrée dans la fenêtre de console pour fermer l'application.</span><span class="sxs-lookup"><span data-stu-id="24bd3-184">Press Enter in the console window to close the application.</span></span>

## <a name="next-steps"></a><span data-ttu-id="24bd3-185">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="24bd3-185">Next Steps</span></span>

<span data-ttu-id="24bd3-186">La [procédure pas à pas : L’interrogation de relationsC#(](walkthrough-querying-across-relationships-csharp.md) ) se poursuit là où cette procédure pas à pas se termine.</span><span class="sxs-lookup"><span data-stu-id="24bd3-186">The [Walkthrough: Querying Across Relationships (C#)](walkthrough-querying-across-relationships-csharp.md) topic continues where this walkthrough ends.</span></span> <span data-ttu-id="24bd3-187">La procédure pas à pas interroger [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] les relations montre comment peut interroger des tables, comme les *jointures* dans une base de données relationnelle.</span><span class="sxs-lookup"><span data-stu-id="24bd3-187">The Query Across Relationships walkthrough demonstrates how [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] can query across tables, similar to *joins* in a relational database.</span></span>

<span data-ttu-id="24bd3-188">Si vous souhaitez suivre la procédure pas à pas Interrogation de relations, pensez à enregistrer la solution de la procédure que vous venez d'exécuter car elle est indispensable.</span><span class="sxs-lookup"><span data-stu-id="24bd3-188">If you want to do the Query Across Relationships walkthrough, make sure to save the solution for the walkthrough you have just completed, which is a prerequisite.</span></span>

## <a name="see-also"></a><span data-ttu-id="24bd3-189">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="24bd3-189">See also</span></span>

- [<span data-ttu-id="24bd3-190">Apprentissage par les procédures pas à pas</span><span class="sxs-lookup"><span data-stu-id="24bd3-190">Learning by Walkthroughs</span></span>](learning-by-walkthroughs.md)

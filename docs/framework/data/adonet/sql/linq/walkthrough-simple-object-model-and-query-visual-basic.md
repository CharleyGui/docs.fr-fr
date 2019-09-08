---
title: 'Procédure pas à pas : Requête et modèle objet simples (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: c878e457-f715-46e4-a136-ff14d6c86018
ms.openlocfilehash: c21a187739ba19be2dc8e89b4dddc94ad799f036
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792118"
---
# <a name="walkthrough-simple-object-model-and-query-visual-basic"></a><span data-ttu-id="e58ef-102">Procédure pas à pas : Requête et modèle objet simples (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e58ef-102">Walkthrough: Simple Object Model and Query (Visual Basic)</span></span>

<span data-ttu-id="e58ef-103">Cette procédure pas à pas fournit un scénario [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] complet essentiel de complexité minimale.</span><span class="sxs-lookup"><span data-stu-id="e58ef-103">This walkthrough provides a fundamental end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario with minimal complexities.</span></span> <span data-ttu-id="e58ef-104">Vous allez créer une classe d'entité qui modélise la table Customers dans l'exemple de base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="e58ef-104">You will create an entity class that models the Customers table in the sample Northwind database.</span></span> <span data-ttu-id="e58ef-105">Vous créerez ensuite une requête simple pour répertorier les clients localisés à Londres.</span><span class="sxs-lookup"><span data-stu-id="e58ef-105">You will then create a simple query to list customers who are located in London.</span></span>

<span data-ttu-id="e58ef-106">Cette procédure pas à pas est orientée code en termes de conception pour permettre l'affichage des concepts [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e58ef-106">This walkthrough is code-oriented by design to help show [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] concepts.</span></span> <span data-ttu-id="e58ef-107">En règle générale, vous utilisez la Concepteur Objet Relationnel pour créer votre modèle objet.</span><span class="sxs-lookup"><span data-stu-id="e58ef-107">Normally speaking, you would use the Object Relational Designer to create your object model.</span></span>

[!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]

<span data-ttu-id="e58ef-108">Cette procédure pas à pas a été écrite à l'aide des paramètres de développement Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e58ef-108">This walkthrough was written by using Visual Basic Development Settings.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e58ef-109">Prérequis</span><span class="sxs-lookup"><span data-stu-id="e58ef-109">Prerequisites</span></span>

- <span data-ttu-id="e58ef-110">Les fichiers sont stockés dans un dossier dédié, c:\linqtest.</span><span class="sxs-lookup"><span data-stu-id="e58ef-110">This walkthrough uses a dedicated folder ("c:\linqtest") to hold files.</span></span> <span data-ttu-id="e58ef-111">Vous devez créer ce dossier avant de commencer la procédure pas à pas.</span><span class="sxs-lookup"><span data-stu-id="e58ef-111">Create this folder before you begin the walkthrough.</span></span>

- <span data-ttu-id="e58ef-112">Cette procédure pas à pas requiert l'exemple de base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="e58ef-112">This walkthrough requires the Northwind sample database.</span></span> <span data-ttu-id="e58ef-113">Si cette base de données n'est pas disponible sur votre ordinateur de développement, vous pouvez la télécharger à partir du site de téléchargement Microsoft.</span><span class="sxs-lookup"><span data-stu-id="e58ef-113">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="e58ef-114">Pour obtenir des instructions, consultez [téléchargement d’exemples de bases de données](downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="e58ef-114">For instructions, see [Downloading Sample Databases](downloading-sample-databases.md).</span></span> <span data-ttu-id="e58ef-115">Après avoir téléchargé la base de données, copiez le fichier dans le dossier c:\linqtest.</span><span class="sxs-lookup"><span data-stu-id="e58ef-115">After you have downloaded the database, copy the file to the c:\linqtest folder.</span></span>

## <a name="overview"></a><span data-ttu-id="e58ef-116">Présentation</span><span class="sxs-lookup"><span data-stu-id="e58ef-116">Overview</span></span>

<span data-ttu-id="e58ef-117">Cette procédure pas à pas se compose de six tâches principales :</span><span class="sxs-lookup"><span data-stu-id="e58ef-117">This walkthrough consists of six main tasks:</span></span>

- <span data-ttu-id="e58ef-118">Création d' [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] une solution dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e58ef-118">Creating a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in Visual Studio.</span></span>

- <span data-ttu-id="e58ef-119">Mappage d'une classe à une table de base de données.</span><span class="sxs-lookup"><span data-stu-id="e58ef-119">Mapping a class to a database table.</span></span>

- <span data-ttu-id="e58ef-120">Désignation de propriétés sur la classe pour représenter des colonnes de base de données.</span><span class="sxs-lookup"><span data-stu-id="e58ef-120">Designating properties on the class to represent database columns.</span></span>

- <span data-ttu-id="e58ef-121">Spécification de la connexion à la base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="e58ef-121">Specifying the connection to the Northwind database.</span></span>

- <span data-ttu-id="e58ef-122">Création d'une requête simple à exécuter sur la base de données.</span><span class="sxs-lookup"><span data-stu-id="e58ef-122">Creating a simple query to run against the database.</span></span>

- <span data-ttu-id="e58ef-123">Exécution de la requête et observation des résultats.</span><span class="sxs-lookup"><span data-stu-id="e58ef-123">Executing the query and observing the results.</span></span>

## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="e58ef-124">Création d'une solution LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="e58ef-124">Creating a LINQ to SQL Solution</span></span>

<span data-ttu-id="e58ef-125">Dans cette première tâche, vous allez créer une solution Visual Studio qui contient les références nécessaires pour générer et exécuter [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] un projet.</span><span class="sxs-lookup"><span data-stu-id="e58ef-125">In this first task, you create a Visual Studio solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>

### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="e58ef-126">Pour créer une solution LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="e58ef-126">To create a LINQ to SQL solution</span></span>

1. <span data-ttu-id="e58ef-127">Dans le menu **Fichier**, cliquez sur **Nouveau projet**.</span><span class="sxs-lookup"><span data-stu-id="e58ef-127">On the **File** menu, click **New Project**.</span></span>

2. <span data-ttu-id="e58ef-128">Dans le volet **types de projets** de la boîte de dialogue **nouveau projet** , cliquez sur **Visual Basic**.</span><span class="sxs-lookup"><span data-stu-id="e58ef-128">In the **Project types** pane of the **New Project** dialog box, click **Visual Basic**.</span></span>

3. <span data-ttu-id="e58ef-129">Dans le volet **Modèles**, cliquez sur **Application console**.</span><span class="sxs-lookup"><span data-stu-id="e58ef-129">In the **Templates** pane, click **Console Application**.</span></span>

4. <span data-ttu-id="e58ef-130">Dans la zone **nom** , tapez **LinqConsoleApp**.</span><span class="sxs-lookup"><span data-stu-id="e58ef-130">In the **Name** box, type **LinqConsoleApp**.</span></span>

5. <span data-ttu-id="e58ef-131">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="e58ef-131">Click **OK**.</span></span>

## <a name="adding-linq-references-and-directives"></a><span data-ttu-id="e58ef-132">Ajout de références et de directives LINQ</span><span class="sxs-lookup"><span data-stu-id="e58ef-132">Adding LINQ References and Directives</span></span>

<span data-ttu-id="e58ef-133">Cette procédure pas à pas utilise des assemblys qui ne sont pas nécessairement installés par défaut dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="e58ef-133">This walkthrough uses assemblies that might not be installed by default in your project.</span></span> <span data-ttu-id="e58ef-134">Si `System.Data.Linq` n’est pas listé comme une référence dans votre projet (cliquez sur **Afficher tous les fichiers** dans **Explorateur de solutions** et développez le nœud **références** ), ajoutez-le, comme expliqué dans les étapes suivantes.</span><span class="sxs-lookup"><span data-stu-id="e58ef-134">If `System.Data.Linq` is not listed as a reference in your project (click **Show All Files** in **Solution Explorer** and expand the **References** node), add it, as explained in the following steps.</span></span>

### <a name="to-add-systemdatalinq"></a><span data-ttu-id="e58ef-135">Pour ajouter System.Data.Linq</span><span class="sxs-lookup"><span data-stu-id="e58ef-135">To add System.Data.Linq</span></span>

1. <span data-ttu-id="e58ef-136">Dans **Explorateur de solutions**, cliquez avec le bouton droit sur **références**, puis cliquez sur **Ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="e58ef-136">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>

2. <span data-ttu-id="e58ef-137">Dans la boîte de dialogue **Ajouter une référence** , cliquez sur **.net**, sur l’assembly System. Data. Linq, puis sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="e58ef-137">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>

     <span data-ttu-id="e58ef-138">L'assembly est ajouté au projet.</span><span class="sxs-lookup"><span data-stu-id="e58ef-138">The assembly is added to the project.</span></span>

3. <span data-ttu-id="e58ef-139">Également dans la boîte de dialogue **Ajouter une référence** , cliquez sur **.net**, faites défiler la liste jusqu’à et cliquez sur System. Windows. Forms, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="e58ef-139">Also in the **Add Reference** dialog box, click **.NET**, scroll to and click System.Windows.Forms, and then click **OK**.</span></span>

     <span data-ttu-id="e58ef-140">Cet assembly qui prend en charge le message dans la procédure pas à pas est ajouté au projet.</span><span class="sxs-lookup"><span data-stu-id="e58ef-140">This assembly, which supports the message box in the walkthrough, is added to the project.</span></span>

4. <span data-ttu-id="e58ef-141">Ajoutez les directives suivantes au-dessus de `Module1` :</span><span class="sxs-lookup"><span data-stu-id="e58ef-141">Add the following directives above `Module1`:</span></span>

     [!code-vb[DLinqWalk1VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#1)]

## <a name="mapping-a-class-to-a-database-table"></a><span data-ttu-id="e58ef-142">Mappage d'une classe à une table de base de données</span><span class="sxs-lookup"><span data-stu-id="e58ef-142">Mapping a Class to a Database Table</span></span>

<span data-ttu-id="e58ef-143">Au cours de cette étape, vous allez créer une classe et la mapper à une table de base de données.</span><span class="sxs-lookup"><span data-stu-id="e58ef-143">In this step, you create a class and map it to a database table.</span></span> <span data-ttu-id="e58ef-144">Une telle classe est appelée classe d' *entité*.</span><span class="sxs-lookup"><span data-stu-id="e58ef-144">Such a class is termed an *entity class*.</span></span> <span data-ttu-id="e58ef-145">Notez que le mappage s'effectue simplement en ajoutant l'attribut <xref:System.Data.Linq.Mapping.TableAttribute>.</span><span class="sxs-lookup"><span data-stu-id="e58ef-145">Note that the mapping is accomplished by just adding the <xref:System.Data.Linq.Mapping.TableAttribute> attribute.</span></span> <span data-ttu-id="e58ef-146">La propriété <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> spécifie le nom de la table dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="e58ef-146">The <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> property specifies the name of the table in the database.</span></span>

### <a name="to-create-an-entity-class-and-map-it-to-a-database-table"></a><span data-ttu-id="e58ef-147">Pour créer une classe d'entité et la mapper à une table de base de données</span><span class="sxs-lookup"><span data-stu-id="e58ef-147">To create an entity class and map it to a database table</span></span>

- <span data-ttu-id="e58ef-148">Tapez ou collez immédiatement le code suivant dans Module1.vb au-dessus de `Sub Main` :</span><span class="sxs-lookup"><span data-stu-id="e58ef-148">Type or paste the following code into Module1.vb immediately above `Sub Main`:</span></span>

     [!code-vb[DLinqWalk1VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#2)]

## <a name="designating-properties-on-the-class-to-represent-database-columns"></a><span data-ttu-id="e58ef-149">Désignation de propriétés sur la classe pour représenter des colonnes de base de données</span><span class="sxs-lookup"><span data-stu-id="e58ef-149">Designating Properties on the Class to Represent Database Columns</span></span>

<span data-ttu-id="e58ef-150">Au cours de cette étape, vous allez effectuer plusieurs tâches.</span><span class="sxs-lookup"><span data-stu-id="e58ef-150">In this step, you accomplish several tasks.</span></span>

- <span data-ttu-id="e58ef-151">Utilisez l'attribut <xref:System.Data.Linq.Mapping.ColumnAttribute> pour désigner les propriétés `CustomerID` et `City` sur la classe d'entité comme représentant des colonnes de la table de base de données.</span><span class="sxs-lookup"><span data-stu-id="e58ef-151">You use the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate `CustomerID` and `City` properties on the entity class as representing columns in the database table.</span></span>

- <span data-ttu-id="e58ef-152">Désignez la propriété `CustomerID` comme représentant une colonne de clé primaire dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="e58ef-152">You designate the `CustomerID` property as representing a primary key column in the database.</span></span>

- <span data-ttu-id="e58ef-153">Désignez les champs `_CustomerID` et `_City` pour le stockage privé.</span><span class="sxs-lookup"><span data-stu-id="e58ef-153">You designate `_CustomerID` and `_City` fields for private storage.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="e58ef-154">peut ensuite stocker et récupérer directement des valeurs, au lieu d'utiliser des accesseurs publics qui peuvent inclure la logique métier.</span><span class="sxs-lookup"><span data-stu-id="e58ef-154">can then store and retrieve values directly, instead of using public accessors that might include business logic.</span></span>

### <a name="to-represent-characteristics-of-two-database-columns"></a><span data-ttu-id="e58ef-155">Pour représenter les caractéristiques de deux colonnes de base de données</span><span class="sxs-lookup"><span data-stu-id="e58ef-155">To represent characteristics of two database columns</span></span>

- <span data-ttu-id="e58ef-156">Tapez ou collez le code suivant dans Module1.vb juste avant `End Class` :</span><span class="sxs-lookup"><span data-stu-id="e58ef-156">Type or paste the following code into Module1.vb just before `End Class`:</span></span>

     [!code-vb[DLinqWalk1VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#3)]

## <a name="specifying-the-connection-to-the-northwind-database"></a><span data-ttu-id="e58ef-157">Spécification de la connexion à la base de données Northwind</span><span class="sxs-lookup"><span data-stu-id="e58ef-157">Specifying the Connection to the Northwind Database</span></span>

<span data-ttu-id="e58ef-158">Au cours de cette étape, vous allez utiliser un objet <xref:System.Data.Linq.DataContext> pour établir une connexion entre vos structures de données basées sur du code et la base de données elle-même.</span><span class="sxs-lookup"><span data-stu-id="e58ef-158">In this step you use a <xref:System.Data.Linq.DataContext> object to establish a connection between your code-based data structures and the database itself.</span></span> <span data-ttu-id="e58ef-159">Le <xref:System.Data.Linq.DataContext> est le canal principal par le biais duquel vous récupérez des objets de la base de données et soumettez des modifications.</span><span class="sxs-lookup"><span data-stu-id="e58ef-159">The <xref:System.Data.Linq.DataContext> is the main channel through which you retrieve objects from the database and submit changes.</span></span>

<span data-ttu-id="e58ef-160">Déclarez également un `Table(Of Customer)` comme jouant le rôle de table typée logique pour vos requêtes sur la table Customers dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="e58ef-160">You also declare a `Table(Of Customer)` to act as the logical, typed table for your queries against the Customers table in the database.</span></span> <span data-ttu-id="e58ef-161">La création et l'exécution de ces requêtes s'effectueront dans des étapes ultérieures.</span><span class="sxs-lookup"><span data-stu-id="e58ef-161">You will create and execute these queries in later steps.</span></span>

### <a name="to-specify-the-database-connection"></a><span data-ttu-id="e58ef-162">Pour spécifier la connexion de base de données</span><span class="sxs-lookup"><span data-stu-id="e58ef-162">To specify the database connection</span></span>

- <span data-ttu-id="e58ef-163">Tapez ou collez le code suivant dans la méthode `Sub Main` :</span><span class="sxs-lookup"><span data-stu-id="e58ef-163">Type or paste the following code into the `Sub Main` method.</span></span>

     <span data-ttu-id="e58ef-164">Notez que le fichier `northwnd.mdf` est censé se trouver dans le dossier linqtest.</span><span class="sxs-lookup"><span data-stu-id="e58ef-164">Note that the `northwnd.mdf` file is assumed to be in the linqtest folder.</span></span> <span data-ttu-id="e58ef-165">Pour plus d'informations, consultez la section Composants requis au début de cette procédure pas à pas.</span><span class="sxs-lookup"><span data-stu-id="e58ef-165">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>

     [!code-vb[DLinqWalk1VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#4)]

## <a name="creating-a-simple-query"></a><span data-ttu-id="e58ef-166">Création d'une requête simple</span><span class="sxs-lookup"><span data-stu-id="e58ef-166">Creating a Simple Query</span></span>

<span data-ttu-id="e58ef-167">Au cours de cette étape, vous allez créer une requête pour rechercher les clients localisés à Londres dans la table Customers de la base de données.</span><span class="sxs-lookup"><span data-stu-id="e58ef-167">In this step, you create a query to find which customers in the database Customers table are located in London.</span></span> <span data-ttu-id="e58ef-168">Le code de requête de cette étape décrit simplement la requête.</span><span class="sxs-lookup"><span data-stu-id="e58ef-168">The query code in this step just describes the query.</span></span> <span data-ttu-id="e58ef-169">Il ne l'exécute pas.</span><span class="sxs-lookup"><span data-stu-id="e58ef-169">It does not execute it.</span></span> <span data-ttu-id="e58ef-170">Cette approche est appelée *exécution différée*.</span><span class="sxs-lookup"><span data-stu-id="e58ef-170">This approach is known as *deferred execution*.</span></span> <span data-ttu-id="e58ef-171">Pour plus d’informations, consultez [Introduction aux requêtes LINQ (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="e58ef-171">For more information, see [Introduction to LINQ Queries (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>

<span data-ttu-id="e58ef-172">Vous produirez également une sortie de journal pour afficher les commandes SQL générées par [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e58ef-172">You will also produce a log output to show the SQL commands that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates.</span></span> <span data-ttu-id="e58ef-173">Cette fonctionnalité d’enregistrement (qui utilise <xref:System.Data.Linq.DataContext.Log%2A>) est utile pour le débogage et pour déterminer que les commandes envoyées à la base de données représentent précisément votre requête.</span><span class="sxs-lookup"><span data-stu-id="e58ef-173">This logging feature (which uses <xref:System.Data.Linq.DataContext.Log%2A>) is helpful in debugging, and in determining that the commands being sent to the database accurately represent your query.</span></span>

### <a name="to-create-a-simple-query"></a><span data-ttu-id="e58ef-174">Pour créer une requête simple</span><span class="sxs-lookup"><span data-stu-id="e58ef-174">To create a simple query</span></span>

- <span data-ttu-id="e58ef-175">Tapez ou collez le code suivant dans la méthode `Sub Main` après la déclaration `Table(Of Customer)` :</span><span class="sxs-lookup"><span data-stu-id="e58ef-175">Type or paste the following code into the `Sub Main` method after the `Table(Of Customer)` declaration:</span></span>

     [!code-vb[DLinqWalk1AVB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1AVB/vb/Module1.vb#5)]

## <a name="executing-the-query"></a><span data-ttu-id="e58ef-176">Exécution de la requête</span><span class="sxs-lookup"><span data-stu-id="e58ef-176">Executing the Query</span></span>

<span data-ttu-id="e58ef-177">Dans cette étape, vous allez exécuter la requête.</span><span class="sxs-lookup"><span data-stu-id="e58ef-177">In this step, you actually execute the query.</span></span> <span data-ttu-id="e58ef-178">Les expressions de requête créées au cours des étapes précédentes ne sont pas évaluées tant que les résultats ne sont pas nécessaires.</span><span class="sxs-lookup"><span data-stu-id="e58ef-178">The query expressions you created in the previous steps are not evaluated until the results are needed.</span></span> <span data-ttu-id="e58ef-179">Lorsque vous commencez l'itération `For Each`, une commande SQL est exécutée sur la base de données et les objets sont matérialisés.</span><span class="sxs-lookup"><span data-stu-id="e58ef-179">When you begin the `For Each` iteration, a SQL command is executed against the database and objects are materialized.</span></span>

### <a name="to-execute-the-query"></a><span data-ttu-id="e58ef-180">Pour exécuter la requête</span><span class="sxs-lookup"><span data-stu-id="e58ef-180">To execute the query</span></span>

1. <span data-ttu-id="e58ef-181">Tapez ou collez le code suivant à la fin de la méthode `Sub Main` (après la description de la requête) :</span><span class="sxs-lookup"><span data-stu-id="e58ef-181">Type or paste the following code at the end of the `Sub Main` method (after the query description):</span></span>

     [!code-vb[DLinqWalk1AVB#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1AVB/vb/Module1.vb#6)]

2. <span data-ttu-id="e58ef-182">Appuyez sur F5 pour déboguer l'application.</span><span class="sxs-lookup"><span data-stu-id="e58ef-182">Press F5 to debug the application.</span></span>

    > [!NOTE]
    > <span data-ttu-id="e58ef-183">Si votre application génère une erreur d’exécution, consultez la section résolution des problèmes d' [apprentissage par les procédures pas à pas](learning-by-walkthroughs.md).</span><span class="sxs-lookup"><span data-stu-id="e58ef-183">If your application generates a run-time error, see the Troubleshooting section of [Learning by Walkthroughs](learning-by-walkthroughs.md).</span></span>

     <span data-ttu-id="e58ef-184">Le message affiche une liste de six clients.</span><span class="sxs-lookup"><span data-stu-id="e58ef-184">The message box displays a list of six customers.</span></span> <span data-ttu-id="e58ef-185">La fenêtre de console affiche le code SQL généré.</span><span class="sxs-lookup"><span data-stu-id="e58ef-185">The Console window displays the generated SQL code.</span></span>

3. <span data-ttu-id="e58ef-186">Cliquez sur **OK** pour fermer la boîte de message.</span><span class="sxs-lookup"><span data-stu-id="e58ef-186">Click **OK** to dismiss the message box.</span></span>

     <span data-ttu-id="e58ef-187">L'application se ferme.</span><span class="sxs-lookup"><span data-stu-id="e58ef-187">The application closes.</span></span>

4. <span data-ttu-id="e58ef-188">Dans le menu **Fichier**, cliquez sur **Enregistrer tout**.</span><span class="sxs-lookup"><span data-stu-id="e58ef-188">On the **File** menu, click **Save All**.</span></span>

     <span data-ttu-id="e58ef-189">Vous aurez besoin de cette application si vous passez à la procédure pas à pas suivante.</span><span class="sxs-lookup"><span data-stu-id="e58ef-189">You will need this application if you continue with the next walkthrough.</span></span>

## <a name="next-steps"></a><span data-ttu-id="e58ef-190">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="e58ef-190">Next Steps</span></span>

<span data-ttu-id="e58ef-191">La [procédure pas à pas : L’interrogation de relations (Visual Basic](walkthrough-querying-across-relationships-visual-basic.md) ) se poursuit là où cette procédure pas à pas se termine.</span><span class="sxs-lookup"><span data-stu-id="e58ef-191">The [Walkthrough: Querying Across Relationships (Visual Basic)](walkthrough-querying-across-relationships-visual-basic.md) topic continues where this walkthrough ends.</span></span> <span data-ttu-id="e58ef-192">La procédure pas à pas relative à l' [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] interrogation des relations montre comment peut interroger des tables, comme les *jointures* d’une base de données relationnelle.</span><span class="sxs-lookup"><span data-stu-id="e58ef-192">The Querying Across Relationships walkthrough demonstrates how [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] can query across tables, similar to *joins* in a relational database.</span></span>

<span data-ttu-id="e58ef-193">Si vous souhaitez suivre la procédure pas à pas Interrogation de relations, pensez à enregistrer la solution de la procédure que vous venez d'exécuter, car elle est indispensable.</span><span class="sxs-lookup"><span data-stu-id="e58ef-193">If you want to do the Querying Across Relationships walkthrough, make sure to save the solution for the walkthrough you have just completed, which is a prerequisite.</span></span>

## <a name="see-also"></a><span data-ttu-id="e58ef-194">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e58ef-194">See also</span></span>

- [<span data-ttu-id="e58ef-195">Apprentissage par les procédures pas à pas</span><span class="sxs-lookup"><span data-stu-id="e58ef-195">Learning by Walkthroughs</span></span>](learning-by-walkthroughs.md)

---
title: 'Procédure pas à pas : Manipulation de données (C#)'
ms.date: 03/30/2017
ms.assetid: 24adfbe0-0ad6-449f-997d-8808e0770d2e
ms.openlocfilehash: fefbee533634ee42785c65e0265ce1e0567561b5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164062"
---
# <a name="walkthrough-manipulating-data-c"></a><span data-ttu-id="938fc-102">Procédure pas à pas : Manipulation de données (C#)</span><span class="sxs-lookup"><span data-stu-id="938fc-102">Walkthrough: Manipulating Data (C#)</span></span>

<span data-ttu-id="938fc-103">Cette procédure pas à pas fournit un scénario [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] complet essentiel pour l'ajout, la modification et la suppression de données dans une base de données.</span><span class="sxs-lookup"><span data-stu-id="938fc-103">This walkthrough provides a fundamental end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario for adding, modifying, and deleting data in a database.</span></span> <span data-ttu-id="938fc-104">Vous utiliserez une copie de l'exemple de base de données Northwind pour ajouter un client, modifier le nom d'un client et supprimer une commande.</span><span class="sxs-lookup"><span data-stu-id="938fc-104">You will use a copy of the sample Northwind database to add a customer, change the name of a customer, and delete an order.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="938fc-105">Cette procédure pas à pas a été écrite à l'aide des paramètres de développement Visual C#.</span><span class="sxs-lookup"><span data-stu-id="938fc-105">This walkthrough was written by using Visual C# Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="938fc-106">Prérequis</span><span class="sxs-lookup"><span data-stu-id="938fc-106">Prerequisites</span></span>  

 <span data-ttu-id="938fc-107">Elle requiert les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="938fc-107">This walkthrough requires the following:</span></span>  
  
- <span data-ttu-id="938fc-108">Les fichiers sont stockés dans un dossier dédié, c:\linqtest6.</span><span class="sxs-lookup"><span data-stu-id="938fc-108">This walkthrough uses a dedicated folder ("c:\linqtest6") to hold files.</span></span> <span data-ttu-id="938fc-109">Vous devez créer ce dossier avant de commencer la procédure pas à pas.</span><span class="sxs-lookup"><span data-stu-id="938fc-109">Create this folder before you begin the walkthrough.</span></span>  
  
- <span data-ttu-id="938fc-110">Exemple de base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="938fc-110">The Northwind sample database.</span></span>  
  
     <span data-ttu-id="938fc-111">Si cette base de données n'est pas disponible sur votre ordinateur de développement, vous pouvez la télécharger à partir du site de téléchargement Microsoft.</span><span class="sxs-lookup"><span data-stu-id="938fc-111">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="938fc-112">Pour obtenir des instructions, consultez [téléchargement d’exemples de bases de données](downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="938fc-112">For instructions, see [Downloading Sample Databases](downloading-sample-databases.md).</span></span> <span data-ttu-id="938fc-113">Après avoir téléchargé la base de données, copiez le fichier northwnd.mdf dans le dossier c:\linqtest6.</span><span class="sxs-lookup"><span data-stu-id="938fc-113">After you have downloaded the database, copy the northwnd.mdf file to the c:\linqtest6 folder.</span></span>  
  
- <span data-ttu-id="938fc-114">Fichier de code C# généré à partir de la base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="938fc-114">A C# code file generated from the Northwind database.</span></span>  
  
     <span data-ttu-id="938fc-115">Vous pouvez générer ce fichier à l’aide de l’Concepteur Objet Relationnel ou de l’outil SQLMetal.</span><span class="sxs-lookup"><span data-stu-id="938fc-115">You can generate this file by using either the Object Relational Designer or the SQLMetal tool.</span></span> <span data-ttu-id="938fc-116">Cette procédure pas à pas a été écrite à l'aide de l'outil SQLMetal, avec la ligne de commande suivante :</span><span class="sxs-lookup"><span data-stu-id="938fc-116">This walkthrough was written by using the SQLMetal tool with the following command line:</span></span>  
  
     <span data-ttu-id="938fc-117">**sqlmetal /code:"c:\linqtest6\northwind.cs" /language:csharp "C:\linqtest6\northwnd.mdf" /pluralize**</span><span class="sxs-lookup"><span data-stu-id="938fc-117">**sqlmetal /code:"c:\linqtest6\northwind.cs" /language:csharp "C:\linqtest6\northwnd.mdf" /pluralize**</span></span>  
  
     <span data-ttu-id="938fc-118">Pour plus d’informations, consultez [SqlMetal.exe (outil de génération de code)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="938fc-118">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="overview"></a><span data-ttu-id="938fc-119">Vue d’ensemble</span><span class="sxs-lookup"><span data-stu-id="938fc-119">Overview</span></span>  

 <span data-ttu-id="938fc-120">Cette procédure pas à pas se compose de six tâches principales :</span><span class="sxs-lookup"><span data-stu-id="938fc-120">This walkthrough consists of six main tasks:</span></span>  
  
- <span data-ttu-id="938fc-121">Création [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] de la solution dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="938fc-121">Creating the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in Visual Studio.</span></span>  
  
- <span data-ttu-id="938fc-122">Ajout du fichier de code de base de données au projet.</span><span class="sxs-lookup"><span data-stu-id="938fc-122">Adding the database code file to the project.</span></span>  
  
- <span data-ttu-id="938fc-123">Création d'un objet représentant un client.</span><span class="sxs-lookup"><span data-stu-id="938fc-123">Creating a new customer object.</span></span>  
  
- <span data-ttu-id="938fc-124">Modification du nom de contact d'un client.</span><span class="sxs-lookup"><span data-stu-id="938fc-124">Modifying the contact name of a customer.</span></span>  
  
- <span data-ttu-id="938fc-125">Suppression d'une commande.</span><span class="sxs-lookup"><span data-stu-id="938fc-125">Deleting an order.</span></span>  
  
- <span data-ttu-id="938fc-126">Soumission de ces modifications à la base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="938fc-126">Submitting these changes to the Northwind database.</span></span>  
  
## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="938fc-127">Création d'une solution LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="938fc-127">Creating a LINQ to SQL Solution</span></span>  

 <span data-ttu-id="938fc-128">Dans cette première tâche, vous allez créer une solution Visual Studio qui contient les références nécessaires pour générer et exécuter un [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projet.</span><span class="sxs-lookup"><span data-stu-id="938fc-128">In this first task, you create a Visual Studio solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>  
  
#### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="938fc-129">Pour créer une solution LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="938fc-129">To create a LINQ to SQL solution</span></span>  
  
1. <span data-ttu-id="938fc-130">Dans le menu **fichier** de Visual Studio, pointez sur **nouveau**, puis cliquez sur **projet**.</span><span class="sxs-lookup"><span data-stu-id="938fc-130">On the Visual Studio **File** menu, point to **New**, and then click **Project**.</span></span>  
  
2. <span data-ttu-id="938fc-131">Dans le volet **types de projets** de la boîte de dialogue **nouveau projet** , cliquez sur **Visual C#**.</span><span class="sxs-lookup"><span data-stu-id="938fc-131">In the **Project types** pane in the **New Project** dialog box, click **Visual C#**.</span></span>  
  
3. <span data-ttu-id="938fc-132">Dans le volet **Modèles**, cliquez sur **Application console**.</span><span class="sxs-lookup"><span data-stu-id="938fc-132">In the **Templates** pane, click **Console Application**.</span></span>  
  
4. <span data-ttu-id="938fc-133">Dans la zone **nom** , tapez **LinqDataManipulationApp**.</span><span class="sxs-lookup"><span data-stu-id="938fc-133">In the **Name** box, type **LinqDataManipulationApp**.</span></span>  
  
5. <span data-ttu-id="938fc-134">Dans la zone **emplacement** , vérifiez l’emplacement où vous souhaitez stocker vos fichiers projet.</span><span class="sxs-lookup"><span data-stu-id="938fc-134">In the **Location** box, verify where you want to store your project files.</span></span>  
  
6. <span data-ttu-id="938fc-135">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="938fc-135">Click **OK**.</span></span>  
  
## <a name="adding-linq-references-and-directives"></a><span data-ttu-id="938fc-136">Ajout de références et de directives LINQ</span><span class="sxs-lookup"><span data-stu-id="938fc-136">Adding LINQ References and Directives</span></span>  

 <span data-ttu-id="938fc-137">Cette procédure pas à pas utilise des assemblys qui ne sont pas nécessairement installés par défaut dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="938fc-137">This walkthrough uses assemblies that might not be installed by default in your project.</span></span> <span data-ttu-id="938fc-138">Si System.Data.Linq n'est pas répertorié comme une référence dans votre projet, ajoutez-le comme indiqué dans les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="938fc-138">If System.Data.Linq is not listed as a reference in your project, add it, as explained in the following steps:</span></span>  
  
#### <a name="to-add-systemdatalinq"></a><span data-ttu-id="938fc-139">Pour ajouter System.Data.Linq</span><span class="sxs-lookup"><span data-stu-id="938fc-139">To add System.Data.Linq</span></span>  
  
1. <span data-ttu-id="938fc-140">Dans **Explorateur de solutions**, cliquez avec le bouton droit sur **références**, puis cliquez sur **Ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="938fc-140">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>  
  
2. <span data-ttu-id="938fc-141">Dans la boîte de dialogue **Ajouter une référence** , cliquez sur **.net**, sur l’assembly System. Data. Linq, puis sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="938fc-141">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>  
  
     <span data-ttu-id="938fc-142">L'assembly est ajouté au projet.</span><span class="sxs-lookup"><span data-stu-id="938fc-142">The assembly is added to the project.</span></span>  
  
3. <span data-ttu-id="938fc-143">Ajoutez les directives suivantes au haut de Program.cs :</span><span class="sxs-lookup"><span data-stu-id="938fc-143">Add the following directives at the top of Program.cs:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#1)]  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a><span data-ttu-id="938fc-144">Ajout du fichier de code Northwind au projet</span><span class="sxs-lookup"><span data-stu-id="938fc-144">Adding the Northwind Code File to the Project</span></span>  

 <span data-ttu-id="938fc-145">Ces étapes supposent que vous avez utilisé l'outil SQLMetal pour générer un fichier de code à partir de l'exemple de base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="938fc-145">These steps assume that you have used the SQLMetal tool to generate a code file from the Northwind sample database.</span></span> <span data-ttu-id="938fc-146">Pour plus d'informations, consultez la section Composants requis au début de cette procédure pas à pas.</span><span class="sxs-lookup"><span data-stu-id="938fc-146">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a><span data-ttu-id="938fc-147">Pour ajouter le fichier de code Northwind au projet</span><span class="sxs-lookup"><span data-stu-id="938fc-147">To add the northwind code file to the project</span></span>  
  
1. <span data-ttu-id="938fc-148">Dans le menu **Projet** , cliquez sur **Ajouter un élément existant**.</span><span class="sxs-lookup"><span data-stu-id="938fc-148">On the **Project** menu, click **Add Existing Item**.</span></span>  
  
2. <span data-ttu-id="938fc-149">Dans la boîte de dialogue **Ajouter un élément existant** , accédez à c:\linqtest6\northwind.cs, puis cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="938fc-149">In the **Add Existing Item** dialog box, navigate to c:\linqtest6\northwind.cs, and then click **Add**.</span></span>  
  
     <span data-ttu-id="938fc-150">Le fichier northwind.cs est ajouté au projet.</span><span class="sxs-lookup"><span data-stu-id="938fc-150">The northwind.cs file is added to the project.</span></span>  
  
## <a name="setting-up-the-database-connection"></a><span data-ttu-id="938fc-151">Paramétrage de la connexion de base de données</span><span class="sxs-lookup"><span data-stu-id="938fc-151">Setting Up the Database Connection</span></span>  

 <span data-ttu-id="938fc-152">Commencez par tester votre connexion à la base de données.</span><span class="sxs-lookup"><span data-stu-id="938fc-152">First, test your connection to the database.</span></span> <span data-ttu-id="938fc-153">Notez en particulier que le nom de la base de données (Northwnd) ne comporte pas de caractère i.</span><span class="sxs-lookup"><span data-stu-id="938fc-153">Note especially that the database, Northwnd, has no i character.</span></span> <span data-ttu-id="938fc-154">Si vous générez des erreurs au cours des étapes suivantes, examinez le fichier northwind.cs pour déterminer comment la classe partielle Northwind est orthographiée.</span><span class="sxs-lookup"><span data-stu-id="938fc-154">If you generate errors in the next steps, review the northwind.cs file to determine how the Northwind partial class is spelled.</span></span>  
  
#### <a name="to-set-up-and-test-the-database-connection"></a><span data-ttu-id="938fc-155">Pour paramétrer et tester la connexion de base de données</span><span class="sxs-lookup"><span data-stu-id="938fc-155">To set up and test the database connection</span></span>  
  
1. <span data-ttu-id="938fc-156">Tapez ou collez le code suivant dans la méthode `Main` de la classe Program :</span><span class="sxs-lookup"><span data-stu-id="938fc-156">Type or paste the following code into the `Main` method in the Program class:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#2)]  
  
2. <span data-ttu-id="938fc-157">Appuyez sur F5 pour tester l'application à ce stade.</span><span class="sxs-lookup"><span data-stu-id="938fc-157">Press F5 to test the application at this point.</span></span>  
  
     <span data-ttu-id="938fc-158">Une fenêtre de **console** s’ouvre.</span><span class="sxs-lookup"><span data-stu-id="938fc-158">A **Console** window opens.</span></span>  
  
     <span data-ttu-id="938fc-159">Vous pouvez fermer l’application en appuyant sur entrée dans la fenêtre de **console** , ou en cliquant sur **arrêter le débogage** dans le menu **Déboguer** de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="938fc-159">You can close the application by pressing Enter in the **Console** window, or by clicking **Stop Debugging** on the Visual Studio **Debug** menu.</span></span>  
  
## <a name="creating-a-new-entity"></a><span data-ttu-id="938fc-160">Création d'une entité</span><span class="sxs-lookup"><span data-stu-id="938fc-160">Creating a New Entity</span></span>  

 <span data-ttu-id="938fc-161">La création d'une entité est une opération simple.</span><span class="sxs-lookup"><span data-stu-id="938fc-161">Creating a new entity is straightforward.</span></span> <span data-ttu-id="938fc-162">Vous pouvez créer des objets (`Customer`, par exemple) à l'aide du mot clé `new`.</span><span class="sxs-lookup"><span data-stu-id="938fc-162">You can create objects (such as `Customer`) by using the `new` keyword.</span></span>  
  
 <span data-ttu-id="938fc-163">Dans cette section et les suivantes, vous apporterez des modifications uniquement au cache local.</span><span class="sxs-lookup"><span data-stu-id="938fc-163">In this and the following sections, you are making changes only to the local cache.</span></span> <span data-ttu-id="938fc-164">Aucune modification n'est envoyée à la base de données tant que vous n'avez pas appelé <xref:System.Data.Linq.DataContext.SubmitChanges%2A> vers la fin de cette procédure pas à pas.</span><span class="sxs-lookup"><span data-stu-id="938fc-164">No changes are sent to the database until you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> toward the end of this walkthrough.</span></span>  
  
#### <a name="to-add-a-new-customer-entity-object"></a><span data-ttu-id="938fc-165">Pour ajouter un nouvel objet d'entité Customer</span><span class="sxs-lookup"><span data-stu-id="938fc-165">To add a new Customer entity object</span></span>  
  
1. <span data-ttu-id="938fc-166">Créez un `Customer` en ajoutant le code suivant avant `Console.ReadLine();` dans la méthode `Main` :</span><span class="sxs-lookup"><span data-stu-id="938fc-166">Create a new `Customer` by adding the following code before `Console.ReadLine();` in the `Main` method:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#3)]  
  
2. <span data-ttu-id="938fc-167">Appuyez sur F5 pour déboguer la solution.</span><span class="sxs-lookup"><span data-stu-id="938fc-167">Press F5 to debug the solution.</span></span>  
  
3. <span data-ttu-id="938fc-168">Appuyez sur entrée dans la fenêtre de **console** pour arrêter le débogage et poursuivez la procédure pas à pas.</span><span class="sxs-lookup"><span data-stu-id="938fc-168">Press Enter in the **Console** window to stop debugging and continue the walkthrough.</span></span>  
  
## <a name="updating-an-entity"></a><span data-ttu-id="938fc-169">Mise à jour d'une entité</span><span class="sxs-lookup"><span data-stu-id="938fc-169">Updating an Entity</span></span>  

 <span data-ttu-id="938fc-170">Au cours des étapes suivantes, vous allez récupérer un objet `Customer` et modifier l'une de ses propriétés.</span><span class="sxs-lookup"><span data-stu-id="938fc-170">In the following steps, you will retrieve a `Customer` object and modify one of its properties.</span></span>  
  
#### <a name="to-change-the-name-of-a-customer"></a><span data-ttu-id="938fc-171">Pour modifier le nom d'un client</span><span class="sxs-lookup"><span data-stu-id="938fc-171">To change the name of a Customer</span></span>  
  
- <span data-ttu-id="938fc-172">Ajoutez le code suivant au-dessus de `Console.ReadLine();` :</span><span class="sxs-lookup"><span data-stu-id="938fc-172">Add the following code above `Console.ReadLine();`:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#4)]  
  
## <a name="deleting-an-entity"></a><span data-ttu-id="938fc-173">Suppression d’une entité</span><span class="sxs-lookup"><span data-stu-id="938fc-173">Deleting an Entity</span></span>  

 <span data-ttu-id="938fc-174">Vous pouvez supprimer la première commande à l'aide du même objet Customer.</span><span class="sxs-lookup"><span data-stu-id="938fc-174">Using the same customer object, you can delete the first order.</span></span>  
  
 <span data-ttu-id="938fc-175">Le code suivant montre comment couper les relations entre les lignes et supprimer une ligne de la base de données.</span><span class="sxs-lookup"><span data-stu-id="938fc-175">The following code demonstrates how to sever relationships between rows, and how to delete a row from the database.</span></span> <span data-ttu-id="938fc-176">Ajoutez le code suivant avant `Console.ReadLine` pour voir comment les objets peuvent être supprimés :</span><span class="sxs-lookup"><span data-stu-id="938fc-176">Add the following code before `Console.ReadLine` to see how objects can be deleted:</span></span>  
  
#### <a name="to-delete-a-row"></a><span data-ttu-id="938fc-177">Pour supprimer une ligne</span><span class="sxs-lookup"><span data-stu-id="938fc-177">To delete a row</span></span>  
  
- <span data-ttu-id="938fc-178">Ajoutez le code suivant juste au-dessus de `Console.ReadLine();` :</span><span class="sxs-lookup"><span data-stu-id="938fc-178">Add the following code just above `Console.ReadLine();`:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#5)]  
  
## <a name="submitting-changes-to-the-database"></a><span data-ttu-id="938fc-179">Soumission des modifications à la base de données</span><span class="sxs-lookup"><span data-stu-id="938fc-179">Submitting Changes to the Database</span></span>  

 <span data-ttu-id="938fc-180">La dernière étape requise pour la création, la mise à jour et la suppression d'objets consiste à soumettre les modifications à la base de données.</span><span class="sxs-lookup"><span data-stu-id="938fc-180">The final step required for creating, updating, and deleting objects, is to actually submit the changes to the database.</span></span> <span data-ttu-id="938fc-181">Sans cette étape, vos modifications restent locales et n'apparaissent pas dans les résultats de requêtes.</span><span class="sxs-lookup"><span data-stu-id="938fc-181">Without this step, your changes are only local and will not appear in query results.</span></span>  
  
#### <a name="to-submit-changes-to-the-database"></a><span data-ttu-id="938fc-182">Pour soumettre les modifications à la base de données</span><span class="sxs-lookup"><span data-stu-id="938fc-182">To submit changes to the database</span></span>  
  
1. <span data-ttu-id="938fc-183">Insérez le code suivant juste au-dessus de `Console.ReadLine` :</span><span class="sxs-lookup"><span data-stu-id="938fc-183">Insert the following code just above `Console.ReadLine`:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#6)]  
  
2. <span data-ttu-id="938fc-184">Insérez le code suivant (après `SubmitChanges`) pour afficher les effets avant/après de la soumission des modifications :</span><span class="sxs-lookup"><span data-stu-id="938fc-184">Insert the following code (after `SubmitChanges`) to show the before and after effects of submitting the changes:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#7)]  
  
3. <span data-ttu-id="938fc-185">Appuyez sur F5 pour déboguer la solution.</span><span class="sxs-lookup"><span data-stu-id="938fc-185">Press F5 to debug the solution.</span></span>  
  
4. <span data-ttu-id="938fc-186">Appuyez sur entrée dans la fenêtre de **console** pour fermer l’application.</span><span class="sxs-lookup"><span data-stu-id="938fc-186">Press Enter in the **Console** window to close the application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="938fc-187">Une fois que vous avez soumis les modifications (ajouté le nouveau client), vous ne pouvez plus exécuter cette solution telle quelle.</span><span class="sxs-lookup"><span data-stu-id="938fc-187">After you have added the new customer by submitting the changes, you cannot execute this solution again as is.</span></span> <span data-ttu-id="938fc-188">Pour l'exécuter à nouveau, modifiez le nom du client et l'ID client à ajouter.</span><span class="sxs-lookup"><span data-stu-id="938fc-188">To execute the solution again, change the name of the customer and customer ID to be added.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="938fc-189">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="938fc-189">See also</span></span>

- [<span data-ttu-id="938fc-190">Apprentissage par les procédures pas à pas</span><span class="sxs-lookup"><span data-stu-id="938fc-190">Learning by Walkthroughs</span></span>](learning-by-walkthroughs.md)

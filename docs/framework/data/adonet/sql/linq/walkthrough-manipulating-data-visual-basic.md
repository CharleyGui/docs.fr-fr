---
title: 'Procédure pas à pas : Manipulation de données (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: 1f6a54f6-ec33-452a-a37d-48122207bf14
ms.openlocfilehash: dbf18273e69ff0977f5d16ff179b8659865ef696
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164049"
---
# <a name="walkthrough-manipulating-data-visual-basic"></a><span data-ttu-id="df35f-102">Procédure pas à pas : Manipulation de données (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="df35f-102">Walkthrough: Manipulating Data (Visual Basic)</span></span>

<span data-ttu-id="df35f-103">Cette procédure pas à pas fournit un scénario [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] complet essentiel pour l'ajout, la modification et la suppression de données dans une base de données.</span><span class="sxs-lookup"><span data-stu-id="df35f-103">This walkthrough provides a fundamental end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario for adding, modifying, and deleting data in a database.</span></span> <span data-ttu-id="df35f-104">Vous utiliserez une copie de l'exemple de base de données Northwind pour ajouter un client, modifier le nom d'un client et supprimer une commande.</span><span class="sxs-lookup"><span data-stu-id="df35f-104">You will use a copy of the sample Northwind database to add a customer, change the name of a customer, and delete an order.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="df35f-105">Cette procédure pas à pas a été écrite à l'aide des paramètres de développement Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="df35f-105">This walkthrough was written by using Visual Basic Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="df35f-106">Prérequis</span><span class="sxs-lookup"><span data-stu-id="df35f-106">Prerequisites</span></span>  

 <span data-ttu-id="df35f-107">Elle requiert les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="df35f-107">This walkthrough requires the following:</span></span>  
  
- <span data-ttu-id="df35f-108">Les fichiers sont stockés dans un dossier dédié, c:\linqtest2.</span><span class="sxs-lookup"><span data-stu-id="df35f-108">This walkthrough uses a dedicated folder ("c:\linqtest2") to hold files.</span></span> <span data-ttu-id="df35f-109">Vous devez créer ce dossier avant de commencer la procédure pas à pas.</span><span class="sxs-lookup"><span data-stu-id="df35f-109">Create this folder before you begin the walkthrough.</span></span>  
  
- <span data-ttu-id="df35f-110">Exemple de base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="df35f-110">The Northwind sample database.</span></span>  
  
     <span data-ttu-id="df35f-111">Si cette base de données n'est pas disponible sur votre ordinateur de développement, vous pouvez la télécharger à partir du site de téléchargement Microsoft.</span><span class="sxs-lookup"><span data-stu-id="df35f-111">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="df35f-112">Pour obtenir des instructions, consultez [téléchargement d’exemples de bases de données](downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="df35f-112">For instructions, see [Downloading Sample Databases](downloading-sample-databases.md).</span></span> <span data-ttu-id="df35f-113">Après avoir téléchargé la base de données, copiez le fichier northwnd.mdf dans le dossier c:\linqtest2.</span><span class="sxs-lookup"><span data-stu-id="df35f-113">After you have downloaded the database, copy the northwnd.mdf file to the c:\linqtest2 folder.</span></span>  
  
- <span data-ttu-id="df35f-114">Fichier de code Visual Basic généré à partir de la base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="df35f-114">A Visual Basic code file generated from the Northwind database.</span></span>  
  
     <span data-ttu-id="df35f-115">Vous pouvez générer ce fichier à l’aide de l’Concepteur Objet Relationnel ou de l’outil SQLMetal.</span><span class="sxs-lookup"><span data-stu-id="df35f-115">You can generate this file by using either the Object Relational Designer or the SQLMetal tool.</span></span> <span data-ttu-id="df35f-116">Cette procédure pas à pas a été écrite à l'aide de l'outil SQLMetal, avec la ligne de commande suivante :</span><span class="sxs-lookup"><span data-stu-id="df35f-116">This walkthrough was written by using the SQLMetal tool with the following command line:</span></span>  
  
     <span data-ttu-id="df35f-117">**sqlmetal /code:"c:\linqtest2\northwind.vb" /language:vb "C:\linqtest2\northwnd.mdf" /pluralize**</span><span class="sxs-lookup"><span data-stu-id="df35f-117">**sqlmetal /code:"c:\linqtest2\northwind.vb" /language:vb "C:\linqtest2\northwnd.mdf" /pluralize**</span></span>  
  
     <span data-ttu-id="df35f-118">Pour plus d’informations, consultez [SqlMetal.exe (outil de génération de code)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="df35f-118">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="overview"></a><span data-ttu-id="df35f-119">Vue d’ensemble</span><span class="sxs-lookup"><span data-stu-id="df35f-119">Overview</span></span>  

 <span data-ttu-id="df35f-120">Cette procédure pas à pas se compose de six tâches principales :</span><span class="sxs-lookup"><span data-stu-id="df35f-120">This walkthrough consists of six main tasks:</span></span>  
  
- <span data-ttu-id="df35f-121">Création [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] de la solution dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="df35f-121">Creating the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in Visual Studio.</span></span>  
  
- <span data-ttu-id="df35f-122">Ajout du fichier de code de base de données au projet.</span><span class="sxs-lookup"><span data-stu-id="df35f-122">Adding the database code file to the project.</span></span>  
  
- <span data-ttu-id="df35f-123">Création d'un objet représentant un client.</span><span class="sxs-lookup"><span data-stu-id="df35f-123">Creating a new customer object.</span></span>  
  
- <span data-ttu-id="df35f-124">Modification du nom de contact d'un client.</span><span class="sxs-lookup"><span data-stu-id="df35f-124">Modifying the contact name of a customer.</span></span>  
  
- <span data-ttu-id="df35f-125">Suppression d'une commande.</span><span class="sxs-lookup"><span data-stu-id="df35f-125">Deleting an order.</span></span>  
  
- <span data-ttu-id="df35f-126">Soumission de ces modifications à la base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="df35f-126">Submitting these changes to the Northwind database.</span></span>  
  
## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="df35f-127">Création d'une solution LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="df35f-127">Creating a LINQ to SQL Solution</span></span>  

 <span data-ttu-id="df35f-128">Dans cette première tâche, vous allez créer une solution Visual Studio qui contient les références nécessaires pour générer et exécuter un [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projet.</span><span class="sxs-lookup"><span data-stu-id="df35f-128">In this first task, you create a Visual Studio solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>  
  
#### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="df35f-129">Pour créer une solution LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="df35f-129">To create a LINQ to SQL solution</span></span>  
  
1. <span data-ttu-id="df35f-130">Dans le menu **Fichier** de Visual Studio, cliquez sur **Nouveau projet**.</span><span class="sxs-lookup"><span data-stu-id="df35f-130">On the Visual Studio **File** menu, click **New Project**.</span></span>  
  
2. <span data-ttu-id="df35f-131">Dans le volet **types de projets** de la boîte de dialogue **nouveau projet** , cliquez sur **Visual Basic**.</span><span class="sxs-lookup"><span data-stu-id="df35f-131">In the **Project types** pane in the **New Project** dialog box, click **Visual Basic**.</span></span>  
  
3. <span data-ttu-id="df35f-132">Dans le volet **Modèles**, cliquez sur **Application console**.</span><span class="sxs-lookup"><span data-stu-id="df35f-132">In the **Templates** pane, click **Console Application**.</span></span>  
  
4. <span data-ttu-id="df35f-133">Dans la zone **nom** , tapez **LinqDataManipulationApp**.</span><span class="sxs-lookup"><span data-stu-id="df35f-133">In the **Name** box, type **LinqDataManipulationApp**.</span></span>  
  
5. <span data-ttu-id="df35f-134">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="df35f-134">Click **OK**.</span></span>  
  
## <a name="adding-linq-references-and-directives"></a><span data-ttu-id="df35f-135">Ajout de références et de directives LINQ</span><span class="sxs-lookup"><span data-stu-id="df35f-135">Adding LINQ References and Directives</span></span>  

 <span data-ttu-id="df35f-136">Cette procédure pas à pas utilise des assemblys qui ne sont pas nécessairement installés par défaut dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="df35f-136">This walkthrough uses assemblies that might not be installed by default in your project.</span></span> <span data-ttu-id="df35f-137">Si `System.Data.Linq` n’est pas listé comme une référence dans votre projet (cliquez sur **Afficher tous les fichiers** dans **Explorateur de solutions** et développez le nœud **références** ), ajoutez-le, comme expliqué dans les étapes suivantes.</span><span class="sxs-lookup"><span data-stu-id="df35f-137">If `System.Data.Linq` is not listed as a reference in your project (click **Show All Files** in **Solution Explorer** and expand the **References** node), add it, as explained in the following steps.</span></span>  
  
#### <a name="to-add-systemdatalinq"></a><span data-ttu-id="df35f-138">Pour ajouter System.Data.Linq</span><span class="sxs-lookup"><span data-stu-id="df35f-138">To add System.Data.Linq</span></span>  
  
1. <span data-ttu-id="df35f-139">Dans **Explorateur de solutions**, cliquez avec le bouton droit sur **références**, puis cliquez sur **Ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="df35f-139">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>  
  
2. <span data-ttu-id="df35f-140">Dans la boîte de dialogue **Ajouter une référence** , cliquez sur **.net**, sur l’assembly System. Data. Linq, puis sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="df35f-140">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>  
  
     <span data-ttu-id="df35f-141">L'assembly est ajouté au projet.</span><span class="sxs-lookup"><span data-stu-id="df35f-141">The assembly is added to the project.</span></span>  
  
3. <span data-ttu-id="df35f-142">Dans l’éditeur de code, ajoutez les directives suivantes au-dessus de **Module1**:</span><span class="sxs-lookup"><span data-stu-id="df35f-142">In the code editor, add the following directives above **Module1**:</span></span>  
  
     [!code-vb[DLinqWalk3VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#1)]  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a><span data-ttu-id="df35f-143">Ajout du fichier de code Northwind au projet</span><span class="sxs-lookup"><span data-stu-id="df35f-143">Adding the Northwind Code File to the Project</span></span>  

 <span data-ttu-id="df35f-144">Ces étapes supposent que vous avez utilisé l'outil SQLMetal pour générer un fichier de code à partir de l'exemple de base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="df35f-144">These steps assume that you have used the SQLMetal tool to generate a code file from the Northwind sample database.</span></span> <span data-ttu-id="df35f-145">Pour plus d'informations, consultez la section Composants requis au début de cette procédure pas à pas.</span><span class="sxs-lookup"><span data-stu-id="df35f-145">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a><span data-ttu-id="df35f-146">Pour ajouter le fichier de code Northwind au projet</span><span class="sxs-lookup"><span data-stu-id="df35f-146">To add the northwind code file to the project</span></span>  
  
1. <span data-ttu-id="df35f-147">Dans le menu **Projet** , cliquez sur **Ajouter un élément existant**.</span><span class="sxs-lookup"><span data-stu-id="df35f-147">On the **Project** menu, click **Add Existing Item**.</span></span>  
  
2. <span data-ttu-id="df35f-148">Dans la boîte de dialogue **Ajouter un élément existant** , accédez à c:\linqtest2\northwind.vb, puis cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="df35f-148">In the **Add Existing Item** dialog box, navigate to c:\linqtest2\northwind.vb, and then click **Add**.</span></span>  
  
     <span data-ttu-id="df35f-149">Le fichier northwind.vb est ajouté au projet.</span><span class="sxs-lookup"><span data-stu-id="df35f-149">The northwind.vb file is added to the project.</span></span>  
  
## <a name="setting-up-the-database-connection"></a><span data-ttu-id="df35f-150">Paramétrage de la connexion de base de données</span><span class="sxs-lookup"><span data-stu-id="df35f-150">Setting Up the Database Connection</span></span>  

 <span data-ttu-id="df35f-151">Commencez par tester votre connexion à la base de données.</span><span class="sxs-lookup"><span data-stu-id="df35f-151">First, test your connection to the database.</span></span> <span data-ttu-id="df35f-152">Notez en particulier que le nom de la base de données (Northwnd) ne comporte pas de caractère i.</span><span class="sxs-lookup"><span data-stu-id="df35f-152">Note especially that the name of the database, Northwnd, has no i character.</span></span> <span data-ttu-id="df35f-153">Si vous générez des erreurs au cours des étapes suivantes, examinez le fichier northwind.vb pour déterminer comment la classe partielle Northwind est orthographiée.</span><span class="sxs-lookup"><span data-stu-id="df35f-153">If you generate errors in the next steps, review the northwind.vb file to determine how the Northwind partial class is spelled.</span></span>  
  
#### <a name="to-set-up-and-test-the-database-connection"></a><span data-ttu-id="df35f-154">Pour paramétrer et tester la connexion de base de données</span><span class="sxs-lookup"><span data-stu-id="df35f-154">To set up and test the database connection</span></span>  
  
1. <span data-ttu-id="df35f-155">Tapez ou collez le code suivant dans `Sub Main` :</span><span class="sxs-lookup"><span data-stu-id="df35f-155">Type or paste the following code into `Sub Main`:</span></span>  
  
     [!code-vb[DLinqWalk3VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#2)]  
  
2. <span data-ttu-id="df35f-156">Appuyez sur F5 pour tester l'application à ce stade.</span><span class="sxs-lookup"><span data-stu-id="df35f-156">Press F5 to test the application at this point.</span></span>  
  
     <span data-ttu-id="df35f-157">Une fenêtre de **console** s’ouvre.</span><span class="sxs-lookup"><span data-stu-id="df35f-157">A **Console** window opens.</span></span>  
  
     <span data-ttu-id="df35f-158">Fermez l’application en appuyant sur entrée dans la fenêtre de la **console** , ou en cliquant sur **arrêter le débogage** dans le menu **Déboguer** de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="df35f-158">Close the application by pressing Enter in the **Console** window, or by clicking **Stop Debugging** on the Visual Studio **Debug** menu.</span></span>  
  
## <a name="creating-a-new-entity"></a><span data-ttu-id="df35f-159">Création d'une entité</span><span class="sxs-lookup"><span data-stu-id="df35f-159">Creating a New Entity</span></span>  

 <span data-ttu-id="df35f-160">La création d'une entité est une opération simple.</span><span class="sxs-lookup"><span data-stu-id="df35f-160">Creating a new entity is straightforward.</span></span> <span data-ttu-id="df35f-161">Vous pouvez créer des objets (`Customer`, par exemple) à l'aide du mot clé `New`.</span><span class="sxs-lookup"><span data-stu-id="df35f-161">You can create objects (such as `Customer`) by using the `New` keyword.</span></span>  
  
 <span data-ttu-id="df35f-162">Dans cette section et les suivantes, vous apporterez des modifications uniquement au cache local.</span><span class="sxs-lookup"><span data-stu-id="df35f-162">In this and the following sections, you are making changes only to the local cache.</span></span> <span data-ttu-id="df35f-163">Aucune modification n'est envoyée à la base de données tant que vous n'avez pas appelé <xref:System.Data.Linq.DataContext.SubmitChanges%2A> vers la fin de cette procédure pas à pas.</span><span class="sxs-lookup"><span data-stu-id="df35f-163">No changes are sent to the database until you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> toward the end of this walkthrough.</span></span>  
  
#### <a name="to-add-a-new-customer-entity-object"></a><span data-ttu-id="df35f-164">Pour ajouter un nouvel objet d'entité Customer</span><span class="sxs-lookup"><span data-stu-id="df35f-164">To add a new Customer entity object</span></span>  
  
1. <span data-ttu-id="df35f-165">Créez un `Customer` en ajoutant le code suivant avant `Console.ReadLine` dans `Sub Main` :</span><span class="sxs-lookup"><span data-stu-id="df35f-165">Create a new `Customer` by adding the following code before `Console.ReadLine` in `Sub Main`:</span></span>  
  
     [!code-vb[DLinqWalk3VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#3)]  
  
2. <span data-ttu-id="df35f-166">Appuyez sur F5 pour déboguer la solution.</span><span class="sxs-lookup"><span data-stu-id="df35f-166">Press F5 to debug the solution.</span></span>  
  
     <span data-ttu-id="df35f-167">Les résultats suivants s'affichent dans la fenêtre de console :</span><span class="sxs-lookup"><span data-stu-id="df35f-167">The results that are shown in the console window are as follows:</span></span>  
  
     `Customers matching CA before insert:`  
  
     `Customer ID: CACTU`  
  
     `Customer ID: RICAR`  
  
     <span data-ttu-id="df35f-168">Notez que la nouvelle ligne n'apparaît pas dans les résultats.</span><span class="sxs-lookup"><span data-stu-id="df35f-168">Note that the new row does not appear in the results.</span></span> <span data-ttu-id="df35f-169">Les nouvelles données n'ont pas encore été soumises à la base de données.</span><span class="sxs-lookup"><span data-stu-id="df35f-169">The new data has not yet been submitted to the database.</span></span>  
  
3. <span data-ttu-id="df35f-170">Appuyez sur entrée dans la fenêtre de **console** pour arrêter le débogage.</span><span class="sxs-lookup"><span data-stu-id="df35f-170">Press Enter in the **Console** window to stop debugging.</span></span>  
  
## <a name="updating-an-entity"></a><span data-ttu-id="df35f-171">Mise à jour d'une entité</span><span class="sxs-lookup"><span data-stu-id="df35f-171">Updating an Entity</span></span>  

 <span data-ttu-id="df35f-172">Au cours des étapes suivantes, vous allez récupérer un objet `Customer` et modifier l'une de ses propriétés.</span><span class="sxs-lookup"><span data-stu-id="df35f-172">In the following steps, you will retrieve a `Customer` object and modify one of its properties.</span></span>  
  
#### <a name="to-change-the-name-of-a-customer"></a><span data-ttu-id="df35f-173">Pour modifier le nom d'un client</span><span class="sxs-lookup"><span data-stu-id="df35f-173">To change the name of a Customer</span></span>  
  
- <span data-ttu-id="df35f-174">Ajoutez le code suivant au-dessus de `Console.ReadLine()` :</span><span class="sxs-lookup"><span data-stu-id="df35f-174">Add the following code above `Console.ReadLine()`:</span></span>  
  
     [!code-vb[DLinqWalk3VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#4)]  
  
## <a name="deleting-an-entity"></a><span data-ttu-id="df35f-175">Suppression d’une entité</span><span class="sxs-lookup"><span data-stu-id="df35f-175">Deleting an Entity</span></span>  

 <span data-ttu-id="df35f-176">Vous pouvez supprimer la première commande à l'aide du même objet Customer.</span><span class="sxs-lookup"><span data-stu-id="df35f-176">Using the same customer object, you can delete the first order.</span></span>  
  
 <span data-ttu-id="df35f-177">Le code suivant montre comment couper les relations entre les lignes et supprimer une ligne de la base de données.</span><span class="sxs-lookup"><span data-stu-id="df35f-177">The following code demonstrates how to sever relationships between rows, and how to delete a row from the database.</span></span>  
  
#### <a name="to-delete-a-row"></a><span data-ttu-id="df35f-178">Pour supprimer une ligne</span><span class="sxs-lookup"><span data-stu-id="df35f-178">To delete a row</span></span>  
  
- <span data-ttu-id="df35f-179">Ajoutez le code suivant juste au-dessus de `Console.ReadLine()` :</span><span class="sxs-lookup"><span data-stu-id="df35f-179">Add the following code just above `Console.ReadLine()`:</span></span>  
  
     [!code-vb[DLinqWalk3VB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#5)]  
  
## <a name="submitting-changes-to-the-database"></a><span data-ttu-id="df35f-180">Soumission des modifications à la base de données</span><span class="sxs-lookup"><span data-stu-id="df35f-180">Submitting Changes to the Database</span></span>  

 <span data-ttu-id="df35f-181">La dernière étape requise pour la création, la mise à jour et la suppression d'objets consiste à soumettre les modifications à la base de données.</span><span class="sxs-lookup"><span data-stu-id="df35f-181">The final step required for creating, updating, and deleting objects is to actually submit the changes to the database.</span></span> <span data-ttu-id="df35f-182">Sans cette étape, vos modifications restent locales et n'apparaissent pas dans les résultats de requêtes.</span><span class="sxs-lookup"><span data-stu-id="df35f-182">Without this step, your changes are only local and will not appear in query results.</span></span>  
  
#### <a name="to-submit-changes-to-the-database"></a><span data-ttu-id="df35f-183">Pour soumettre les modifications à la base de données</span><span class="sxs-lookup"><span data-stu-id="df35f-183">To submit changes to the database</span></span>  
  
1. <span data-ttu-id="df35f-184">Insérez le code suivant juste au-dessus de `Console.ReadLine` :</span><span class="sxs-lookup"><span data-stu-id="df35f-184">Insert the following code just above `Console.ReadLine`:</span></span>  
  
     [!code-vb[DLinqWalk3VB#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#6)]  
  
2. <span data-ttu-id="df35f-185">Insérez le code suivant (après `SubmitChanges`) pour afficher les effets avant/après de la soumission des modifications :</span><span class="sxs-lookup"><span data-stu-id="df35f-185">Insert the following code (after `SubmitChanges`) to show the before and after effects of submitting the changes:</span></span>  
  
     [!code-vb[DLinqWalk3VB#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#7)]  
  
3. <span data-ttu-id="df35f-186">Appuyez sur F5 pour déboguer la solution.</span><span class="sxs-lookup"><span data-stu-id="df35f-186">Press F5 to debug the solution.</span></span>  
  
     <span data-ttu-id="df35f-187">La fenêtre de console se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="df35f-187">The console window appears as follows:</span></span>  
  
    ```console
    Customers matching CA before update:  
    Customer ID: CACTU  
    Customer ID: RICAR  
  
    The Order Detail to be deleted is: OrderID = 10643  
  
    Customers matching CA after update:  
    Customer ID: A3VCA  
    Customer ID: CACTU  
    Customer ID: RICAR  
    ```  
  
4. <span data-ttu-id="df35f-188">Appuyez sur entrée dans la fenêtre de **console** pour arrêter le débogage.</span><span class="sxs-lookup"><span data-stu-id="df35f-188">Press Enter in the **Console** window to stop debugging.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="df35f-189">Une fois que vous avez soumis les modifications (ajouté le nouveau client), vous ne pouvez plus exécuter cette solution telle quelle car vous ne pouvez plus ajouter le même client tel quel.</span><span class="sxs-lookup"><span data-stu-id="df35f-189">After you have added the new customer by submitting the changes, you cannot execute this solution again as is, because you cannot add the same customer again as is.</span></span> <span data-ttu-id="df35f-190">Pour exécuter à nouveau la solution, modifiez la valeur de l'ID client à ajouter.</span><span class="sxs-lookup"><span data-stu-id="df35f-190">To execute the solution again, change the value of the customer ID to be added.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df35f-191">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="df35f-191">See also</span></span>

- [<span data-ttu-id="df35f-192">Apprentissage par les procédures pas à pas</span><span class="sxs-lookup"><span data-stu-id="df35f-192">Learning by Walkthroughs</span></span>](learning-by-walkthroughs.md)

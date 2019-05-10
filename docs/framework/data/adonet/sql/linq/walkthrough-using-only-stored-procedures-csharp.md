---
title: 'Procédure pas à pas : Utilisation de procédures stockées uniquement (C#)'
ms.date: 03/30/2017
ms.assetid: ecde4bf2-fa4d-4252-b5e4-96a46b9e097d
ms.openlocfilehash: f4c34252f7d92985dac94663c85d3cca0dc58ab3
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64655124"
---
# <a name="walkthrough-using-only-stored-procedures-c"></a><span data-ttu-id="20936-102">Procédure pas à pas : Utilisation de procédures stockées uniquement (C#)</span><span class="sxs-lookup"><span data-stu-id="20936-102">Walkthrough: Using Only Stored Procedures (C#)</span></span>
<span data-ttu-id="20936-103">Cette procédure pas à pas fournit un scénario [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] de base de bout en bout pour accéder aux données en exécutant des procédures stockées uniquement.</span><span class="sxs-lookup"><span data-stu-id="20936-103">This walkthrough provides a basic end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario for accessing data by executing stored procedures only.</span></span> <span data-ttu-id="20936-104">Cette approche est souvent utilisée par les administrateurs de base de données pour limiter les moyens d'accès au magasin de données.</span><span class="sxs-lookup"><span data-stu-id="20936-104">This approach is often used by database administrators to limit how the datastore is accessed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="20936-105">Vous pouvez également utiliser des procédures stockées dans les applications [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pour substituer le comportement par défaut, plus particulièrement pour les processus `Create`, `Update` et `Delete`.</span><span class="sxs-lookup"><span data-stu-id="20936-105">You can also use stored procedures in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications to override default behavior, especially for `Create`, `Update`, and `Delete` processes.</span></span> <span data-ttu-id="20936-106">Pour plus d’informations, consultez [personnalisation des opérations d’insertion, mise à jour et supprimer](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="20936-106">For more information, see [Customizing Insert, Update, and Delete Operations](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span></span>  
  
 <span data-ttu-id="20936-107">Dans le cadre de cette procédure pas à pas, vous allez utiliser deux méthodes qui ont été mappés à des procédures stockées dans la base de données Northwind : CustOrdersDetail et CustOrderHist.</span><span class="sxs-lookup"><span data-stu-id="20936-107">For purposes of this walkthrough, you will use two methods that have been mapped to stored procedures in the Northwind sample database: CustOrdersDetail and CustOrderHist.</span></span> <span data-ttu-id="20936-108">Le mappage se produit lorsque vous exécutez l'outil en ligne de commande SQLMetal pour générer un fichier C#.</span><span class="sxs-lookup"><span data-stu-id="20936-108">The mapping occurs when you run the SqlMetal command-line tool to generate a C# file.</span></span> <span data-ttu-id="20936-109">Pour plus d'informations, consultez la section Composants requis par la suite dans cette procédure pas à pas.</span><span class="sxs-lookup"><span data-stu-id="20936-109">For more information, see the Prerequisites section later in this walkthrough.</span></span>  
  
 <span data-ttu-id="20936-110">Cette procédure pas à pas ne s'appuie pas sur le [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="20936-110">This walkthrough does not rely on the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)].</span></span> <span data-ttu-id="20936-111">Les développeurs à l’aide de Visual Studio peuvent également utiliser le [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] pour implémenter des fonctionnalités de procédure stockée.</span><span class="sxs-lookup"><span data-stu-id="20936-111">Developers using Visual Studio can also use the [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] to implement stored procedure functionality.</span></span> <span data-ttu-id="20936-112">Consultez [outils LINQ to SQL dans Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span><span class="sxs-lookup"><span data-stu-id="20936-112">See [LINQ to SQL Tools in Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="20936-113">Cette procédure pas à pas a été écrite à l'aide des paramètres de développement Visual C#.</span><span class="sxs-lookup"><span data-stu-id="20936-113">This walkthrough was written by using Visual C# Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="20936-114">Prérequis</span><span class="sxs-lookup"><span data-stu-id="20936-114">Prerequisites</span></span>  
 <span data-ttu-id="20936-115">Elle requiert les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="20936-115">This walkthrough requires the following:</span></span>  
  
- <span data-ttu-id="20936-116">Les fichiers sont stockés dans un dossier dédié, c:\linqtest7.</span><span class="sxs-lookup"><span data-stu-id="20936-116">This walkthrough uses a dedicated folder ("c:\linqtest7") to hold files.</span></span> <span data-ttu-id="20936-117">Vous devez créer ce dossier avant de commencer la procédure pas à pas.</span><span class="sxs-lookup"><span data-stu-id="20936-117">Create this folder before you begin the walkthrough.</span></span>  
  
- <span data-ttu-id="20936-118">Exemple de base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="20936-118">The Northwind sample database.</span></span>  
  
     <span data-ttu-id="20936-119">Si cette base de données n'est pas disponible sur votre ordinateur de développement, vous pouvez la télécharger à partir du site de téléchargement Microsoft.</span><span class="sxs-lookup"><span data-stu-id="20936-119">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="20936-120">Pour obtenir des instructions, consultez [téléchargement d’exemples de bases de données](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="20936-120">For instructions, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span> <span data-ttu-id="20936-121">Après avoir téléchargé la base de données, copiez le fichier northwnd.mdf dans le dossier c:\linqtest7.</span><span class="sxs-lookup"><span data-stu-id="20936-121">After you have downloaded the database, copy the northwnd.mdf file to the c:\linqtest7 folder.</span></span>  
  
- <span data-ttu-id="20936-122">Fichier de code C# généré à partir de la base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="20936-122">A C# code file generated from the Northwind database.</span></span>  
  
     <span data-ttu-id="20936-123">Cette procédure pas à pas a été écrite à l'aide de l'outil SQLMetal, avec la ligne de commande suivante :</span><span class="sxs-lookup"><span data-stu-id="20936-123">This walkthrough was written by using the SqlMetal tool with the following command line:</span></span>  
  
     <span data-ttu-id="20936-124">**sqlmetal /code:"c:\linqtest7\northwind.cs" /language:csharp "c:\linqtest7\northwnd.mdf" /sprocs /functions /pluralize**</span><span class="sxs-lookup"><span data-stu-id="20936-124">**sqlmetal /code:"c:\linqtest7\northwind.cs" /language:csharp "c:\linqtest7\northwnd.mdf" /sprocs /functions /pluralize**</span></span>  
  
     <span data-ttu-id="20936-125">Pour plus d’informations, consultez [SqlMetal.exe (outil de génération de code)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="20936-125">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="overview"></a><span data-ttu-id="20936-126">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="20936-126">Overview</span></span>  
 <span data-ttu-id="20936-127">Cette procédure pas à pas se compose de six tâches principales :</span><span class="sxs-lookup"><span data-stu-id="20936-127">This walkthrough consists of six main tasks:</span></span>  
  
- <span data-ttu-id="20936-128">Configurer le [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="20936-128">Setting up the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in Visual Studio.</span></span>  
  
- <span data-ttu-id="20936-129">Ajout de l'assembly System.Data.Linq au projet.</span><span class="sxs-lookup"><span data-stu-id="20936-129">Adding the System.Data.Linq assembly to the project.</span></span>  
  
- <span data-ttu-id="20936-130">Ajout du fichier de code de base de données au projet.</span><span class="sxs-lookup"><span data-stu-id="20936-130">Adding the database code file to the project.</span></span>  
  
- <span data-ttu-id="20936-131">Création d'une connexion à la base de données.</span><span class="sxs-lookup"><span data-stu-id="20936-131">Creating a connection with the database.</span></span>  
  
- <span data-ttu-id="20936-132">Configuration de l'interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="20936-132">Setting up the user interface.</span></span>  
  
- <span data-ttu-id="20936-133">Exécution et test de l'application.</span><span class="sxs-lookup"><span data-stu-id="20936-133">Running and testing the application.</span></span>  
  
## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="20936-134">Création d'une solution LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="20936-134">Creating a LINQ to SQL Solution</span></span>  
 <span data-ttu-id="20936-135">Dans cette première tâche, vous créez une solution Visual Studio qui contient les références nécessaires pour générer et exécuter un [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projet.</span><span class="sxs-lookup"><span data-stu-id="20936-135">In this first task, you create a Visual Studio solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>  
  
#### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="20936-136">Pour créer une solution LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="20936-136">To create a LINQ to SQL solution</span></span>  
  
1. <span data-ttu-id="20936-137">Dans Visual Studio **fichier** menu, pointez sur **New**, puis cliquez sur **projet**.</span><span class="sxs-lookup"><span data-stu-id="20936-137">On the Visual Studio **File** menu, point to **New**, and then click **Project**.</span></span>  
  
2. <span data-ttu-id="20936-138">Dans le **types de projets** volet dans le **nouveau projet** boîte de dialogue, cliquez sur **Visual C#** .</span><span class="sxs-lookup"><span data-stu-id="20936-138">In the **Project types** pane in the **New Project** dialog box, click **Visual C#**.</span></span>  
  
3. <span data-ttu-id="20936-139">Dans le volet **Modèles** , cliquez sur **Application Windows Forms**.</span><span class="sxs-lookup"><span data-stu-id="20936-139">In the **Templates** pane, click **Windows Forms Application**.</span></span>  
  
4. <span data-ttu-id="20936-140">Dans le **nom** , tapez **SprocOnlyApp**.</span><span class="sxs-lookup"><span data-stu-id="20936-140">In the **Name** box, type **SprocOnlyApp**.</span></span>  
  
5. <span data-ttu-id="20936-141">Dans le **emplacement** , vérifiez où vous souhaitez stocker vos fichiers projet.</span><span class="sxs-lookup"><span data-stu-id="20936-141">In the **Location** box, verify where you want to store your project files.</span></span>  
  
6. <span data-ttu-id="20936-142">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="20936-142">Click **OK**.</span></span>  
  
     <span data-ttu-id="20936-143">Le Concepteur Windows Forms s'ouvre.</span><span class="sxs-lookup"><span data-stu-id="20936-143">The Windows Forms Designer opens.</span></span>  
  
## <a name="adding-the-linq-to-sql-assembly-reference"></a><span data-ttu-id="20936-144">Ajout de la référence à l'assembly LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="20936-144">Adding the LINQ to SQL Assembly Reference</span></span>  
 <span data-ttu-id="20936-145">L'assembly [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] n'est pas inclus dans le modèle Application Windows Forms standard.</span><span class="sxs-lookup"><span data-stu-id="20936-145">The [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] assembly is not included in the standard Windows Forms Application template.</span></span> <span data-ttu-id="20936-146">Vous devrez ajouter l'assembly vous-même, comme expliqué dans les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="20936-146">You will have to add the assembly yourself, as explained in the following steps:</span></span>  
  
#### <a name="to-add-systemdatalinqdll"></a><span data-ttu-id="20936-147">Pour ajouter System.Data.Linq.dll</span><span class="sxs-lookup"><span data-stu-id="20936-147">To add System.Data.Linq.dll</span></span>  
  
1. <span data-ttu-id="20936-148">Dans **l’Explorateur de solutions**, avec le bouton droit **références**, puis cliquez sur **ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="20936-148">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>  
  
2. <span data-ttu-id="20936-149">Dans le **ajouter une référence** boîte de dialogue, cliquez sur **.NET**et cliquez sur l’assembly System.Data.Linq, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="20936-149">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>  
  
     <span data-ttu-id="20936-150">L'assembly est ajouté au projet.</span><span class="sxs-lookup"><span data-stu-id="20936-150">The assembly is added to the project.</span></span>  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a><span data-ttu-id="20936-151">Ajout du fichier de code Northwind au projet</span><span class="sxs-lookup"><span data-stu-id="20936-151">Adding the Northwind Code File to the Project</span></span>  
 <span data-ttu-id="20936-152">Ces étapes supposent que vous avez utilisé l'outil SQLMetal pour générer un fichier de code à partir de l'exemple de base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="20936-152">This step assumes that you have used the SqlMetal tool to generate a code file from the Northwind sample database.</span></span> <span data-ttu-id="20936-153">Pour plus d'informations, consultez la section Composants requis au début de cette procédure pas à pas.</span><span class="sxs-lookup"><span data-stu-id="20936-153">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a><span data-ttu-id="20936-154">Pour ajouter le fichier de code Northwind au projet</span><span class="sxs-lookup"><span data-stu-id="20936-154">To add the northwind code file to the project</span></span>  
  
1. <span data-ttu-id="20936-155">Sur le **projet** menu, cliquez sur **ajouter un élément existant**.</span><span class="sxs-lookup"><span data-stu-id="20936-155">On the **Project** menu, click **Add Existing Item**.</span></span>  
  
2. <span data-ttu-id="20936-156">Dans le **ajouter un élément existant** boîte de dialogue Déplacer vers c:\linqtest7\northwind.cs, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="20936-156">In the **Add Existing Item** dialog box, move to c:\linqtest7\northwind.cs, and then click **Add**.</span></span>  
  
     <span data-ttu-id="20936-157">Le fichier northwind.cs est ajouté au projet.</span><span class="sxs-lookup"><span data-stu-id="20936-157">The northwind.cs file is added to the project.</span></span>  
  
## <a name="creating-a-database-connection"></a><span data-ttu-id="20936-158">Création d'une connexion à une base de données</span><span class="sxs-lookup"><span data-stu-id="20936-158">Creating a Database Connection</span></span>  
 <span data-ttu-id="20936-159">Au cours de cette étape, vous allez définir la connexion à l'exemple de base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="20936-159">In this step, you define the connection to the Northwind sample database.</span></span> <span data-ttu-id="20936-160">Cette procédure pas à pas utilise "c:\linqtest7\northwnd.mdf" comme chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="20936-160">This walkthrough uses "c:\linqtest7\northwnd.mdf" as the path.</span></span>  
  
#### <a name="to-create-the-database-connection"></a><span data-ttu-id="20936-161">Pour créer la connexion de base de données</span><span class="sxs-lookup"><span data-stu-id="20936-161">To create the database connection</span></span>  
  
1. <span data-ttu-id="20936-162">Dans **l’Explorateur de solutions**, avec le bouton droit **Form1.cs**, puis cliquez sur **afficher le Code**.</span><span class="sxs-lookup"><span data-stu-id="20936-162">In **Solution Explorer**, right-click **Form1.cs**, and then click **View Code**.</span></span>  
  
2. <span data-ttu-id="20936-163">Tapez le code suivant dans la classe `Form1` :</span><span class="sxs-lookup"><span data-stu-id="20936-163">Type the following code into the `Form1` class:</span></span>  
  
     [!code-csharp[DLinqWalk4CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#1)]  
  
## <a name="setting-up-the-user-interface"></a><span data-ttu-id="20936-164">Configuration de l'interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="20936-164">Setting up the User Interface</span></span>  
 <span data-ttu-id="20936-165">Au cours de cette tâche, vous configurez une interface afin que les utilisateurs puissent exécuter des procédures stockées pour accéder aux données dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="20936-165">In this task you set up an interface so that users can execute stored procedures to access data in the database.</span></span> <span data-ttu-id="20936-166">Dans les applications que vous développez avec cette procédure pas à pas, les utilisateurs peuvent accéder aux données dans la base de données uniquement en utilisant les procédures stockées incorporées dans l'application.</span><span class="sxs-lookup"><span data-stu-id="20936-166">In the applications that you are developing with this walkthrough, users can access data in the database only by using the stored procedures embedded in the application.</span></span>  
  
#### <a name="to-set-up-the-user-interface"></a><span data-ttu-id="20936-167">Pour configurer l'interface utilisateur</span><span class="sxs-lookup"><span data-stu-id="20936-167">To set up the user interface</span></span>  
  
1. <span data-ttu-id="20936-168">Revenez à la Windows Forms concepteur (**Form1.cs [Design]**).</span><span class="sxs-lookup"><span data-stu-id="20936-168">Return to the Windows Forms Designer (**Form1.cs[Design]**).</span></span>  
  
2. <span data-ttu-id="20936-169">Dans le menu **Affichage** , cliquez sur **Boîte à outils**.</span><span class="sxs-lookup"><span data-stu-id="20936-169">On the **View** menu, click **Toolbox**.</span></span>  
  
     <span data-ttu-id="20936-170">La boîte à outils s'ouvre.</span><span class="sxs-lookup"><span data-stu-id="20936-170">The toolbox opens.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="20936-171">Cliquez sur le **masquage automatique** punaise pour maintenir la boîte à outils ouverte pendant que vous effectuez les autres étapes de cette section.</span><span class="sxs-lookup"><span data-stu-id="20936-171">Click the **AutoHide** pushpin to keep the toolbox open while you perform the remaining steps in this section.</span></span>  
  
3. <span data-ttu-id="20936-172">Faites glisser deux boutons, deux zones de texte et deux étiquettes à partir de la boîte à outils vers **Form1**.</span><span class="sxs-lookup"><span data-stu-id="20936-172">Drag two buttons, two text boxes, and two labels from the toolbox onto **Form1**.</span></span>  
  
     <span data-ttu-id="20936-173">Disposez les contrôles comme dans l'illustration associée.</span><span class="sxs-lookup"><span data-stu-id="20936-173">Arrange the controls as in the accompanying illustration.</span></span> <span data-ttu-id="20936-174">Développez **Form1** afin que les contrôles s’ajustent facilement.</span><span class="sxs-lookup"><span data-stu-id="20936-174">Expand **Form1** so that the controls fit easily.</span></span>  
  
4. <span data-ttu-id="20936-175">Avec le bouton droit **label1**, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="20936-175">Right-click **label1**, and then click **Properties**.</span></span>  
  
5. <span data-ttu-id="20936-176">Modifier le **texte** propriété à partir de **label1** à **Enter OrderID :**.</span><span class="sxs-lookup"><span data-stu-id="20936-176">Change the **Text** property from **label1** to **Enter OrderID:**.</span></span>  
  
6. <span data-ttu-id="20936-177">Dans la même façon pour **label2**, modifiez le **texte** propriété à partir de **label2** à **Enter CustomerID :**.</span><span class="sxs-lookup"><span data-stu-id="20936-177">In the same way for **label2**, change the **Text** property from **label2** to **Enter CustomerID:**.</span></span>  
  
7. <span data-ttu-id="20936-178">Dans la même façon, modifiez le **texte** propriété pour **button1** à **Order Details**.</span><span class="sxs-lookup"><span data-stu-id="20936-178">In the same way, change the **Text** property for **button1** to **Order Details**.</span></span>  
  
8. <span data-ttu-id="20936-179">Modifier le **texte** propriété pour **button2** à **l’historique des commandes**.</span><span class="sxs-lookup"><span data-stu-id="20936-179">Change the **Text** property for **button2** to **Order History**.</span></span>  
  
     <span data-ttu-id="20936-180">Élargissez les contrôles boutons afin que tout le texte soit visible.</span><span class="sxs-lookup"><span data-stu-id="20936-180">Widen the button controls so that all the text is visible.</span></span>  
  
#### <a name="to-handle-button-clicks"></a><span data-ttu-id="20936-181">Pour gérer des clics de bouton</span><span class="sxs-lookup"><span data-stu-id="20936-181">To handle button clicks</span></span>  
  
1. <span data-ttu-id="20936-182">Double-cliquez sur **Order Details** sur **Form1** pour ouvrir le Gestionnaire d’événements button1 dans l’éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="20936-182">Double-click **Order Details** on **Form1** to open the button1 event handler in the code editor.</span></span>  
  
2. <span data-ttu-id="20936-183">Tapez le code suivant dans le gestionnaire d'événements `button1` :</span><span class="sxs-lookup"><span data-stu-id="20936-183">Type the following code into the `button1` handler:</span></span>  
  
     [!code-csharp[DLinqWalk4CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#2)]  
  
3. <span data-ttu-id="20936-184">Double-cliquez maintenant sur **button2** sur **Form1** pour ouvrir le `button2` Gestionnaire</span><span class="sxs-lookup"><span data-stu-id="20936-184">Now double-click **button2** on **Form1** to open the `button2` handler</span></span>  
  
4. <span data-ttu-id="20936-185">Tapez le code suivant dans le gestionnaire d'événements `button2` :</span><span class="sxs-lookup"><span data-stu-id="20936-185">Type the following code into the `button2` handler:</span></span>  
  
     [!code-csharp[DLinqWalk4CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#3)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="20936-186">Test de l'application</span><span class="sxs-lookup"><span data-stu-id="20936-186">Testing the Application</span></span>  
 <span data-ttu-id="20936-187">Vous allez maintenant tester votre application.</span><span class="sxs-lookup"><span data-stu-id="20936-187">Now it is time to test your application.</span></span> <span data-ttu-id="20936-188">Notez que votre contact avec le magasin de données est limité aux actions que les deux procédures stockées peuvent accepter.</span><span class="sxs-lookup"><span data-stu-id="20936-188">Note that your contact with the datastore is limited to whatever actions the two stored procedures can take.</span></span> <span data-ttu-id="20936-189">Ces actions consistent à retourner les produits inclus pour n'importe quel orderID que vous entrez ou à retourner un historique des produits commandés pour n'importe quel CustomerID que vous entrez.</span><span class="sxs-lookup"><span data-stu-id="20936-189">Those actions are to return the products included for any orderID you enter, or to return a history of products ordered for any CustomerID you enter.</span></span>  
  
#### <a name="to-test-the-application"></a><span data-ttu-id="20936-190">Pour tester l'application</span><span class="sxs-lookup"><span data-stu-id="20936-190">To test the application</span></span>  
  
1. <span data-ttu-id="20936-191">Appuyez sur F5 pour démarrer le débogage.</span><span class="sxs-lookup"><span data-stu-id="20936-191">Press F5 to start debugging.</span></span>  
  
     <span data-ttu-id="20936-192">Form1 s'affiche.</span><span class="sxs-lookup"><span data-stu-id="20936-192">Form1 appears.</span></span>  
  
2. <span data-ttu-id="20936-193">Dans le **Enter OrderID** , tapez `10249`, puis cliquez sur **Order Details**.</span><span class="sxs-lookup"><span data-stu-id="20936-193">In the **Enter OrderID** box, type `10249`, and then click **Order Details**.</span></span>  
  
     <span data-ttu-id="20936-194">Un message répertorie les produits inclus dans la commande 10249.</span><span class="sxs-lookup"><span data-stu-id="20936-194">A message box lists the products included in order 10249.</span></span>  
  
     <span data-ttu-id="20936-195">Cliquez sur **OK** pour fermer la boîte de message.</span><span class="sxs-lookup"><span data-stu-id="20936-195">Click **OK** to close the message box.</span></span>  
  
3. <span data-ttu-id="20936-196">Dans le **Enter CustomerID** , tapez `ALFKI`, puis cliquez sur **l’historique des commandes**.</span><span class="sxs-lookup"><span data-stu-id="20936-196">In the **Enter CustomerID** box, type `ALFKI`, and then click **Order History**.</span></span>  
  
     <span data-ttu-id="20936-197">Le message qui apparaît répertorie l'historique des commandes pour le client ALFKI.</span><span class="sxs-lookup"><span data-stu-id="20936-197">A message box appears that lists the order history for customer ALFKI.</span></span>  
  
     <span data-ttu-id="20936-198">Cliquez sur **OK** pour fermer la boîte de message.</span><span class="sxs-lookup"><span data-stu-id="20936-198">Click **OK** to close the message box.</span></span>  
  
4. <span data-ttu-id="20936-199">Dans le **Enter OrderID** , tapez `123`, puis cliquez sur **Order Details**.</span><span class="sxs-lookup"><span data-stu-id="20936-199">In the **Enter OrderID** box, type `123`, and then click **Order Details**.</span></span>  
  
     <span data-ttu-id="20936-200">Le message suivant s'affiche : « Aucun résultat ».</span><span class="sxs-lookup"><span data-stu-id="20936-200">A message box appears that displays "No results."</span></span>  
  
     <span data-ttu-id="20936-201">Cliquez sur **OK** pour fermer la boîte de message.</span><span class="sxs-lookup"><span data-stu-id="20936-201">Click **OK** to close the message box.</span></span>  
  
5. <span data-ttu-id="20936-202">Sur le **déboguer** menu, cliquez sur **arrêter le débogage**.</span><span class="sxs-lookup"><span data-stu-id="20936-202">On the **Debug** menu, click **Stop debugging**.</span></span>  
  
     <span data-ttu-id="20936-203">La session de débogage s'arrête.</span><span class="sxs-lookup"><span data-stu-id="20936-203">The debug session closes.</span></span>  
  
6. <span data-ttu-id="20936-204">Si vous avez terminé les tests, vous pouvez cliquer sur **fermer le projet** sur le **fichier** menu et enregistrez votre projet lorsque vous y êtes invité.</span><span class="sxs-lookup"><span data-stu-id="20936-204">If you have finished experimenting, you can click **Close Project** on the **File** menu, and save your project when you are prompted.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="20936-205">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="20936-205">Next Steps</span></span>  
 <span data-ttu-id="20936-206">Vous pouvez améliorer ce projet en apportant des modifications.</span><span class="sxs-lookup"><span data-stu-id="20936-206">You can enhance this project by making some changes.</span></span> <span data-ttu-id="20936-207">Par exemple, vous pouvez répertorier les procédures stockées disponibles dans une zone de liste et demander à l'utilisateur de sélectionner les procédures à exécuter.</span><span class="sxs-lookup"><span data-stu-id="20936-207">For example, you could list available stored procedures in a list box and have the user select which procedures to execute.</span></span> <span data-ttu-id="20936-208">Vous pouvez également transmettre en continu la sortie des rapports dans un fichier texte.</span><span class="sxs-lookup"><span data-stu-id="20936-208">You could also stream the output of the reports to a text file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20936-209">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="20936-209">See also</span></span>

- [<span data-ttu-id="20936-210">Apprentissage par les procédures pas à pas</span><span class="sxs-lookup"><span data-stu-id="20936-210">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
- [<span data-ttu-id="20936-211">Procédures stockées</span><span class="sxs-lookup"><span data-stu-id="20936-211">Stored Procedures</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)

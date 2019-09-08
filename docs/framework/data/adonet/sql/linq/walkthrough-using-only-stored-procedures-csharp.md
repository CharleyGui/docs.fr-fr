---
title: 'Procédure pas à pas : Utilisation de procédures stockées uniquement (C#)'
ms.date: 03/30/2017
ms.assetid: ecde4bf2-fa4d-4252-b5e4-96a46b9e097d
ms.openlocfilehash: f980402c976db9ee327a7b726e36a0a4d9d6d73f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792111"
---
# <a name="walkthrough-using-only-stored-procedures-c"></a><span data-ttu-id="0a362-102">Procédure pas à pas : Utilisation de procédures stockées uniquement (C#)</span><span class="sxs-lookup"><span data-stu-id="0a362-102">Walkthrough: Using Only Stored Procedures (C#)</span></span>

<span data-ttu-id="0a362-103">Cette procédure pas à pas fournit un scénario [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] de base de bout en bout pour accéder aux données en exécutant des procédures stockées uniquement.</span><span class="sxs-lookup"><span data-stu-id="0a362-103">This walkthrough provides a basic end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario for accessing data by executing stored procedures only.</span></span> <span data-ttu-id="0a362-104">Cette approche est souvent utilisée par les administrateurs de base de données pour limiter les moyens d'accès au magasin de données.</span><span class="sxs-lookup"><span data-stu-id="0a362-104">This approach is often used by database administrators to limit how the datastore is accessed.</span></span>

> [!NOTE]
> <span data-ttu-id="0a362-105">Vous pouvez également utiliser des procédures stockées dans les applications [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pour substituer le comportement par défaut, plus particulièrement pour les processus `Create`, `Update` et `Delete`.</span><span class="sxs-lookup"><span data-stu-id="0a362-105">You can also use stored procedures in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications to override default behavior, especially for `Create`, `Update`, and `Delete` processes.</span></span> <span data-ttu-id="0a362-106">Pour plus d’informations, consultez [Personnalisation des opérations d’insertion, de mise à jour et de suppression](customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="0a362-106">For more information, see [Customizing Insert, Update, and Delete Operations](customizing-insert-update-and-delete-operations.md).</span></span>

<span data-ttu-id="0a362-107">Dans le cadre de cette procédure pas à pas, vous allez utiliser deux méthodes qui ont été mappées à des procédures stockées dans l’exemple de base de données Northwind : CustOrdersDetail et CustOrderHist.</span><span class="sxs-lookup"><span data-stu-id="0a362-107">For purposes of this walkthrough, you will use two methods that have been mapped to stored procedures in the Northwind sample database: CustOrdersDetail and CustOrderHist.</span></span> <span data-ttu-id="0a362-108">Le mappage se produit lorsque vous exécutez l'outil en ligne de commande SQLMetal pour générer un fichier C#.</span><span class="sxs-lookup"><span data-stu-id="0a362-108">The mapping occurs when you run the SqlMetal command-line tool to generate a C# file.</span></span> <span data-ttu-id="0a362-109">Pour plus d'informations, consultez la section Composants requis par la suite dans cette procédure pas à pas.</span><span class="sxs-lookup"><span data-stu-id="0a362-109">For more information, see the Prerequisites section later in this walkthrough.</span></span>

<span data-ttu-id="0a362-110">Cette procédure pas à pas ne repose pas sur le Concepteur Objet Relationnel.</span><span class="sxs-lookup"><span data-stu-id="0a362-110">This walkthrough does not rely on the Object Relational Designer.</span></span> <span data-ttu-id="0a362-111">Les développeurs qui utilisent Visual Studio peuvent également utiliser le Concepteur O/R pour implémenter les fonctionnalités de procédure stockée.</span><span class="sxs-lookup"><span data-stu-id="0a362-111">Developers using Visual Studio can also use the O/R Designer to implement stored procedure functionality.</span></span> <span data-ttu-id="0a362-112">Consultez [LINQ to SQL Tools dans Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span><span class="sxs-lookup"><span data-stu-id="0a362-112">See [LINQ to SQL Tools in Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span></span>

[!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]

<span data-ttu-id="0a362-113">Cette procédure pas à pas a été écrite à l'aide des paramètres de développement Visual C#.</span><span class="sxs-lookup"><span data-stu-id="0a362-113">This walkthrough was written by using Visual C# Development Settings.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0a362-114">Prérequis</span><span class="sxs-lookup"><span data-stu-id="0a362-114">Prerequisites</span></span>

<span data-ttu-id="0a362-115">Elle requiert les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="0a362-115">This walkthrough requires the following:</span></span>

- <span data-ttu-id="0a362-116">Les fichiers sont stockés dans un dossier dédié, c:\linqtest7.</span><span class="sxs-lookup"><span data-stu-id="0a362-116">This walkthrough uses a dedicated folder ("c:\linqtest7") to hold files.</span></span> <span data-ttu-id="0a362-117">Vous devez créer ce dossier avant de commencer la procédure pas à pas.</span><span class="sxs-lookup"><span data-stu-id="0a362-117">Create this folder before you begin the walkthrough.</span></span>

- <span data-ttu-id="0a362-118">Exemple de base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="0a362-118">The Northwind sample database.</span></span>

     <span data-ttu-id="0a362-119">Si cette base de données n'est pas disponible sur votre ordinateur de développement, vous pouvez la télécharger à partir du site de téléchargement Microsoft.</span><span class="sxs-lookup"><span data-stu-id="0a362-119">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="0a362-120">Pour obtenir des instructions, consultez [téléchargement d’exemples de bases de données](downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="0a362-120">For instructions, see [Downloading Sample Databases](downloading-sample-databases.md).</span></span> <span data-ttu-id="0a362-121">Après avoir téléchargé la base de données, copiez le fichier northwnd.mdf dans le dossier c:\linqtest7.</span><span class="sxs-lookup"><span data-stu-id="0a362-121">After you have downloaded the database, copy the northwnd.mdf file to the c:\linqtest7 folder.</span></span>

- <span data-ttu-id="0a362-122">Fichier de code C# généré à partir de la base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="0a362-122">A C# code file generated from the Northwind database.</span></span>

     <span data-ttu-id="0a362-123">Cette procédure pas à pas a été écrite à l'aide de l'outil SQLMetal, avec la ligne de commande suivante :</span><span class="sxs-lookup"><span data-stu-id="0a362-123">This walkthrough was written by using the SqlMetal tool with the following command line:</span></span>

     <span data-ttu-id="0a362-124">**sqlmetal /code:"c:\linqtest7\northwind.cs" /language:csharp "c:\linqtest7\northwnd.mdf" /sprocs /functions /pluralize**</span><span class="sxs-lookup"><span data-stu-id="0a362-124">**sqlmetal /code:"c:\linqtest7\northwind.cs" /language:csharp "c:\linqtest7\northwnd.mdf" /sprocs /functions /pluralize**</span></span>

     <span data-ttu-id="0a362-125">Pour plus d’informations, consultez [SqlMetal.exe (outil de génération de code)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="0a362-125">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>

## <a name="overview"></a><span data-ttu-id="0a362-126">Présentation</span><span class="sxs-lookup"><span data-stu-id="0a362-126">Overview</span></span>

<span data-ttu-id="0a362-127">Cette procédure pas à pas se compose de six tâches principales :</span><span class="sxs-lookup"><span data-stu-id="0a362-127">This walkthrough consists of six main tasks:</span></span>

- <span data-ttu-id="0a362-128">Configuration de la [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0a362-128">Setting up the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in Visual Studio.</span></span>

- <span data-ttu-id="0a362-129">Ajout de l'assembly System.Data.Linq au projet.</span><span class="sxs-lookup"><span data-stu-id="0a362-129">Adding the System.Data.Linq assembly to the project.</span></span>

- <span data-ttu-id="0a362-130">Ajout du fichier de code de base de données au projet.</span><span class="sxs-lookup"><span data-stu-id="0a362-130">Adding the database code file to the project.</span></span>

- <span data-ttu-id="0a362-131">Création d'une connexion à la base de données.</span><span class="sxs-lookup"><span data-stu-id="0a362-131">Creating a connection with the database.</span></span>

- <span data-ttu-id="0a362-132">Configuration de l'interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="0a362-132">Setting up the user interface.</span></span>

- <span data-ttu-id="0a362-133">Exécution et test de l'application.</span><span class="sxs-lookup"><span data-stu-id="0a362-133">Running and testing the application.</span></span>

## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="0a362-134">Création d'une solution LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="0a362-134">Creating a LINQ to SQL Solution</span></span>

<span data-ttu-id="0a362-135">Dans cette première tâche, vous allez créer une solution Visual Studio qui contient les références nécessaires pour générer et exécuter [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] un projet.</span><span class="sxs-lookup"><span data-stu-id="0a362-135">In this first task, you create a Visual Studio solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>

### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="0a362-136">Pour créer une solution LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="0a362-136">To create a LINQ to SQL solution</span></span>

1. <span data-ttu-id="0a362-137">Dans le menu **fichier** de Visual Studio, pointez sur **nouveau**, puis cliquez sur **projet**.</span><span class="sxs-lookup"><span data-stu-id="0a362-137">On the Visual Studio **File** menu, point to **New**, and then click **Project**.</span></span>

2. <span data-ttu-id="0a362-138">Dans le volet **types de projets** de la boîte de dialogue **nouveau projet** , cliquez sur **visuel C#** .</span><span class="sxs-lookup"><span data-stu-id="0a362-138">In the **Project types** pane in the **New Project** dialog box, click **Visual C#**.</span></span>

3. <span data-ttu-id="0a362-139">Dans le volet **Modèles** , cliquez sur **Application Windows Forms**.</span><span class="sxs-lookup"><span data-stu-id="0a362-139">In the **Templates** pane, click **Windows Forms Application**.</span></span>

4. <span data-ttu-id="0a362-140">Dans la zone **nom** , tapez **SprocOnlyApp**.</span><span class="sxs-lookup"><span data-stu-id="0a362-140">In the **Name** box, type **SprocOnlyApp**.</span></span>

5. <span data-ttu-id="0a362-141">Dans la zone **emplacement** , vérifiez l’emplacement où vous souhaitez stocker vos fichiers projet.</span><span class="sxs-lookup"><span data-stu-id="0a362-141">In the **Location** box, verify where you want to store your project files.</span></span>

6. <span data-ttu-id="0a362-142">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="0a362-142">Click **OK**.</span></span>

     <span data-ttu-id="0a362-143">Le Concepteur Windows Forms s'ouvre.</span><span class="sxs-lookup"><span data-stu-id="0a362-143">The Windows Forms Designer opens.</span></span>

## <a name="adding-the-linq-to-sql-assembly-reference"></a><span data-ttu-id="0a362-144">Ajout de la référence à l'assembly LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="0a362-144">Adding the LINQ to SQL Assembly Reference</span></span>

<span data-ttu-id="0a362-145">L'assembly [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] n'est pas inclus dans le modèle Application Windows Forms standard.</span><span class="sxs-lookup"><span data-stu-id="0a362-145">The [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] assembly is not included in the standard Windows Forms Application template.</span></span> <span data-ttu-id="0a362-146">Vous devrez ajouter l'assembly vous-même, comme expliqué dans les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="0a362-146">You will have to add the assembly yourself, as explained in the following steps:</span></span>

### <a name="to-add-systemdatalinqdll"></a><span data-ttu-id="0a362-147">Pour ajouter System.Data.Linq.dll</span><span class="sxs-lookup"><span data-stu-id="0a362-147">To add System.Data.Linq.dll</span></span>

1. <span data-ttu-id="0a362-148">Dans **Explorateur de solutions**, cliquez avec le bouton droit sur **références**, puis cliquez sur **Ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="0a362-148">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>

2. <span data-ttu-id="0a362-149">Dans la boîte de dialogue **Ajouter une référence** , cliquez sur **.net**, sur l’assembly System. Data. Linq, puis sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="0a362-149">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>

     <span data-ttu-id="0a362-150">L'assembly est ajouté au projet.</span><span class="sxs-lookup"><span data-stu-id="0a362-150">The assembly is added to the project.</span></span>

## <a name="adding-the-northwind-code-file-to-the-project"></a><span data-ttu-id="0a362-151">Ajout du fichier de code Northwind au projet</span><span class="sxs-lookup"><span data-stu-id="0a362-151">Adding the Northwind Code File to the Project</span></span>

<span data-ttu-id="0a362-152">Ces étapes supposent que vous avez utilisé l'outil SQLMetal pour générer un fichier de code à partir de l'exemple de base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="0a362-152">This step assumes that you have used the SqlMetal tool to generate a code file from the Northwind sample database.</span></span> <span data-ttu-id="0a362-153">Pour plus d'informations, consultez la section Composants requis au début de cette procédure pas à pas.</span><span class="sxs-lookup"><span data-stu-id="0a362-153">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>

### <a name="to-add-the-northwind-code-file-to-the-project"></a><span data-ttu-id="0a362-154">Pour ajouter le fichier de code Northwind au projet</span><span class="sxs-lookup"><span data-stu-id="0a362-154">To add the northwind code file to the project</span></span>

1. <span data-ttu-id="0a362-155">Dans le menu **projet** , cliquez sur **Ajouter un élément existant**.</span><span class="sxs-lookup"><span data-stu-id="0a362-155">On the **Project** menu, click **Add Existing Item**.</span></span>

2. <span data-ttu-id="0a362-156">Dans la boîte de dialogue **Ajouter un élément existant** , accédez à c:\linqtest7\northwind.cs, puis cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="0a362-156">In the **Add Existing Item** dialog box, move to c:\linqtest7\northwind.cs, and then click **Add**.</span></span>

     <span data-ttu-id="0a362-157">Le fichier northwind.cs est ajouté au projet.</span><span class="sxs-lookup"><span data-stu-id="0a362-157">The northwind.cs file is added to the project.</span></span>

## <a name="creating-a-database-connection"></a><span data-ttu-id="0a362-158">Création d'une connexion à une base de données</span><span class="sxs-lookup"><span data-stu-id="0a362-158">Creating a Database Connection</span></span>

<span data-ttu-id="0a362-159">Au cours de cette étape, vous allez définir la connexion à l'exemple de base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="0a362-159">In this step, you define the connection to the Northwind sample database.</span></span> <span data-ttu-id="0a362-160">Cette procédure pas à pas utilise "c:\linqtest7\northwnd.mdf" comme chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="0a362-160">This walkthrough uses "c:\linqtest7\northwnd.mdf" as the path.</span></span>

### <a name="to-create-the-database-connection"></a><span data-ttu-id="0a362-161">Pour créer la connexion de base de données</span><span class="sxs-lookup"><span data-stu-id="0a362-161">To create the database connection</span></span>

1. <span data-ttu-id="0a362-162">Dans **Explorateur de solutions**, cliquez avec le bouton droit sur **Form1.cs**, puis cliquez sur **afficher le code**.</span><span class="sxs-lookup"><span data-stu-id="0a362-162">In **Solution Explorer**, right-click **Form1.cs**, and then click **View Code**.</span></span>

2. <span data-ttu-id="0a362-163">Tapez le code suivant dans la classe `Form1` :</span><span class="sxs-lookup"><span data-stu-id="0a362-163">Type the following code into the `Form1` class:</span></span>

     [!code-csharp[DLinqWalk4CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#1)]

## <a name="setting-up-the-user-interface"></a><span data-ttu-id="0a362-164">Configuration de l'interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="0a362-164">Setting up the User Interface</span></span>

<span data-ttu-id="0a362-165">Au cours de cette tâche, vous configurez une interface afin que les utilisateurs puissent exécuter des procédures stockées pour accéder aux données dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="0a362-165">In this task you set up an interface so that users can execute stored procedures to access data in the database.</span></span> <span data-ttu-id="0a362-166">Dans les applications que vous développez avec cette procédure pas à pas, les utilisateurs peuvent accéder aux données dans la base de données uniquement en utilisant les procédures stockées incorporées dans l'application.</span><span class="sxs-lookup"><span data-stu-id="0a362-166">In the applications that you are developing with this walkthrough, users can access data in the database only by using the stored procedures embedded in the application.</span></span>

### <a name="to-set-up-the-user-interface"></a><span data-ttu-id="0a362-167">Pour configurer l'interface utilisateur</span><span class="sxs-lookup"><span data-stu-id="0a362-167">To set up the user interface</span></span>

1. <span data-ttu-id="0a362-168">Revenez au Concepteur Windows Forms (**Form1. cs [Design]** ).</span><span class="sxs-lookup"><span data-stu-id="0a362-168">Return to the Windows Forms Designer (**Form1.cs[Design]**).</span></span>

2. <span data-ttu-id="0a362-169">Dans le menu **Affichage** , cliquez sur **Boîte à outils**.</span><span class="sxs-lookup"><span data-stu-id="0a362-169">On the **View** menu, click **Toolbox**.</span></span>

     <span data-ttu-id="0a362-170">La boîte à outils s'ouvre.</span><span class="sxs-lookup"><span data-stu-id="0a362-170">The toolbox opens.</span></span>

    > [!NOTE]
    > <span data-ttu-id="0a362-171">Cliquez sur le punaise **Masquer automatiquement** pour maintenir la boîte à outils ouverte pendant que vous effectuez les étapes restantes de cette section.</span><span class="sxs-lookup"><span data-stu-id="0a362-171">Click the **AutoHide** pushpin to keep the toolbox open while you perform the remaining steps in this section.</span></span>

3. <span data-ttu-id="0a362-172">Faites glisser deux boutons, deux zones de texte et deux étiquettes de la boîte à outils vers **Form1**.</span><span class="sxs-lookup"><span data-stu-id="0a362-172">Drag two buttons, two text boxes, and two labels from the toolbox onto **Form1**.</span></span>

     <span data-ttu-id="0a362-173">Disposez les contrôles comme dans l'illustration associée.</span><span class="sxs-lookup"><span data-stu-id="0a362-173">Arrange the controls as in the accompanying illustration.</span></span> <span data-ttu-id="0a362-174">Développez **Form1** afin que les contrôles s’ajustent facilement.</span><span class="sxs-lookup"><span data-stu-id="0a362-174">Expand **Form1** so that the controls fit easily.</span></span>

4. <span data-ttu-id="0a362-175">Cliquez avec le bouton droit sur **Label1**, puis cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="0a362-175">Right-click **label1**, and then click **Properties**.</span></span>

5. <span data-ttu-id="0a362-176">Modifiez la propriété **Text** de **Label1** en **Enter OrderID :** .</span><span class="sxs-lookup"><span data-stu-id="0a362-176">Change the **Text** property from **label1** to **Enter OrderID:**.</span></span>

6. <span data-ttu-id="0a362-177">De la même façon pour **Label2**, modifiez la propriété **Text** de **Label2** en **Enter CustomerID :** .</span><span class="sxs-lookup"><span data-stu-id="0a362-177">In the same way for **label2**, change the **Text** property from **label2** to **Enter CustomerID:**.</span></span>

7. <span data-ttu-id="0a362-178">De la même façon, modifiez la propriété **Text** de **Button1** en **Order Details**.</span><span class="sxs-lookup"><span data-stu-id="0a362-178">In the same way, change the **Text** property for **button1** to **Order Details**.</span></span>

8. <span data-ttu-id="0a362-179">Modifiez la propriété **Text** de **button2** en **Order History**.</span><span class="sxs-lookup"><span data-stu-id="0a362-179">Change the **Text** property for **button2** to **Order History**.</span></span>

     <span data-ttu-id="0a362-180">Élargissez les contrôles boutons afin que tout le texte soit visible.</span><span class="sxs-lookup"><span data-stu-id="0a362-180">Widen the button controls so that all the text is visible.</span></span>

### <a name="to-handle-button-clicks"></a><span data-ttu-id="0a362-181">Pour gérer des clics de bouton</span><span class="sxs-lookup"><span data-stu-id="0a362-181">To handle button clicks</span></span>

1. <span data-ttu-id="0a362-182">Double-cliquez sur **Order Details** sur **Form1** pour ouvrir le gestionnaire d’événements Button1 dans l’éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="0a362-182">Double-click **Order Details** on **Form1** to open the button1 event handler in the code editor.</span></span>

2. <span data-ttu-id="0a362-183">Tapez le code suivant dans le gestionnaire d'événements `button1` :</span><span class="sxs-lookup"><span data-stu-id="0a362-183">Type the following code into the `button1` handler:</span></span>

     [!code-csharp[DLinqWalk4CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#2)]

3. <span data-ttu-id="0a362-184">Double-cliquez maintenant sur **button2** sur **Form1** pour ouvrir `button2` le gestionnaire</span><span class="sxs-lookup"><span data-stu-id="0a362-184">Now double-click **button2** on **Form1** to open the `button2` handler</span></span>

4. <span data-ttu-id="0a362-185">Tapez le code suivant dans le gestionnaire d'événements `button2` :</span><span class="sxs-lookup"><span data-stu-id="0a362-185">Type the following code into the `button2` handler:</span></span>

     [!code-csharp[DLinqWalk4CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#3)]

## <a name="testing-the-application"></a><span data-ttu-id="0a362-186">Test de l'application</span><span class="sxs-lookup"><span data-stu-id="0a362-186">Testing the Application</span></span>

<span data-ttu-id="0a362-187">Vous allez maintenant tester votre application.</span><span class="sxs-lookup"><span data-stu-id="0a362-187">Now it is time to test your application.</span></span> <span data-ttu-id="0a362-188">Notez que votre contact avec le magasin de données est limité aux actions que les deux procédures stockées peuvent accepter.</span><span class="sxs-lookup"><span data-stu-id="0a362-188">Note that your contact with the datastore is limited to whatever actions the two stored procedures can take.</span></span> <span data-ttu-id="0a362-189">Ces actions consistent à retourner les produits inclus pour n'importe quel orderID que vous entrez ou à retourner un historique des produits commandés pour n'importe quel CustomerID que vous entrez.</span><span class="sxs-lookup"><span data-stu-id="0a362-189">Those actions are to return the products included for any orderID you enter, or to return a history of products ordered for any CustomerID you enter.</span></span>

### <a name="to-test-the-application"></a><span data-ttu-id="0a362-190">Pour tester l'application</span><span class="sxs-lookup"><span data-stu-id="0a362-190">To test the application</span></span>

1. <span data-ttu-id="0a362-191">Appuyez sur F5 pour démarrer le débogage.</span><span class="sxs-lookup"><span data-stu-id="0a362-191">Press F5 to start debugging.</span></span>

     <span data-ttu-id="0a362-192">Form1 s'affiche.</span><span class="sxs-lookup"><span data-stu-id="0a362-192">Form1 appears.</span></span>

2. <span data-ttu-id="0a362-193">Dans la zone **Enter OrderID** , tapez `10249`, puis cliquez sur **Order Details**.</span><span class="sxs-lookup"><span data-stu-id="0a362-193">In the **Enter OrderID** box, type `10249`, and then click **Order Details**.</span></span>

     <span data-ttu-id="0a362-194">Un message répertorie les produits inclus dans la commande 10249.</span><span class="sxs-lookup"><span data-stu-id="0a362-194">A message box lists the products included in order 10249.</span></span>

     <span data-ttu-id="0a362-195">Cliquez sur **OK** pour fermer la boîte de message.</span><span class="sxs-lookup"><span data-stu-id="0a362-195">Click **OK** to close the message box.</span></span>

3. <span data-ttu-id="0a362-196">Dans la zone **entrer CustomerID** , tapez `ALFKI`, puis cliquez sur **historique des commandes**.</span><span class="sxs-lookup"><span data-stu-id="0a362-196">In the **Enter CustomerID** box, type `ALFKI`, and then click **Order History**.</span></span>

     <span data-ttu-id="0a362-197">Le message qui apparaît répertorie l'historique des commandes pour le client ALFKI.</span><span class="sxs-lookup"><span data-stu-id="0a362-197">A message box appears that lists the order history for customer ALFKI.</span></span>

     <span data-ttu-id="0a362-198">Cliquez sur **OK** pour fermer la boîte de message.</span><span class="sxs-lookup"><span data-stu-id="0a362-198">Click **OK** to close the message box.</span></span>

4. <span data-ttu-id="0a362-199">Dans la zone **Enter OrderID** , tapez `123`, puis cliquez sur **Order Details**.</span><span class="sxs-lookup"><span data-stu-id="0a362-199">In the **Enter OrderID** box, type `123`, and then click **Order Details**.</span></span>

     <span data-ttu-id="0a362-200">Le message suivant s'affiche : « Aucun résultat ».</span><span class="sxs-lookup"><span data-stu-id="0a362-200">A message box appears that displays "No results."</span></span>

     <span data-ttu-id="0a362-201">Cliquez sur **OK** pour fermer la boîte de message.</span><span class="sxs-lookup"><span data-stu-id="0a362-201">Click **OK** to close the message box.</span></span>

5. <span data-ttu-id="0a362-202">Dans le menu **Déboguer** , cliquez sur **arrêter le débogage**.</span><span class="sxs-lookup"><span data-stu-id="0a362-202">On the **Debug** menu, click **Stop debugging**.</span></span>

     <span data-ttu-id="0a362-203">La session de débogage s'arrête.</span><span class="sxs-lookup"><span data-stu-id="0a362-203">The debug session closes.</span></span>

6. <span data-ttu-id="0a362-204">Si vous avez terminé l’expérimentation, vous pouvez cliquer sur **Fermer le projet** dans le menu **fichier** et enregistrer votre projet lorsque vous y êtes invité.</span><span class="sxs-lookup"><span data-stu-id="0a362-204">If you have finished experimenting, you can click **Close Project** on the **File** menu, and save your project when you are prompted.</span></span>

## <a name="next-steps"></a><span data-ttu-id="0a362-205">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="0a362-205">Next Steps</span></span>

<span data-ttu-id="0a362-206">Vous pouvez améliorer ce projet en apportant des modifications.</span><span class="sxs-lookup"><span data-stu-id="0a362-206">You can enhance this project by making some changes.</span></span> <span data-ttu-id="0a362-207">Par exemple, vous pouvez répertorier les procédures stockées disponibles dans une zone de liste et demander à l'utilisateur de sélectionner les procédures à exécuter.</span><span class="sxs-lookup"><span data-stu-id="0a362-207">For example, you could list available stored procedures in a list box and have the user select which procedures to execute.</span></span> <span data-ttu-id="0a362-208">Vous pouvez également transmettre en continu la sortie des rapports dans un fichier texte.</span><span class="sxs-lookup"><span data-stu-id="0a362-208">You could also stream the output of the reports to a text file.</span></span>

## <a name="see-also"></a><span data-ttu-id="0a362-209">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0a362-209">See also</span></span>

- [<span data-ttu-id="0a362-210">Apprentissage par les procédures pas à pas</span><span class="sxs-lookup"><span data-stu-id="0a362-210">Learning by Walkthroughs</span></span>](learning-by-walkthroughs.md)
- [<span data-ttu-id="0a362-211">Procédures stockées</span><span class="sxs-lookup"><span data-stu-id="0a362-211">Stored Procedures</span></span>](stored-procedures.md)

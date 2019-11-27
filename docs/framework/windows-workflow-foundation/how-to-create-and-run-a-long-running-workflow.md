---
title: Comment créer et exécuter un flux de travail de longue durée
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c0043c89-2192-43c9-986d-3ecec4dd8c9c
ms.openlocfilehash: 10eb4e2947bed9cea89f1cda05272aa3fa0fadaa
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204882"
---
# <a name="how-to-create-and-run-a-long-running-workflow"></a><span data-ttu-id="a7863-102">Comment créer et exécuter un flux de travail de longue durée</span><span class="sxs-lookup"><span data-stu-id="a7863-102">How to create and run a long-running workflow</span></span>

<span data-ttu-id="a7863-103">L’une des fonctionnalités centrales de Windows Workflow Foundation (WF) est la capacité du runtime à conserver et à décharger les workflows inactifs dans une base de données.</span><span class="sxs-lookup"><span data-stu-id="a7863-103">One of the central features of Windows Workflow Foundation (WF) is the runtime’s ability to persist and unload idle workflows to a database.</span></span> <span data-ttu-id="a7863-104">Les étapes de l' [exécution d’un flux de travail](how-to-run-a-workflow.md) ont démontré les principes fondamentaux de l’hébergement de workflow à l’aide d’une application console.</span><span class="sxs-lookup"><span data-stu-id="a7863-104">The steps in [How to: Run a Workflow](how-to-run-a-workflow.md) demonstrated the basics of workflow hosting using a console application.</span></span> <span data-ttu-id="a7863-105">Des exemples de démarrage de workflow, gestionnaires de cycle de vie de workflow et de reprise des signets ont été donnés.</span><span class="sxs-lookup"><span data-stu-id="a7863-105">Examples were shown of starting workflows, workflow lifecycle handlers, and resuming bookmarks.</span></span> <span data-ttu-id="a7863-106">Pour illustrer la persistance de workflow efficacement, un hôte de workflow plus complexe est nécessaire, prenant en charge le démarrage et la reprise de plusieurs instances de workflow.</span><span class="sxs-lookup"><span data-stu-id="a7863-106">In order to demonstrate workflow persistence effectively, a more complex workflow host is required that supports starting and resuming multiple workflow instances.</span></span> <span data-ttu-id="a7863-107">Cette étape du didacticiel explique comment créer une application hôte de formulaire Windows qui prend en charge le démarrage et la reprise de plusieurs instances de workflow, la persistance de workflow, et constitue une base pour les fonctionnalités avancées telles que le suivi et le versioning qui sont expliquées dans les étapes suivantes du didacticiel.</span><span class="sxs-lookup"><span data-stu-id="a7863-107">This step in the tutorial demonstrates how to create a Windows form host application that supports starting and resuming multiple workflow instances, workflow persistence, and provides a basis for the advanced features such as tracking and versioning that are demonstrated in subsequent tutorial steps.</span></span>

> [!NOTE]
> <span data-ttu-id="a7863-108">Cette étape du didacticiel et les étapes suivantes utilisent les trois types de flux de travail à partir de [Comment : créer un flux de travail](how-to-create-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="a7863-108">This tutorial step and the subsequent steps use all three workflow types from [How to: Create a Workflow](how-to-create-a-workflow.md).</span></span> <span data-ttu-id="a7863-109">Si vous n’avez pas effectué les trois types, vous pouvez télécharger une version terminée des étapes à partir de [Windows Workflow Foundation (WF45)-prise en main didacticiel](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="a7863-109">If you did not complete all three types you can download a completed version of the steps from [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>

> [!NOTE]
> <span data-ttu-id="a7863-110">Pour télécharger une version complète ou afficher une vidéo pas à pas du didacticiel, consultez [Windows Workflow Foundation (WF45)-prise en main didacticiel](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="a7863-110">To download a completed version or view a video walkthrough of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>

## <a name="to-create-the-persistence-database"></a><span data-ttu-id="a7863-111">Pour créer la base de données de persistance</span><span class="sxs-lookup"><span data-stu-id="a7863-111">To create the persistence database</span></span>

1. <span data-ttu-id="a7863-112">Ouvrez SQL Server Management Studio et connectez-vous au serveur local, par exemple **.\SQLEXPRESS**.</span><span class="sxs-lookup"><span data-stu-id="a7863-112">Open SQL Server Management Studio and connect to the local server, for example **.\SQLEXPRESS**.</span></span> <span data-ttu-id="a7863-113">Cliquez avec le bouton droit sur le nœud **bases de données** sur le serveur local, puis sélectionnez **nouvelle base de données**.</span><span class="sxs-lookup"><span data-stu-id="a7863-113">Right-click the **Databases** node on the local server, and select **New Database**.</span></span> <span data-ttu-id="a7863-114">Nommez la nouvelle base de données **WF45GettingStartedTutorial**, acceptez toutes les autres valeurs, puis sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="a7863-114">Name the new database **WF45GettingStartedTutorial**, accept all other values, and select **OK**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="a7863-115">Vérifiez que vous disposez de l’autorisation **Create Database** sur le serveur local avant de créer la base de données.</span><span class="sxs-lookup"><span data-stu-id="a7863-115">Ensure that you have **Create Database** permission on the local server before creating the database.</span></span>

2. <span data-ttu-id="a7863-116">Dans le menu **fichier** , choisissez **ouvrir**, **fichier** .</span><span class="sxs-lookup"><span data-stu-id="a7863-116">Choose **Open**, **File** from the **File** menu.</span></span> <span data-ttu-id="a7863-117">Accédez au dossier suivant : *C:\Windows\Microsoft.NET\Framework\v4.0.30319\sql\en*</span><span class="sxs-lookup"><span data-stu-id="a7863-117">Browse to the following folder: *C:\Windows\Microsoft.NET\Framework\v4.0.30319\sql\en*</span></span>

    <span data-ttu-id="a7863-118">Sélectionnez les deux fichiers suivants, puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="a7863-118">Select the following two files and click **Open**.</span></span>

    - <span data-ttu-id="a7863-119">*SqlWorkflowInstanceStoreLogic. SQL*</span><span class="sxs-lookup"><span data-stu-id="a7863-119">*SqlWorkflowInstanceStoreLogic.sql*</span></span>

    - <span data-ttu-id="a7863-120">*SqlWorkflowInstanceStoreSchema. SQL*</span><span class="sxs-lookup"><span data-stu-id="a7863-120">*SqlWorkflowInstanceStoreSchema.sql*</span></span>

3. <span data-ttu-id="a7863-121">Choisissez **SqlWorkflowInstanceStoreSchema. SQL** dans le menu **fenêtre** .</span><span class="sxs-lookup"><span data-stu-id="a7863-121">Choose **SqlWorkflowInstanceStoreSchema.sql** from the **Window** menu.</span></span> <span data-ttu-id="a7863-122">Vérifiez que **WF45GettingStartedTutorial** est sélectionné dans la liste déroulante **bases de données disponibles** et choisissez **exécuter** dans le menu **requête** .</span><span class="sxs-lookup"><span data-stu-id="a7863-122">Ensure that **WF45GettingStartedTutorial** is selected in the **Available Databases** drop-down and choose **Execute** from the **Query** menu.</span></span>

4. <span data-ttu-id="a7863-123">Choisissez **SqlWorkflowInstanceStoreLogic. SQL** dans le menu **fenêtre** .</span><span class="sxs-lookup"><span data-stu-id="a7863-123">Choose **SqlWorkflowInstanceStoreLogic.sql** from the **Window** menu.</span></span> <span data-ttu-id="a7863-124">Vérifiez que **WF45GettingStartedTutorial** est sélectionné dans la liste déroulante **bases de données disponibles** et choisissez **exécuter** dans le menu **requête** .</span><span class="sxs-lookup"><span data-stu-id="a7863-124">Ensure that **WF45GettingStartedTutorial** is selected in the **Available Databases** drop-down and choose **Execute** from the **Query** menu.</span></span>

    > [!WARNING]
    > <span data-ttu-id="a7863-125">Il est important d'effectuer les deux étapes précédentes dans l'ordre approprié.</span><span class="sxs-lookup"><span data-stu-id="a7863-125">It is important to perform the previous two steps in the correct order.</span></span> <span data-ttu-id="a7863-126">Si les requêtes ne sont pas exécutées dans l'ordre, des erreurs se produisent et la base de données de persistance n'est pas configurée correctement.</span><span class="sxs-lookup"><span data-stu-id="a7863-126">If the queries are executed out of order, errors occur and the persistence database is not configured correctly.</span></span>

## <a name="to-add-the-reference-to-the-durableinstancing-assemblies"></a><span data-ttu-id="a7863-127">Pour ajouter la référence aux assemblys DurableInstancing</span><span class="sxs-lookup"><span data-stu-id="a7863-127">To add the reference to the DurableInstancing assemblies</span></span>

1. <span data-ttu-id="a7863-128">Cliquez avec le bouton droit sur **NumberGuessWorkflowHost** dans **Explorateur de solutions** , puis sélectionnez **Ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="a7863-128">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and select **Add Reference**.</span></span>

2. <span data-ttu-id="a7863-129">Sélectionnez **assemblys** dans la liste **Ajouter une référence** , puis tapez `DurableInstancing` dans la zone Rechercher dans les **assemblys** .</span><span class="sxs-lookup"><span data-stu-id="a7863-129">Select **Assemblies** from the **Add Reference** list, and type `DurableInstancing` into the **Search Assemblies** box.</span></span> <span data-ttu-id="a7863-130">Cette opération filtre les assemblys et facilite la sélection des références souhaitées.</span><span class="sxs-lookup"><span data-stu-id="a7863-130">This filters the assemblies and makes the desired references easier to select.</span></span>

3. <span data-ttu-id="a7863-131">Activez la case à cocher en regard de **System. Activities. DurableInstancing** et **System. Runtime. DurableInstancing** dans la liste des **résultats** de la recherche, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="a7863-131">Check the checkbox beside **System.Activities.DurableInstancing** and **System.Runtime.DurableInstancing** from the **Search Results** list, and click **OK**.</span></span>

## <a name="to-create-the-workflow-host-form"></a><span data-ttu-id="a7863-132">Pour créer le formulaire hôte de workflow</span><span class="sxs-lookup"><span data-stu-id="a7863-132">To create the workflow host form</span></span>

> [!NOTE]
> <span data-ttu-id="a7863-133">Les étapes de cette procédure expliquent comment ajouter et configurer le formulaire manuellement.</span><span class="sxs-lookup"><span data-stu-id="a7863-133">The steps in this procedure describe how to add and configure the form manually.</span></span> <span data-ttu-id="a7863-134">Si vous le souhaitez, téléchargez les fichiers solution pour le didacticiel et ajoutez le formulaire rempli au projet.</span><span class="sxs-lookup"><span data-stu-id="a7863-134">If desired, you can download the solution files for the tutorial and add the completed form to the project.</span></span> <span data-ttu-id="a7863-135">Pour télécharger les fichiers du didacticiel, consultez [Windows Workflow Foundation (WF45)-prise en main didacticiel](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="a7863-135">To download the tutorial files, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span> <span data-ttu-id="a7863-136">Une fois les fichiers téléchargés, cliquez avec le bouton droit sur **NumberGuessWorkflowHost** et choisissez **Ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="a7863-136">Once the files are downloaded, right-click **NumberGuessWorkflowHost** and choose **Add Reference**.</span></span> <span data-ttu-id="a7863-137">Ajoutez une référence à **System. Windows. Forms** et **System. Drawing**.</span><span class="sxs-lookup"><span data-stu-id="a7863-137">Add a reference to **System.Windows.Forms** and **System.Drawing**.</span></span> <span data-ttu-id="a7863-138">Ces références sont ajoutées automatiquement si vous ajoutez un nouveau formulaire à partir du menu **Ajouter**, **nouvel élément** , mais vous devez les ajouter manuellement lors de l’importation d’un formulaire.</span><span class="sxs-lookup"><span data-stu-id="a7863-138">These references are added automatically if you add a new form from the **Add**, **New Item** menu, but must be added manually when importing a form.</span></span> <span data-ttu-id="a7863-139">Une fois les références ajoutées, cliquez avec le bouton droit sur **NumberGuessWorkflowHost** dans **Explorateur de solutions** , puis choisissez **Ajouter**, **élément existant**.</span><span class="sxs-lookup"><span data-stu-id="a7863-139">Once the references are added, right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Add**, **Existing Item**.</span></span> <span data-ttu-id="a7863-140">Accédez au dossier `Form` dans les fichiers projet, sélectionnez **WorkflowHostForm.cs** (ou **WorkflowHostForm. vb**), puis cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="a7863-140">Browse to the `Form` folder in the project files, select **WorkflowHostForm.cs** (or **WorkflowHostForm.vb**), and click **Add**.</span></span> <span data-ttu-id="a7863-141">Si vous choisissez d’importer le formulaire, vous pouvez passer à la section suivante [pour ajouter les propriétés et les méthodes d’assistance du formulaire](#to-add-the-properties-and-helper-methods-of-the-form).</span><span class="sxs-lookup"><span data-stu-id="a7863-141">If you choose to import the form, then you can skip down to the next section, [To add the properties and helper methods of the form](#to-add-the-properties-and-helper-methods-of-the-form).</span></span>

1. <span data-ttu-id="a7863-142">Cliquez avec le bouton droit sur **NumberGuessWorkflowHost** dans **Explorateur de solutions** , puis choisissez **Ajouter**, **nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="a7863-142">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Add**, **New Item**.</span></span>

2. <span data-ttu-id="a7863-143">Dans la liste modèles **installés** , choisissez **Windows Form**, tapez `WorkflowHostForm` dans la zone **nom** , puis cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="a7863-143">In the **Installed** templates list, choose **Windows Form**, type `WorkflowHostForm` in the **Name** box, and click **Add**.</span></span>

3. <span data-ttu-id="a7863-144">Configurez les propriétés suivantes sur le formulaire.</span><span class="sxs-lookup"><span data-stu-id="a7863-144">Configure the following properties on the form.</span></span>

    |<span data-ttu-id="a7863-145">Propriété</span><span class="sxs-lookup"><span data-stu-id="a7863-145">Property</span></span>|<span data-ttu-id="a7863-146">Valeur</span><span class="sxs-lookup"><span data-stu-id="a7863-146">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="a7863-147">FormBorderStyle</span><span class="sxs-lookup"><span data-stu-id="a7863-147">FormBorderStyle</span></span>|<span data-ttu-id="a7863-148">FixedSingle</span><span class="sxs-lookup"><span data-stu-id="a7863-148">FixedSingle</span></span>|
    |<span data-ttu-id="a7863-149">MaximizeBox</span><span class="sxs-lookup"><span data-stu-id="a7863-149">MaximizeBox</span></span>|<span data-ttu-id="a7863-150">False</span><span class="sxs-lookup"><span data-stu-id="a7863-150">False</span></span>|
    |<span data-ttu-id="a7863-151">Taille</span><span class="sxs-lookup"><span data-stu-id="a7863-151">Size</span></span>|<span data-ttu-id="a7863-152">400, 420</span><span class="sxs-lookup"><span data-stu-id="a7863-152">400, 420</span></span>|

4. <span data-ttu-id="a7863-153">Ajoutez les contrôles suivants au formulaire dans l'ordre spécifié et configurez les propriétés selon les instructions.</span><span class="sxs-lookup"><span data-stu-id="a7863-153">Add the following controls to the form in the order specified and configure the properties as directed.</span></span>

    |<span data-ttu-id="a7863-154">Contrôle</span><span class="sxs-lookup"><span data-stu-id="a7863-154">Control</span></span>|<span data-ttu-id="a7863-155">Propriété : valeur</span><span class="sxs-lookup"><span data-stu-id="a7863-155">Property: Value</span></span>|
    |-------------|---------------------|
    |<span data-ttu-id="a7863-156">**Button**</span><span class="sxs-lookup"><span data-stu-id="a7863-156">**Button**</span></span>|<span data-ttu-id="a7863-157">Nom : NewGame</span><span class="sxs-lookup"><span data-stu-id="a7863-157">Name: NewGame</span></span><br /><br /> <span data-ttu-id="a7863-158">Emplacement : 13, 13</span><span class="sxs-lookup"><span data-stu-id="a7863-158">Location: 13, 13</span></span><br /><br /> <span data-ttu-id="a7863-159">Taille : 75, 23</span><span class="sxs-lookup"><span data-stu-id="a7863-159">Size: 75, 23</span></span><br /><br /> <span data-ttu-id="a7863-160">Texte : nouveau jeu</span><span class="sxs-lookup"><span data-stu-id="a7863-160">Text: New Game</span></span>|
    |<span data-ttu-id="a7863-161">**Étiquette**</span><span class="sxs-lookup"><span data-stu-id="a7863-161">**Label**</span></span>|<span data-ttu-id="a7863-162">Emplacement : 94, 18</span><span class="sxs-lookup"><span data-stu-id="a7863-162">Location: 94, 18</span></span><br /><br /> <span data-ttu-id="a7863-163">Texte : estimation d’un nombre compris entre 1 et</span><span class="sxs-lookup"><span data-stu-id="a7863-163">Text: Guess a number from 1 to</span></span>|
    |<span data-ttu-id="a7863-164">**ComboBox**</span><span class="sxs-lookup"><span data-stu-id="a7863-164">**ComboBox**</span></span>|<span data-ttu-id="a7863-165">Nom : NumberRange</span><span class="sxs-lookup"><span data-stu-id="a7863-165">Name: NumberRange</span></span><br /><br /> <span data-ttu-id="a7863-166">DropDownStyle : DropDownList</span><span class="sxs-lookup"><span data-stu-id="a7863-166">DropDownStyle: DropDownList</span></span><br /><br /> <span data-ttu-id="a7863-167">Éléments : 10, 100, 1000</span><span class="sxs-lookup"><span data-stu-id="a7863-167">Items: 10, 100, 1000</span></span><br /><br /> <span data-ttu-id="a7863-168">Emplacement : 228, 12</span><span class="sxs-lookup"><span data-stu-id="a7863-168">Location: 228, 12</span></span><br /><br /> <span data-ttu-id="a7863-169">Taille : 143, 21</span><span class="sxs-lookup"><span data-stu-id="a7863-169">Size: 143, 21</span></span>|
    |<span data-ttu-id="a7863-170">**Étiquette**</span><span class="sxs-lookup"><span data-stu-id="a7863-170">**Label**</span></span>|<span data-ttu-id="a7863-171">Emplacement : 13, 43</span><span class="sxs-lookup"><span data-stu-id="a7863-171">Location: 13, 43</span></span><br /><br /> <span data-ttu-id="a7863-172">Text : type de workflow</span><span class="sxs-lookup"><span data-stu-id="a7863-172">Text: Workflow type</span></span>|
    |<span data-ttu-id="a7863-173">**ComboBox**</span><span class="sxs-lookup"><span data-stu-id="a7863-173">**ComboBox**</span></span>|<span data-ttu-id="a7863-174">Nom : WorkflowType</span><span class="sxs-lookup"><span data-stu-id="a7863-174">Name: WorkflowType</span></span><br /><br /> <span data-ttu-id="a7863-175">DropDownStyle : DropDownList</span><span class="sxs-lookup"><span data-stu-id="a7863-175">DropDownStyle: DropDownList</span></span><br /><br /> <span data-ttu-id="a7863-176">Éléments : StateMachineNumberGuessWorkflow, FlowchartNumberGuessWorkflow, SequentialNumberGuessWorkflow</span><span class="sxs-lookup"><span data-stu-id="a7863-176">Items: StateMachineNumberGuessWorkflow, FlowchartNumberGuessWorkflow, SequentialNumberGuessWorkflow</span></span><br /><br /> <span data-ttu-id="a7863-177">Emplacement : 94, 40</span><span class="sxs-lookup"><span data-stu-id="a7863-177">Location: 94, 40</span></span><br /><br /> <span data-ttu-id="a7863-178">Taille : 277, 21</span><span class="sxs-lookup"><span data-stu-id="a7863-178">Size: 277, 21</span></span>|
    |<span data-ttu-id="a7863-179">**Étiquette**</span><span class="sxs-lookup"><span data-stu-id="a7863-179">**Label**</span></span>|<span data-ttu-id="a7863-180">Nom : WorkflowVersion</span><span class="sxs-lookup"><span data-stu-id="a7863-180">Name: WorkflowVersion</span></span><br /><br /> <span data-ttu-id="a7863-181">Emplacement : 13, 362</span><span class="sxs-lookup"><span data-stu-id="a7863-181">Location: 13, 362</span></span><br /><br /> <span data-ttu-id="a7863-182">Text : version de workflow</span><span class="sxs-lookup"><span data-stu-id="a7863-182">Text: Workflow version</span></span>|
    |<span data-ttu-id="a7863-183">**GroupBox**</span><span class="sxs-lookup"><span data-stu-id="a7863-183">**GroupBox**</span></span>|<span data-ttu-id="a7863-184">Emplacement : 13, 67</span><span class="sxs-lookup"><span data-stu-id="a7863-184">Location: 13, 67</span></span><br /><br /> <span data-ttu-id="a7863-185">Taille : 358, 287</span><span class="sxs-lookup"><span data-stu-id="a7863-185">Size: 358, 287</span></span><br /><br /> <span data-ttu-id="a7863-186">Texte : jeu</span><span class="sxs-lookup"><span data-stu-id="a7863-186">Text: Game</span></span>|

    > [!NOTE]
    > <span data-ttu-id="a7863-187">Lorsque vous ajoutez les contrôles suivants, placez-les dans le GroupBox.</span><span class="sxs-lookup"><span data-stu-id="a7863-187">When adding the following controls, put them into the GroupBox.</span></span>

    |<span data-ttu-id="a7863-188">Contrôle</span><span class="sxs-lookup"><span data-stu-id="a7863-188">Control</span></span>|<span data-ttu-id="a7863-189">Propriété : valeur</span><span class="sxs-lookup"><span data-stu-id="a7863-189">Property: Value</span></span>|
    |-------------|---------------------|
    |<span data-ttu-id="a7863-190">**Étiquette**</span><span class="sxs-lookup"><span data-stu-id="a7863-190">**Label**</span></span>|<span data-ttu-id="a7863-191">Emplacement : 7, 20</span><span class="sxs-lookup"><span data-stu-id="a7863-191">Location: 7, 20</span></span><br /><br /> <span data-ttu-id="a7863-192">Texte : ID d’instance de workflow</span><span class="sxs-lookup"><span data-stu-id="a7863-192">Text: Workflow Instance Id</span></span>|
    |<span data-ttu-id="a7863-193">**ComboBox**</span><span class="sxs-lookup"><span data-stu-id="a7863-193">**ComboBox**</span></span>|<span data-ttu-id="a7863-194">Nom : InstanceId</span><span class="sxs-lookup"><span data-stu-id="a7863-194">Name: InstanceId</span></span><br /><br /> <span data-ttu-id="a7863-195">DropDownStyle : DropDownList</span><span class="sxs-lookup"><span data-stu-id="a7863-195">DropDownStyle: DropDownList</span></span><br /><br /> <span data-ttu-id="a7863-196">Emplacement : 121, 17</span><span class="sxs-lookup"><span data-stu-id="a7863-196">Location: 121, 17</span></span><br /><br /> <span data-ttu-id="a7863-197">Taille : 227, 21</span><span class="sxs-lookup"><span data-stu-id="a7863-197">Size: 227, 21</span></span>|
    |<span data-ttu-id="a7863-198">**Étiquette**</span><span class="sxs-lookup"><span data-stu-id="a7863-198">**Label**</span></span>|<span data-ttu-id="a7863-199">Emplacement : 7, 47</span><span class="sxs-lookup"><span data-stu-id="a7863-199">Location: 7, 47</span></span><br /><br /> <span data-ttu-id="a7863-200">Texte : estimation</span><span class="sxs-lookup"><span data-stu-id="a7863-200">Text: Guess</span></span>|
    |<span data-ttu-id="a7863-201">**TextBox**</span><span class="sxs-lookup"><span data-stu-id="a7863-201">**TextBox**</span></span>|<span data-ttu-id="a7863-202">Nom : Guess</span><span class="sxs-lookup"><span data-stu-id="a7863-202">Name: Guess</span></span><br /><br /> <span data-ttu-id="a7863-203">Emplacement : 50, 44</span><span class="sxs-lookup"><span data-stu-id="a7863-203">Location: 50, 44</span></span><br /><br /> <span data-ttu-id="a7863-204">Taille : 65, 20</span><span class="sxs-lookup"><span data-stu-id="a7863-204">Size: 65, 20</span></span>|
    |<span data-ttu-id="a7863-205">**Button**</span><span class="sxs-lookup"><span data-stu-id="a7863-205">**Button**</span></span>|<span data-ttu-id="a7863-206">Nom : EnterGuess</span><span class="sxs-lookup"><span data-stu-id="a7863-206">Name: EnterGuess</span></span><br /><br /> <span data-ttu-id="a7863-207">Emplacement : 121, 42</span><span class="sxs-lookup"><span data-stu-id="a7863-207">Location: 121, 42</span></span><br /><br /> <span data-ttu-id="a7863-208">Taille : 75, 23</span><span class="sxs-lookup"><span data-stu-id="a7863-208">Size: 75, 23</span></span><br /><br /> <span data-ttu-id="a7863-209">Texte : entrez l’estimation</span><span class="sxs-lookup"><span data-stu-id="a7863-209">Text: Enter Guess</span></span>|
    |<span data-ttu-id="a7863-210">**Button**</span><span class="sxs-lookup"><span data-stu-id="a7863-210">**Button**</span></span>|<span data-ttu-id="a7863-211">Nom : QuitGame</span><span class="sxs-lookup"><span data-stu-id="a7863-211">Name: QuitGame</span></span><br /><br /> <span data-ttu-id="a7863-212">Emplacement : 274, 42</span><span class="sxs-lookup"><span data-stu-id="a7863-212">Location: 274, 42</span></span><br /><br /> <span data-ttu-id="a7863-213">Taille : 75, 23</span><span class="sxs-lookup"><span data-stu-id="a7863-213">Size: 75, 23</span></span><br /><br /> <span data-ttu-id="a7863-214">Texte : quitter</span><span class="sxs-lookup"><span data-stu-id="a7863-214">Text: Quit</span></span>|
    |<span data-ttu-id="a7863-215">**TextBox**</span><span class="sxs-lookup"><span data-stu-id="a7863-215">**TextBox**</span></span>|<span data-ttu-id="a7863-216">Nom : WorkflowStatus</span><span class="sxs-lookup"><span data-stu-id="a7863-216">Name: WorkflowStatus</span></span><br /><br /> <span data-ttu-id="a7863-217">Emplacement : 10, 73</span><span class="sxs-lookup"><span data-stu-id="a7863-217">Location: 10, 73</span></span><br /><br /> <span data-ttu-id="a7863-218">Multiligne : true</span><span class="sxs-lookup"><span data-stu-id="a7863-218">Multiline: True</span></span><br /><br /> <span data-ttu-id="a7863-219">Lecture seule : true</span><span class="sxs-lookup"><span data-stu-id="a7863-219">ReadOnly: True</span></span><br /><br /> <span data-ttu-id="a7863-220">Barres de défilement : verticale</span><span class="sxs-lookup"><span data-stu-id="a7863-220">ScrollBars: Vertical</span></span><br /><br /> <span data-ttu-id="a7863-221">Taille : 338, 208</span><span class="sxs-lookup"><span data-stu-id="a7863-221">Size: 338, 208</span></span>|

5. <span data-ttu-id="a7863-222">Affectez à la propriété **AcceptButton** du formulaire la valeur **EnterGuess**.</span><span class="sxs-lookup"><span data-stu-id="a7863-222">Set the **AcceptButton** property of the form to **EnterGuess**.</span></span>

 <span data-ttu-id="a7863-223">L'exemple suivant illustre le formulaire terminé.</span><span class="sxs-lookup"><span data-stu-id="a7863-223">The following example illustrates the completed form.</span></span>

 ![Capture d’écran d’un formulaire hôte de flux de travail Windows Workflow Foundation.](./media/how-to-create-and-run-a-long-running-workflow/windows-workflow-foundation-workflowhostform.png)

## <a name="to-add-the-properties-and-helper-methods-of-the-form"></a><span data-ttu-id="a7863-225">Pour ajouter les propriétés et les méthodes d'assistance au formulaire</span><span class="sxs-lookup"><span data-stu-id="a7863-225">To add the properties and helper methods of the form</span></span>

<span data-ttu-id="a7863-226">La procédure de cette section permet d'ajouter des propriétés et des méthodes d'assistance à la classe de formulaire qui configure l'interface utilisateur du formulaire pour prendre en charge l'exécution et la reprise des workflows d'estimation.</span><span class="sxs-lookup"><span data-stu-id="a7863-226">The steps in this section add properties and helper methods to the form class that configure the UI of the form to support running and resuming number guess workflows.</span></span>

1. <span data-ttu-id="a7863-227">Dans **Explorateur de solutions** , cliquez avec le bouton droit sur **WorkflowHostForm** , puis choisissez **afficher le code**.</span><span class="sxs-lookup"><span data-stu-id="a7863-227">Right-click **WorkflowHostForm** in **Solution Explorer** and choose **View Code**.</span></span>

2. <span data-ttu-id="a7863-228">Ajoutez les instructions `using` (ou `Imports`) suivantes au début du fichier avec les autres instructions `using` (ou `Imports`).</span><span class="sxs-lookup"><span data-stu-id="a7863-228">Add the following `using` (or `Imports`) statements at the top of the file with the other `using` (or `Imports`) statements.</span></span>

    ```vb
    Imports System.Activities
    Imports System.Activities.DurableInstancing
    Imports System.Data.SqlClient
    Imports System.IO
    Imports System.Windows.Forms
    ```

    ```csharp
    using System.Activities;
    using System.Activities.DurableInstancing;
    using System.Data.SqlClient;
    using System.IO;
    using System.Windows.Forms;
    ```

3. <span data-ttu-id="a7863-229">Ajoutez les déclarations de membre suivantes à la classe **WorkflowHostForm** .</span><span class="sxs-lookup"><span data-stu-id="a7863-229">Add the following member declarations to the **WorkflowHostForm** class.</span></span>

    ```vb
    Const connectionString = "Server=.\SQLEXPRESS;Initial Catalog=WF45GettingStartedTutorial;Integrated Security=SSPI"
    Dim store As SqlWorkflowInstanceStore
    Dim workflowStarting As Boolean
    ```

    ```csharp
    const string connectionString = "Server=.\\SQLEXPRESS;Initial Catalog=WF45GettingStartedTutorial;Integrated Security=SSPI";
    SqlWorkflowInstanceStore store;
    bool workflowStarting;
    ```

    > [!NOTE]
    > <span data-ttu-id="a7863-230">Si votre chaîne de connexion est différente, mettez à jour `connectionString` pour faire référence à votre base de données.</span><span class="sxs-lookup"><span data-stu-id="a7863-230">If your connection string is different, update `connectionString` to refer to your database.</span></span>

4. <span data-ttu-id="a7863-231">Ajoutez une propriété `WorkflowInstanceId` à la classe `WorkflowFormHost`.</span><span class="sxs-lookup"><span data-stu-id="a7863-231">Add a `WorkflowInstanceId` property to the `WorkflowFormHost` class.</span></span>

    ```vb
    Public ReadOnly Property WorkflowInstanceId() As Guid
        Get
            If InstanceId.SelectedIndex = -1 Then
                Return Guid.Empty
            Else
                Return New Guid(InstanceId.SelectedItem.ToString())
            End If
        End Get
    End Property
    ```

    ```csharp
    public Guid WorkflowInstanceId
    {
        get
        {
            return InstanceId.SelectedIndex == -1 ? Guid.Empty : (Guid)InstanceId.SelectedItem;
        }
    }
    ```

    <span data-ttu-id="a7863-232">La zone de liste déroulante `InstanceId` affiche une liste des ID d’instance de flux de travail persistants, tandis que la propriété `WorkflowInstanceId` retourne le workflow actuellement sélectionné.</span><span class="sxs-lookup"><span data-stu-id="a7863-232">The `InstanceId` combo box displays a list of persisted workflow instance ids, and the `WorkflowInstanceId` property returns the currently selected workflow.</span></span>

5. <span data-ttu-id="a7863-233">Ajoutez un gestionnaire pour l'événement `Load` du formulaire.</span><span class="sxs-lookup"><span data-stu-id="a7863-233">Add a handler for the form `Load` event.</span></span> <span data-ttu-id="a7863-234">Pour ajouter le gestionnaire, basculez en **mode Design** pour le formulaire, cliquez sur l’icône **événements** en haut de la fenêtre **Propriétés** , puis double-cliquez sur **charger**.</span><span class="sxs-lookup"><span data-stu-id="a7863-234">To add the handler, switch to **Design View** for the form, click the **Events** icon at the top of the **Properties** window, and double-click **Load**.</span></span>

    ```vb
    Private Sub WorkflowHostForm_Load(sender As Object, e As EventArgs) Handles Me.Load

    End Sub
    ```

    ```csharp
    private void WorkflowHostForm_Load(object sender, EventArgs e)
    {

    }
    ```

6. <span data-ttu-id="a7863-235">Ajoutez le code suivant à `WorkflowHostForm_Load`.</span><span class="sxs-lookup"><span data-stu-id="a7863-235">Add the following code to `WorkflowHostForm_Load`.</span></span>

    ```vb
    ' Initialize the store and configure it so that it can be used for
    ' multiple WorkflowApplication instances.
    store = New SqlWorkflowInstanceStore(connectionString)
    WorkflowApplication.CreateDefaultInstanceOwner(store, Nothing, WorkflowIdentityFilter.Any)

    ' Set default ComboBox selections.
    NumberRange.SelectedIndex = 0
    WorkflowType.SelectedIndex = 0

    ListPersistedWorkflows()
    ```

    ```csharp
    // Initialize the store and configure it so that it can be used for
    // multiple WorkflowApplication instances.
    store = new SqlWorkflowInstanceStore(connectionString);
    WorkflowApplication.CreateDefaultInstanceOwner(store, null, WorkflowIdentityFilter.Any);

    // Set default ComboBox selections.
    NumberRange.SelectedIndex = 0;
    WorkflowType.SelectedIndex = 0;

    ListPersistedWorkflows();
    ```

    <span data-ttu-id="a7863-236">Lors du chargement du formulaire, `SqlWorkflowInstanceStore` est configuré, les zones de liste déroulante de plage et de type de workflow ont les valeurs par défaut, et les instances persistantes de workflow sont ajoutées à la zone de liste modifiable `InstanceId`.</span><span class="sxs-lookup"><span data-stu-id="a7863-236">When the form loads, the `SqlWorkflowInstanceStore` is configured, the range and workflow type combo boxes are set to default values, and the persisted workflow instances are added to the `InstanceId` combo box.</span></span>

7. <span data-ttu-id="a7863-237">Ajoutez un gestionnaire `SelectedIndexChanged` pour `InstanceId`.</span><span class="sxs-lookup"><span data-stu-id="a7863-237">Add a `SelectedIndexChanged` handler for `InstanceId`.</span></span> <span data-ttu-id="a7863-238">Pour ajouter le gestionnaire, basculez en **mode Design** pour le formulaire, sélectionnez la zone de liste déroulante `InstanceId`, cliquez sur l’icône **événements** en haut de la fenêtre **Propriétés** , puis double-cliquez sur **SelectedIndexChanged**.</span><span class="sxs-lookup"><span data-stu-id="a7863-238">To add the handler, switch to **Design View** for the form, select the `InstanceId` combo box, click the **Events** icon at the top of the **Properties** window, and double-click **SelectedIndexChanged**.</span></span>

    ```vb
    Private Sub InstanceId_SelectedIndexChanged(sender As Object, e As EventArgs) Handles InstanceId.SelectedIndexChanged

    End Sub
    ```

    ```csharp
    private void InstanceId_SelectedIndexChanged(object sender, EventArgs e)
    {

    }
    ```

8. <span data-ttu-id="a7863-239">Ajoutez le code suivant à `InstanceId_SelectedIndexChanged`.</span><span class="sxs-lookup"><span data-stu-id="a7863-239">Add the following code to `InstanceId_SelectedIndexChanged`.</span></span> <span data-ttu-id="a7863-240">Chaque fois que l'utilisateur sélectionne un workflow à l'aide de la zone de liste modifiable, ce gestionnaire met à jour la fenêtre d'état.</span><span class="sxs-lookup"><span data-stu-id="a7863-240">Whenever the user selects a workflow by using the combo box this handler updates the status window.</span></span>

    ```vb
    If InstanceId.SelectedIndex = -1 Then
        Return
    End If

    ' Clear the status window.
    WorkflowStatus.Clear()

    ' Get the workflow version and display it.
    ' If the workflow is just starting then this info will not
    ' be available in the persistence store so do not try and retrieve it.
    If Not workflowStarting Then
        Dim instance As WorkflowApplicationInstance = _
            WorkflowApplication.GetInstance(WorkflowInstanceId, store)

        WorkflowVersion.Text = _
            WorkflowVersionMap.GetIdentityDescription(instance.DefinitionIdentity)

        ' Unload the instance.
        instance.Abandon()
    End If
    ```

    ```csharp
    if (InstanceId.SelectedIndex == -1)
    {
        return;
    }

    // Clear the status window.
    WorkflowStatus.Clear();

    // Get the workflow version and display it.
    // If the workflow is just starting then this info will not
    // be available in the persistence store so do not try and retrieve it.
    if (!workflowStarting)
    {
        WorkflowApplicationInstance instance =
            WorkflowApplication.GetInstance(this.WorkflowInstanceId, store);

        WorkflowVersion.Text =
            WorkflowVersionMap.GetIdentityDescription(instance.DefinitionIdentity);

        // Unload the instance.
        instance.Abandon();
    }
    ```

9. <span data-ttu-id="a7863-241">Ajoutez la méthode `ListPersistedWorkflows` suivante à la classe de formulaire.</span><span class="sxs-lookup"><span data-stu-id="a7863-241">Add the following `ListPersistedWorkflows` method to the form class.</span></span>

    ```vb
    Private Sub ListPersistedWorkflows()
        Using localCon As New SqlConnection(connectionString)
            Dim localCmd As String = _
                "SELECT [InstanceId] FROM [System.Activities.DurableInstancing].[Instances] ORDER BY [CreationTime]"

            Dim cmd As SqlCommand = localCon.CreateCommand()
            cmd.CommandText = localCmd
            localCon.Open()
            Using reader As SqlDataReader = cmd.ExecuteReader(CommandBehavior.CloseConnection)

                While (reader.Read())
                    ' Get the InstanceId of the persisted Workflow.
                    Dim id As Guid = Guid.Parse(reader(0).ToString())
                    InstanceId.Items.Add(id)
                End While
            End Using
        End Using
    End Sub
    ```

    ```csharp
    using (var localCon = new SqlConnection(connectionString))
    {
        string localCmd =
            "SELECT [InstanceId] FROM [System.Activities.DurableInstancing].[Instances] ORDER BY [CreationTime]";

        SqlCommand cmd = localCon.CreateCommand();
        cmd.CommandText = localCmd;
        localCon.Open();
        using (SqlDataReader reader = cmd.ExecuteReader(CommandBehavior.CloseConnection))
        {
            while (reader.Read())
            {
                // Get the InstanceId of the persisted Workflow.
                Guid id = Guid.Parse(reader[0].ToString());
                InstanceId.Items.Add(id);
            }
        }
    }
    ```

    <span data-ttu-id="a7863-242">`ListPersistedWorkflows` interroge le magasin d’instances pour les instances de workflow persistantes et ajoute les ID d’instance à la zone de liste déroulante `cboInstanceId`.</span><span class="sxs-lookup"><span data-stu-id="a7863-242">`ListPersistedWorkflows` queries the instance store for persisted workflow instances, and adds the instance ids to the `cboInstanceId` combo box.</span></span>

10. <span data-ttu-id="a7863-243">Ajoutez la méthode `UpdateStatus` suivante et le délégué correspondant à la classe de formulaire.</span><span class="sxs-lookup"><span data-stu-id="a7863-243">Add the following `UpdateStatus` method and corresponding delegate to the form class.</span></span> <span data-ttu-id="a7863-244">Cette méthode met à jour la fenêtre d'état du formulaire avec l'état du workflow en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="a7863-244">This method updates the status window on the form with the status of the currently running workflow.</span></span>

    ```vb
    Private Delegate Sub UpdateStatusDelegate(msg As String)
    Public Sub UpdateStatus(msg As String)
        ' We may be on a different thread so we need to
        ' make this call using BeginInvoke.
        If InvokeRequired Then
            BeginInvoke(New UpdateStatusDelegate(AddressOf UpdateStatus), msg)
        Else
            If Not msg.EndsWith(vbCrLf) Then
                msg = msg & vbCrLf
            End If

            WorkflowStatus.AppendText(msg)

            ' Ensure that the newly added status is visible.
            WorkflowStatus.SelectionStart = WorkflowStatus.Text.Length
            WorkflowStatus.ScrollToCaret()
        End If
    End Sub
    ```

    ```csharp
    private delegate void UpdateStatusDelegate(string msg);
    public void UpdateStatus(string msg)
    {
        // We may be on a different thread so we need to
        // make this call using BeginInvoke.
        if (InvokeRequired)
        {
            BeginInvoke(new UpdateStatusDelegate(UpdateStatus), msg);
        }
        else
        {
            if (!msg.EndsWith("\r\n"))
            {
                msg += "\r\n";
            }
            WorkflowStatus.AppendText(msg);

            WorkflowStatus.SelectionStart = WorkflowStatus.Text.Length;
            WorkflowStatus.ScrollToCaret();
        }
    }
    ```

11. <span data-ttu-id="a7863-245">Ajoutez la méthode `GameOver` suivante et le délégué correspondant à la classe de formulaire.</span><span class="sxs-lookup"><span data-stu-id="a7863-245">Add the following `GameOver` method and corresponding delegate to the form class.</span></span> <span data-ttu-id="a7863-246">Lorsqu’un workflow se termine, cette méthode met à jour l’interface utilisateur du formulaire en supprimant l’ID d’instance du workflow terminé de la zone de liste déroulante **InstanceID** .</span><span class="sxs-lookup"><span data-stu-id="a7863-246">When a workflow completes, this method updates the form UI by removing the instance id of the completed workflow from the **InstanceId** combo box.</span></span>

    ```vb
    Private Delegate Sub GameOverDelegate()
    Private Sub GameOver()
        If InvokeRequired Then
            BeginInvoke(New GameOverDelegate(AddressOf GameOver))
        Else
            ' Remove this instance from the InstanceId combo box.
            InstanceId.Items.Remove(InstanceId.SelectedItem)
            InstanceId.SelectedIndex = -1
        End If
    End Sub
    ```

    ```csharp
    private delegate void GameOverDelegate();
    private void GameOver()
    {
        if (InvokeRequired)
        {
            BeginInvoke(new GameOverDelegate(GameOver));
        }
        else
        {
            // Remove this instance from the combo box.
            InstanceId.Items.Remove(InstanceId.SelectedItem);
            InstanceId.SelectedIndex = -1;
        }
    }
    ```

## <a name="to-configure-the-instance-store-workflow-lifecycle-handlers-and-extensions"></a><span data-ttu-id="a7863-247">Pour configurer le magasin d’instances, les gestionnaires de cycle de vie de workflow et les extensions</span><span class="sxs-lookup"><span data-stu-id="a7863-247">To configure the instance store, workflow lifecycle handlers, and extensions</span></span>

1. <span data-ttu-id="a7863-248">Ajoutez une méthode `ConfigureWorkflowApplication` à la classe de formulaire.</span><span class="sxs-lookup"><span data-stu-id="a7863-248">Add a `ConfigureWorkflowApplication` method to the form class.</span></span>

    ```vb
    Private Sub ConfigureWorkflowApplication(wfApp As WorkflowApplication)

    End Sub
    ```

    ```csharp
    private void ConfigureWorkflowApplication(WorkflowApplication wfApp)
    {
    }
    ```

    <span data-ttu-id="a7863-249">Cette méthode configure `WorkflowApplication`, ajoute les extensions souhaitées, et ajoute des gestionnaires pour les événements de cycle de vie de workflow.</span><span class="sxs-lookup"><span data-stu-id="a7863-249">This method configures the `WorkflowApplication`, adds the desired extensions, and adds handlers for the workflow lifecycle events.</span></span>

2. <span data-ttu-id="a7863-250">Dans `ConfigureWorkflowApplication`, spécifiez le `SqlWorkflowInstanceStore` pour `WorkflowApplication`.</span><span class="sxs-lookup"><span data-stu-id="a7863-250">In `ConfigureWorkflowApplication`, specify the `SqlWorkflowInstanceStore` for the `WorkflowApplication`.</span></span>

    ```vb
    ' Configure the persistence store.
    wfApp.InstanceStore = store
    ```

    ```csharp
    // Configure the persistence store.
    wfApp.InstanceStore = store;
    ```

3. <span data-ttu-id="a7863-251">Ensuite, créez une instance de `StringWriter` et ajoutez-la à la collection `Extensions` de `WorkflowApplication`.</span><span class="sxs-lookup"><span data-stu-id="a7863-251">Next, create a `StringWriter` instance and add it to the `Extensions` collection of the `WorkflowApplication`.</span></span> <span data-ttu-id="a7863-252">Lorsqu’un `StringWriter` est ajouté aux extensions, il capture toutes les sorties d’activité `WriteLine`.</span><span class="sxs-lookup"><span data-stu-id="a7863-252">When a `StringWriter` is added to the extensions it captures all `WriteLine` activity output.</span></span> <span data-ttu-id="a7863-253">Lorsque le workflow devient inactif, la sortie de `WriteLine` peut être récupérée à partir de `StringWriter` et s'afficher sur le formulaire.</span><span class="sxs-lookup"><span data-stu-id="a7863-253">When the workflow becomes idle, the `WriteLine` output can be extracted from the `StringWriter` and displayed on the form.</span></span>

    ```vb
    ' Add a StringWriter to the extensions. This captures the output
    ' from the WriteLine activities so we can display it in the form.
    Dim sw As New StringWriter()
    wfApp.Extensions.Add(sw)
    ```

    ```csharp
    // Add a StringWriter to the extensions. This captures the output
    // from the WriteLine activities so we can display it in the form.
    var sw = new StringWriter();
    wfApp.Extensions.Add(sw);
    ```

4. <span data-ttu-id="a7863-254">Ajoutez le gestionnaire suivant pour l'événement `Completed`.</span><span class="sxs-lookup"><span data-stu-id="a7863-254">Add the following handler for the `Completed` event.</span></span> <span data-ttu-id="a7863-255">Lorsqu'un workflow se termine correctement, le nombre de tours utilisés pour deviner le nombre est affiché dans la fenêtre d'état.</span><span class="sxs-lookup"><span data-stu-id="a7863-255">When a workflow successfully completes, the number of turns taken to guess the number is displayed to the status window.</span></span> <span data-ttu-id="a7863-256">Si le workflow se termine, les informations sur les exceptions qui ont provoqué l'arrêt sont affichées.</span><span class="sxs-lookup"><span data-stu-id="a7863-256">If the workflow terminates, the exception information that caused the termination is displayed.</span></span> <span data-ttu-id="a7863-257">À la fin du gestionnaire, la méthode `GameOver` est appelée, ce qui supprime le workflow terminé de la liste de workflow.</span><span class="sxs-lookup"><span data-stu-id="a7863-257">At the end of the handler the `GameOver` method is called, which removes the completed workflow from the workflow list.</span></span>

    ```vb
    wfApp.Completed = _
        Sub(e As WorkflowApplicationCompletedEventArgs)
            If e.CompletionState = ActivityInstanceState.Faulted Then
                UpdateStatus($"Workflow Terminated. Exception: {e.TerminationException.GetType().FullName}{vbCrLf}{e.TerminationException.Message}")
            ElseIf e.CompletionState = ActivityInstanceState.Canceled Then
                UpdateStatus("Workflow Canceled.")
            Else
                Dim turns As Integer = Convert.ToInt32(e.Outputs("Turns"))
                UpdateStatus($"Congratulations, you guessed the number in {turns} turns.")
            End If
            GameOver()
        End Sub
    ```

    ```csharp
    wfApp.Completed = delegate(WorkflowApplicationCompletedEventArgs e)
    {
        if (e.CompletionState == ActivityInstanceState.Faulted)
        {
            UpdateStatus($"Workflow Terminated. Exception: {e.TerminationException.GetType().FullName}\r\n{e.TerminationException.Message}");
        }
        else if (e.CompletionState == ActivityInstanceState.Canceled)
        {
            UpdateStatus("Workflow Canceled.");
        }
        else
        {
            int turns = Convert.ToInt32(e.Outputs["Turns"]);
            UpdateStatus($"Congratulations, you guessed the number in {turns} turns.");
        }
        GameOver();
    };
    ```

5. <span data-ttu-id="a7863-258">Ajoutez les gestionnaires `Aborted` et `OnUnhandledException` suivants.</span><span class="sxs-lookup"><span data-stu-id="a7863-258">Add the following `Aborted` and `OnUnhandledException` handlers.</span></span> <span data-ttu-id="a7863-259">La méthode `GameOver` n'est pas appelée à partir du gestionnaire `Aborted`, car lorsqu'une instance du workflow est interrompue, elle ne se termine pas, et il est possible de reprendre l'instance ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="a7863-259">The `GameOver` method is not called from the `Aborted` handler because when a workflow instance is aborted, it does not terminate, and it is possible to resume the instance at a later time.</span></span>

    ```vb
    wfApp.Aborted = _
        Sub(e As WorkflowApplicationAbortedEventArgs)
            UpdateStatus($"Workflow Aborted. Exception: {e.Reason.GetType().FullName}{vbCrLf}{e.Reason.Message}")
        End Sub

    wfApp.OnUnhandledException = _
        Function(e As WorkflowApplicationUnhandledExceptionEventArgs)
            UpdateStatus($"Unhandled Exception: {e.UnhandledException.GetType().FullName}{vbCrLf}{e.UnhandledException.Message}")
            GameOver()
            Return UnhandledExceptionAction.Terminate
        End Function
    ```

    ```csharp
    wfApp.Aborted = delegate(WorkflowApplicationAbortedEventArgs e)
    {
        UpdateStatus($"Workflow Aborted. Exception: {e.Reason.GetType().FullName}\r\n{e.Reason.Message}");
    };

    wfApp.OnUnhandledException = delegate(WorkflowApplicationUnhandledExceptionEventArgs e)
    {
        UpdateStatus($"Unhandled Exception: {e.UnhandledException.GetType().FullName}\r\n{e.UnhandledException.Message}");
        GameOver();
        return UnhandledExceptionAction.Terminate;
    };
    ```

6. <span data-ttu-id="a7863-260">Ajoutez le gestionnaire `PersistableIdle` suivant.</span><span class="sxs-lookup"><span data-stu-id="a7863-260">Add the following `PersistableIdle` handler.</span></span> <span data-ttu-id="a7863-261">Ce gestionnaire extrait l’extension `StringWriter` ajoutée, récupère la sortie des activités `WriteLine`, et l’affiche dans la fenêtre d’état.</span><span class="sxs-lookup"><span data-stu-id="a7863-261">This handler retrieves the `StringWriter` extension that was added, extracts the output from the `WriteLine` activities, and displays it in the status window.</span></span>

    ```vb
    wfApp.PersistableIdle = _
        Function(e As WorkflowApplicationIdleEventArgs)
            ' Send the current WriteLine outputs to the status window.
            Dim writers = e.GetInstanceExtensions(Of StringWriter)()
            For Each writer In writers
                UpdateStatus(writer.ToString())
            Next
            Return PersistableIdleAction.Unload
        End Function
    ```

    ```csharp
    wfApp.PersistableIdle = delegate(WorkflowApplicationIdleEventArgs e)
    {
        // Send the current WriteLine outputs to the status window.
        var writers = e.GetInstanceExtensions<StringWriter>();
        foreach (var writer in writers)
        {
            UpdateStatus(writer.ToString());
        }
        return PersistableIdleAction.Unload;
    };
    ```

    <span data-ttu-id="a7863-262">L'énumération <xref:System.Activities.PersistableIdleAction> a trois valeurs : <xref:System.Activities.PersistableIdleAction.None>, <xref:System.Activities.PersistableIdleAction.Persist> et <xref:System.Activities.PersistableIdleAction.Unload>.</span><span class="sxs-lookup"><span data-stu-id="a7863-262">The <xref:System.Activities.PersistableIdleAction> enumeration has three values: <xref:System.Activities.PersistableIdleAction.None>, <xref:System.Activities.PersistableIdleAction.Persist>, and <xref:System.Activities.PersistableIdleAction.Unload>.</span></span> <span data-ttu-id="a7863-263"><xref:System.Activities.PersistableIdleAction.Persist> entraîne la persistance du flux de travail, mais n’entraîne pas le déchargement du flux de travail.</span><span class="sxs-lookup"><span data-stu-id="a7863-263"><xref:System.Activities.PersistableIdleAction.Persist> causes the workflow to persist but it does not cause the workflow to unload.</span></span> <span data-ttu-id="a7863-264"><xref:System.Activities.PersistableIdleAction.Unload> entraîne la persistance et le déchargement du flux de travail.</span><span class="sxs-lookup"><span data-stu-id="a7863-264"><xref:System.Activities.PersistableIdleAction.Unload> causes the workflow to persist and be unloaded.</span></span>

    <span data-ttu-id="a7863-265">L'exemple suivant illustre la méthode `ConfigureWorkflowApplication` complète.</span><span class="sxs-lookup"><span data-stu-id="a7863-265">The following example is the completed `ConfigureWorkflowApplication` method.</span></span>

    ```vb
    Private Sub ConfigureWorkflowApplication(wfApp As WorkflowApplication)
        ' Configure the persistence store.
        wfApp.InstanceStore = store

        ' Add a StringWriter to the extensions. This captures the output
        ' from the WriteLine activities so we can display it in the form.
        Dim sw As New StringWriter()
        wfApp.Extensions.Add(sw)

        wfApp.Completed = _
            Sub(e As WorkflowApplicationCompletedEventArgs)
                If e.CompletionState = ActivityInstanceState.Faulted Then
                    UpdateStatus($"Workflow Terminated. Exception: {e.TerminationException.GetType().FullName}{vbCrLf}{e.TerminationException.Message}")
                ElseIf e.CompletionState = ActivityInstanceState.Canceled Then
                    UpdateStatus("Workflow Canceled.")
                Else
                    Dim turns As Integer = Convert.ToInt32(e.Outputs("Turns"))
                    UpdateStatus($"Congratulations, you guessed the number in {turns} turns.")
                End If
                GameOver()
            End Sub

        wfApp.Aborted = _
            Sub(e As WorkflowApplicationAbortedEventArgs)
                UpdateStatus($"Workflow Aborted. Exception: {e.Reason.GetType().FullName}{vbCrLf}{e.Reason.Message}")
            End Sub

        wfApp.OnUnhandledException = _
            Function(e As WorkflowApplicationUnhandledExceptionEventArgs)
                UpdateStatus($"Unhandled Exception: {e.UnhandledException.GetType().FullName}{vbCrLf}{e.UnhandledException.Message}")
                GameOver()
                Return UnhandledExceptionAction.Terminate
            End Function

        wfApp.PersistableIdle = _
            Function(e As WorkflowApplicationIdleEventArgs)
                ' Send the current WriteLine outputs to the status window.
                Dim writers = e.GetInstanceExtensions(Of StringWriter)()
                For Each writer In writers
                    UpdateStatus(writer.ToString())
                Next
                Return PersistableIdleAction.Unload
            End Function
    End Sub
    ```

    ```csharp
    private void ConfigureWorkflowApplication(WorkflowApplication wfApp)
    {
        // Configure the persistence store.
        wfApp.InstanceStore = store;

        // Add a StringWriter to the extensions. This captures the output
        // from the WriteLine activities so we can display it in the form.
        var sw = new StringWriter();
        wfApp.Extensions.Add(sw);

        wfApp.Completed = delegate(WorkflowApplicationCompletedEventArgs e)
        {
            if (e.CompletionState == ActivityInstanceState.Faulted)
            {
                UpdateStatus($"Workflow Terminated. Exception: {e.TerminationException.GetType().FullName}\r\n{e.TerminationException.Message}");
            }
            else if (e.CompletionState == ActivityInstanceState.Canceled)
            {
                UpdateStatus("Workflow Canceled.");
            }
            else
            {
                int turns = Convert.ToInt32(e.Outputs["Turns"]);
                UpdateStatus($"Congratulations, you guessed the number in {turns} turns.");
            }
            GameOver();
        };

        wfApp.Aborted = delegate(WorkflowApplicationAbortedEventArgs e)
        {
            UpdateStatus($"Workflow Aborted. Exception: {e.Reason.GetType().FullName}\r\n{e.Reason.Message}");
        };

        wfApp.OnUnhandledException = delegate(WorkflowApplicationUnhandledExceptionEventArgs e)
        {
            UpdateStatus($"Unhandled Exception: {e.UnhandledException.GetType().FullName}\r\n{e.UnhandledException.Message}");
            GameOver();
            return UnhandledExceptionAction.Terminate;
        };

        wfApp.PersistableIdle = delegate(WorkflowApplicationIdleEventArgs e)
        {
            // Send the current WriteLine outputs to the status window.
            var writers = e.GetInstanceExtensions<StringWriter>();
            foreach (var writer in writers)
            {
                UpdateStatus(writer.ToString());
            }
            return PersistableIdleAction.Unload;
        };
    }
    ```

## <a name="to-enable-starting-and-resuming-multiple-workflow-types"></a><span data-ttu-id="a7863-266">Pour activer le démarrage et la reprise de plusieurs types de workflow</span><span class="sxs-lookup"><span data-stu-id="a7863-266">To enable starting and resuming multiple workflow types</span></span>

<span data-ttu-id="a7863-267">Afin de reprendre une instance de workflow, l'hôte doit fournir la définition du workflow.</span><span class="sxs-lookup"><span data-stu-id="a7863-267">In order to resume a workflow instance, the host has to provide the workflow definition.</span></span> <span data-ttu-id="a7863-268">Dans ce didacticiel il existe trois types de workflow, et les étapes suivantes présentent plusieurs versions de ces types.</span><span class="sxs-lookup"><span data-stu-id="a7863-268">In this tutorial there are three workflow types, and subsequent tutorial steps introduce multiple versions of these types.</span></span> <span data-ttu-id="a7863-269">`WorkflowIdentity` permet à une application hôte d’associer des informations d’identification à une instance de flux de travail persistante.</span><span class="sxs-lookup"><span data-stu-id="a7863-269">`WorkflowIdentity` provides a way for a host application to associate identifying information with a persisted workflow instance.</span></span> <span data-ttu-id="a7863-270">Les étapes de cette section expliquent comment créer une classe utilitaire pour assister le mappage de l'identité de workflow d'une instance persistante de workflow à la définition correspondante de workflow.</span><span class="sxs-lookup"><span data-stu-id="a7863-270">The steps in this section demonstrate how to create a utility class to assist with mapping the workflow identity from a persisted workflow instance to the corresponding workflow definition.</span></span> <span data-ttu-id="a7863-271">Pour plus d’informations sur la `WorkflowIdentity` et le contrôle de version, consultez [utilisation de WorkflowIdentity et de versioning](using-workflowidentity-and-versioning.md).</span><span class="sxs-lookup"><span data-stu-id="a7863-271">For more information about `WorkflowIdentity` and versioning, see [Using WorkflowIdentity and Versioning](using-workflowidentity-and-versioning.md).</span></span>

1. <span data-ttu-id="a7863-272">Cliquez avec le bouton droit sur **NumberGuessWorkflowHost** dans **Explorateur de solutions** , puis choisissez **Ajouter**, **classe**.</span><span class="sxs-lookup"><span data-stu-id="a7863-272">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Add**, **Class**.</span></span> <span data-ttu-id="a7863-273">Tapez `WorkflowVersionMap` dans la zone **nom** , puis cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="a7863-273">Type `WorkflowVersionMap` into the **Name** box and click **Add**.</span></span>

2. <span data-ttu-id="a7863-274">Ajoutez les instructions `using` (ou `Imports`) suivantes au début du fichier avec les autres instructions `using` (ou `Imports`).</span><span class="sxs-lookup"><span data-stu-id="a7863-274">Add the following `using` or `Imports` statements at the top of the file with the other `using` or `Imports` statements.</span></span>

    ```vb
    Imports System.Activities
    Imports NumberGuessWorkflowActivities
    ```

    ```csharp
    using System.Activities;
    using NumberGuessWorkflowActivities;
    ```

3. <span data-ttu-id="a7863-275">Remplacez la déclaration de classe `WorkflowVersionMap` par la déclaration suivante.</span><span class="sxs-lookup"><span data-stu-id="a7863-275">Replace the `WorkflowVersionMap` class declaration with the following declaration.</span></span>

    ```vb
    Public Module WorkflowVersionMap
        Dim map As Dictionary(Of WorkflowIdentity, Activity)

        ' Current version identities.
        Public StateMachineNumberGuessIdentity As WorkflowIdentity
        Public FlowchartNumberGuessIdentity As WorkflowIdentity
        Public SequentialNumberGuessIdentity As WorkflowIdentity

        Sub New()
            map = New Dictionary(Of WorkflowIdentity, Activity)

            ' Add the current workflow version identities.
            StateMachineNumberGuessIdentity = New WorkflowIdentity With
            {
                .Name = "StateMachineNumberGuessWorkflow",
                .Version = New Version(1, 0, 0, 0)
            }

            FlowchartNumberGuessIdentity = New WorkflowIdentity With
            {
                .Name = "FlowchartNumberGuessWorkflow",
                .Version = New Version(1, 0, 0, 0)
            }

            SequentialNumberGuessIdentity = New WorkflowIdentity With
            {
                .Name = "SequentialNumberGuessWorkflow",
                .Version = New Version(1, 0, 0, 0)
            }

            map.Add(StateMachineNumberGuessIdentity, New StateMachineNumberGuessWorkflow())
            map.Add(FlowchartNumberGuessIdentity, New FlowchartNumberGuessWorkflow())
            map.Add(SequentialNumberGuessIdentity, New SequentialNumberGuessWorkflow())
        End Sub

        Public Function GetWorkflowDefinition(identity As WorkflowIdentity) As Activity
            Return map(identity)
        End Function

        Public Function GetIdentityDescription(identity As WorkflowIdentity) As String
            Return identity.ToString()
        End Function
    End Module
    ```

    ```csharp
    public static class WorkflowVersionMap
    {
        static Dictionary<WorkflowIdentity, Activity> map;

        // Current version identities.
        static public WorkflowIdentity StateMachineNumberGuessIdentity;
        static public WorkflowIdentity FlowchartNumberGuessIdentity;
        static public WorkflowIdentity SequentialNumberGuessIdentity;

        static WorkflowVersionMap()
        {
            map = new Dictionary<WorkflowIdentity, Activity>();

            // Add the current workflow version identities.
            StateMachineNumberGuessIdentity = new WorkflowIdentity
            {
                Name = "StateMachineNumberGuessWorkflow",
                Version = new Version(1, 0, 0, 0)
            };

            FlowchartNumberGuessIdentity = new WorkflowIdentity
            {
                Name = "FlowchartNumberGuessWorkflow",
                Version = new Version(1, 0, 0, 0)
            };

            SequentialNumberGuessIdentity = new WorkflowIdentity
            {
                Name = "SequentialNumberGuessWorkflow",
                Version = new Version(1, 0, 0, 0)
            };

            map.Add(StateMachineNumberGuessIdentity, new StateMachineNumberGuessWorkflow());
            map.Add(FlowchartNumberGuessIdentity, new FlowchartNumberGuessWorkflow());
            map.Add(SequentialNumberGuessIdentity, new SequentialNumberGuessWorkflow());
        }

        public static Activity GetWorkflowDefinition(WorkflowIdentity identity)
        {
            return map[identity];
        }

        public static string GetIdentityDescription(WorkflowIdentity identity)
        {
            return identity.ToString();
       }
    }
    ```

    <span data-ttu-id="a7863-276">`WorkflowVersionMap` contient trois identités de flux de travail qui correspondent aux trois définitions de flux de travail de ce didacticiel et est utilisée dans les sections suivantes lorsque les workflows sont démarrés et repris.</span><span class="sxs-lookup"><span data-stu-id="a7863-276">`WorkflowVersionMap` contains three workflow identities that map to the three workflow definitions from this tutorial and is used in the following sections when workflows are started and resumed.</span></span>

## <a name="to-start-a-new-workflow"></a><span data-ttu-id="a7863-277">Pour démarrer un nouveau workflow</span><span class="sxs-lookup"><span data-stu-id="a7863-277">To start a new workflow</span></span>

1. <span data-ttu-id="a7863-278">Ajoutez un gestionnaire `Click` pour `NewGame`.</span><span class="sxs-lookup"><span data-stu-id="a7863-278">Add a `Click` handler for `NewGame`.</span></span> <span data-ttu-id="a7863-279">Pour ajouter le gestionnaire, basculez en **mode Design** pour le formulaire, puis double-cliquez sur `NewGame`.</span><span class="sxs-lookup"><span data-stu-id="a7863-279">To add the handler, switch to **Design View** for the form, and double-click `NewGame`.</span></span> <span data-ttu-id="a7863-280">Un gestionnaire `NewGame_Click` est ajouté et l'affichage bascule en mode Code pour le formulaire.</span><span class="sxs-lookup"><span data-stu-id="a7863-280">A `NewGame_Click` handler is added and the view switches to code view for the form.</span></span> <span data-ttu-id="a7863-281">Chaque fois que l'utilisateur clique sur ce bouton un nouveau workflow est démarré.</span><span class="sxs-lookup"><span data-stu-id="a7863-281">Whenever the user clicks this button a new workflow is started.</span></span>

    ```vb
    Private Sub NewGame_Click(sender As Object, e As EventArgs) Handles NewGame.Click

    End Sub
    ```

    ```csharp
    private void NewGame_Click(object sender, EventArgs e)
    {

    }
    ```

2. <span data-ttu-id="a7863-282">Ajoutez le code suivant au gestionnaire de clics.</span><span class="sxs-lookup"><span data-stu-id="a7863-282">Add the following code to the click handler.</span></span> <span data-ttu-id="a7863-283">Ce code crée un dictionnaire d'arguments d'entrée du workflow, indexés par nom d'argument.</span><span class="sxs-lookup"><span data-stu-id="a7863-283">This code creates a dictionary of input arguments for the workflow, keyed by argument name.</span></span> <span data-ttu-id="a7863-284">Ce dictionnaire a une entrée qui contient la plage du nombre généré de manière aléatoire extrait de la zone de liste modifiable de plage.</span><span class="sxs-lookup"><span data-stu-id="a7863-284">This dictionary has one entry that contains the range of the randomly generated number retrieved from the range combo box.</span></span>

    ```vb
    Dim inputs As New Dictionary(Of String, Object)()
    inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem))
    ```

    ```csharp
    var inputs = new Dictionary<string, object>();
    inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem));
    ```

3. <span data-ttu-id="a7863-285">Ensuite, ajoutez le code suivant qui démarre le workflow.</span><span class="sxs-lookup"><span data-stu-id="a7863-285">Next, add the following code that starts the workflow.</span></span> <span data-ttu-id="a7863-286">`WorkflowIdentity` et la définition de workflow correspondant au type de workflow sélectionné sont récupérés à l'aide de la classe d'assistance `WorkflowVersionMap`.</span><span class="sxs-lookup"><span data-stu-id="a7863-286">The `WorkflowIdentity` and workflow definition corresponding to the type of workflow selected are retrieved using the `WorkflowVersionMap` helper class.</span></span> <span data-ttu-id="a7863-287">Ensuite, une nouvelle instance `WorkflowApplication` est créée à l’aide de la définition de workflow, `WorkflowIdentity`, et du dictionnaire d’arguments d’entrée.</span><span class="sxs-lookup"><span data-stu-id="a7863-287">Next, a new `WorkflowApplication` instance is created using the workflow definition, `WorkflowIdentity`, and dictionary of input arguments.</span></span>

    ```vb
    Dim identity As WorkflowIdentity = Nothing
    Select Case WorkflowType.SelectedItem.ToString()
        Case "SequentialNumberGuessWorkflow"
            identity = WorkflowVersionMap.SequentialNumberGuessIdentity

        Case "StateMachineNumberGuessWorkflow"
            identity = WorkflowVersionMap.StateMachineNumberGuessIdentity

        Case "FlowchartNumberGuessWorkflow"
            identity = WorkflowVersionMap.FlowchartNumberGuessIdentity
    End Select

    Dim wf As Activity = WorkflowVersionMap.GetWorkflowDefinition(identity)

    Dim wfApp = New WorkflowApplication(wf, inputs, identity)
    ```

    ```csharp
    WorkflowIdentity identity = null;
    switch (WorkflowType.SelectedItem.ToString())
    {
        case "SequentialNumberGuessWorkflow":
            identity = WorkflowVersionMap.SequentialNumberGuessIdentity;
            break;

        case "StateMachineNumberGuessWorkflow":
            identity = WorkflowVersionMap.StateMachineNumberGuessIdentity;
            break;

        case "FlowchartNumberGuessWorkflow":
            identity = WorkflowVersionMap.FlowchartNumberGuessIdentity;
            break;
    };

    Activity wf = WorkflowVersionMap.GetWorkflowDefinition(identity);

    WorkflowApplication wfApp = new WorkflowApplication(wf, inputs, identity);
    ```

4. <span data-ttu-id="a7863-288">Ensuite, ajoutez le code suivant qui ajoute le workflow à la liste de workflow et affiche les informations de version du workflow sur le formulaire.</span><span class="sxs-lookup"><span data-stu-id="a7863-288">Next, add the following code which adds the workflow to the workflow list and displays the workflow's version information on the form.</span></span>

    ```vb
    ' Add the workflow to the list and display the version information.
    workflowStarting = True
    InstanceId.SelectedIndex = InstanceId.Items.Add(wfApp.Id)
    WorkflowVersion.Text = identity.ToString()
    workflowStarting = False
    ```

    ```csharp
    // Add the workflow to the list and display the version information.
    workflowStarting = true;
    InstanceId.SelectedIndex = InstanceId.Items.Add(wfApp.Id);
    WorkflowVersion.Text = identity.ToString();
    workflowStarting = false;
    ```

5. <span data-ttu-id="a7863-289">Appelez `ConfigureWorkflowApplication` pour configurer le magasin d'instances, les extensions et les gestionnaires du cycle de vie de workflow pour cette instance `WorkflowApplication`.</span><span class="sxs-lookup"><span data-stu-id="a7863-289">Call `ConfigureWorkflowApplication` to configure the instance store, extensions, and workflow lifecycle handlers for this `WorkflowApplication` instance.</span></span>

    ```vb
    ' Configure the instance store, extensions, and
    ' workflow lifecycle handlers.
    ConfigureWorkflowApplication(wfApp)
    ```

    ```csharp
    // Configure the instance store, extensions, and
    // workflow lifecycle handlers.
    ConfigureWorkflowApplication(wfApp);
    ```

6. <span data-ttu-id="a7863-290">Pour finir, appelez `Run`.</span><span class="sxs-lookup"><span data-stu-id="a7863-290">Finally, call `Run`.</span></span>

    ```vb
    ' Start the workflow.
    wfApp.Run()
    ```

    ```csharp
    // Start the workflow.
    wfApp.Run();
    ```

     <span data-ttu-id="a7863-291">Cet exemple est le gestionnaire `NewGame_Click` terminé.</span><span class="sxs-lookup"><span data-stu-id="a7863-291">The following example is the completed `NewGame_Click` handler.</span></span>

    ```vb
    Private Sub NewGame_Click(sender As Object, e As EventArgs) Handles NewGame.Click
        ' Start a new workflow.
        Dim inputs As New Dictionary(Of String, Object)()
        inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem))

        Dim identity As WorkflowIdentity = Nothing
        Select Case WorkflowType.SelectedItem.ToString()
            Case "SequentialNumberGuessWorkflow"
                identity = WorkflowVersionMap.SequentialNumberGuessIdentity

            Case "StateMachineNumberGuessWorkflow"
                identity = WorkflowVersionMap.StateMachineNumberGuessIdentity

            Case "FlowchartNumberGuessWorkflow"
                identity = WorkflowVersionMap.FlowchartNumberGuessIdentity
        End Select

        Dim wf As Activity = WorkflowVersionMap.GetWorkflowDefinition(identity)

        Dim wfApp = New WorkflowApplication(wf, inputs, identity)

        ' Add the workflow to the list and display the version information.
        workflowStarting = True
        InstanceId.SelectedIndex = InstanceId.Items.Add(wfApp.Id)
        WorkflowVersion.Text = identity.ToString()
        workflowStarting = False

        ' Configure the instance store, extensions, and
        ' workflow lifecycle handlers.
        ConfigureWorkflowApplication(wfApp)

        ' Start the workflow.
        wfApp.Run()
    End Sub
    ```

    ```csharp
    private void NewGame_Click(object sender, EventArgs e)
    {
        var inputs = new Dictionary<string, object>();
        inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem));

        WorkflowIdentity identity = null;
        switch (WorkflowType.SelectedItem.ToString())
        {
            case "SequentialNumberGuessWorkflow":
                identity = WorkflowVersionMap.SequentialNumberGuessIdentity;
                break;

            case "StateMachineNumberGuessWorkflow":
                identity = WorkflowVersionMap.StateMachineNumberGuessIdentity;
                break;

            case "FlowchartNumberGuessWorkflow":
                identity = WorkflowVersionMap.FlowchartNumberGuessIdentity;
                break;
        };

        Activity wf = WorkflowVersionMap.GetWorkflowDefinition(identity);

        var wfApp = new WorkflowApplication(wf, inputs, identity);

        // Add the workflow to the list and display the version information.
        workflowStarting = true;
        InstanceId.SelectedIndex = InstanceId.Items.Add(wfApp.Id);
        WorkflowVersion.Text = identity.ToString();
        workflowStarting = false;

        // Configure the instance store, extensions, and
        // workflow lifecycle handlers.
        ConfigureWorkflowApplication(wfApp);

        // Start the workflow.
        wfApp.Run();
    }
    ```

## <a name="to-resume-a-workflow"></a><span data-ttu-id="a7863-292">Pour reprendre un workflow</span><span class="sxs-lookup"><span data-stu-id="a7863-292">To resume a workflow</span></span>

1. <span data-ttu-id="a7863-293">Ajoutez un gestionnaire `Click` pour `EnterGuess`.</span><span class="sxs-lookup"><span data-stu-id="a7863-293">Add a `Click` handler for `EnterGuess`.</span></span> <span data-ttu-id="a7863-294">Pour ajouter le gestionnaire, basculez en **mode Design** pour le formulaire, puis double-cliquez sur `EnterGuess`.</span><span class="sxs-lookup"><span data-stu-id="a7863-294">To add the handler, switch to **Design View** for the form, and double-click `EnterGuess`.</span></span> <span data-ttu-id="a7863-295">Chaque fois que l'utilisateur clique sur ce bouton un nouveau workflow reprend.</span><span class="sxs-lookup"><span data-stu-id="a7863-295">Whenever the user clicks this button a workflow is resumed.</span></span>

    ```vb
    Private Sub EnterGuess_Click(sender As Object, e As EventArgs) Handles EnterGuess.Click

    End Sub
    ```

    ```csharp
    private void EnterGuess_Click(object sender, EventArgs e)
    {

    }
    ```

2. <span data-ttu-id="a7863-296">Ajoutez le code suivant pour vous assurer qu'un workflow est sélectionné dans la liste de workflow, et que l'estimation de l'utilisateur est valide.</span><span class="sxs-lookup"><span data-stu-id="a7863-296">Add the following code to ensure that a workflow is selected in the workflow list, and that the user's guess is valid.</span></span>

    ```vb
    If WorkflowInstanceId = Guid.Empty Then
        MessageBox.Show("Please select a workflow.")
        Return
    End If

    Dim userGuess As Integer
    If Not Int32.TryParse(Guess.Text, userGuess) Then
        MessageBox.Show("Please enter an integer.")
        Guess.SelectAll()
        Guess.Focus()
        Return
    End If
    ```

    ```csharp
    if (WorkflowInstanceId == Guid.Empty)
    {
        MessageBox.Show("Please select a workflow.");
        return;
    }

    int guess;
    if (!Int32.TryParse(Guess.Text, out guess))
    {
        MessageBox.Show("Please enter an integer.");
        Guess.SelectAll();
        Guess.Focus();
        return;
    }
    ```

3. <span data-ttu-id="a7863-297">Ensuite, récupérez `WorkflowApplicationInstance` de l'instance persistante de workflow.</span><span class="sxs-lookup"><span data-stu-id="a7863-297">Next, retrieve the `WorkflowApplicationInstance` of the persisted workflow instance.</span></span> <span data-ttu-id="a7863-298">`WorkflowApplicationInstance` représente une instance persistante de workflow qui n'a pas encore été associée à une définition de workflow.</span><span class="sxs-lookup"><span data-stu-id="a7863-298">A `WorkflowApplicationInstance` represents a persisted workflow instance that has not yet been associated with a workflow definition.</span></span> <span data-ttu-id="a7863-299">`DefinitionIdentity` de `WorkflowApplicationInstance` contient `WorkflowIdentity` de l'instance persistante de workflow.</span><span class="sxs-lookup"><span data-stu-id="a7863-299">The `DefinitionIdentity` of the `WorkflowApplicationInstance` contains the `WorkflowIdentity` of the persisted workflow instance.</span></span> <span data-ttu-id="a7863-300">Dans ce didacticiel, la classe utilitaire `WorkflowVersionMap` est utilisée pour mapper `WorkflowIdentity` à la définition appropriée de workflow.</span><span class="sxs-lookup"><span data-stu-id="a7863-300">In this tutorial, the `WorkflowVersionMap` utility class is used to map the `WorkflowIdentity` to the correct workflow definition.</span></span> <span data-ttu-id="a7863-301">Une fois que la définition de workflow est récupérée, `WorkflowApplication` est créé, à l'aide de la définition appropriée de workflow.</span><span class="sxs-lookup"><span data-stu-id="a7863-301">Once the workflow definition is retrieved, a `WorkflowApplication` is created, using the correct workflow definition.</span></span>

    ```vb
    Dim instance As WorkflowApplicationInstance = _
        WorkflowApplication.GetInstance(WorkflowInstanceId, store)

    ' Use the persisted WorkflowIdentity to retrieve the correct workflow
    ' definition from the dictionary.
    Dim wf As Activity = _
        WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity)

    ' Associate the WorkflowApplication with the correct definition
    Dim wfApp As New WorkflowApplication(wf, instance.DefinitionIdentity)
    ```

    ```csharp
    WorkflowApplicationInstance instance =
        WorkflowApplication.GetInstance(WorkflowInstanceId, store);

    // Use the persisted WorkflowIdentity to retrieve the correct workflow
    // definition from the dictionary.
    Activity wf =
        WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity);

    // Associate the WorkflowApplication with the correct definition
    var wfApp = new WorkflowApplication(wf, instance.DefinitionIdentity);
    ```

4. <span data-ttu-id="a7863-302">Une fois que `WorkflowApplication` est créé, configurez le magasin d’instances, les gestionnaires du cycle de vie de workflow et les extensions en appelant `ConfigureWorkflowApplication`.</span><span class="sxs-lookup"><span data-stu-id="a7863-302">Once the `WorkflowApplication` is created, configure the instance store, workflow lifecycle handlers, and extensions by calling `ConfigureWorkflowApplication`.</span></span> <span data-ttu-id="a7863-303">Ces étapes doivent être effectuées chaque fois qu'un nouveau`WorkflowApplication` est créé, et elles doivent être effectuées avant que l'instance de workflow ne soit chargée dans `WorkflowApplication`.</span><span class="sxs-lookup"><span data-stu-id="a7863-303">These steps must be done every time a new `WorkflowApplication` is created, and they must be done before the workflow instance is loaded into the `WorkflowApplication`.</span></span> <span data-ttu-id="a7863-304">Une fois que le workflow est chargé, il reprend à l'estimation de l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a7863-304">After the workflow is loaded, it is resumed with the user's guess.</span></span>

    ```vb
    ' Configure the extensions and lifecycle handlers.
    ' Do this before the instance is loaded. Once the instance is
    ' loaded it is too late to add extensions.
    ConfigureWorkflowApplication(wfApp)

    ' Load the workflow.
    wfApp.Load(instance)

    ' Resume the workflow.
    wfApp.ResumeBookmark("EnterGuess", userGuess)
    ```

    ```csharp
    // Configure the extensions and lifecycle handlers.
    // Do this before the instance is loaded. Once the instance is
    // loaded it is too late to add extensions.
    ConfigureWorkflowApplication(wfApp);

    // Load the workflow.
    wfApp.Load(instance);

    // Resume the workflow.
    wfApp.ResumeBookmark("EnterGuess", guess);
    ```

5. <span data-ttu-id="a7863-305">Enfin, effacez la zone de texte d'estimation et préparez le formulaire pour recevoir une autre estimation.</span><span class="sxs-lookup"><span data-stu-id="a7863-305">Finally, clear the guess textbox and prepare the form to accept another guess.</span></span>

    ```vb
    ' Clear the Guess textbox.
    Guess.Clear()
    Guess.Focus()
    ```

    ```csharp
    // Clear the Guess textbox.
    Guess.Clear();
    Guess.Focus();
    ```

    <span data-ttu-id="a7863-306">Cet exemple est le gestionnaire `EnterGuess_Click` terminé.</span><span class="sxs-lookup"><span data-stu-id="a7863-306">The following example is the completed `EnterGuess_Click` handler.</span></span>

    ```vb
    Private Sub EnterGuess_Click(sender As Object, e As EventArgs) Handles EnterGuess.Click
        If WorkflowInstanceId = Guid.Empty Then
            MessageBox.Show("Please select a workflow.")
            Return
        End If

        Dim userGuess As Integer
        If Not Int32.TryParse(Guess.Text, userGuess) Then
            MessageBox.Show("Please enter an integer.")
            Guess.SelectAll()
            Guess.Focus()
            Return
        End If

        Dim instance As WorkflowApplicationInstance = _
            WorkflowApplication.GetInstance(WorkflowInstanceId, store)

        ' Use the persisted WorkflowIdentity to retrieve the correct workflow
        ' definition from the dictionary.
        Dim wf As Activity = _
            WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity)

        ' Associate the WorkflowApplication with the correct definition
        Dim wfApp As New WorkflowApplication(wf, instance.DefinitionIdentity)

        ' Configure the extensions and lifecycle handlers.
        ' Do this before the instance is loaded. Once the instance is
        ' loaded it is too late to add extensions.
        ConfigureWorkflowApplication(wfApp)

        ' Load the workflow.
        wfApp.Load(instance)

        ' Resume the workflow.
        wfApp.ResumeBookmark("EnterGuess", userGuess)

        ' Clear the Guess textbox.
        Guess.Clear()
        Guess.Focus()
    End Sub
    ```

    ```csharp
    private void EnterGuess_Click(object sender, EventArgs e)
    {
        if (WorkflowInstanceId == Guid.Empty)
        {
            MessageBox.Show("Please select a workflow.");
            return;
        }

        int guess;
        if (!Int32.TryParse(Guess.Text, out guess))
        {
            MessageBox.Show("Please enter an integer.");
            Guess.SelectAll();
            Guess.Focus();
            return;
        }

        WorkflowApplicationInstance instance =
            WorkflowApplication.GetInstance(WorkflowInstanceId, store);

        // Use the persisted WorkflowIdentity to retrieve the correct workflow
        // definition from the dictionary.
        Activity wf =
            WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity);

        // Associate the WorkflowApplication with the correct definition
        var wfApp = new WorkflowApplication(wf, instance.DefinitionIdentity);

        // Configure the extensions and lifecycle handlers.
        // Do this before the instance is loaded. Once the instance is
        // loaded it is too late to add extensions.
        ConfigureWorkflowApplication(wfApp);

        // Load the workflow.
        wfApp.Load(instance);

        // Resume the workflow.
        wfApp.ResumeBookmark("EnterGuess", guess);

        // Clear the Guess textbox.
        Guess.Clear();
        Guess.Focus();
    }
    ```

## <a name="to-terminate-a-workflow"></a><span data-ttu-id="a7863-307">Pour terminer un workflow</span><span class="sxs-lookup"><span data-stu-id="a7863-307">To terminate a workflow</span></span>

1. <span data-ttu-id="a7863-308">Ajoutez un gestionnaire `Click` pour `QuitGame`.</span><span class="sxs-lookup"><span data-stu-id="a7863-308">Add a `Click` handler for `QuitGame`.</span></span> <span data-ttu-id="a7863-309">Pour ajouter le gestionnaire, basculez en **mode Design** pour le formulaire, puis double-cliquez sur `QuitGame`.</span><span class="sxs-lookup"><span data-stu-id="a7863-309">To add the handler, switch to **Design View** for the form, and double-click `QuitGame`.</span></span> <span data-ttu-id="a7863-310">Chaque fois que l'utilisateur clique sur ce bouton le workflow actuellement sélectionné est terminé.</span><span class="sxs-lookup"><span data-stu-id="a7863-310">Whenever the user clicks this button the currently selected workflow is terminated.</span></span>

    ```vb
    Private Sub QuitGame_Click(sender As Object, e As EventArgs) Handles QuitGame.Click

    End Sub
    ```

    ```csharp
    private void QuitGame_Click(object sender, EventArgs e)
    {

    }
    ```

2. <span data-ttu-id="a7863-311">Ajoutez le code suivant au gestionnaire `QuitGame_Click`.</span><span class="sxs-lookup"><span data-stu-id="a7863-311">Add the following code to the `QuitGame_Click` handler.</span></span> <span data-ttu-id="a7863-312">Ce code vérifie d'abord qu'un workflow est sélectionné dans la liste de workflow.</span><span class="sxs-lookup"><span data-stu-id="a7863-312">This code first checks to ensure that a workflow is selected in the workflow list.</span></span> <span data-ttu-id="a7863-313">Ensuite, il charge l'instance persistante dans `WorkflowApplicationInstance`, utilise `DefinitionIdentity` pour déterminer la définition appropriée de workflow, puis initialise `WorkflowApplication`.</span><span class="sxs-lookup"><span data-stu-id="a7863-313">Then it loads the persisted instance into a `WorkflowApplicationInstance`, uses the `DefinitionIdentity` to determine the correct workflow definition, and then initializes the `WorkflowApplication`.</span></span> <span data-ttu-id="a7863-314">Ensuite, les extensions et les gestionnaires de cycle de vie de workflow sont configurés avec un appel à `ConfigureWorkflowApplication`.</span><span class="sxs-lookup"><span data-stu-id="a7863-314">Next the extensions and workflow lifecycle handlers are configured with a call to `ConfigureWorkflowApplication`.</span></span> <span data-ttu-id="a7863-315">Une fois que `WorkflowApplication` est configuré, il est chargé, puis `Terminate` est appelé.</span><span class="sxs-lookup"><span data-stu-id="a7863-315">Once the `WorkflowApplication` is configured, it is loaded, and then `Terminate` is called.</span></span>

    ```vb
    If WorkflowInstanceId = Guid.Empty Then
        MessageBox.Show("Please select a workflow.")
        Return
    End If

    Dim instance As WorkflowApplicationInstance = _
        WorkflowApplication.GetInstance(WorkflowInstanceId, store)

    ' Use the persisted WorkflowIdentity to retrieve the correct workflow
    ' definition from the dictionary.
    Dim wf As Activity = WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity)

    ' Associate the WorkflowApplication with the correct definition.
    Dim wfApp As New WorkflowApplication(wf, instance.DefinitionIdentity)

    ' Configure the extensions and lifecycle handlers.
    ConfigureWorkflowApplication(wfApp)

    ' Load the workflow.
    wfApp.Load(instance)

    ' Terminate the workflow.
    wfApp.Terminate("User resigns.")
    ```

    ```csharp
    if (WorkflowInstanceId == Guid.Empty)
    {
        MessageBox.Show("Please select a workflow.");
        return;
    }

    WorkflowApplicationInstance instance =
        WorkflowApplication.GetInstance(WorkflowInstanceId, store);

    // Use the persisted WorkflowIdentity to retrieve the correct workflow
    // definition from the dictionary.
    Activity wf = WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity);

    // Associate the WorkflowApplication with the correct definition
    var wfApp = new WorkflowApplication(wf, instance.DefinitionIdentity);

    // Configure the extensions and lifecycle handlers
    ConfigureWorkflowApplication(wfApp);

    // Load the workflow.
    wfApp.Load(instance);

    // Terminate the workflow.
    wfApp.Terminate("User resigns.");
    ```

## <a name="to-build-and-run-the-application"></a><span data-ttu-id="a7863-316">Pour générer et exécuter l'application</span><span class="sxs-lookup"><span data-stu-id="a7863-316">To build and run the application</span></span>

1. <span data-ttu-id="a7863-317">Double-cliquez sur **Program.cs** (ou **Module1. vb**) dans **Explorateur de solutions** pour afficher le code.</span><span class="sxs-lookup"><span data-stu-id="a7863-317">Double-click **Program.cs** (or **Module1.vb**) in **Solution Explorer** to display the code.</span></span>

2. <span data-ttu-id="a7863-318">Ajoutez l'instruction `using` (ou `Imports`) suivante au début du fichier avec les autres instructions `using` (ou `Imports`).</span><span class="sxs-lookup"><span data-stu-id="a7863-318">Add the following `using` (or `Imports`) statement at the top of the file with the other `using` (or `Imports`) statements.</span></span>

    ```vb
    Imports System.Windows.Forms
    ```

    ```csharp
    using System.Windows.Forms;
    ```

3. <span data-ttu-id="a7863-319">Supprimez ou commentez le code d’hébergement du flux de travail existant à partir de la [procédure : exécuter un workflow](how-to-run-a-workflow.md)et remplacez-le par le code suivant.</span><span class="sxs-lookup"><span data-stu-id="a7863-319">Remove or comment out the existing workflow hosting code from [How to: Run a Workflow](how-to-run-a-workflow.md), and replace it with the following code.</span></span>

    ```vb
    Sub Main()
        Application.EnableVisualStyles()
        Application.Run(New WorkflowHostForm())
    End Sub
    ```

    ```csharp
    static void Main(string[] args)
    {
        Application.EnableVisualStyles();
        Application.Run(new WorkflowHostForm());
    }
    ```

4. <span data-ttu-id="a7863-320">Cliquez avec le bouton droit sur **NumberGuessWorkflowHost** dans **Explorateur de solutions** , puis choisissez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="a7863-320">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Properties**.</span></span> <span data-ttu-id="a7863-321">Dans l’onglet **application** , spécifiez **application Windows** pour le **type de sortie**.</span><span class="sxs-lookup"><span data-stu-id="a7863-321">In the **Application** tab, specify **Windows Application** for the **Output type**.</span></span> <span data-ttu-id="a7863-322">Cette étape est facultative, mais si elle n'est pas suivie, la fenêtre de console s'affiche en plus du formulaire.</span><span class="sxs-lookup"><span data-stu-id="a7863-322">This step is optional, but if it is not followed the console window is displayed in addition to the form.</span></span>

5. <span data-ttu-id="a7863-323">Appuyez sur Ctrl+Maj+B pour générer l'application.</span><span class="sxs-lookup"><span data-stu-id="a7863-323">Press Ctrl+Shift+B to build the application.</span></span>

6. <span data-ttu-id="a7863-324">Vérifiez que **NumberGuessWorkflowHost** est défini comme application de démarrage, puis appuyez sur CTRL + F5 pour démarrer l’application.</span><span class="sxs-lookup"><span data-stu-id="a7863-324">Ensure that **NumberGuessWorkflowHost** is set as the startup application, and press Ctrl+F5 to start the application.</span></span>

7. <span data-ttu-id="a7863-325">Sélectionnez une plage pour le jeu d’estimation et le type de flux de travail à démarrer, puis cliquez sur **nouveau jeu**.</span><span class="sxs-lookup"><span data-stu-id="a7863-325">Select a range for the guessing game and the type of workflow to start, and click **New Game**.</span></span> <span data-ttu-id="a7863-326">Entrez une estimation dans la zone **deviner** , puis cliquez sur **OK** pour envoyer votre estimation.</span><span class="sxs-lookup"><span data-stu-id="a7863-326">Enter a guess in the **Guess** box and click **Go** to submit your guess.</span></span> <span data-ttu-id="a7863-327">Notez que la sortie des activités `WriteLine` s'affiche sur le formulaire.</span><span class="sxs-lookup"><span data-stu-id="a7863-327">Note that the output from the `WriteLine` activities is displayed on the form.</span></span>

8. <span data-ttu-id="a7863-328">Démarrez plusieurs flux de travail à l’aide de différents types de flux de travail et de plages de nombres, entrez des estimations et basculez entre les workflows en sélectionnant dans la liste **ID d’instance de workflow** .</span><span class="sxs-lookup"><span data-stu-id="a7863-328">Start several workflows using different workflow types and number ranges, enter some guesses, and switch between the workflows by selecting from the **Workflow Instance Id** list.</span></span>

    <span data-ttu-id="a7863-329">Notez que lorsque vous basculez vers un nouveau workflow, les propositions précédentes et la progression du workflow ne s'affichent pas dans la fenêtre d'état.</span><span class="sxs-lookup"><span data-stu-id="a7863-329">Note that when you switch to a new workflow, the previous guesses and progress of the workflow are not displayed in the status window.</span></span> <span data-ttu-id="a7863-330">En effet, l'état n'est pas disponible, car il n'est pas capturé ni enregistré.</span><span class="sxs-lookup"><span data-stu-id="a7863-330">The reason the status is not available is because it is not captured and saved anywhere.</span></span> <span data-ttu-id="a7863-331">Dans l’étape suivante du didacticiel, [Comment : créer un participant de suivi personnalisé](how-to-create-a-custom-tracking-participant.md), vous créez un participant de suivi personnalisé qui enregistre ces informations.</span><span class="sxs-lookup"><span data-stu-id="a7863-331">In the next step of the tutorial, [How to: Create a Custom Tracking Participant](how-to-create-a-custom-tracking-participant.md), you create a custom tracking participant that saves this information.</span></span>

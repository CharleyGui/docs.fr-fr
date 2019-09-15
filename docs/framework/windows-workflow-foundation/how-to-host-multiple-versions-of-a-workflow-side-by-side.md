---
title: 'Procédure : héberger plusieurs versions d’un workflow côte à côte'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 09c575df-e0a3-4f3b-9e01-a7ac59d65287
ms.openlocfilehash: 820ed324c8095e2f9f2823513a37965099f42c48
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989648"
---
# <a name="how-to-host-multiple-versions-of-a-workflow-side-by-side"></a><span data-ttu-id="aba5f-102">Procédure : héberger plusieurs versions d’un workflow côte à côte</span><span class="sxs-lookup"><span data-stu-id="aba5f-102">How to: Host Multiple Versions of a Workflow Side-by-Side</span></span>

<span data-ttu-id="aba5f-103">`WorkflowIdentity` permet aux développeurs d'applications de workflow d'associer un nom et une version à une définition de workflow, et d'associer ces informations à une instance persistante de workflow.</span><span class="sxs-lookup"><span data-stu-id="aba5f-103">`WorkflowIdentity` provides a way for workflow application developers to associate a name and a version with a workflow definition, and for this information to be associated with a persisted workflow instance.</span></span> <span data-ttu-id="aba5f-104">Ces informations d'identité peuvent être utilisées par les développeurs d'applications de workflow pour activer des scénarios tels que l'exécution côte à côte de plusieurs versions d'une définition de workflow, et fournir la base d'autres fonctionnalités telles que la mise à jour dynamique.</span><span class="sxs-lookup"><span data-stu-id="aba5f-104">This identity information can be used by workflow application developers to enable scenarios such as side-by-side execution of multiple versions of a workflow definition, and provides the cornerstone for other functionality such as dynamic update.</span></span> <span data-ttu-id="aba5f-105">Cette étape du didacticiel explique comment utiliser `WorkflowIdentity` pour héberger plusieurs versions de workflow en même temps.</span><span class="sxs-lookup"><span data-stu-id="aba5f-105">This step in the tutorial demonstrates how to use `WorkflowIdentity` to host multiple versions of a workflow at the same time.</span></span>

> [!NOTE]
> <span data-ttu-id="aba5f-106">Pour télécharger une version complète ou afficher une vidéo pas à pas du didacticiel, consultez [Windows Workflow Foundation (WF45)-prise en main didacticiel](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="aba5f-106">To download a completed version or view a video walkthrough of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>

## <a name="in-this-topic"></a><span data-ttu-id="aba5f-107">Dans cette rubrique</span><span class="sxs-lookup"><span data-stu-id="aba5f-107">In this topic</span></span>

<span data-ttu-id="aba5f-108">Dans cette étape du didacticiel, les activités `WriteLine` dans le workflow sont modifiées pour fournir des informations supplémentaires, et une nouvelle activité `WriteLine` est ajoutée.</span><span class="sxs-lookup"><span data-stu-id="aba5f-108">In this step of the tutorial, the `WriteLine` activities in the workflow are modified to provide additional information, and a new `WriteLine` activity is added.</span></span> <span data-ttu-id="aba5f-109">Une copie de l'assembly de workflow d'origine est enregistrée, et l'application hôte est mise à jour afin qu'elle puisse exécuter simultanément les workflows d'origine et mis à jour.</span><span class="sxs-lookup"><span data-stu-id="aba5f-109">A copy of the original workflow assembly is stored, and the host application is updated so that it can run both the original and the updated workflows at the same time.</span></span>

- [<span data-ttu-id="aba5f-110">Pour effectuer une copie du projet NumberGuessWorkflowActivities</span><span class="sxs-lookup"><span data-stu-id="aba5f-110">To make a copy of the NumberGuessWorkflowActivities project</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_BackupCopy)

- [<span data-ttu-id="aba5f-111">Pour mettre à jour les workflows</span><span class="sxs-lookup"><span data-stu-id="aba5f-111">To update the workflows</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateWorkflows)

  - [<span data-ttu-id="aba5f-112">Pour mettre à jour le flux de travail StateMachine</span><span class="sxs-lookup"><span data-stu-id="aba5f-112">To update the StateMachine workflow</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateStateMachine)

  - [<span data-ttu-id="aba5f-113">Pour mettre à jour le flux de travail de l’organigramme</span><span class="sxs-lookup"><span data-stu-id="aba5f-113">To update the Flowchart workflow</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateFlowchart)

  - [<span data-ttu-id="aba5f-114">Pour mettre à jour le flux de travail séquentiel</span><span class="sxs-lookup"><span data-stu-id="aba5f-114">To update the Sequential workflow</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateSequential)

- [<span data-ttu-id="aba5f-115">Pour mettre à jour WorkflowVersionMap afin d’inclure les versions de flux de travail précédentes</span><span class="sxs-lookup"><span data-stu-id="aba5f-115">To update WorkflowVersionMap to include the previous workflow versions</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateWorkflowVersionMap)

- [<span data-ttu-id="aba5f-116">Pour générer et exécuter l’application</span><span class="sxs-lookup"><span data-stu-id="aba5f-116">To build and run the application</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_BuildAndRun)

> [!NOTE]
> <span data-ttu-id="aba5f-117">Avant de suivre les étapes de cette rubrique, exécutez l'application, démarrez plusieurs workflows de chaque type et effectuez une ou deux propositions pour chacun.</span><span class="sxs-lookup"><span data-stu-id="aba5f-117">Before following the steps in this topic, run the application, start several workflows of each type, and making one or two guesses for each one.</span></span> <span data-ttu-id="aba5f-118">Ces flux de travail persistants sont utilisés au cours de cette étape et de [l’étape suivante : Met à jour la définition d’une instance](how-to-update-the-definition-of-a-running-workflow-instance.md)de workflow en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="aba5f-118">These persisted workflows are used in this step and the following step, [How to: Update the Definition of a Running Workflow Instance](how-to-update-the-definition-of-a-running-workflow-instance.md).</span></span>

> [!NOTE]
> <span data-ttu-id="aba5f-119">Chaque étape du didacticiel de mise en route dépend des étapes précédentes.</span><span class="sxs-lookup"><span data-stu-id="aba5f-119">Each step in the Getting Started tutorial depends on the previous steps.</span></span> <span data-ttu-id="aba5f-120">Si vous n’avez pas effectué les étapes précédentes, vous pouvez télécharger une version complète du didacticiel à partir de [Windows Workflow Foundation (WF45)-prise en main didacticiel](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="aba5f-120">If you did not complete the previous steps you can download a completed version of the tutorial from [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>

### <a name="BKMK_BackupCopy"></a><span data-ttu-id="aba5f-121">Pour effectuer une copie du projet NumberGuessWorkflowActivities</span><span class="sxs-lookup"><span data-stu-id="aba5f-121">To make a copy of the NumberGuessWorkflowActivities project</span></span>

1. <span data-ttu-id="aba5f-122">Ouvrez la solution **WF45GettingStartedTutorial** dans Visual Studio 2012 si elle n’est pas ouverte.</span><span class="sxs-lookup"><span data-stu-id="aba5f-122">Open the **WF45GettingStartedTutorial** solution in Visual Studio 2012 if it is not open.</span></span>

2. <span data-ttu-id="aba5f-123">Appuyez sur Ctrl+Maj+B pour générer la solution.</span><span class="sxs-lookup"><span data-stu-id="aba5f-123">Press CTRL+SHIFT+B to build the solution.</span></span>

3. <span data-ttu-id="aba5f-124">Fermez la solution **WF45GettingStartedTutorial** .</span><span class="sxs-lookup"><span data-stu-id="aba5f-124">Close the **WF45GettingStartedTutorial** solution.</span></span>

4. <span data-ttu-id="aba5f-125">Ouvrez l’Explorateur Windows et accédez au répertoire dans lequel le fichier solution du didacticiel et les dossiers du projet sont situés.</span><span class="sxs-lookup"><span data-stu-id="aba5f-125">Open Windows Explorer and navigate to the folder where the tutorial solution file and the project folders are located.</span></span>

5. <span data-ttu-id="aba5f-126">Créez un dossier nommé **PreviousVersions** dans le même dossier que **NumberGuessWorkflowHost** et **NumberGuessWorkflowActivities**.</span><span class="sxs-lookup"><span data-stu-id="aba5f-126">Create a new folder named **PreviousVersions** in the same folder as **NumberGuessWorkflowHost** and **NumberGuessWorkflowActivities**.</span></span> <span data-ttu-id="aba5f-127">Ce dossier est utilisé pour contenir les assemblys qui contiennent les différentes versions de workflow utilisées dans les étapes du didacticiel suivantes.</span><span class="sxs-lookup"><span data-stu-id="aba5f-127">This folder is used to contain the assemblies that contain the different versions of the workflows used in the subsequent tutorial steps.</span></span>

6. <span data-ttu-id="aba5f-128">Accédez au dossier **NumberGuessWorkflowActivities\bin\debug** (ou **bin\Release** selon les paramètres de votre projet).</span><span class="sxs-lookup"><span data-stu-id="aba5f-128">Navigate to the **NumberGuessWorkflowActivities\bin\debug** folder (or **bin\release** depending on your project settings).</span></span> <span data-ttu-id="aba5f-129">Copiez **NumberGuessWorkflowActivities. dll** et collez-le dans le dossier **PreviousVersions** .</span><span class="sxs-lookup"><span data-stu-id="aba5f-129">Copy **NumberGuessWorkflowActivities.dll** and paste it into the **PreviousVersions** folder.</span></span>

7. <span data-ttu-id="aba5f-130">Renommez **NumberGuessWorkflowActivities. dll** dans le dossier **PreviousVersions** en **NumberGuessWorkflowActivities_v1. dll**.</span><span class="sxs-lookup"><span data-stu-id="aba5f-130">Rename **NumberGuessWorkflowActivities.dll** in the **PreviousVersions** folder to **NumberGuessWorkflowActivities_v1.dll**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="aba5f-131">Les étapes de cette rubrique illustrent une façon de gérer les assemblys utilisés pour contenir plusieurs versions de workflow.</span><span class="sxs-lookup"><span data-stu-id="aba5f-131">The steps in this topic demonstrate one way to manage the assemblies used to contain multiple versions of the workflows.</span></span> <span data-ttu-id="aba5f-132">D'autres méthodes, telles que celles d'attribution de nom fort aux assemblys et d'inscription des assemblys dans le Global Assembly Cache peuvent également être utilisées.</span><span class="sxs-lookup"><span data-stu-id="aba5f-132">Other methods such as strong naming the assemblies and registering them in the global assembly cache could also be used.</span></span>

8. <span data-ttu-id="aba5f-133">Créez un dossier nommé **NumberGuessWorkflowActivities_du** dans le même dossier que **NumberGuessWorkflowHost**, **NumberGuessWorkflowActivities**et le dossier **PreviousVersions** qui vient d’être ajouté, puis copiez tous les fichiers et sous-dossiers du dossier **NumberGuessWorkflowActivities** dans le nouveau dossier **NumberGuessWorkflowActivities_du** .</span><span class="sxs-lookup"><span data-stu-id="aba5f-133">Create a new folder named **NumberGuessWorkflowActivities_du** in the same folder as **NumberGuessWorkflowHost**, **NumberGuessWorkflowActivities**, and the newly added **PreviousVersions** folder, and copy all of the files and subfolders from the **NumberGuessWorkflowActivities** folder into the new **NumberGuessWorkflowActivities_du** folder.</span></span> <span data-ttu-id="aba5f-134">Cette copie de sauvegarde du projet pour la version initiale des activités est utilisée dans [procédure : Met à jour la définition d’une instance](how-to-update-the-definition-of-a-running-workflow-instance.md)de workflow en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="aba5f-134">This backup copy of the project for the initial version of the activities is used in [How to: Update the Definition of a Running Workflow Instance](how-to-update-the-definition-of-a-running-workflow-instance.md).</span></span>

9. <span data-ttu-id="aba5f-135">Rouvrez la solution **WF45GettingStartedTutorial** dans Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="aba5f-135">Re-open the **WF45GettingStartedTutorial** solution in Visual Studio 2012.</span></span>

### <a name="BKMK_UpdateWorkflows"></a><span data-ttu-id="aba5f-136">Pour mettre à jour les workflows</span><span class="sxs-lookup"><span data-stu-id="aba5f-136">To update the workflows</span></span>

<span data-ttu-id="aba5f-137">Dans cette section, les définitions de workflow sont mises à jour.</span><span class="sxs-lookup"><span data-stu-id="aba5f-137">In this section, the workflow definitions are updated.</span></span> <span data-ttu-id="aba5f-138">Les deux activités `WriteLine` qui fournissent des commentaires sur la proposition de l'utilisateur sont mises à jour, et une nouvelle activité `WriteLine`, qui fournit des informations supplémentaires sur le jeu une fois que le nombre est deviné, est ajoutée.</span><span class="sxs-lookup"><span data-stu-id="aba5f-138">The two `WriteLine` activities that give feedback on the user's guess are updated, and a new `WriteLine` activity is added that provides additional information about the game once the number is guessed.</span></span>

#### <a name="BKMK_UpdateStateMachine"></a><span data-ttu-id="aba5f-139">Pour mettre à jour le flux de travail StateMachine</span><span class="sxs-lookup"><span data-stu-id="aba5f-139">To update the StateMachine workflow</span></span>

1. <span data-ttu-id="aba5f-140">Dans **Explorateur de solutions**, sous le projet **NumberGuessWorkflowActivities** , double-cliquez sur **StateMachineNumberGuessWorkflow. Xaml**.</span><span class="sxs-lookup"><span data-stu-id="aba5f-140">In **Solution Explorer**, under the **NumberGuessWorkflowActivities** project, double-click **StateMachineNumberGuessWorkflow.xaml**.</span></span>

2. <span data-ttu-id="aba5f-141">Double-cliquez sur la transition **Guess incorrect** sur la machine à États.</span><span class="sxs-lookup"><span data-stu-id="aba5f-141">Double-click the **Guess Incorrect** transition on the state machine.</span></span>

3. <span data-ttu-id="aba5f-142">Mettez à jour la propriété `Text` de l'activité `WriteLine` située le plus à gauche dans l'activité `If`.</span><span class="sxs-lookup"><span data-stu-id="aba5f-142">Update the `Text` of the left-most `WriteLine` in the `If` activity.</span></span>

    ```vb
    Guess & " is too low."
    ```

    ```csharp
    Guess + " is too low."
    ```

4. <span data-ttu-id="aba5f-143">Mettez à jour la propriété `Text` de l'activité `WriteLine` située le plus à droite dans l'activité `If`.</span><span class="sxs-lookup"><span data-stu-id="aba5f-143">Update the `Text` of the right-most `WriteLine` in the `If` activity.</span></span>

    ```vb
    Guess & " is too high."
    ```

    ```csharp
    Guess + " is too high."
    ```

5. <span data-ttu-id="aba5f-144">Revenez à la vue globale de l’ordinateur d’État dans le concepteur de flux de travail en cliquant sur **StateMachine** dans l’affichage de navigation en haut du concepteur de Workflow.</span><span class="sxs-lookup"><span data-stu-id="aba5f-144">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>

6. <span data-ttu-id="aba5f-145">Double-cliquez sur la transition **estimation correcte** sur la machine à États.</span><span class="sxs-lookup"><span data-stu-id="aba5f-145">Double-click the **Guess Correct** transition on the state machine.</span></span>

7. <span data-ttu-id="aba5f-146">Faites glisser une activité **WriteLine** de la section **primitives** de la **boîte à outils** et déposez-la sur l’étiquette de l' **activité déposer l’action ici** de la transition.</span><span class="sxs-lookup"><span data-stu-id="aba5f-146">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it on the **Drop Action activity here** label of the transition.</span></span>

8. <span data-ttu-id="aba5f-147">Dans la zone de propriété `Text`, tapez l'expression suivante :</span><span class="sxs-lookup"><span data-stu-id="aba5f-147">Type the following expression into the `Text` property box.</span></span>

    ```vb
    Guess & " is correct. You guessed it in " & Turns & " turns."
    ```

    ```csharp
    Guess + " is correct. You guessed it in " + Turns + " turns."
    ```

#### <a name="BKMK_UpdateFlowchart"></a><span data-ttu-id="aba5f-148">Pour mettre à jour le flux de travail de l’organigramme</span><span class="sxs-lookup"><span data-stu-id="aba5f-148">To update the Flowchart workflow</span></span>

1. <span data-ttu-id="aba5f-149">Dans **Explorateur de solutions**, sous le projet **NumberGuessWorkflowActivities** , double-cliquez sur **FlowchartNumberGuessWorkflow. Xaml**.</span><span class="sxs-lookup"><span data-stu-id="aba5f-149">In **Solution Explorer**, under the **NumberGuessWorkflowActivities** project, double-click **FlowchartNumberGuessWorkflow.xaml**.</span></span>

2. <span data-ttu-id="aba5f-150">Mettez à jour la propriété `Text` de l'activité `WriteLine` située le plus à gauche.</span><span class="sxs-lookup"><span data-stu-id="aba5f-150">Update the `Text` of the left-most `WriteLine` activity.</span></span>

    ```vb
    Guess & " is too low."
    ```

    ```csharp
    Guess + " is too low."
    ```

3. <span data-ttu-id="aba5f-151">Mettez à jour la propriété `Text` de l'activité `WriteLine` située le plus à droite.</span><span class="sxs-lookup"><span data-stu-id="aba5f-151">Update the `Text` of the right-most `WriteLine` activity.</span></span>

    ```vb
    Guess & " is too high."
    ```

    ```csharp
    Guess + " is too high."
    ```

4. <span data-ttu-id="aba5f-152">Faites glisser une activité **WriteLine** de la section **primitives** de la **boîte à outils** et déposez-la `True` sur le point de déplacement `FlowDecision`de l’action du plus haut.</span><span class="sxs-lookup"><span data-stu-id="aba5f-152">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it on the drop point of the `True` action of the topmost `FlowDecision`.</span></span> <span data-ttu-id="aba5f-153">L'activité `WriteLine` est ajoutée à l'organigramme et liée à l'action `True` de `FlowDecision`.</span><span class="sxs-lookup"><span data-stu-id="aba5f-153">The `WriteLine` activity is added to the flowchart and linked to the `True` action of the `FlowDecision`.</span></span>

5. <span data-ttu-id="aba5f-154">Dans la zone de propriété `Text`, tapez l'expression suivante :</span><span class="sxs-lookup"><span data-stu-id="aba5f-154">Type the following expression into the `Text` property box.</span></span>

    ```vb
    Guess & " is correct. You guessed it in " & Turns & " turns."
    ```

    ```csharp
    Guess + " is correct. You guessed it in " + Turns + " turns."
    ```

#### <a name="BKMK_UpdateSequential"></a><span data-ttu-id="aba5f-155">Pour mettre à jour le flux de travail séquentiel</span><span class="sxs-lookup"><span data-stu-id="aba5f-155">To update the Sequential workflow</span></span>

1. <span data-ttu-id="aba5f-156">Dans **Explorateur de solutions**, sous le projet **NumberGuessWorkflowActivities** , double-cliquez sur **SequentialNumberGuessWorkflow. Xaml**.</span><span class="sxs-lookup"><span data-stu-id="aba5f-156">In **Solution Explorer**, under the **NumberGuessWorkflowActivities** project, double-click **SequentialNumberGuessWorkflow.xaml**.</span></span>

2. <span data-ttu-id="aba5f-157">Mettez à jour la propriété `Text` de l'activité `WriteLine` située le plus à gauche dans l'activité `If`.</span><span class="sxs-lookup"><span data-stu-id="aba5f-157">Update the `Text` of the left-most `WriteLine` in the `If` activity.</span></span>

    ```vb
    Guess & " is too low."
    ```

    ```csharp
    Guess + " is too low."
    ```

3. <span data-ttu-id="aba5f-158">Mettez à jour la propriété `Text` de l'activité `WriteLine` située le plus à droite dans l'activité `If`.</span><span class="sxs-lookup"><span data-stu-id="aba5f-158">Update the `Text` of the right-most `WriteLine` activity in the `If` activity.</span></span>

    ```vb
    Guess & " is too high."
    ```

    ```csharp
    Guess + " is too high."
    ```

4. <span data-ttu-id="aba5f-159">Faites glisser une activité **WriteLine** de la section **primitives** de **la boîte à outils** et déposez **-la après l’activité de** fait afin que **WriteLine** soit l' `Sequence` activité finale dans l’activité racine.</span><span class="sxs-lookup"><span data-stu-id="aba5f-159">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it after the **DoWhile** activity so that the **WriteLine** is the final activity in the root `Sequence` activity.</span></span>

5. <span data-ttu-id="aba5f-160">Dans la zone de propriété `Text`, tapez l'expression suivante :</span><span class="sxs-lookup"><span data-stu-id="aba5f-160">Type the following expression into the `Text` property box.</span></span>

    ```vb
    Guess & " is correct. You guessed it in " & Turns & " turns."
    ```

    ```csharp
    Guess + " is correct. You guessed it in " + Turns + " turns."
    ```

### <a name="BKMK_UpdateWorkflowVersionMap"></a><span data-ttu-id="aba5f-161">Pour mettre à jour WorkflowVersionMap afin d’inclure les versions de flux de travail précédentes</span><span class="sxs-lookup"><span data-stu-id="aba5f-161">To update WorkflowVersionMap to include the previous workflow versions</span></span>

1. <span data-ttu-id="aba5f-162">Double-cliquez sur **WorkflowVersionMap.cs** (ou **WorkflowVersionMap. vb**) sous le projet **NumberGuessWorkflowHost** pour l’ouvrir.</span><span class="sxs-lookup"><span data-stu-id="aba5f-162">Double-click **WorkflowVersionMap.cs** (or **WorkflowVersionMap.vb**) under the **NumberGuessWorkflowHost** project to open it.</span></span>

2. <span data-ttu-id="aba5f-163">Ajoutez les instructions `using` (ou `Imports`) suivantes au début du fichier avec les autres instructions `using` (ou `Imports`).</span><span class="sxs-lookup"><span data-stu-id="aba5f-163">Add the following `using` (or `Imports`) statements to the top of the file with the other `using` (or `Imports`) statements.</span></span>

    ```vb
    Imports System.Reflection
    Imports System.IO
    ```

    ```csharp
    using System.Reflection;
    using System.IO;
    ```

3. <span data-ttu-id="aba5f-164">Ajoutez trois nouvelles identités de workflow juste au-dessous des trois déclarations d'identité de workflow existantes.</span><span class="sxs-lookup"><span data-stu-id="aba5f-164">Add three new workflow identities just below the three existing workflow identity declarations.</span></span> <span data-ttu-id="aba5f-165">Ces nouvelles identités de workflow `v1` seront utilisées pour fournir la définition appropriée de workflow aux workflows démarrés avant que les mises à jour aient été effectuées.</span><span class="sxs-lookup"><span data-stu-id="aba5f-165">These new `v1` workflow identities will be used provide the correct workflow definition to workflows started before the updates were made.</span></span>

    ```vb
    'Current version identities.
    Public StateMachineNumberGuessIdentity As WorkflowIdentity
    Public FlowchartNumberGuessIdentity As WorkflowIdentity
    Public SequentialNumberGuessIdentity As WorkflowIdentity

    'v1 Identities.
    Public StateMachineNumberGuessIdentity_v1 As WorkflowIdentity
    Public FlowchartNumberGuessIdentity_v1 As WorkflowIdentity
    Public SequentialNumberGuessIdentity_v1 As WorkflowIdentity
    ```

    ```csharp
    // Current version identities.
    static public WorkflowIdentity StateMachineNumberGuessIdentity;
    static public WorkflowIdentity FlowchartNumberGuessIdentity;
    static public WorkflowIdentity SequentialNumberGuessIdentity;

    // v1 identities.
    static public WorkflowIdentity StateMachineNumberGuessIdentity_v1;
    static public WorkflowIdentity FlowchartNumberGuessIdentity_v1;
    static public WorkflowIdentity SequentialNumberGuessIdentity_v1;
    ```

4. <span data-ttu-id="aba5f-166">Dans le constructeur `WorkflowVersionMap`, mettez à jour la propriété `Version` des trois identités actuelles de workflow vers `2.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="aba5f-166">In the `WorkflowVersionMap` constructor, update the `Version` property of the three current workflow identities to `2.0.0.0`.</span></span>

    ```vb
    'Add the current workflow version identities.
    StateMachineNumberGuessIdentity = New WorkflowIdentity With
    {
        .Name = "StateMachineNumberGuessWorkflow",
        .Version = New Version(2, 0, 0, 0)
    }

    FlowchartNumberGuessIdentity = New WorkflowIdentity With
    {
        .Name = "FlowchartNumberGuessWorkflow",
        .Version = New Version(2, 0, 0, 0)
    }

    SequentialNumberGuessIdentity = New WorkflowIdentity With
    {
        .Name = "SequentialNumberGuessWorkflow",
        .Version = New Version(2, 0, 0, 0)
    }

    map.Add(StateMachineNumberGuessIdentity, New StateMachineNumberGuessWorkflow())
    map.Add(FlowchartNumberGuessIdentity, New FlowchartNumberGuessWorkflow())
    map.Add(SequentialNumberGuessIdentity, New SequentialNumberGuessWorkflow())
    ```

    ```csharp
    // Add the current workflow version identities.
    StateMachineNumberGuessIdentity = new WorkflowIdentity
    {
        Name = "StateMachineNumberGuessWorkflow",
        // Version = new Version(1, 0, 0, 0),
        Version = new Version(2, 0, 0, 0)
    };

    FlowchartNumberGuessIdentity = new WorkflowIdentity
    {
        Name = "FlowchartNumberGuessWorkflow",
        // Version = new Version(1, 0, 0, 0),
        Version = new Version(2, 0, 0, 0)
    };

    SequentialNumberGuessIdentity = new WorkflowIdentity
    {
        Name = "SequentialNumberGuessWorkflow",
        // Version = new Version(1, 0, 0, 0),
        Version = new Version(2, 0, 0, 0)
    };

    map.Add(StateMachineNumberGuessIdentity, new StateMachineNumberGuessWorkflow());
    map.Add(FlowchartNumberGuessIdentity, new FlowchartNumberGuessWorkflow());
    map.Add(SequentialNumberGuessIdentity, new SequentialNumberGuessWorkflow());
    ```

    <span data-ttu-id="aba5f-167">Le code qui ajoute les versions actuelles des workflow au dictionnaire utilise les versions actuelles qui sont référencées dans le projet ainsi, le code qui initialise les définitions de workflow n'a pas besoin d'être mis à jour.</span><span class="sxs-lookup"><span data-stu-id="aba5f-167">The code in that adds the current versions of the workflows to the dictionary uses the current versions that are referenced in the project, so the code that initializes the workflow definitions does not need to be updated.</span></span>

5. <span data-ttu-id="aba5f-168">Ajoutez le code suivant dans le constructeur juste après le code qui ajoute les versions actuelles au dictionnaire.</span><span class="sxs-lookup"><span data-stu-id="aba5f-168">Add the following code in the constructor just after the code that adds the current versions to the dictionary.</span></span>

    ```vb
    'Initialize the previous workflow version identities.
    StateMachineNumberGuessIdentity_v1 = New WorkflowIdentity With
    {
        .Name = "StateMachineNumberGuessWorkflow",
        .Version = New Version(1, 0, 0, 0)
    }

    FlowchartNumberGuessIdentity_v1 = New WorkflowIdentity With
    {
        .Name = "FlowchartNumberGuessWorkflow",
        .Version = New Version(1, 0, 0, 0)
    }

    SequentialNumberGuessIdentity_v1 = New WorkflowIdentity With
    {
        .Name = "SequentialNumberGuessWorkflow",
        .Version = New Version(1, 0, 0, 0)
    }
    ```

    ```csharp
    // Initialize the previous workflow version identities.
    StateMachineNumberGuessIdentity_v1 = new WorkflowIdentity
    {
        Name = "StateMachineNumberGuessWorkflow",
        Version = new Version(1, 0, 0, 0)
    };

    FlowchartNumberGuessIdentity_v1 = new WorkflowIdentity
    {
        Name = "FlowchartNumberGuessWorkflow",
        Version = new Version(1, 0, 0, 0)
    };

    SequentialNumberGuessIdentity_v1 = new WorkflowIdentity
    {
        Name = "SequentialNumberGuessWorkflow",
        Version = new Version(1, 0, 0, 0)
    };
    ```

    <span data-ttu-id="aba5f-169">Ces identités de workflow sont associées aux versions initiales des définitions correspondantes de workflow.</span><span class="sxs-lookup"><span data-stu-id="aba5f-169">These workflow identities are associated with the initial versions of the corresponding workflow definitions.</span></span>

6. <span data-ttu-id="aba5f-170">Ensuite, chargez l'assembly qui contient la première version des définitions de workflow, puis créez et ajoutez des définitions correspondantes de workflow au dictionnaire.</span><span class="sxs-lookup"><span data-stu-id="aba5f-170">Next, load the assembly that contains the initial version of the workflow definitions, and create and add the corresponding workflow definitions to the dictionary.</span></span>

    ```vb
    'Add the previous version workflow identities to the dictionary along with
    'the corresponding workflow definitions loaded from the v1 assembly.
    'Assembly.LoadFile requires an absolute path so convert this relative path
    'to an absolute path.
    Dim v1AssemblyPath As String = "..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v1.dll"
    v1AssemblyPath = Path.GetFullPath(v1AssemblyPath)
    Dim v1Assembly As Assembly = Assembly.LoadFile(v1AssemblyPath)

    map.Add(StateMachineNumberGuessIdentity_v1,
        v1Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow"))

    map.Add(SequentialNumberGuessIdentity_v1,
        v1Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow"))

    map.Add(FlowchartNumberGuessIdentity_v1,
        v1Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow"))
    ```

    ```csharp
    // Add the previous version workflow identities to the dictionary along with
    // the corresponding workflow definitions loaded from the v1 assembly.
    // Assembly.LoadFile requires an absolute path so convert this relative path
    // to an absolute path.
    string v1AssemblyPath = @"..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v1.dll";
    v1AssemblyPath = Path.GetFullPath(v1AssemblyPath);
    Assembly v1Assembly = Assembly.LoadFile(v1AssemblyPath);

    map.Add(StateMachineNumberGuessIdentity_v1,
        v1Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow") as Activity);

    map.Add(SequentialNumberGuessIdentity_v1,
        v1Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow") as Activity);

    map.Add(FlowchartNumberGuessIdentity_v1,
        v1Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow") as Activity);
    ```

    <span data-ttu-id="aba5f-171">L'exemple suivant constitue l'intégralité de la classe `WorkflowVersionMap` mise à jour.</span><span class="sxs-lookup"><span data-stu-id="aba5f-171">The following example is the complete listing for the updated `WorkflowVersionMap` class.</span></span>

    ```vb
    Public Module WorkflowVersionMap
        Dim map As Dictionary(Of WorkflowIdentity, Activity)

        'Current version identities.
        Public StateMachineNumberGuessIdentity As WorkflowIdentity
        Public FlowchartNumberGuessIdentity As WorkflowIdentity
        Public SequentialNumberGuessIdentity As WorkflowIdentity

        'v1 Identities.
        Public StateMachineNumberGuessIdentity_v1 As WorkflowIdentity
        Public FlowchartNumberGuessIdentity_v1 As WorkflowIdentity
        Public SequentialNumberGuessIdentity_v1 As WorkflowIdentity

        Sub New()
            map = New Dictionary(Of WorkflowIdentity, Activity)

            'Add the current workflow version identities.
            StateMachineNumberGuessIdentity = New WorkflowIdentity With
            {
                .Name = "StateMachineNumberGuessWorkflow",
                .Version = New Version(2, 0, 0, 0)
            }

            FlowchartNumberGuessIdentity = New WorkflowIdentity With
            {
                .Name = "FlowchartNumberGuessWorkflow",
                .Version = New Version(2, 0, 0, 0)
            }

            SequentialNumberGuessIdentity = New WorkflowIdentity With
            {
                .Name = "SequentialNumberGuessWorkflow",
                .Version = New Version(2, 0, 0, 0)
            }

            map.Add(StateMachineNumberGuessIdentity, New StateMachineNumberGuessWorkflow())
            map.Add(FlowchartNumberGuessIdentity, New FlowchartNumberGuessWorkflow())
            map.Add(SequentialNumberGuessIdentity, New SequentialNumberGuessWorkflow())

            'Initialize the previous workflow version identities.
            StateMachineNumberGuessIdentity_v1 = New WorkflowIdentity With
            {
                .Name = "StateMachineNumberGuessWorkflow",
                .Version = New Version(1, 0, 0, 0)
            }

            FlowchartNumberGuessIdentity_v1 = New WorkflowIdentity With
            {
                .Name = "FlowchartNumberGuessWorkflow",
                .Version = New Version(1, 0, 0, 0)
            }

            SequentialNumberGuessIdentity_v1 = New WorkflowIdentity With
            {
                .Name = "SequentialNumberGuessWorkflow",
                .Version = New Version(1, 0, 0, 0)
            }

            'Add the previous version workflow identities to the dictionary along with
            'the corresponding workflow definitions loaded from the v1 assembly.
            'Assembly.LoadFile requires an absolute path so convert this relative path
            'to an absolute path.
            Dim v1AssemblyPath As String = "..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v1.dll"
            v1AssemblyPath = Path.GetFullPath(v1AssemblyPath)
            Dim v1Assembly As Assembly = Assembly.LoadFile(v1AssemblyPath)

            map.Add(StateMachineNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow"))

            map.Add(SequentialNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow"))

            map.Add(FlowchartNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow"))
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

        // v1 identities.
        static public WorkflowIdentity StateMachineNumberGuessIdentity_v1;
        static public WorkflowIdentity FlowchartNumberGuessIdentity_v1;
        static public WorkflowIdentity SequentialNumberGuessIdentity_v1;

        static WorkflowVersionMap()
        {
            map = new Dictionary<WorkflowIdentity, Activity>();

            // Add the current workflow version identities.
            StateMachineNumberGuessIdentity = new WorkflowIdentity
            {
                Name = "StateMachineNumberGuessWorkflow",
                // Version = new Version(1, 0, 0, 0),
                Version = new Version(2, 0, 0, 0)
            };

            FlowchartNumberGuessIdentity = new WorkflowIdentity
            {
                Name = "FlowchartNumberGuessWorkflow",
                // Version = new Version(1, 0, 0, 0),
                Version = new Version(2, 0, 0, 0)
            };

            SequentialNumberGuessIdentity = new WorkflowIdentity
            {
                Name = "SequentialNumberGuessWorkflow",
                // Version = new Version(1, 0, 0, 0),
                Version = new Version(2, 0, 0, 0)
            };

            map.Add(StateMachineNumberGuessIdentity, new StateMachineNumberGuessWorkflow());
            map.Add(FlowchartNumberGuessIdentity, new FlowchartNumberGuessWorkflow());
            map.Add(SequentialNumberGuessIdentity, new SequentialNumberGuessWorkflow());

            // Initialize the previous workflow version identities.
            StateMachineNumberGuessIdentity_v1 = new WorkflowIdentity
            {
                Name = "StateMachineNumberGuessWorkflow",
                Version = new Version(1, 0, 0, 0)
            };

            FlowchartNumberGuessIdentity_v1 = new WorkflowIdentity
            {
                Name = "FlowchartNumberGuessWorkflow",
                Version = new Version(1, 0, 0, 0)
            };

            SequentialNumberGuessIdentity_v1 = new WorkflowIdentity
            {
                Name = "SequentialNumberGuessWorkflow",
                Version = new Version(1, 0, 0, 0)
            };

            // Add the previous version workflow identities to the dictionary along with
            // the corresponding workflow definitions loaded from the v1 assembly.
            // Assembly.LoadFile requires an absolute path so convert this relative path
            // to an absolute path.
            string v1AssemblyPath = @"..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v1.dll";
            v1AssemblyPath = Path.GetFullPath(v1AssemblyPath);
            Assembly v1Assembly = Assembly.LoadFile(v1AssemblyPath);

            map.Add(StateMachineNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow") as Activity);

            map.Add(SequentialNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow") as Activity);

            map.Add(FlowchartNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow") as Activity);
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

### <a name="BKMK_BuildAndRun"></a> <span data-ttu-id="aba5f-172">Pour générer et exécuter l'application</span><span class="sxs-lookup"><span data-stu-id="aba5f-172">To build and run the application</span></span>

1. <span data-ttu-id="aba5f-173">Appuyez sur Ctrl+Maj+B pour générer l'application, puis sur Ctrl+F5 pour démarrer.</span><span class="sxs-lookup"><span data-stu-id="aba5f-173">Press CTRL+SHIFT+B to build the application, and then CTRL+F5 to start.</span></span>

2. <span data-ttu-id="aba5f-174">Démarrez un nouveau flux de travail en cliquant sur **nouveau jeu**.</span><span class="sxs-lookup"><span data-stu-id="aba5f-174">Start a new workflow by clicking **New Game**.</span></span> <span data-ttu-id="aba5f-175">La version du workflow s'affiche dans la fenêtre d'état et reflète la version mise à jour du `WorkflowIdentity` associé.</span><span class="sxs-lookup"><span data-stu-id="aba5f-175">The version of the workflow is displayed under the status window and reflects the updated version from the associated `WorkflowIdentity`.</span></span> <span data-ttu-id="aba5f-176">Notez `InstanceId` de façon à afficher le fichier de suivi du workflow lorsqu'il se termine, puis entrez des propositions jusqu'à ce que le jeu soit terminé.</span><span class="sxs-lookup"><span data-stu-id="aba5f-176">Make a note of the `InstanceId` so you can view the tracking file for the workflow when it completes, and then enter guesses until the game is complete.</span></span> <span data-ttu-id="aba5f-177">Notez comment la proposition de l'utilisateur est affichée dans les informations affichées dans la fenêtre d'état basée sur les mises à jour dans les activités `WriteLine`.</span><span class="sxs-lookup"><span data-stu-id="aba5f-177">Note how the user's guess is displayed in the information displayed in the status window based on the updates to the `WriteLine` activities.</span></span>

    ```console
    Please enter a number between 1 and 10
    5 is too high.
    Please enter a number between 1 and 10
    3 is too high.
    Please enter a number between 1 and 10
    1 is too low.
    Please enter a number between 1 and 10
    Congratulations, you guessed the number in 4 turns.
    ```

    > [!NOTE]
    > <span data-ttu-id="aba5f-178">Le texte mis à jour à partir des activités `WriteLine` s'affiche, mais la sortie de l'activité finale `WriteLine` ajoutée dans cette rubrique ne s'affiche pas.</span><span class="sxs-lookup"><span data-stu-id="aba5f-178">The updated text from the `WriteLine` activities is displayed, but the output of the final `WriteLine` activity that was added in this topic is not.</span></span> <span data-ttu-id="aba5f-179">Cela est dû au fait que la fenêtre d'état est mise à jour par le gestionnaire `PersistableIdle`.</span><span class="sxs-lookup"><span data-stu-id="aba5f-179">That is because the status window is updated by the `PersistableIdle` handler.</span></span> <span data-ttu-id="aba5f-180">Étant donné que le workflow se termine et n'est pas inactif après l'activité finale, le gestionnaire `PersistableIdle` n'est pas appelé.</span><span class="sxs-lookup"><span data-stu-id="aba5f-180">Because the workflow completes and does not go idle after the final activity, the `PersistableIdle` handler is not called.</span></span> <span data-ttu-id="aba5f-181">Toutefois, un message similaire est affiché dans la fenêtre d'état par le gestionnaire `Completed`.</span><span class="sxs-lookup"><span data-stu-id="aba5f-181">However, a similar message is displayed in the status window by the `Completed` handler.</span></span> <span data-ttu-id="aba5f-182">Si vous le souhaitez, le code peut être ajouté au gestionnaire `Completed` pour extraire le texte de `StringWriter` et pour l'afficher dans la fenêtre d'état.</span><span class="sxs-lookup"><span data-stu-id="aba5f-182">If desired, code could be added to the `Completed` handler to extract the text from the `StringWriter` and display it to the status window.</span></span>

3. <span data-ttu-id="aba5f-183">Ouvrez l’Explorateur Windows et accédez au dossier **NumberGuessWorkflowHost\bin\debug** (ou **bin\Release** selon les paramètres de votre projet), puis ouvrez le fichier de suivi à l’aide du bloc-notes qui correspond au workflow terminé.</span><span class="sxs-lookup"><span data-stu-id="aba5f-183">Open Windows Explorer and navigate to the **NumberGuessWorkflowHost\bin\debug** folder (or **bin\release** depending on your project settings) and open the tracking file using Notepad that corresponds to the completed workflow.</span></span> <span data-ttu-id="aba5f-184">Si vous n’avez pas noté le `InstanceId`, vous pouvez identifier le fichier de suivi approprié à l’aide des informations de date de **modification** dans l’Explorateur Windows.</span><span class="sxs-lookup"><span data-stu-id="aba5f-184">If you did not make a note of the `InstanceId`, you can identify the correct tracking file by using the **Date modified** information in Windows Explorer.</span></span>

    ```console
    Please enter a number between 1 and 10
    5 is too high.
    Please enter a number between 1 and 10
    3 is too high.
    Please enter a number between 1 and 10
    1 is too low.
    Please enter a number between 1 and 10
    2 is correct. You guessed it in 4 turns.
    ```

    <span data-ttu-id="aba5f-185">La sortie mise à jour `WriteLine` est contenue dans le fichier de trace, y compris la sortie `WriteLine` ajoutée dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="aba5f-185">The updated `WriteLine` output is contained within the tracking file, including the output of the `WriteLine` that was added in this topic.</span></span>

4. <span data-ttu-id="aba5f-186">Revenez à l'application d'estimation de nombre et sélectionnez l'un des workflows qui a été démarré avant que les mises à jour n'aient été effectuées.</span><span class="sxs-lookup"><span data-stu-id="aba5f-186">Switch back to the number guessing application and select one of the workflows that was started before the updates were made.</span></span> <span data-ttu-id="aba5f-187">Vous pouvez identifier la version du workflow actuellement sélectionné en examinant les informations de version qui s'affichent sous la fenêtre d'état.</span><span class="sxs-lookup"><span data-stu-id="aba5f-187">You can identify the version of the currently selected workflow by looking at the version information that is displayed below the status window.</span></span> <span data-ttu-id="aba5f-188">Entrez des propositions et notez que les mises à jour d'état correspondent à la sortie d'activité `WriteLine` de la version antérieure, et n'incluez pas l'estimation de l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="aba5f-188">Enter some guesses and note that the status updates match the `WriteLine` activity output from the previous version, and do not include the user's guess.</span></span> <span data-ttu-id="aba5f-189">Cela est dû au fait que ces workflows utilisent la définition de workflow précédente qui n'a pas les mises à jour de `WriteLine`.</span><span class="sxs-lookup"><span data-stu-id="aba5f-189">That is because these workflows are using the previous workflow definition that does not have the `WriteLine` updates.</span></span>

    <span data-ttu-id="aba5f-190">À l’étape suivante, [Comment : Mettre à jour la définition d’une instance](how-to-update-the-definition-of-a-running-workflow-instance.md)de workflow en `v1` cours d’exécution, les instances de workflow en cours d’exécution `v2` sont mises à jour afin qu’elles contiennent les nouvelles fonctionnalités en tant qu’instances.</span><span class="sxs-lookup"><span data-stu-id="aba5f-190">In the next step, [How to: Update the Definition of a Running Workflow Instance](how-to-update-the-definition-of-a-running-workflow-instance.md), the running `v1` workflow instances are updated so they contain the new functionality as the `v2` instances.</span></span>

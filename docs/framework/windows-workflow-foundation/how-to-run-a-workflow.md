---
title: 'Procédure : exécuter un workflow'
description: Cet article explique comment créer un hôte de workflow et exécuter le workflow défini dans un article précédent de cette série de didacticiels Windows Workflow Foundation.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f814ff82-fe2b-4614-aebb-b768c3e61179
ms.openlocfilehash: 7f76ed5ad1a76a155489339a9febf12eefd64ae8
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96279985"
---
# <a name="how-to-run-a-workflow"></a><span data-ttu-id="d63ab-103">Procédure : exécuter un workflow</span><span class="sxs-lookup"><span data-stu-id="d63ab-103">How to: Run a Workflow</span></span>

<span data-ttu-id="d63ab-104">Cette rubrique est la suite du didacticiel de mise en route de Windows Workflow Foundation et explique comment créer un hôte de workflow et exécuter le workflow défini dans la rubrique précédente [How to: Create a Workflow](how-to-create-a-workflow.md) .</span><span class="sxs-lookup"><span data-stu-id="d63ab-104">This topic is a continuation of the Windows Workflow Foundation Getting Started tutorial and discusses how to create a workflow host and run the workflow defined in the previous [How to: Create a Workflow](how-to-create-a-workflow.md) topic.</span></span>

> [!NOTE]
> <span data-ttu-id="d63ab-105">Chaque rubrique du didacticiel de mise en route dépend des rubriques précédentes.</span><span class="sxs-lookup"><span data-stu-id="d63ab-105">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="d63ab-106">Avant de parcourir cette rubrique, vous devez avoir parcouru [How to: Create an Activity](how-to-create-an-activity.md) et [How to: Create a Workflow](how-to-create-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="d63ab-106">To complete this topic you must first complete [How to: Create an Activity](how-to-create-an-activity.md) and [How to: Create a Workflow](how-to-create-a-workflow.md).</span></span>

> [!NOTE]
> <span data-ttu-id="d63ab-107">Pour télécharger une version complète du didacticiel, consultez [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976)(Windows Workflow Foundation (WF45) - Didacticiel de mise en route).</span><span class="sxs-lookup"><span data-stu-id="d63ab-107">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
### <a name="to-create-the-workflow-host-project"></a><span data-ttu-id="d63ab-108">Pour créer le projet d'hôte du workflow</span><span class="sxs-lookup"><span data-stu-id="d63ab-108">To create the workflow host project</span></span>  
  
1. <span data-ttu-id="d63ab-109">Ouvrez la solution de la rubrique précédente [Comment : créer une activité](how-to-create-an-activity.md) à l’aide de Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="d63ab-109">Open the solution from the previous [How to: Create an Activity](how-to-create-an-activity.md) topic by using Visual Studio 2012.</span></span>  
  
2. <span data-ttu-id="d63ab-110">Dans l' **Explorateur de solutions** , cliquez avec le bouton droit sur la solution **WF45GettingStartedTutorial** , puis sélectionnez **Ajouter**, **Nouveau projet**.</span><span class="sxs-lookup"><span data-stu-id="d63ab-110">Right-click the **WF45GettingStartedTutorial** solution in **Solution Explorer** and select **Add**, **New Project**.</span></span>  
  
    > [!TIP]
    > <span data-ttu-id="d63ab-111">Si la fenêtre **Explorateur de solutions** ne s'affiche pas, sélectionnez **Explorateur de solutions** dans le menu **Afficher**.</span><span class="sxs-lookup"><span data-stu-id="d63ab-111">If the **Solution Explorer** window is not displayed, select **Solution Explorer** from the **View** menu.</span></span>

3. <span data-ttu-id="d63ab-112">Dans le nœud **Installé** , sélectionnez **Visual C#**, **Workflow** (ou **Visual Basic**, **Workflow**).</span><span class="sxs-lookup"><span data-stu-id="d63ab-112">In the **Installed** node, select **Visual C#**, **Workflow** (or **Visual Basic**, **Workflow**).</span></span>

    > [!NOTE]
    > <span data-ttu-id="d63ab-113">Selon le langage de programmation configuré comme langage principal dans Visual Studio, le nœud **Visual C#** ou **Visual Basic** peut se trouver sous le nœud **Autres langages** dans le nœud **Installé**.</span><span class="sxs-lookup"><span data-stu-id="d63ab-113">Depending on which programming language is configured as the primary language in Visual Studio, the **Visual C#** or **Visual Basic** node may be under the **Other Languages** node in the **Installed** node.</span></span>

     <span data-ttu-id="d63ab-114">Assurez-vous que **.NET Framework 4.5** est sélectionné dans la liste déroulante de la version .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d63ab-114">Ensure that **.NET Framework 4.5** is selected in the .NET Framework version drop-down list.</span></span> <span data-ttu-id="d63ab-115">Dans la liste **Workflow** , sélectionnez **Application console de workflow** .</span><span class="sxs-lookup"><span data-stu-id="d63ab-115">Select **Workflow Console Application** from the **Workflow** list.</span></span> <span data-ttu-id="d63ab-116">Dans la zone `NumberGuessWorkflowHost` Nom **, tapez** et cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="d63ab-116">Type `NumberGuessWorkflowHost` into the **Name** box and click **OK**.</span></span> <span data-ttu-id="d63ab-117">Une application de workflow de démarrage est ainsi créée, ainsi qu'un support d'hébergement de workflow de base.</span><span class="sxs-lookup"><span data-stu-id="d63ab-117">This creates a starter workflow application with basic workflow hosting support.</span></span> <span data-ttu-id="d63ab-118">Le code d'hébergement de base est modifié et sert à exécuter l'application de workflow.</span><span class="sxs-lookup"><span data-stu-id="d63ab-118">This basic hosting code is modified and used to run the workflow application.</span></span>

4. <span data-ttu-id="d63ab-119">Cliquez avec le bouton droit sur le projet **NumberGuessWorkflowHost** récemment ajouté dans l' **Explorateur de solutions** , puis sélectionnez **Ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="d63ab-119">Right-click the newly added **NumberGuessWorkflowHost** project in **Solution Explorer** and select **Add Reference**.</span></span> <span data-ttu-id="d63ab-120">Dans la liste **Ajouter une référence** , sélectionnez **Solution** , activez la case à cocher en regard de **NumberGuessWorkflowActivities**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="d63ab-120">Select **Solution** from the **Add Reference** list, check the checkbox beside **NumberGuessWorkflowActivities**, and then click **OK**.</span></span>

5. <span data-ttu-id="d63ab-121">Cliquez avec le bouton droit sur **Workflow1.xaml** dans l' **Explorateur de solutions** et choisissez **Supprimer**.</span><span class="sxs-lookup"><span data-stu-id="d63ab-121">Right-click **Workflow1.xaml** in **Solution Explorer** and choose **Delete**.</span></span> <span data-ttu-id="d63ab-122">Cliquez sur **OK** pour confirmer.</span><span class="sxs-lookup"><span data-stu-id="d63ab-122">Click **OK** to confirm.</span></span>

### <a name="to-modify-the-workflow-hosting-code"></a><span data-ttu-id="d63ab-123">Pour modifier le code d'hébergement de workflow</span><span class="sxs-lookup"><span data-stu-id="d63ab-123">To modify the workflow hosting code</span></span>

1. <span data-ttu-id="d63ab-124">Double-cliquez sur **Program.cs** ou sur **Module1.vb** dans l' **Explorateur de solutions** pour afficher le code.</span><span class="sxs-lookup"><span data-stu-id="d63ab-124">Double-click **Program.cs** or **Module1.vb** in **Solution Explorer** to display the code.</span></span>

    > [!TIP]
    > <span data-ttu-id="d63ab-125">Si la fenêtre **Explorateur de solutions** ne s'affiche pas, sélectionnez **Explorateur de solutions** dans le menu **Afficher**.</span><span class="sxs-lookup"><span data-stu-id="d63ab-125">If the **Solution Explorer** window is not displayed, select **Solution Explorer** from the **View** menu.</span></span>

     <span data-ttu-id="d63ab-126">Étant donné que ce projet a été créé à l'aide du modèle **Application console de workflow** , **Program.cs** ou **Module1.vb** contient le code d'hébergement de workflow de base suivant.</span><span class="sxs-lookup"><span data-stu-id="d63ab-126">Because this project was created by using the **Workflow Console Application** template, **Program.cs** or **Module1.vb** contains the following basic workflow hosting code.</span></span>

    ```vb
    ' Create and cache the workflow definition.
    Dim workflow1 As Activity = New Workflow1()
    WorkflowInvoker.Invoke(workflow1)
    ```

    ```csharp
    // Create and cache the workflow definition.
    Activity workflow1 = new Workflow1();
    WorkflowInvoker.Invoke(workflow1);
    ```

     <span data-ttu-id="d63ab-127">Ce code d'hébergement généré utilise <xref:System.Activities.WorkflowInvoker>.</span><span class="sxs-lookup"><span data-stu-id="d63ab-127">This generated hosting code uses <xref:System.Activities.WorkflowInvoker>.</span></span> <span data-ttu-id="d63ab-128"><xref:System.Activities.WorkflowInvoker> offre un moyen simple pour appeler un workflow comme s'il s'agissait d'un appel de méthode et ne peut être utilisé que pour les workflows qui n'utilisent pas la persistance.</span><span class="sxs-lookup"><span data-stu-id="d63ab-128"><xref:System.Activities.WorkflowInvoker> provides a simple way for invoking a workflow as if it were a method call and can be used only for workflows that do not use persistence.</span></span> <span data-ttu-id="d63ab-129"><xref:System.Activities.WorkflowApplication> fournit un modèle plus riche pour exécuter des workflows, qui inclut la notification des événements de cycle de vie, le contrôle d'exécution, la modification de signet et la persistance.</span><span class="sxs-lookup"><span data-stu-id="d63ab-129"><xref:System.Activities.WorkflowApplication> provides a richer model for executing workflows that includes notification of life-cycle events, execution control, bookmark resumption, and persistence.</span></span> <span data-ttu-id="d63ab-130">Cet exemple utilise des signets et <xref:System.Activities.WorkflowApplication> est utilisé pour l'hébergement du workflow.</span><span class="sxs-lookup"><span data-stu-id="d63ab-130">This example uses bookmarks and <xref:System.Activities.WorkflowApplication> is used for hosting the workflow.</span></span> <span data-ttu-id="d63ab-131">Ajoutez l'instruction `using` ou **Imports** suivante dans la partie supérieure de **Program.cs** ou **Module1.vb** sous les instructions **using** ou **Imports** existantes.</span><span class="sxs-lookup"><span data-stu-id="d63ab-131">Add the following `using` or **Imports** statement at the top of **Program.cs** or **Module1.vb** below the existing **using** or **Imports** statements.</span></span>

    ```vb
    Imports NumberGuessWorkflowActivities
    Imports System.Threading
    ```

    ```csharp
    using NumberGuessWorkflowActivities;
    using System.Threading;
    ```

     <span data-ttu-id="d63ab-132">Remplacez les lignes de code qui utilisent <xref:System.Activities.WorkflowInvoker> par le code d'hébergement <xref:System.Activities.WorkflowApplication> de base suivant.</span><span class="sxs-lookup"><span data-stu-id="d63ab-132">Replace the lines of code that use <xref:System.Activities.WorkflowInvoker> with the following basic <xref:System.Activities.WorkflowApplication> hosting code.</span></span> <span data-ttu-id="d63ab-133">Cet exemple de code d'hébergement montre les étapes de base pour l'hébergement et l'appel d'un workflow, mais ne contient pas encore les fonctionnalités pour exécuter avec succès le workflow à partir de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="d63ab-133">This sample hosting code demonstrates the basic steps for hosting and invoking a workflow, but does not yet contain the functionality to successfully run the workflow from this topic.</span></span> <span data-ttu-id="d63ab-134">Au cours des étapes suivantes, le code de base est modifié et des fonctionnalités supplémentaires sont ajoutées jusqu'à ce que l'application soit terminée.</span><span class="sxs-lookup"><span data-stu-id="d63ab-134">In the following steps, this basic code is modified and additional features are added until the application is complete.</span></span>

    > [!NOTE]
    > <span data-ttu-id="d63ab-135">Remplacez `Workflow1` dans ces exemples par `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`ou `StateMachineNumberGuessWorkflow`, en fonction du workflow que vous avez effectué à l’étape précédente [How to: Create a Workflow](how-to-create-a-workflow.md) .</span><span class="sxs-lookup"><span data-stu-id="d63ab-135">Please replace `Workflow1` in these examples with `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, or `StateMachineNumberGuessWorkflow`, depending on which workflow you completed in the previous [How to: Create a Workflow](how-to-create-a-workflow.md) step.</span></span> <span data-ttu-id="d63ab-136">Si vous ne substituez pas `Workflow1` , vous obtiendrez des erreurs de build lors de la génération ou de l'exécution du workflow.</span><span class="sxs-lookup"><span data-stu-id="d63ab-136">If you do not replace `Workflow1` then you will get build errors when you try and build or run the workflow.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#4](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/extrasnippets.cs#4)]
     [!code-vb[CFX_WF_GettingStarted#4](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/extrasnippets.vb#4)]

     <span data-ttu-id="d63ab-137">Ce code crée un <xref:System.Activities.WorkflowApplication>, s'abonne à trois événements de cycle de vie du workflow, démarre le workflow avec un appel à la méthode <xref:System.Activities.WorkflowApplication.Run%2A>, puis attend que le workflow soit terminé.</span><span class="sxs-lookup"><span data-stu-id="d63ab-137">This code creates a <xref:System.Activities.WorkflowApplication>, subscribes to three workflow life-cycle events, starts the workflow with a call to <xref:System.Activities.WorkflowApplication.Run%2A>, and then waits for the workflow to complete.</span></span> <span data-ttu-id="d63ab-138">Lorsque le workflow est terminé, le <xref:System.Threading.AutoResetEvent> est défini et l'application hôte se termine.</span><span class="sxs-lookup"><span data-stu-id="d63ab-138">When the workflow completes, the <xref:System.Threading.AutoResetEvent> is set and the host application completes.</span></span>

### <a name="to-set-input-arguments-of-a-workflow"></a><span data-ttu-id="d63ab-139">Pour définir des arguments d'entrée d'un workflow</span><span class="sxs-lookup"><span data-stu-id="d63ab-139">To set input arguments of a workflow</span></span>

1. <span data-ttu-id="d63ab-140">Ajoutez l'instruction suivante dans la partie supérieure de **Program.cs** ou **Module1.vb** sous les instructions `using` ou `Imports` existantes.</span><span class="sxs-lookup"><span data-stu-id="d63ab-140">Add the following statement at the top of **Program.cs** or **Module1.vb** below the existing `using` or `Imports` statements.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#5](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#5)]
     [!code-vb[CFX_WF_GettingStarted#5](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#5)]

2. <span data-ttu-id="d63ab-141">Remplacez la ligne de code qui crée le <xref:System.Activities.WorkflowApplication> par le code suivant qui crée et passe un dictionnaire de paramètres au workflow lorsqu'il est créé.</span><span class="sxs-lookup"><span data-stu-id="d63ab-141">Replace the line of code that creates the new <xref:System.Activities.WorkflowApplication> with the following code that creates and passes a dictionary of parameters to the workflow when it is created.</span></span>

    > [!NOTE]
    > <span data-ttu-id="d63ab-142">Remplacez `Workflow1` dans ces exemples par `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`ou `StateMachineNumberGuessWorkflow`, en fonction du workflow que vous avez effectué à l’étape précédente [How to: Create a Workflow](how-to-create-a-workflow.md) .</span><span class="sxs-lookup"><span data-stu-id="d63ab-142">Please replace `Workflow1` in these examples with `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, or `StateMachineNumberGuessWorkflow`, depending on which workflow you completed in the previous [How to: Create a Workflow](how-to-create-a-workflow.md) step.</span></span> <span data-ttu-id="d63ab-143">Si vous ne substituez pas `Workflow1` , vous obtiendrez des erreurs de build lors de la génération ou de l'exécution du workflow.</span><span class="sxs-lookup"><span data-stu-id="d63ab-143">If you do not replace `Workflow1` then you will get build errors when you try and build or run the workflow.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#6](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#6)]
     [!code-vb[CFX_WF_GettingStarted#6](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#6)]

     <span data-ttu-id="d63ab-144">Ce dictionnaire contient un élément avec une clé de `MaxNumber`.</span><span class="sxs-lookup"><span data-stu-id="d63ab-144">This dictionary contains one element with a key of `MaxNumber`.</span></span> <span data-ttu-id="d63ab-145">Les clés du dictionnaire d'entrée correspondent aux arguments d'entrée sur l'activité racine du workflow.</span><span class="sxs-lookup"><span data-stu-id="d63ab-145">Keys in the input dictionary correspond to input arguments on the root activity of the workflow.</span></span> <span data-ttu-id="d63ab-146">`MaxNumber` est utilisé par le workflow pour déterminer la limite supérieure pour le nombre généré de manière aléatoire.</span><span class="sxs-lookup"><span data-stu-id="d63ab-146">`MaxNumber` is used by the workflow to determine the upper bound for the randomly generated number.</span></span>

### <a name="to-retrieve-output-arguments-of-a-workflow"></a><span data-ttu-id="d63ab-147">Pour récupérer des arguments de sortie d'un workflow</span><span class="sxs-lookup"><span data-stu-id="d63ab-147">To retrieve output arguments of a workflow</span></span>

1. <span data-ttu-id="d63ab-148">Modifiez le gestionnaire <xref:System.Activities.WorkflowApplication.Completed%2A> pour récupérer et afficher le nombre de tours utilisé par le workflow.</span><span class="sxs-lookup"><span data-stu-id="d63ab-148">Modify the <xref:System.Activities.WorkflowApplication.Completed%2A> handler to retrieve and display the number of turns used by the workflow.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#7](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#7)]
     [!code-vb[CFX_WF_GettingStarted#7](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#7)]

### <a name="to-resume-a-bookmark"></a><span data-ttu-id="d63ab-149">Pour reprendre un signet</span><span class="sxs-lookup"><span data-stu-id="d63ab-149">To resume a bookmark</span></span>

1. <span data-ttu-id="d63ab-150">Ajoutez le code suivant en haut de la méthode `Main` , juste après la déclaration <xref:System.Threading.AutoResetEvent> existante.</span><span class="sxs-lookup"><span data-stu-id="d63ab-150">Add the following code at the top of the `Main` method just after the existing <xref:System.Threading.AutoResetEvent> declaration.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#8](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#8)]
     [!code-vb[CFX_WF_GettingStarted#8](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#8)]

2. <span data-ttu-id="d63ab-151">Ajoutez le gestionnaire <xref:System.Activities.WorkflowApplication.Idle%2A> suivant, juste en dessous des trois gestionnaires de cycle de vie du workflow existants dans `Main`.</span><span class="sxs-lookup"><span data-stu-id="d63ab-151">Add the following <xref:System.Activities.WorkflowApplication.Idle%2A> handler just below the existing three workflow life-cycle handlers in `Main`.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#9](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#9)]
     [!code-vb[CFX_WF_GettingStarted#9](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#9)]

     <span data-ttu-id="d63ab-152">Chaque fois que le workflow devient inactif, en attendant la prochaine estimation, ce gestionnaire est appelé et le `idleAction` <xref:System.Threading.AutoResetEvent> est défini.</span><span class="sxs-lookup"><span data-stu-id="d63ab-152">Each time the workflow becomes idle waiting for the next guess, this handler is called and the `idleAction` <xref:System.Threading.AutoResetEvent> is set.</span></span> <span data-ttu-id="d63ab-153">Le code de l'étape suivante utilise `idleEvent` et `syncEvent` pour déterminer si le workflow attend l'estimation suivante ou s'il est terminé.</span><span class="sxs-lookup"><span data-stu-id="d63ab-153">The code in the following step uses `idleEvent` and `syncEvent` to determine whether the workflow is waiting for the next guess or is complete.</span></span>

    > [!NOTE]
    > <span data-ttu-id="d63ab-154">Dans cet exemple, l'application hôte utilise des événements à réinitialisation automatique dans les gestionnaires <xref:System.Activities.WorkflowApplication.Completed%2A> et <xref:System.Activities.WorkflowApplication.Idle%2A> pour synchroniser l'application hôte avec la progression du workflow.</span><span class="sxs-lookup"><span data-stu-id="d63ab-154">In this example, the host application uses auto-reset events in the <xref:System.Activities.WorkflowApplication.Completed%2A> and <xref:System.Activities.WorkflowApplication.Idle%2A> handlers to synchronize the host application with the progress of the workflow.</span></span> <span data-ttu-id="d63ab-155">Il n'est pas nécessaire de bloquer et d'attendre que le workflow devienne inactif avant de reprendre un signet mais, dans cet exemple, les événements de synchronisation sont nécessaires afin que l'hôte sache si le workflow est terminé ou s'il attend une ou plusieurs autres entrées d'utilisateur à l'aide de <xref:System.Activities.Bookmark>.</span><span class="sxs-lookup"><span data-stu-id="d63ab-155">It is not necessary to block and wait for the workflow to become idle before resuming a bookmark, but in this example the synchronization events are required so the host knows whether the workflow is complete or whether it is waiting on more user input by using the <xref:System.Activities.Bookmark>.</span></span> <span data-ttu-id="d63ab-156">Pour plus d’informations, consultez [signets](bookmarks.md).</span><span class="sxs-lookup"><span data-stu-id="d63ab-156">For more information, see [Bookmarks](bookmarks.md).</span></span>

3. <span data-ttu-id="d63ab-157">Supprimez l'appel à `WaitOne`et remplacez-le par du code pour recueillir l'entrée de l'utilisateur et reprendre le <xref:System.Activities.Bookmark>.</span><span class="sxs-lookup"><span data-stu-id="d63ab-157">Remove the call to `WaitOne`, and replace it with code to gather input from the user and resume the <xref:System.Activities.Bookmark>.</span></span>

     <span data-ttu-id="d63ab-158">Supprimez la ligne de code suivante.</span><span class="sxs-lookup"><span data-stu-id="d63ab-158">Remove the following line of code.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#10](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/extrasnippets.cs#10)]
     [!code-vb[CFX_WF_GettingStarted#10](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/extrasnippets.vb#10)]

     <span data-ttu-id="d63ab-159">Remplacez-la par l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="d63ab-159">Replace it with the following example.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#11](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#11)]
     [!code-vb[CFX_WF_GettingStarted#11](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#11)]

## <a name="to-build-and-run-the-application"></a><a name="BKMK_ToRunTheApplication"></a> <span data-ttu-id="d63ab-160">Pour générer et exécuter l’application</span><span class="sxs-lookup"><span data-stu-id="d63ab-160">To build and run the application</span></span>

1. <span data-ttu-id="d63ab-161">Cliquez avec le bouton droit sur **NumberGuessWorkflowHost** dans l' **Explorateur de solutions** , puis sélectionnez **Définir comme projet de démarrage**.</span><span class="sxs-lookup"><span data-stu-id="d63ab-161">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and select **Set as StartUp Project**.</span></span>

2. <span data-ttu-id="d63ab-162">Appuyez sur Ctrl+F5 pour générer et exécuter l'application.</span><span class="sxs-lookup"><span data-stu-id="d63ab-162">Press CTRL+F5 to build and run the application.</span></span> <span data-ttu-id="d63ab-163">Essayez de deviner le nombre en aussi peu de tours que possible.</span><span class="sxs-lookup"><span data-stu-id="d63ab-163">Try to guess the number in as few turns as possible.</span></span>

     <span data-ttu-id="d63ab-164">Pour essayer l'application avec un des autres styles de workflow, remplacez `Workflow1` dans le code qui crée le <xref:System.Activities.WorkflowApplication> par `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, ou `StateMachineNumberGuessWorkflow`, en fonction du style de workflow souhaité.</span><span class="sxs-lookup"><span data-stu-id="d63ab-164">To try the application with one of the other styles of workflow, replace `Workflow1` in the code that creates the <xref:System.Activities.WorkflowApplication> with `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, or `StateMachineNumberGuessWorkflow`, depending on which workflow style you desire.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#6](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#6)]
     [!code-vb[CFX_WF_GettingStarted#6](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#6)]

     <span data-ttu-id="d63ab-165">Pour obtenir des instructions sur la façon d’ajouter la persistance à une application de workflow, consultez la rubrique suivante, [How to: Create and Run a Long Running Workflow](how-to-create-and-run-a-long-running-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="d63ab-165">For instructions about how to add persistence to a workflow application, see the next topic, [How to: Create and Run a Long Running Workflow](how-to-create-and-run-a-long-running-workflow.md).</span></span>

## <a name="example"></a><span data-ttu-id="d63ab-166"> Exemple</span><span class="sxs-lookup"><span data-stu-id="d63ab-166">Example</span></span>

 <span data-ttu-id="d63ab-167">L'exemple suivant constitue l'intégralité du code de la méthode `Main` .</span><span class="sxs-lookup"><span data-stu-id="d63ab-167">The following example is the complete code listing for the `Main` method.</span></span>

> [!NOTE]
> <span data-ttu-id="d63ab-168">Remplacez `Workflow1` dans ces exemples par `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`ou `StateMachineNumberGuessWorkflow`, en fonction du workflow que vous avez effectué à l’étape précédente [How to: Create a Workflow](how-to-create-a-workflow.md) .</span><span class="sxs-lookup"><span data-stu-id="d63ab-168">Please replace `Workflow1` in these examples with `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, or `StateMachineNumberGuessWorkflow`, depending on which workflow you completed in the previous [How to: Create a Workflow](how-to-create-a-workflow.md) step.</span></span> <span data-ttu-id="d63ab-169">Si vous ne substituez pas `Workflow1` , vous obtiendrez des erreurs de build lors de la génération ou de l'exécution du workflow.</span><span class="sxs-lookup"><span data-stu-id="d63ab-169">If you do not replace `Workflow1` then you will get build errors when you try and build or run the workflow.</span></span>

 [!code-csharp[CFX_WF_GettingStarted#12](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#12)]
 [!code-vb[CFX_WF_GettingStarted#12](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#12)]

## <a name="see-also"></a><span data-ttu-id="d63ab-170">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d63ab-170">See also</span></span>

- <xref:System.Activities.WorkflowApplication>
- <xref:System.Activities.Bookmark>
- [<span data-ttu-id="d63ab-171">Programmation Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="d63ab-171">Windows Workflow Foundation Programming</span></span>](programming.md)
- [<span data-ttu-id="d63ab-172">Didacticiel de mise en route</span><span class="sxs-lookup"><span data-stu-id="d63ab-172">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
- [<span data-ttu-id="d63ab-173">Procédure : créer un workflow</span><span class="sxs-lookup"><span data-stu-id="d63ab-173">How to: Create a Workflow</span></span>](how-to-create-a-workflow.md)
- [<span data-ttu-id="d63ab-174">Procédure : créer et exécuter un workflow durable</span><span class="sxs-lookup"><span data-stu-id="d63ab-174">How to: Create and Run a Long Running Workflow</span></span>](how-to-create-and-run-a-long-running-workflow.md)
- [<span data-ttu-id="d63ab-175">Attente d'une entrée dans un flux de travail</span><span class="sxs-lookup"><span data-stu-id="d63ab-175">Waiting for Input in a Workflow</span></span>](waiting-for-input-in-a-workflow.md)
- [<span data-ttu-id="d63ab-176">Hébergement de workflows</span><span class="sxs-lookup"><span data-stu-id="d63ab-176">Hosting Workflows</span></span>](hosting-workflows.md)

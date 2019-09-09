---
title: 'Procédure : exécuter un workflow'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f814ff82-fe2b-4614-aebb-b768c3e61179
ms.openlocfilehash: 07f0e5dc232411633626add460ffc29cc7a79d81
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044351"
---
# <a name="how-to-run-a-workflow"></a><span data-ttu-id="a099a-102">Procédure : exécuter un workflow</span><span class="sxs-lookup"><span data-stu-id="a099a-102">How to: Run a Workflow</span></span>
<span data-ttu-id="a099a-103">Cette rubrique est une suite de la Windows Workflow Foundation prise en main didacticiel et explique comment créer un hôte de workflow et exécuter le workflow défini dans la procédure précédente [: Créer une rubrique](how-to-create-a-workflow.md) de Workflow.</span><span class="sxs-lookup"><span data-stu-id="a099a-103">This topic is a continuation of the Windows Workflow Foundation Getting Started tutorial and discusses how to create a workflow host and run the workflow defined in the previous [How to: Create a Workflow](how-to-create-a-workflow.md) topic.</span></span>

> [!NOTE]
> <span data-ttu-id="a099a-104">Chaque rubrique du didacticiel de mise en route dépend des rubriques précédentes.</span><span class="sxs-lookup"><span data-stu-id="a099a-104">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="a099a-105">Pour suivre cette rubrique, vous devez d' [abord effectuer les opérations suivantes : Créer une activité](how-to-create-an-activity.md) et [Comment : Créer un flux](how-to-create-a-workflow.md)de travail.</span><span class="sxs-lookup"><span data-stu-id="a099a-105">To complete this topic you must first complete [How to: Create an Activity](how-to-create-an-activity.md) and [How to: Create a Workflow](how-to-create-a-workflow.md).</span></span>

> [!NOTE]
> <span data-ttu-id="a099a-106">Pour télécharger une version complète du didacticiel, consultez [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976)(Windows Workflow Foundation (WF45) - Didacticiel de mise en route).</span><span class="sxs-lookup"><span data-stu-id="a099a-106">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
### <a name="to-create-the-workflow-host-project"></a><span data-ttu-id="a099a-107">Pour créer le projet d'hôte du workflow</span><span class="sxs-lookup"><span data-stu-id="a099a-107">To create the workflow host project</span></span>  
  
1. <span data-ttu-id="a099a-108">Ouvrez la solution à partir de [la procédure précédente Comment : Créez une rubrique](how-to-create-an-activity.md) d’activité à l’aide de Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="a099a-108">Open the solution from the previous [How to: Create an Activity](how-to-create-an-activity.md) topic by using Visual Studio 2012.</span></span>  
  
2. <span data-ttu-id="a099a-109">Dans l' **Explorateur de solutions** , cliquez avec le bouton droit sur la solution **WF45GettingStartedTutorial** , puis sélectionnez **Ajouter**, **Nouveau projet**.</span><span class="sxs-lookup"><span data-stu-id="a099a-109">Right-click the **WF45GettingStartedTutorial** solution in **Solution Explorer** and select **Add**, **New Project**.</span></span>  
  
    > [!TIP]
    > <span data-ttu-id="a099a-110">Si la fenêtre **Explorateur de solutions** n'est pas affichée, sélectionnez **Explorateur de solutions** dans le menu **Affichage** .</span><span class="sxs-lookup"><span data-stu-id="a099a-110">If the **Solution Explorer** window is not displayed, select **Solution Explorer** from the **View** menu.</span></span>

3. <span data-ttu-id="a099a-111">Dans le nœud **Installé** , sélectionnez **Visual C#** , **Workflow** (ou **Visual Basic**, **Workflow**).</span><span class="sxs-lookup"><span data-stu-id="a099a-111">In the **Installed** node, select **Visual C#**, **Workflow** (or **Visual Basic**, **Workflow**).</span></span>

    > [!NOTE]
    > <span data-ttu-id="a099a-112">En fonction du langage de programmation qui est configuré comme langage principal dans Visual Studio, le nœud **Visual C#** ou **Visual Basic** peut se trouver sous le nœud **Autres langages** dans le nœud **Installé** .</span><span class="sxs-lookup"><span data-stu-id="a099a-112">Depending on which programming language is configured as the primary language in Visual Studio, the **Visual C#** or **Visual Basic** node may be under the **Other Languages** node in the **Installed** node.</span></span>

     <span data-ttu-id="a099a-113">Dans la liste déroulante de la version du .NET Framework, vérifiez que **.NET Framework 4.5** est sélectionné.</span><span class="sxs-lookup"><span data-stu-id="a099a-113">Ensure that **.NET Framework 4.5** is selected in the .NET Framework version drop-down list.</span></span> <span data-ttu-id="a099a-114">Dans la liste **Workflow** , sélectionnez **Application console de workflow** .</span><span class="sxs-lookup"><span data-stu-id="a099a-114">Select **Workflow Console Application** from the **Workflow** list.</span></span> <span data-ttu-id="a099a-115">Dans la zone `NumberGuessWorkflowHost` Nom **, tapez** et cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="a099a-115">Type `NumberGuessWorkflowHost` into the **Name** box and click **OK**.</span></span> <span data-ttu-id="a099a-116">Une application de workflow de démarrage est ainsi créée, ainsi qu'un support d'hébergement de workflow de base.</span><span class="sxs-lookup"><span data-stu-id="a099a-116">This creates a starter workflow application with basic workflow hosting support.</span></span> <span data-ttu-id="a099a-117">Le code d'hébergement de base est modifié et sert à exécuter l'application de workflow.</span><span class="sxs-lookup"><span data-stu-id="a099a-117">This basic hosting code is modified and used to run the workflow application.</span></span>

4. <span data-ttu-id="a099a-118">Cliquez avec le bouton droit sur le projet **NumberGuessWorkflowHost** récemment ajouté dans l' **Explorateur de solutions** , puis sélectionnez **Ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="a099a-118">Right-click the newly added **NumberGuessWorkflowHost** project in **Solution Explorer** and select **Add Reference**.</span></span> <span data-ttu-id="a099a-119">Dans la liste **Ajouter une référence** , sélectionnez **Solution** , activez la case à cocher en regard de **NumberGuessWorkflowActivities**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="a099a-119">Select **Solution** from the **Add Reference** list, check the checkbox beside **NumberGuessWorkflowActivities**, and then click **OK**.</span></span>

5. <span data-ttu-id="a099a-120">Cliquez avec le bouton droit sur **Workflow1.xaml** dans l' **Explorateur de solutions** et choisissez **Supprimer**.</span><span class="sxs-lookup"><span data-stu-id="a099a-120">Right-click **Workflow1.xaml** in **Solution Explorer** and choose **Delete**.</span></span> <span data-ttu-id="a099a-121">Pour confirmer, cliquez sur **OK** .</span><span class="sxs-lookup"><span data-stu-id="a099a-121">Click **OK** to confirm.</span></span>

### <a name="to-modify-the-workflow-hosting-code"></a><span data-ttu-id="a099a-122">Pour modifier le code d'hébergement de workflow</span><span class="sxs-lookup"><span data-stu-id="a099a-122">To modify the workflow hosting code</span></span>

1. <span data-ttu-id="a099a-123">Double-cliquez sur **Program.cs** ou sur **Module1.vb** dans l' **Explorateur de solutions** pour afficher le code.</span><span class="sxs-lookup"><span data-stu-id="a099a-123">Double-click **Program.cs** or **Module1.vb** in **Solution Explorer** to display the code.</span></span>

    > [!TIP]
    > <span data-ttu-id="a099a-124">Si la fenêtre **Explorateur de solutions** n'est pas affichée, sélectionnez **Explorateur de solutions** dans le menu **Affichage** .</span><span class="sxs-lookup"><span data-stu-id="a099a-124">If the **Solution Explorer** window is not displayed, select **Solution Explorer** from the **View** menu.</span></span>

     <span data-ttu-id="a099a-125">Étant donné que ce projet a été créé à l'aide du modèle **Application console de workflow** , **Program.cs** ou **Module1.vb** contient le code d'hébergement de workflow de base suivant.</span><span class="sxs-lookup"><span data-stu-id="a099a-125">Because this project was created by using the **Workflow Console Application** template, **Program.cs** or **Module1.vb** contains the following basic workflow hosting code.</span></span>

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

     <span data-ttu-id="a099a-126">Ce code d'hébergement généré utilise <xref:System.Activities.WorkflowInvoker>.</span><span class="sxs-lookup"><span data-stu-id="a099a-126">This generated hosting code uses <xref:System.Activities.WorkflowInvoker>.</span></span> <span data-ttu-id="a099a-127"><xref:System.Activities.WorkflowInvoker> offre un moyen simple pour appeler un workflow comme s'il s'agissait d'un appel de méthode et ne peut être utilisé que pour les workflows qui n'utilisent pas la persistance.</span><span class="sxs-lookup"><span data-stu-id="a099a-127"><xref:System.Activities.WorkflowInvoker> provides a simple way for invoking a workflow as if it were a method call and can be used only for workflows that do not use persistence.</span></span> <span data-ttu-id="a099a-128"><xref:System.Activities.WorkflowApplication> fournit un modèle plus riche pour exécuter des workflows, qui inclut la notification des événements de cycle de vie, le contrôle d'exécution, la modification de signet et la persistance.</span><span class="sxs-lookup"><span data-stu-id="a099a-128"><xref:System.Activities.WorkflowApplication> provides a richer model for executing workflows that includes notification of life-cycle events, execution control, bookmark resumption, and persistence.</span></span> <span data-ttu-id="a099a-129">Cet exemple utilise des signets et <xref:System.Activities.WorkflowApplication> est utilisé pour l'hébergement du workflow.</span><span class="sxs-lookup"><span data-stu-id="a099a-129">This example uses bookmarks and <xref:System.Activities.WorkflowApplication> is used for hosting the workflow.</span></span> <span data-ttu-id="a099a-130">Ajoutez l'instruction `using` ou **Imports** suivante dans la partie supérieure de **Program.cs** ou **Module1.vb** sous les instructions **using** ou **Imports** existantes.</span><span class="sxs-lookup"><span data-stu-id="a099a-130">Add the following `using` or **Imports** statement at the top of **Program.cs** or **Module1.vb** below the existing **using** or **Imports** statements.</span></span>

    ```vb
    Imports NumberGuessWorkflowActivities
    Imports System.Threading
    ```

    ```csharp
    using NumberGuessWorkflowActivities;
    using System.Threading;
    ```

     <span data-ttu-id="a099a-131">Remplacez les lignes de code qui utilisent <xref:System.Activities.WorkflowInvoker> par le code d'hébergement <xref:System.Activities.WorkflowApplication> de base suivant.</span><span class="sxs-lookup"><span data-stu-id="a099a-131">Replace the lines of code that use <xref:System.Activities.WorkflowInvoker> with the following basic <xref:System.Activities.WorkflowApplication> hosting code.</span></span> <span data-ttu-id="a099a-132">Cet exemple de code d'hébergement montre les étapes de base pour l'hébergement et l'appel d'un workflow, mais ne contient pas encore les fonctionnalités pour exécuter avec succès le workflow à partir de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="a099a-132">This sample hosting code demonstrates the basic steps for hosting and invoking a workflow, but does not yet contain the functionality to successfully run the workflow from this topic.</span></span> <span data-ttu-id="a099a-133">Au cours des étapes suivantes, le code de base est modifié et des fonctionnalités supplémentaires sont ajoutées jusqu'à ce que l'application soit terminée.</span><span class="sxs-lookup"><span data-stu-id="a099a-133">In the following steps, this basic code is modified and additional features are added until the application is complete.</span></span>

    > [!NOTE]
    > <span data-ttu-id="a099a-134">Remplacez `Workflow1` dans ces exemples par `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`ou `StateMachineNumberGuessWorkflow`, selon le flux de travail que vous avez effectué dans la procédure [précédente : Créer une étape](how-to-create-a-workflow.md) de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="a099a-134">Please replace `Workflow1` in these examples with `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, or `StateMachineNumberGuessWorkflow`, depending on which workflow you completed in the previous [How to: Create a Workflow](how-to-create-a-workflow.md) step.</span></span> <span data-ttu-id="a099a-135">Si vous ne substituez pas `Workflow1` , vous obtiendrez des erreurs de build lors de la génération ou de l'exécution du workflow.</span><span class="sxs-lookup"><span data-stu-id="a099a-135">If you do not replace `Workflow1` then you will get build errors when you try and build or run the workflow.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#4](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/extrasnippets.cs#4)]
     [!code-vb[CFX_WF_GettingStarted#4](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/extrasnippets.vb#4)]

     <span data-ttu-id="a099a-136">Ce code crée un <xref:System.Activities.WorkflowApplication>, s'abonne à trois événements de cycle de vie du workflow, démarre le workflow avec un appel à la méthode <xref:System.Activities.WorkflowApplication.Run%2A>, puis attend que le workflow soit terminé.</span><span class="sxs-lookup"><span data-stu-id="a099a-136">This code creates a <xref:System.Activities.WorkflowApplication>, subscribes to three workflow life-cycle events, starts the workflow with a call to <xref:System.Activities.WorkflowApplication.Run%2A>, and then waits for the workflow to complete.</span></span> <span data-ttu-id="a099a-137">Lorsque le workflow est terminé, le <xref:System.Threading.AutoResetEvent> est défini et l'application hôte se termine.</span><span class="sxs-lookup"><span data-stu-id="a099a-137">When the workflow completes, the <xref:System.Threading.AutoResetEvent> is set and the host application completes.</span></span>

### <a name="to-set-input-arguments-of-a-workflow"></a><span data-ttu-id="a099a-138">Pour définir des arguments d'entrée d'un workflow</span><span class="sxs-lookup"><span data-stu-id="a099a-138">To set input arguments of a workflow</span></span>

1. <span data-ttu-id="a099a-139">Ajoutez l'instruction suivante dans la partie supérieure de **Program.cs** ou **Module1.vb** sous les instructions `using` ou `Imports` existantes.</span><span class="sxs-lookup"><span data-stu-id="a099a-139">Add the following statement at the top of **Program.cs** or **Module1.vb** below the existing `using` or `Imports` statements.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#5](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#5)]
     [!code-vb[CFX_WF_GettingStarted#5](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#5)]

2. <span data-ttu-id="a099a-140">Remplacez la ligne de code qui crée le <xref:System.Activities.WorkflowApplication> par le code suivant qui crée et passe un dictionnaire de paramètres au workflow lorsqu'il est créé.</span><span class="sxs-lookup"><span data-stu-id="a099a-140">Replace the line of code that creates the new <xref:System.Activities.WorkflowApplication> with the following code that creates and passes a dictionary of parameters to the workflow when it is created.</span></span>

    > [!NOTE]
    > <span data-ttu-id="a099a-141">Remplacez `Workflow1` dans ces exemples par `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`ou `StateMachineNumberGuessWorkflow`, selon le flux de travail que vous avez effectué dans la procédure [précédente : Créer une étape](how-to-create-a-workflow.md) de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="a099a-141">Please replace `Workflow1` in these examples with `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, or `StateMachineNumberGuessWorkflow`, depending on which workflow you completed in the previous [How to: Create a Workflow](how-to-create-a-workflow.md) step.</span></span> <span data-ttu-id="a099a-142">Si vous ne substituez pas `Workflow1` , vous obtiendrez des erreurs de build lors de la génération ou de l'exécution du workflow.</span><span class="sxs-lookup"><span data-stu-id="a099a-142">If you do not replace `Workflow1` then you will get build errors when you try and build or run the workflow.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#6](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#6)]
     [!code-vb[CFX_WF_GettingStarted#6](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#6)]

     <span data-ttu-id="a099a-143">Ce dictionnaire contient un élément avec une clé de `MaxNumber`.</span><span class="sxs-lookup"><span data-stu-id="a099a-143">This dictionary contains one element with a key of `MaxNumber`.</span></span> <span data-ttu-id="a099a-144">Les clés du dictionnaire d'entrée correspondent aux arguments d'entrée sur l'activité racine du workflow.</span><span class="sxs-lookup"><span data-stu-id="a099a-144">Keys in the input dictionary correspond to input arguments on the root activity of the workflow.</span></span> <span data-ttu-id="a099a-145">`MaxNumber` est utilisé par le workflow pour déterminer la limite supérieure pour le nombre généré de manière aléatoire.</span><span class="sxs-lookup"><span data-stu-id="a099a-145">`MaxNumber` is used by the workflow to determine the upper bound for the randomly generated number.</span></span>

### <a name="to-retrieve-output-arguments-of-a-workflow"></a><span data-ttu-id="a099a-146">Pour récupérer des arguments de sortie d'un workflow</span><span class="sxs-lookup"><span data-stu-id="a099a-146">To retrieve output arguments of a workflow</span></span>

1. <span data-ttu-id="a099a-147">Modifiez le gestionnaire <xref:System.Activities.WorkflowApplication.Completed%2A> pour récupérer et afficher le nombre de tours utilisé par le workflow.</span><span class="sxs-lookup"><span data-stu-id="a099a-147">Modify the <xref:System.Activities.WorkflowApplication.Completed%2A> handler to retrieve and display the number of turns used by the workflow.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#7](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#7)]
     [!code-vb[CFX_WF_GettingStarted#7](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#7)]

### <a name="to-resume-a-bookmark"></a><span data-ttu-id="a099a-148">Pour reprendre un signet</span><span class="sxs-lookup"><span data-stu-id="a099a-148">To resume a bookmark</span></span>

1. <span data-ttu-id="a099a-149">Ajoutez le code suivant en haut de la méthode `Main` , juste après la déclaration <xref:System.Threading.AutoResetEvent> existante.</span><span class="sxs-lookup"><span data-stu-id="a099a-149">Add the following code at the top of the `Main` method just after the existing <xref:System.Threading.AutoResetEvent> declaration.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#8](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#8)]
     [!code-vb[CFX_WF_GettingStarted#8](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#8)]

2. <span data-ttu-id="a099a-150">Ajoutez le gestionnaire <xref:System.Activities.WorkflowApplication.Idle%2A> suivant, juste en dessous des trois gestionnaires de cycle de vie du workflow existants dans `Main`.</span><span class="sxs-lookup"><span data-stu-id="a099a-150">Add the following <xref:System.Activities.WorkflowApplication.Idle%2A> handler just below the existing three workflow life-cycle handlers in `Main`.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#9](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#9)]
     [!code-vb[CFX_WF_GettingStarted#9](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#9)]

     <span data-ttu-id="a099a-151">Chaque fois que le workflow devient inactif, en attendant la prochaine estimation, ce gestionnaire est `idleAction` appelé et le <xref:System.Threading.AutoResetEvent> est défini.</span><span class="sxs-lookup"><span data-stu-id="a099a-151">Each time the workflow becomes idle waiting for the next guess, this handler is called and the `idleAction` <xref:System.Threading.AutoResetEvent> is set.</span></span> <span data-ttu-id="a099a-152">Le code de l'étape suivante utilise `idleEvent` et `syncEvent` pour déterminer si le workflow attend l'estimation suivante ou s'il est terminé.</span><span class="sxs-lookup"><span data-stu-id="a099a-152">The code in the following step uses `idleEvent` and `syncEvent` to determine whether the workflow is waiting for the next guess or is complete.</span></span>

    > [!NOTE]
    > <span data-ttu-id="a099a-153">Dans cet exemple, l'application hôte utilise des événements à réinitialisation automatique dans les gestionnaires <xref:System.Activities.WorkflowApplication.Completed%2A> et <xref:System.Activities.WorkflowApplication.Idle%2A> pour synchroniser l'application hôte avec la progression du workflow.</span><span class="sxs-lookup"><span data-stu-id="a099a-153">In this example, the host application uses auto-reset events in the <xref:System.Activities.WorkflowApplication.Completed%2A> and <xref:System.Activities.WorkflowApplication.Idle%2A> handlers to synchronize the host application with the progress of the workflow.</span></span> <span data-ttu-id="a099a-154">Il n'est pas nécessaire de bloquer et d'attendre que le workflow devienne inactif avant de reprendre un signet mais, dans cet exemple, les événements de synchronisation sont nécessaires afin que l'hôte sache si le workflow est terminé ou s'il attend une ou plusieurs autres entrées d'utilisateur à l'aide de <xref:System.Activities.Bookmark>.</span><span class="sxs-lookup"><span data-stu-id="a099a-154">It is not necessary to block and wait for the workflow to become idle before resuming a bookmark, but in this example the synchronization events are required so the host knows whether the workflow is complete or whether it is waiting on more user input by using the <xref:System.Activities.Bookmark>.</span></span> <span data-ttu-id="a099a-155">Pour plus d’informations, consultez [signets](bookmarks.md).</span><span class="sxs-lookup"><span data-stu-id="a099a-155">For more information, see [Bookmarks](bookmarks.md).</span></span>

3. <span data-ttu-id="a099a-156">Supprimez l'appel à `WaitOne`et remplacez-le par du code pour recueillir l'entrée de l'utilisateur et reprendre le <xref:System.Activities.Bookmark>.</span><span class="sxs-lookup"><span data-stu-id="a099a-156">Remove the call to `WaitOne`, and replace it with code to gather input from the user and resume the <xref:System.Activities.Bookmark>.</span></span>

     <span data-ttu-id="a099a-157">Supprimez la ligne de code suivante.</span><span class="sxs-lookup"><span data-stu-id="a099a-157">Remove the following line of code.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#10](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/extrasnippets.cs#10)]
     [!code-vb[CFX_WF_GettingStarted#10](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/extrasnippets.vb#10)]

     <span data-ttu-id="a099a-158">Remplacez-la par l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="a099a-158">Replace it with the following example.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#11](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#11)]
     [!code-vb[CFX_WF_GettingStarted#11](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#11)]

## <a name="BKMK_ToRunTheApplication"></a> <span data-ttu-id="a099a-159">Pour générer et exécuter l'application</span><span class="sxs-lookup"><span data-stu-id="a099a-159">To build and run the application</span></span>

1. <span data-ttu-id="a099a-160">Cliquez avec le bouton droit sur **NumberGuessWorkflowHost** dans l' **Explorateur de solutions** , puis sélectionnez **Définir comme projet de démarrage**.</span><span class="sxs-lookup"><span data-stu-id="a099a-160">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and select **Set as StartUp Project**.</span></span>

2. <span data-ttu-id="a099a-161">Appuyez sur Ctrl+F5 pour générer et exécuter l'application.</span><span class="sxs-lookup"><span data-stu-id="a099a-161">Press CTRL+F5 to build and run the application.</span></span> <span data-ttu-id="a099a-162">Essayez de deviner le nombre en aussi peu de tours que possible.</span><span class="sxs-lookup"><span data-stu-id="a099a-162">Try to guess the number in as few turns as possible.</span></span>

     <span data-ttu-id="a099a-163">Pour essayer l'application avec un des autres styles de workflow, remplacez `Workflow1` dans le code qui crée le <xref:System.Activities.WorkflowApplication> par `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, ou `StateMachineNumberGuessWorkflow`, en fonction du style de workflow souhaité.</span><span class="sxs-lookup"><span data-stu-id="a099a-163">To try the application with one of the other styles of workflow, replace `Workflow1` in the code that creates the <xref:System.Activities.WorkflowApplication> with `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, or `StateMachineNumberGuessWorkflow`, depending on which workflow style you desire.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#6](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#6)]
     [!code-vb[CFX_WF_GettingStarted#6](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#6)]

     <span data-ttu-id="a099a-164">Pour obtenir des instructions sur la façon d’ajouter la persistance à une application de workflow, [consultez la rubrique suivante, comment : Créer et exécuter un flux de travail](how-to-create-and-run-a-long-running-workflow.md)à long terme.</span><span class="sxs-lookup"><span data-stu-id="a099a-164">For instructions about how to add persistence to a workflow application, see the next topic, [How to: Create and Run a Long Running Workflow](how-to-create-and-run-a-long-running-workflow.md).</span></span>

## <a name="example"></a><span data-ttu-id="a099a-165">Exemple</span><span class="sxs-lookup"><span data-stu-id="a099a-165">Example</span></span>
 <span data-ttu-id="a099a-166">L'exemple suivant constitue l'intégralité du code de la méthode `Main` .</span><span class="sxs-lookup"><span data-stu-id="a099a-166">The following example is the complete code listing for the `Main` method.</span></span>

> [!NOTE]
> <span data-ttu-id="a099a-167">Remplacez `Workflow1` dans ces exemples par `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`ou `StateMachineNumberGuessWorkflow`, selon le flux de travail que vous avez effectué dans la procédure [précédente : Créer une étape](how-to-create-a-workflow.md) de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="a099a-167">Please replace `Workflow1` in these examples with `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, or `StateMachineNumberGuessWorkflow`, depending on which workflow you completed in the previous [How to: Create a Workflow](how-to-create-a-workflow.md) step.</span></span> <span data-ttu-id="a099a-168">Si vous ne substituez pas `Workflow1` , vous obtiendrez des erreurs de build lors de la génération ou de l'exécution du workflow.</span><span class="sxs-lookup"><span data-stu-id="a099a-168">If you do not replace `Workflow1` then you will get build errors when you try and build or run the workflow.</span></span>

 [!code-csharp[CFX_WF_GettingStarted#12](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#12)]
 [!code-vb[CFX_WF_GettingStarted#12](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#12)]

## <a name="see-also"></a><span data-ttu-id="a099a-169">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a099a-169">See also</span></span>

- <xref:System.Activities.WorkflowApplication>
- <xref:System.Activities.Bookmark>
- [<span data-ttu-id="a099a-170">Programmation Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="a099a-170">Windows Workflow Foundation Programming</span></span>](programming.md)
- [<span data-ttu-id="a099a-171">Didacticiel Bien démarrer</span><span class="sxs-lookup"><span data-stu-id="a099a-171">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
- [<span data-ttu-id="a099a-172">Guide pratique pour Créer un flux de travail</span><span class="sxs-lookup"><span data-stu-id="a099a-172">How to: Create a Workflow</span></span>](how-to-create-a-workflow.md)
- [<span data-ttu-id="a099a-173">Guide pratique : Créer et exécuter un flux de travail à long terme</span><span class="sxs-lookup"><span data-stu-id="a099a-173">How to: Create and Run a Long Running Workflow</span></span>](how-to-create-and-run-a-long-running-workflow.md)
- [<span data-ttu-id="a099a-174">Attente d’une entrée dans un workflow</span><span class="sxs-lookup"><span data-stu-id="a099a-174">Waiting for Input in a Workflow</span></span>](waiting-for-input-in-a-workflow.md)
- [<span data-ttu-id="a099a-175">Hébergement de workflows</span><span class="sxs-lookup"><span data-stu-id="a099a-175">Hosting Workflows</span></span>](hosting-workflows.md)

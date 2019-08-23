---
title: 'Procédure : Créer un workflow séquentiel'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5280e816-ae17-48c4-8de0-a1e6895dd8f0
ms.openlocfilehash: 9c9746305b251e7d48ee34c2cccd5afae174ee90
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962369"
---
# <a name="how-to-create-a-sequential-workflow"></a><span data-ttu-id="2fb88-102">Procédure : Créer un workflow séquentiel</span><span class="sxs-lookup"><span data-stu-id="2fb88-102">How to: Create a Sequential Workflow</span></span>
<span data-ttu-id="2fb88-103">Les workflows peuvent être construits aussi bien à partir d'activités intégrées que d'activités personnalisées.</span><span class="sxs-lookup"><span data-stu-id="2fb88-103">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="2fb88-104">Cette rubrique explique comment créer un workflow qui utilise à la fois des activités intégrées telles que <xref:System.Activities.Statements.Sequence> l’activité, et les activités personnalisées de [la procédure précédente Comment: Créer une rubrique](how-to-create-an-activity.md) d’activité.</span><span class="sxs-lookup"><span data-stu-id="2fb88-104">This topic steps through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.Sequence> activity, and the custom activities from the previous [How to: Create an Activity](how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="2fb88-105">Le workflow modélise un jeu d'estimation de nombre.</span><span class="sxs-lookup"><span data-stu-id="2fb88-105">The workflow models a number guessing game.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2fb88-106">Chaque rubrique du didacticiel de mise en route dépend des rubriques précédentes.</span><span class="sxs-lookup"><span data-stu-id="2fb88-106">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="2fb88-107">Pour effectuer cette rubrique, vous devez d’abord [effectuer les opérations suivantes: Créer une activité](how-to-create-an-activity.md).</span><span class="sxs-lookup"><span data-stu-id="2fb88-107">To complete this topic, you must first complete [How to: Create an Activity](how-to-create-an-activity.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2fb88-108">Pour télécharger une version complète du didacticiel, consultez [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976)(Windows Workflow Foundation (WF45) - Didacticiel de mise en route).</span><span class="sxs-lookup"><span data-stu-id="2fb88-108">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
## <a name="to-create-the-workflow"></a><span data-ttu-id="2fb88-109">Pour créer le flux de travail</span><span class="sxs-lookup"><span data-stu-id="2fb88-109">To create the workflow</span></span>  
  
1. <span data-ttu-id="2fb88-110">Cliquez avec le bouton droit sur **NumberGuessWorkflowActivities** dans **Explorateur de solutions** , puis sélectionnez **Ajouter**, **nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="2fb88-110">Right-click **NumberGuessWorkflowActivities** in **Solution Explorer** and select **Add**, **New Item**.</span></span>  
  
2. <span data-ttu-id="2fb88-111">Dans le nœud **éléments communs** **installés**, sélectionnez **flux de travail**.</span><span class="sxs-lookup"><span data-stu-id="2fb88-111">In the **Installed**, **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="2fb88-112">Sélectionnez **activité** dans la liste **flux de travail** .</span><span class="sxs-lookup"><span data-stu-id="2fb88-112">Select **Activity** from the **Workflow** list.</span></span>  
  
3. <span data-ttu-id="2fb88-113">Tapez `SequentialNumberGuessWorkflow` dans la zone **nom** , puis cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="2fb88-113">Type `SequentialNumberGuessWorkflow` into the **Name** box and click **Add**.</span></span>  
  
4. <span data-ttu-id="2fb88-114">Faites glisser une activité **Sequence** de la section **flux de contrôle** de la **boîte à outils** et déposez-la sur l’étiquette **déposer l’activité ici** sur l’aire de conception de Workflow.</span><span class="sxs-lookup"><span data-stu-id="2fb88-114">Drag a **Sequence** activity from the **Control Flow** section of the **Toolbox** and drop it onto the **Drop activity here** label on the workflow design surface.</span></span>  
  
## <a name="to-create-the-workflow-variables-and-arguments"></a><span data-ttu-id="2fb88-115">Pour créer les variables et arguments du flux de travail</span><span class="sxs-lookup"><span data-stu-id="2fb88-115">To create the workflow variables and arguments</span></span>  
  
1. <span data-ttu-id="2fb88-116">Double-cliquez sur **SequentialNumberGuessWorkflow. Xaml** dans **Explorateur de solutions** pour afficher le flux de travail dans le concepteur, s’il n’est pas déjà affiché.</span><span class="sxs-lookup"><span data-stu-id="2fb88-116">Double-click **SequentialNumberGuessWorkflow.xaml** in **Solution Explorer** to display the workflow in the designer, if it is not already displayed.</span></span>  
  
2. <span data-ttu-id="2fb88-117">Cliquez sur **arguments** dans la partie inférieure gauche du concepteur de flux de travail pour afficher le volet **arguments** .</span><span class="sxs-lookup"><span data-stu-id="2fb88-117">Click **Arguments** in the lower-left side of the workflow designer to display the **Arguments** pane.</span></span>  
  
3. <span data-ttu-id="2fb88-118">Cliquez sur **créer un argument**.</span><span class="sxs-lookup"><span data-stu-id="2fb88-118">Click **Create Argument**.</span></span>  
  
4. <span data-ttu-id="2fb88-119">Tapez `MaxNumber` dans la zone **nom** , sélectionnez **in** dans la liste déroulante **direction** , sélectionnez **Int32** dans la liste déroulante **type d’argument** , puis appuyez sur entrée pour enregistrer l’argument.</span><span class="sxs-lookup"><span data-stu-id="2fb88-119">Type `MaxNumber` into the **Name** box, select **In** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER to save the argument.</span></span>  
  
5. <span data-ttu-id="2fb88-120">Cliquez sur **créer un argument**.</span><span class="sxs-lookup"><span data-stu-id="2fb88-120">Click **Create Argument**.</span></span>  
  
6. <span data-ttu-id="2fb88-121">Tapez `Turns` dans la zone **nom** située sous l’argument nouvellement ajouté `MaxNumber` , sélectionnez **out** dans la liste déroulante **direction** , sélectionnez **Int32** dans la liste déroulante **type d’argument** , puis appuyez sur entrée.</span><span class="sxs-lookup"><span data-stu-id="2fb88-121">Type `Turns` into the **Name** box that is below the newly added `MaxNumber` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER.</span></span>  
  
7. <span data-ttu-id="2fb88-122">Cliquez sur **arguments** dans la partie inférieure gauche du concepteur d’activités pour fermer le volet **arguments** .</span><span class="sxs-lookup"><span data-stu-id="2fb88-122">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>  
  
8. <span data-ttu-id="2fb88-123">Cliquez sur **variables** dans la partie inférieure gauche du concepteur de flux de travail pour afficher le volet **variables** .</span><span class="sxs-lookup"><span data-stu-id="2fb88-123">Click **Variables** in the lower-left side of the workflow designer to display the **Variables** pane.</span></span>  
  
9. <span data-ttu-id="2fb88-124">Cliquez sur **créer une variable**.</span><span class="sxs-lookup"><span data-stu-id="2fb88-124">Click **Create Variable**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="2fb88-125">Si aucune zone **créer une variable** n’est affichée, cliquez sur l’activité **séquence** sur l’aire du concepteur de flux de travail pour la sélectionner.</span><span class="sxs-lookup"><span data-stu-id="2fb88-125">If no **Create Variable** box is displayed, click the **Sequence** activity on the workflow designer surface to select it.</span></span>  
  
10. <span data-ttu-id="2fb88-126">Tapez `Guess` dans la zone **nom** , sélectionnez **Int32** dans la liste déroulante **type de variable** , puis appuyez sur entrée pour enregistrer la variable.</span><span class="sxs-lookup"><span data-stu-id="2fb88-126">Type `Guess` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
11. <span data-ttu-id="2fb88-127">Cliquez sur **créer une variable**.</span><span class="sxs-lookup"><span data-stu-id="2fb88-127">Click **Create Variable**.</span></span>  
  
12. <span data-ttu-id="2fb88-128">Tapez `Target` dans la zone **nom** , sélectionnez **Int32** dans la liste déroulante **type de variable** , puis appuyez sur entrée pour enregistrer la variable.</span><span class="sxs-lookup"><span data-stu-id="2fb88-128">Type `Target` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
13. <span data-ttu-id="2fb88-129">Cliquez sur **variables** dans la partie inférieure gauche du concepteur d’activités pour fermer le volet **variables** .</span><span class="sxs-lookup"><span data-stu-id="2fb88-129">Click **Variables** in the lower-left side of the activity designer to close the **Variables** pane.</span></span>  
  
## <a name="to-add-the-workflow-activities"></a><span data-ttu-id="2fb88-130">Pour ajouter les activités de flux de travail</span><span class="sxs-lookup"><span data-stu-id="2fb88-130">To add the workflow activities</span></span>  
  
1. <span data-ttu-id="2fb88-131">Faites glisser une activité **Assign** de la section primitives de la **boîte à outils** et déposez-la sur l’activité **Sequence** .</span><span class="sxs-lookup"><span data-stu-id="2fb88-131">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Sequence** activity.</span></span> <span data-ttu-id="2fb88-132">Tapez `Target` dans la zone **à** et l’expression suivante dans la zone **entrer C# une expression** ou **entrer une expression VB** .</span><span class="sxs-lookup"><span data-stu-id="2fb88-132">Type `Target` into the **To** box and the following expression into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  <span data-ttu-id="2fb88-133">Si la fenêtre **boîte à outils** n’est pas affichée, sélectionnez **boîte à outils** dans le menu **affichage** .</span><span class="sxs-lookup"><span data-stu-id="2fb88-133">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>  
  
2. <span data-ttu-id="2fb88-134">Faites glisser une activité While à partir de la section **flux de contrôle** de la **boîte à outils** et déposez-la sur le workflow afin qu’elle soit en dessous de l’activité **Assign** .</span><span class="sxs-lookup"><span data-stu-id="2fb88-134">Drag a **DoWhile** activity from the **Control Flow** section of the **Toolbox** and drop it on the workflow so that it is below the **Assign** activity.</span></span>  
  
3. <span data-ttu-id="2fb88-135">Tapez l’expression suivante dans la zone de valeur de propriété **condition** de l’activité de l’activité.</span><span class="sxs-lookup"><span data-stu-id="2fb88-135">Type the following expression into the **DoWhile** activity’s **Condition** property value box.</span></span>  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
     <span data-ttu-id="2fb88-136">Une activité <xref:System.Activities.Statements.DoWhile> exécute ses activités enfants puis évalue son <xref:System.Activities.Statements.DoWhile.Condition%2A>.</span><span class="sxs-lookup"><span data-stu-id="2fb88-136">A <xref:System.Activities.Statements.DoWhile> activity executes its child activities and then evaluates its <xref:System.Activities.Statements.DoWhile.Condition%2A>.</span></span> <span data-ttu-id="2fb88-137">Si <xref:System.Activities.Statements.DoWhile.Condition%2A> a la valeur `True`, les activités dans <xref:System.Activities.Statements.DoWhile> s'exécutent encore.</span><span class="sxs-lookup"><span data-stu-id="2fb88-137">If the <xref:System.Activities.Statements.DoWhile.Condition%2A> evaluates to `True`, then the activities in the <xref:System.Activities.Statements.DoWhile> execute again.</span></span> <span data-ttu-id="2fb88-138">Dans cet exemple, l'estimation de l'utilisateur est évaluée et <xref:System.Activities.Statements.DoWhile> continue jusqu'à ce que l'estimation soit correcte.</span><span class="sxs-lookup"><span data-stu-id="2fb88-138">In this example, the user’s guess is evaluated and the <xref:System.Activities.Statements.DoWhile> continues until the guess is correct.</span></span>  
  
4. <span data-ttu-id="2fb88-139">Faites glisser une activité **prompt** de la section **NumberGuessWorkflowActivities** de la **boîte à outils** et déposez-la dans l’activité en **cours** à partir de l’étape précédente.</span><span class="sxs-lookup"><span data-stu-id="2fb88-139">Drag a **Prompt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox** and drop it in the **DoWhile** activity from the previous step.</span></span>  
  
5. <span data-ttu-id="2fb88-140">Dans la **fenêtre Propriétés**, tapez `"EnterGuess"` en incluant les guillemets dans la zone de valeur de propriété **NomSignet** pour l’activité **prompt** .</span><span class="sxs-lookup"><span data-stu-id="2fb88-140">In the **Properties Window**, type `"EnterGuess"` including the quotes into the **BookmarkName** property value box for the **Prompt** activity.</span></span> <span data-ttu-id="2fb88-141">Tapez `Guess` dans la zone valeur de la propriété de **résultat** , puis tapez l’expression suivante dans la zone de propriété **texte** .</span><span class="sxs-lookup"><span data-stu-id="2fb88-141">Type `Guess` into the **Result** property value box, and type the following expression into the **Text** property box.</span></span>  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
    > [!TIP]
    >  <span data-ttu-id="2fb88-142">Si la **fenêtre Propriétés** n’est pas affichée, sélectionnez **fenêtre Propriétés** dans le menu **affichage** .</span><span class="sxs-lookup"><span data-stu-id="2fb88-142">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>  
  
6. <span data-ttu-id="2fb88-143">Faites glisser une activité **Assign** de la section **primitives** de la **boîte à outils** et déposez-la dans l’activité de fait pour qu’elle suive l’activité **prompt** .</span><span class="sxs-lookup"><span data-stu-id="2fb88-143">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop it in the **DoWhile** activity so that it follows the **Prompt** activity.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="2fb88-144">Lorsque vous déposez l’activité **Assign** , Notez comment le concepteur de workflow ajoute automatiquement une activité **Sequence** pour contenir à la fois l’activité **prompt** et l’activité Assign qui vient d' **être** ajoutée.</span><span class="sxs-lookup"><span data-stu-id="2fb88-144">When you drop the **Assign** activity, note how the workflow designer automatically adds a **Sequence** activity to contain both the **Prompt** activity and the newly added **Assign** activity.</span></span>  
  
7. <span data-ttu-id="2fb88-145">Tapez `Turns` dans la zone **à** , `Turns + 1` puis dans la zone **entrer une C# expression** ou **entrer une expression VB** .</span><span class="sxs-lookup"><span data-stu-id="2fb88-145">Type `Turns` into the **To** box and `Turns + 1` into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>  
  
8. <span data-ttu-id="2fb88-146">Faites glisser une activité **If** de la section **Control Flow** de **la boîte à outils** et déposez-la dans l’activité **Sequence** afin qu’elle suive l’activité Assign qui vient d' **être** ajoutée.</span><span class="sxs-lookup"><span data-stu-id="2fb88-146">Drag an **If** activity from the **Control Flow** section of the **Toolbox** and drop it in the **Sequence** activity so that it follows the newly added **Assign** activity.</span></span>  
  
9. <span data-ttu-id="2fb88-147">Tapez l’expression suivante dans la zone de valeur de propriété **condition** de l’activité **If** .</span><span class="sxs-lookup"><span data-stu-id="2fb88-147">Type the following expression into the **If** activity’s **Condition** property value box.</span></span>  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
10. <span data-ttu-id="2fb88-148">Faites glisser une autre activité **If** de la section **Control Flow** de la **boîte à outils** et déposez-la dans la section **Then** de la première activité **If** .</span><span class="sxs-lookup"><span data-stu-id="2fb88-148">Drag another **If** activity from the **Control Flow** section of the **Toolbox** and drop it in the **Then** section of the first **If** activity.</span></span>  
  
11. <span data-ttu-id="2fb88-149">Tapez l’expression suivante dans la zone de valeur de propriété **condition** de l’activité nouvellement ajoutée.</span><span class="sxs-lookup"><span data-stu-id="2fb88-149">Type the following expression into the newly added **If** activity’s **Condition** property value box.</span></span>  
  
    ```
    Guess < Target  
    ```  
  
12. <span data-ttu-id="2fb88-150">Faites glisser deux activités **WriteLine** de la section primitives de **la boîte à outils** et déposez-les de façon à ce qu’elles se trouvent dans la section **Then** de l’activité **If** nouvellement ajoutée, et l’autre dans la section **else** .</span><span class="sxs-lookup"><span data-stu-id="2fb88-150">Drag two **WriteLine** activities from the **Primitives** section of the **Toolbox** and drop them so that one is in the **Then** section of the newly added **If** activity, and one is in the **Else** section.</span></span>  
  
13. <span data-ttu-id="2fb88-151">Cliquez sur l’activité **WriteLine** dans la section **Then** pour la sélectionner, puis tapez l’expression suivante dans la zone de valeur de propriété **Text** .</span><span class="sxs-lookup"><span data-stu-id="2fb88-151">Click the **WriteLine** activity in the **Then** section to select it, and type the following expression into the **Text** property value box.</span></span>  
  
    ```text
    "Your guess is too low."  
    ```  
  
14. <span data-ttu-id="2fb88-152">Cliquez sur l’activité **WriteLine** dans la section **sinon** pour la sélectionner, puis tapez l’expression suivante dans la zone de valeur de propriété **texte** .</span><span class="sxs-lookup"><span data-stu-id="2fb88-152">Click the **WriteLine** activity in the **Else** section to select it, and type the following expression into the **Text** property value box.</span></span>  
  
    ```text
    "Your guess is too high."  
    ```  
  
     <span data-ttu-id="2fb88-153">L’exemple suivant illustre le flux de travail terminé:</span><span class="sxs-lookup"><span data-stu-id="2fb88-153">The following example illustrates the completed workflow:</span></span>  
  
     ![Capture d’écran montrant le flux de travail séquentiel terminé.](./media/how-to-create-a-sequential-workflow/complete-sequential-workflow.jpg)  
  
## <a name="to-build-the-workflow"></a><span data-ttu-id="2fb88-155">Pour générer le flux de travail</span><span class="sxs-lookup"><span data-stu-id="2fb88-155">To build the workflow</span></span>  
  
1. <span data-ttu-id="2fb88-156">Appuyez sur Ctrl+Maj+B pour générer la solution.</span><span class="sxs-lookup"><span data-stu-id="2fb88-156">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
     <span data-ttu-id="2fb88-157">Pour obtenir des instructions sur l’exécution du flux de travail, consultez la rubrique [suivante, comment: Exécuter un flux](how-to-run-a-workflow.md)de travail.</span><span class="sxs-lookup"><span data-stu-id="2fb88-157">For instructions on how to run the workflow, please see the next topic, [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span> <span data-ttu-id="2fb88-158">Si vous avez déjà effectué les [opérations suivantes: Exécutez une étape](how-to-run-a-workflow.md) de workflow avec un style différent de workflow et souhaitez l’exécuter à l’aide du flux de travail séquentiel de cette étape, passez à la section [ [pour générer et exécuter l’application](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) dans How to: Exécuter un flux](how-to-run-a-workflow.md)de travail.</span><span class="sxs-lookup"><span data-stu-id="2fb88-158">If you have already completed the [How to: Run a Workflow](how-to-run-a-workflow.md) step with a different style of workflow and wish to run it using the sequential workflow from this step, skip ahead to the [To build and run the application](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) section of [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fb88-159">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2fb88-159">See also</span></span>

- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [<span data-ttu-id="2fb88-160">Programmation Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="2fb88-160">Windows Workflow Foundation Programming</span></span>](programming.md)
- [<span data-ttu-id="2fb88-161">Conception des workflows</span><span class="sxs-lookup"><span data-stu-id="2fb88-161">Designing Workflows</span></span>](designing-workflows.md)
- [<span data-ttu-id="2fb88-162">Didacticiel Bien démarrer</span><span class="sxs-lookup"><span data-stu-id="2fb88-162">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
- [<span data-ttu-id="2fb88-163">Guide pratique pour Créer une activité</span><span class="sxs-lookup"><span data-stu-id="2fb88-163">How to: Create an Activity</span></span>](how-to-create-an-activity.md)
- [<span data-ttu-id="2fb88-164">Guide pratique pour Exécuter un flux de travail</span><span class="sxs-lookup"><span data-stu-id="2fb88-164">How to: Run a Workflow</span></span>](how-to-run-a-workflow.md)

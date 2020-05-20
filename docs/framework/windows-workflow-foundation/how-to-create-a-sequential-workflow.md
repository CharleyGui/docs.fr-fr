---
title: 'Procédure : créer un workflow séquentiel'
description: Cet article crée un flux de travail qui utilise à la fois des activités intégrées, telles que l’activité Sequence et des activités personnalisées.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5280e816-ae17-48c4-8de0-a1e6895dd8f0
ms.openlocfilehash: f80ac471fdcc425504b11b5fb17effa888aa9590
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83419692"
---
# <a name="how-to-create-a-sequential-workflow"></a><span data-ttu-id="b846f-103">Procédure : créer un workflow séquentiel</span><span class="sxs-lookup"><span data-stu-id="b846f-103">How to: Create a Sequential Workflow</span></span>

<span data-ttu-id="b846f-104">Les workflows peuvent être construits aussi bien à partir d'activités intégrées que d'activités personnalisées.</span><span class="sxs-lookup"><span data-stu-id="b846f-104">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="b846f-105">Cette rubrique décrit comment créer un workflow qui utilise à la fois des activités intégrées, telles que l' <xref:System.Activities.Statements.Sequence> activité, et les activités personnalisées de la rubrique précédente [Comment : créer une activité](how-to-create-an-activity.md) .</span><span class="sxs-lookup"><span data-stu-id="b846f-105">This topic steps through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.Sequence> activity, and the custom activities from the previous [How to: Create an Activity](how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="b846f-106">Le workflow modélise un jeu d'estimation de nombre.</span><span class="sxs-lookup"><span data-stu-id="b846f-106">The workflow models a number guessing game.</span></span>

> [!NOTE]
> <span data-ttu-id="b846f-107">Chaque rubrique du didacticiel de mise en route dépend des rubriques précédentes.</span><span class="sxs-lookup"><span data-stu-id="b846f-107">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="b846f-108">Pour effectuer cette rubrique, vous devez d’abord terminer [la procédure : créer une activité](how-to-create-an-activity.md).</span><span class="sxs-lookup"><span data-stu-id="b846f-108">To complete this topic, you must first complete [How to: Create an Activity](how-to-create-an-activity.md).</span></span>

> [!NOTE]
> <span data-ttu-id="b846f-109">Pour télécharger une version complète du didacticiel, consultez [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976)(Windows Workflow Foundation (WF45) - Didacticiel de mise en route).</span><span class="sxs-lookup"><span data-stu-id="b846f-109">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>

## <a name="to-create-the-workflow"></a><span data-ttu-id="b846f-110">Pour créer le flux de travail</span><span class="sxs-lookup"><span data-stu-id="b846f-110">To create the workflow</span></span>

1. <span data-ttu-id="b846f-111">Cliquez avec le bouton droit sur **NumberGuessWorkflowActivities** dans **Explorateur de solutions** , puis sélectionnez **Ajouter**, **nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="b846f-111">Right-click **NumberGuessWorkflowActivities** in **Solution Explorer** and select **Add**, **New Item**.</span></span>

2. <span data-ttu-id="b846f-112">Dans le nœud **éléments communs** **installés**, sélectionnez **flux de travail**.</span><span class="sxs-lookup"><span data-stu-id="b846f-112">In the **Installed**, **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="b846f-113">Sélectionnez **Activité** dans la liste **Flux de travail**.</span><span class="sxs-lookup"><span data-stu-id="b846f-113">Select **Activity** from the **Workflow** list.</span></span>

3. <span data-ttu-id="b846f-114">Tapez `SequentialNumberGuessWorkflow` dans la zone **nom** , puis cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="b846f-114">Type `SequentialNumberGuessWorkflow` into the **Name** box and click **Add**.</span></span>

4. <span data-ttu-id="b846f-115">Faites glisser une activité **Sequence** de la section **flux de contrôle** de la **boîte à outils** et déposez-la sur l’étiquette **déposer l’activité ici** sur l’aire de conception de Workflow.</span><span class="sxs-lookup"><span data-stu-id="b846f-115">Drag a **Sequence** activity from the **Control Flow** section of the **Toolbox** and drop it onto the **Drop activity here** label on the workflow design surface.</span></span>

## <a name="to-create-the-workflow-variables-and-arguments"></a><span data-ttu-id="b846f-116">Pour créer les variables et arguments du flux de travail</span><span class="sxs-lookup"><span data-stu-id="b846f-116">To create the workflow variables and arguments</span></span>

1. <span data-ttu-id="b846f-117">Double-cliquez sur **SequentialNumberGuessWorkflow. Xaml** dans **Explorateur de solutions** pour afficher le flux de travail dans le concepteur, s’il n’est pas déjà affiché.</span><span class="sxs-lookup"><span data-stu-id="b846f-117">Double-click **SequentialNumberGuessWorkflow.xaml** in **Solution Explorer** to display the workflow in the designer, if it is not already displayed.</span></span>

2. <span data-ttu-id="b846f-118">Cliquez sur **arguments** dans la partie inférieure gauche du concepteur de flux de travail pour afficher le volet **arguments** .</span><span class="sxs-lookup"><span data-stu-id="b846f-118">Click **Arguments** in the lower-left side of the workflow designer to display the **Arguments** pane.</span></span>

3. <span data-ttu-id="b846f-119">Cliquez sur **Créer un argument**.</span><span class="sxs-lookup"><span data-stu-id="b846f-119">Click **Create Argument**.</span></span>

4. <span data-ttu-id="b846f-120">Tapez dans `MaxNumber` la **zone Nom** , sélectionnez **in** dans la liste déroulante **direction** , sélectionnez **Int32** dans la liste déroulante type d' **argument** , puis appuyez sur entrée pour enregistrer l’argument.</span><span class="sxs-lookup"><span data-stu-id="b846f-120">Type `MaxNumber` into the **Name** box, select **In** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER to save the argument.</span></span>

5. <span data-ttu-id="b846f-121">Cliquez sur **Créer un argument**.</span><span class="sxs-lookup"><span data-stu-id="b846f-121">Click **Create Argument**.</span></span>

6. <span data-ttu-id="b846f-122">Tapez `Turns` dans la zone **nom** située sous l’argument nouvellement ajouté `MaxNumber` , sélectionnez **out** dans la liste déroulante **direction** , sélectionnez **Int32** dans la liste déroulante **type d’argument** , puis appuyez sur entrée.</span><span class="sxs-lookup"><span data-stu-id="b846f-122">Type `Turns` into the **Name** box that is below the newly added `MaxNumber` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER.</span></span>

7. <span data-ttu-id="b846f-123">Cliquez sur **Arguments** dans la partie inférieure gauche du concepteur d'activités pour fermer le volet **Arguments**.</span><span class="sxs-lookup"><span data-stu-id="b846f-123">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>

8. <span data-ttu-id="b846f-124">Cliquez sur **variables** dans la partie inférieure gauche du concepteur de flux de travail pour afficher le volet **variables** .</span><span class="sxs-lookup"><span data-stu-id="b846f-124">Click **Variables** in the lower-left side of the workflow designer to display the **Variables** pane.</span></span>

9. <span data-ttu-id="b846f-125">Cliquez sur **Créer une variable**.</span><span class="sxs-lookup"><span data-stu-id="b846f-125">Click **Create Variable**.</span></span>

    > [!TIP]
    > <span data-ttu-id="b846f-126">Si aucune zone **créer une variable** n’est affichée, cliquez sur l’activité **séquence** sur l’aire du concepteur de flux de travail pour la sélectionner.</span><span class="sxs-lookup"><span data-stu-id="b846f-126">If no **Create Variable** box is displayed, click the **Sequence** activity on the workflow designer surface to select it.</span></span>

10. <span data-ttu-id="b846f-127">Tapez `Guess` dans la zone **nom** , sélectionnez **Int32** dans la liste déroulante **type de variable** , puis appuyez sur entrée pour enregistrer la variable.</span><span class="sxs-lookup"><span data-stu-id="b846f-127">Type `Guess` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>

11. <span data-ttu-id="b846f-128">Cliquez sur **Créer une variable**.</span><span class="sxs-lookup"><span data-stu-id="b846f-128">Click **Create Variable**.</span></span>

12. <span data-ttu-id="b846f-129">Tapez `Target` dans la zone **nom** , sélectionnez **Int32** dans la liste déroulante **type de variable** , puis appuyez sur entrée pour enregistrer la variable.</span><span class="sxs-lookup"><span data-stu-id="b846f-129">Type `Target` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>

13. <span data-ttu-id="b846f-130">Cliquez sur **Variables** dans la partie inférieure gauche du concepteur d'activités pour fermer le volet **Variables**.</span><span class="sxs-lookup"><span data-stu-id="b846f-130">Click **Variables** in the lower-left side of the activity designer to close the **Variables** pane.</span></span>

## <a name="to-add-the-workflow-activities"></a><span data-ttu-id="b846f-131">Pour ajouter les activités de flux de travail</span><span class="sxs-lookup"><span data-stu-id="b846f-131">To add the workflow activities</span></span>

1. <span data-ttu-id="b846f-132">Faites glisser une activité **Assign** de la section **primitives** de la **boîte à outils** et déposez-la sur l’activité **Sequence** .</span><span class="sxs-lookup"><span data-stu-id="b846f-132">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Sequence** activity.</span></span> <span data-ttu-id="b846f-133">Tapez `Target` dans la zone **à** et l’expression suivante dans la zone **entrer une expression C#** ou **entrer une expression VB** .</span><span class="sxs-lookup"><span data-stu-id="b846f-133">Type `Target` into the **To** box and the following expression into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>

    ```vb
    New System.Random().Next(1, MaxNumber + 1)
    ```

    ```csharp
    new System.Random().Next(1, MaxNumber + 1)
    ```

    > [!TIP]
    > <span data-ttu-id="b846f-134">Si la fenêtre **Boîte à outils** ne s'affiche pas, sélectionnez **Boîte à outils** dans le menu **Afficher**.</span><span class="sxs-lookup"><span data-stu-id="b846f-134">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>

2. <span data-ttu-id="b846f-135">Faites glisser une activité **while** à partir de la section **flux de contrôle** de la **boîte à outils** et déposez-la sur le workflow afin qu’elle soit en dessous de l’activité **Assign** .</span><span class="sxs-lookup"><span data-stu-id="b846f-135">Drag a **DoWhile** activity from the **Control Flow** section of the **Toolbox** and drop it on the workflow so that it is below the **Assign** activity.</span></span>

3. <span data-ttu-id="b846f-136">Tapez l’expression suivante dans la zone de valeur de propriété **condition** de **l’activité de** l’activité.</span><span class="sxs-lookup"><span data-stu-id="b846f-136">Type the following expression into the **DoWhile** activity’s **Condition** property value box.</span></span>

    ```vb
    Guess <> Target
    ```

    ```csharp
    Guess != Target
    ```

     <span data-ttu-id="b846f-137">Une activité <xref:System.Activities.Statements.DoWhile> exécute ses activités enfants puis évalue son <xref:System.Activities.Statements.DoWhile.Condition%2A>.</span><span class="sxs-lookup"><span data-stu-id="b846f-137">A <xref:System.Activities.Statements.DoWhile> activity executes its child activities and then evaluates its <xref:System.Activities.Statements.DoWhile.Condition%2A>.</span></span> <span data-ttu-id="b846f-138">Si <xref:System.Activities.Statements.DoWhile.Condition%2A> a la valeur `True`, les activités dans <xref:System.Activities.Statements.DoWhile> s'exécutent encore.</span><span class="sxs-lookup"><span data-stu-id="b846f-138">If the <xref:System.Activities.Statements.DoWhile.Condition%2A> evaluates to `True`, then the activities in the <xref:System.Activities.Statements.DoWhile> execute again.</span></span> <span data-ttu-id="b846f-139">Dans cet exemple, l'estimation de l'utilisateur est évaluée et <xref:System.Activities.Statements.DoWhile> continue jusqu'à ce que l'estimation soit correcte.</span><span class="sxs-lookup"><span data-stu-id="b846f-139">In this example, the user’s guess is evaluated and the <xref:System.Activities.Statements.DoWhile> continues until the guess is correct.</span></span>

4. <span data-ttu-id="b846f-140">Faites glisser une activité **prompt** de la section **NumberGuessWorkflowActivities** de la **boîte à outils** et déposez-la dans l’activité en **cours** à partir de l’étape précédente.</span><span class="sxs-lookup"><span data-stu-id="b846f-140">Drag a **Prompt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox** and drop it in the **DoWhile** activity from the previous step.</span></span>

5. <span data-ttu-id="b846f-141">Dans la **fenêtre Propriétés**, tapez en `"EnterGuess"` incluant les guillemets dans la zone de valeur de propriété **NomSignet** pour l’activité **prompt** .</span><span class="sxs-lookup"><span data-stu-id="b846f-141">In the **Properties Window**, type `"EnterGuess"` including the quotes into the **BookmarkName** property value box for the **Prompt** activity.</span></span> <span data-ttu-id="b846f-142">Tapez `Guess` dans la zone valeur de la propriété de **résultat** , puis tapez l’expression suivante dans la zone de propriété **texte** .</span><span class="sxs-lookup"><span data-stu-id="b846f-142">Type `Guess` into the **Result** property value box, and type the following expression into the **Text** property box.</span></span>

    ```vb
    "Please enter a number between 1 and " & MaxNumber
    ```

    ```csharp
    "Please enter a number between 1 and " + MaxNumber
    ```

    > [!TIP]
    > <span data-ttu-id="b846f-143">Si la **fenêtre Propriétés** n’est pas affichée, sélectionnez **fenêtre Propriétés** dans le menu **affichage** .</span><span class="sxs-lookup"><span data-stu-id="b846f-143">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>

6. <span data-ttu-id="b846f-144">Faites glisser une activité **Assign** de la section **primitives** de **la boîte à outils** et déposez-la dans **l’activité de** fait pour qu’elle suive l’activité **prompt** .</span><span class="sxs-lookup"><span data-stu-id="b846f-144">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop it in the **DoWhile** activity so that it follows the **Prompt** activity.</span></span>

    > [!NOTE]
    > <span data-ttu-id="b846f-145">Lorsque vous déposez l’activité **Assign** , Notez comment le concepteur de workflow ajoute automatiquement une activité **Sequence** pour contenir à la fois l’activité **prompt** et l’activité Assign qui vient d' **être** ajoutée.</span><span class="sxs-lookup"><span data-stu-id="b846f-145">When you drop the **Assign** activity, note how the workflow designer automatically adds a **Sequence** activity to contain both the **Prompt** activity and the newly added **Assign** activity.</span></span>

7. <span data-ttu-id="b846f-146">Tapez `Turns` dans la zone **à** , puis `Turns + 1` dans la zone **entrer une expression C#** ou **entrer une expression VB** .</span><span class="sxs-lookup"><span data-stu-id="b846f-146">Type `Turns` into the **To** box and `Turns + 1` into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>

8. <span data-ttu-id="b846f-147">Faites glisser une activité **If** de la section **Control Flow** de **la boîte à outils** et déposez-la dans l’activité **Sequence** afin qu’elle suive l’activité Assign qui vient d' **être** ajoutée.</span><span class="sxs-lookup"><span data-stu-id="b846f-147">Drag an **If** activity from the **Control Flow** section of the **Toolbox** and drop it in the **Sequence** activity so that it follows the newly added **Assign** activity.</span></span>

9. <span data-ttu-id="b846f-148">Tapez l’expression suivante dans la zone de valeur de propriété **condition** de l’activité **If** .</span><span class="sxs-lookup"><span data-stu-id="b846f-148">Type the following expression into the **If** activity’s **Condition** property value box.</span></span>

    ```vb
    Guess <> Target
    ```

    ```csharp
    Guess != Target
    ```

10. <span data-ttu-id="b846f-149">Faites glisser une autre activité **If** de la section **Control Flow** de la **boîte à outils** et déposez-la dans la section **Then** de la première activité **If** .</span><span class="sxs-lookup"><span data-stu-id="b846f-149">Drag another **If** activity from the **Control Flow** section of the **Toolbox** and drop it in the **Then** section of the first **If** activity.</span></span>

11. <span data-ttu-id="b846f-150">Tapez l’expression suivante dans la zone de valeur de propriété **condition** de **l’activité nouvellement** ajoutée.</span><span class="sxs-lookup"><span data-stu-id="b846f-150">Type the following expression into the newly added **If** activity’s **Condition** property value box.</span></span>

    ```text
    Guess < Target
    ```

12. <span data-ttu-id="b846f-151">Faites glisser deux activités **WriteLine** de la section **primitives** de **la boîte à outils** et déposez-les de façon à ce qu’elles se trouvent dans la section **Then** de l’activité **If** nouvellement ajoutée, et l’autre dans la section **else** .</span><span class="sxs-lookup"><span data-stu-id="b846f-151">Drag two **WriteLine** activities from the **Primitives** section of the **Toolbox** and drop them so that one is in the **Then** section of the newly added **If** activity, and one is in the **Else** section.</span></span>

13. <span data-ttu-id="b846f-152">Cliquez sur l’activité **WriteLine** dans la section **Then** pour la sélectionner, puis tapez l’expression suivante dans la zone de valeur de propriété **Text** .</span><span class="sxs-lookup"><span data-stu-id="b846f-152">Click the **WriteLine** activity in the **Then** section to select it, and type the following expression into the **Text** property value box.</span></span>

    ```text
    "Your guess is too low."
    ```

14. <span data-ttu-id="b846f-153">Cliquez sur l’activité **WriteLine** dans la section **sinon** pour la sélectionner, puis tapez l’expression suivante dans la zone de valeur de propriété **texte** .</span><span class="sxs-lookup"><span data-stu-id="b846f-153">Click the **WriteLine** activity in the **Else** section to select it, and type the following expression into the **Text** property value box.</span></span>

    ```text
    "Your guess is too high."
    ```

     <span data-ttu-id="b846f-154">L’exemple suivant illustre le flux de travail terminé :</span><span class="sxs-lookup"><span data-stu-id="b846f-154">The following example illustrates the completed workflow:</span></span>

     ![Capture d’écran montrant le flux de travail séquentiel terminé.](./media/how-to-create-a-sequential-workflow/complete-sequential-workflow.jpg)

## <a name="to-build-the-workflow"></a><span data-ttu-id="b846f-156">Pour générer le flux de travail</span><span class="sxs-lookup"><span data-stu-id="b846f-156">To build the workflow</span></span>

1. <span data-ttu-id="b846f-157">Appuyez sur Ctrl+Maj+B pour générer la solution.</span><span class="sxs-lookup"><span data-stu-id="b846f-157">Press CTRL+SHIFT+B to build the solution.</span></span>

     <span data-ttu-id="b846f-158">Pour obtenir des instructions sur l’exécution du flux de travail, consultez la rubrique suivante, [Comment : exécuter un workflow](how-to-run-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="b846f-158">For instructions on how to run the workflow, please see the next topic, [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span> <span data-ttu-id="b846f-159">Si vous avez déjà effectué l’étape [Comment : exécuter un flux de travail](how-to-run-a-workflow.md) avec un style différent de workflow et que vous souhaitez l’exécuter à l’aide du flux de travail séquentiel de cette étape, passez à la section [pour générer et exécuter l’application](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) dans [procédure : exécuter un workflow](how-to-run-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="b846f-159">If you have already completed the [How to: Run a Workflow](how-to-run-a-workflow.md) step with a different style of workflow and wish to run it using the sequential workflow from this step, skip ahead to the [To build and run the application](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) section of [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b846f-160">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b846f-160">See also</span></span>

- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [<span data-ttu-id="b846f-161">Programmation Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="b846f-161">Windows Workflow Foundation Programming</span></span>](programming.md)
- [<span data-ttu-id="b846f-162">Conception des workflows</span><span class="sxs-lookup"><span data-stu-id="b846f-162">Designing Workflows</span></span>](designing-workflows.md)
- [<span data-ttu-id="b846f-163">Didacticiel Prise en main</span><span class="sxs-lookup"><span data-stu-id="b846f-163">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
- [<span data-ttu-id="b846f-164">Guide pratique pour créer une activité</span><span class="sxs-lookup"><span data-stu-id="b846f-164">How to: Create an Activity</span></span>](how-to-create-an-activity.md)
- [<span data-ttu-id="b846f-165">Guide pratique pour exécuter un workflow</span><span class="sxs-lookup"><span data-stu-id="b846f-165">How to: Run a Workflow</span></span>](how-to-run-a-workflow.md)

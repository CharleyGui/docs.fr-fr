---
title: 'Procédure : créer un workflow d’organigramme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 185d7aea-68a6-4bd8-adde-45050f33170a
ms.openlocfilehash: 0faf4d77b1ea2881ba8e029d544f2e42cf552349
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989691"
---
# <a name="how-to-create-a-flowchart-workflow"></a><span data-ttu-id="b9d0a-102">Procédure : créer un workflow d’organigramme</span><span class="sxs-lookup"><span data-stu-id="b9d0a-102">How to: Create a Flowchart Workflow</span></span>
<span data-ttu-id="b9d0a-103">Les workflows peuvent être construits aussi bien à partir d'activités intégrées que d'activités personnalisées.</span><span class="sxs-lookup"><span data-stu-id="b9d0a-103">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="b9d0a-104">Cette rubrique décrit comment créer un workflow qui utilise à la fois des activités intégrées, telles que l’activité <xref:System.Activities.Statements.Flowchart>, et les activités personnalisées de la [précédente Comment : Créer une activité](how-to-create-an-activity.md) rubrique.</span><span class="sxs-lookup"><span data-stu-id="b9d0a-104">This topic steps through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.Flowchart> activity, and the custom activities from the previous [How to: Create an Activity](how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="b9d0a-105">Le workflow modélise un jeu d'estimation de nombre.</span><span class="sxs-lookup"><span data-stu-id="b9d0a-105">The workflow models a number guessing game.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b9d0a-106">Chaque rubrique du didacticiel de mise en route dépend des rubriques précédentes.</span><span class="sxs-lookup"><span data-stu-id="b9d0a-106">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="b9d0a-107">Pour effectuer cette rubrique, vous devez d’abord terminer [procédure : Créer une](how-to-create-an-activity.md)d’activité.</span><span class="sxs-lookup"><span data-stu-id="b9d0a-107">To complete this topic, you must first complete [How to: Create an Activity](how-to-create-an-activity.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b9d0a-108">Pour télécharger une version complète du didacticiel, consultez [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976)(Windows Workflow Foundation (WF45) - Didacticiel de mise en route).</span><span class="sxs-lookup"><span data-stu-id="b9d0a-108">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
### <a name="to-create-the-workflow"></a><span data-ttu-id="b9d0a-109">Pour créer le flux de travail</span><span class="sxs-lookup"><span data-stu-id="b9d0a-109">To create the workflow</span></span>  
  
1. <span data-ttu-id="b9d0a-110">Cliquez avec le bouton droit sur **NumberGuessWorkflowActivities** dans **Explorateur de solutions** , puis sélectionnez **Ajouter**, **nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="b9d0a-110">Right-click **NumberGuessWorkflowActivities** in **Solution Explorer** and select **Add**, **New Item**.</span></span>  
  
2. <span data-ttu-id="b9d0a-111">Dans le nœud **éléments communs** **installés**, sélectionnez **flux de travail**.</span><span class="sxs-lookup"><span data-stu-id="b9d0a-111">In the **Installed**, **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="b9d0a-112">Sélectionnez **activité** dans la liste **flux de travail** .</span><span class="sxs-lookup"><span data-stu-id="b9d0a-112">Select **Activity** from the **Workflow** list.</span></span>  
  
3. <span data-ttu-id="b9d0a-113">Tapez `FlowchartNumberGuessWorkflow` dans la zone **nom** , puis cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="b9d0a-113">Type `FlowchartNumberGuessWorkflow` into the **Name** box and click **Add**.</span></span>  
  
4. <span data-ttu-id="b9d0a-114">Faites glisser une activité **Flowchart** de la section **organigramme** de la **boîte à outils** et déposez-la sur l’étiquette déposer l' **activité ici** sur l’aire de conception de Workflow.</span><span class="sxs-lookup"><span data-stu-id="b9d0a-114">Drag a **Flowchart** activity from the **Flowchart** section of the **Toolbox** and drop it onto the **Drop activity here** label on the workflow design surface.</span></span>  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a><span data-ttu-id="b9d0a-115">Pour créer les variables et arguments du flux de travail</span><span class="sxs-lookup"><span data-stu-id="b9d0a-115">To create the workflow variables and arguments</span></span>  
  
1. <span data-ttu-id="b9d0a-116">Double-cliquez sur **FlowchartNumberGuessWorkflow. Xaml** dans **Explorateur de solutions** pour afficher le flux de travail dans le concepteur, s’il n’est pas déjà affiché.</span><span class="sxs-lookup"><span data-stu-id="b9d0a-116">Double-click **FlowchartNumberGuessWorkflow.xaml** in **Solution Explorer** to display the workflow in the designer, if it is not already displayed.</span></span>  
  
2. <span data-ttu-id="b9d0a-117">Cliquez sur **arguments** dans la partie inférieure gauche du concepteur de flux de travail pour afficher le volet **arguments** .</span><span class="sxs-lookup"><span data-stu-id="b9d0a-117">Click **Arguments** in the lower-left side of the workflow designer to display the **Arguments** pane.</span></span>  
  
3. <span data-ttu-id="b9d0a-118">Cliquez sur **créer un argument**.</span><span class="sxs-lookup"><span data-stu-id="b9d0a-118">Click **Create Argument**.</span></span>  
  
4. <span data-ttu-id="b9d0a-119">Tapez `MaxNumber` dans la zone **nom** , sélectionnez **in** dans la liste déroulante **direction** , sélectionnez **Int32** dans la liste déroulante **type d’argument** , puis appuyez sur entrée pour enregistrer l’argument.</span><span class="sxs-lookup"><span data-stu-id="b9d0a-119">Type `MaxNumber` into the **Name** box, select **In** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER to save the argument.</span></span>  
  
5. <span data-ttu-id="b9d0a-120">Cliquez sur **créer un argument**.</span><span class="sxs-lookup"><span data-stu-id="b9d0a-120">Click **Create Argument**.</span></span>  
  
6. <span data-ttu-id="b9d0a-121">Tapez `Turns` dans la zone **nom** située sous l’argument `MaxNumber` récemment ajouté, sélectionnez **out** dans la liste déroulante **direction** , sélectionnez **Int32** dans la liste déroulante **type d’argument** , puis appuyez sur entrée.</span><span class="sxs-lookup"><span data-stu-id="b9d0a-121">Type `Turns` into the **Name** box that is below the newly added `MaxNumber` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER.</span></span>  
  
7. <span data-ttu-id="b9d0a-122">Cliquez sur **arguments** dans la partie inférieure gauche du concepteur d’activités pour fermer le volet **arguments** .</span><span class="sxs-lookup"><span data-stu-id="b9d0a-122">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>  
  
8. <span data-ttu-id="b9d0a-123">Cliquez sur **variables** dans la partie inférieure gauche du concepteur de flux de travail pour afficher le volet **variables** .</span><span class="sxs-lookup"><span data-stu-id="b9d0a-123">Click **Variables** in the lower-left side of the workflow designer to display the **Variables** pane.</span></span>  
  
9. <span data-ttu-id="b9d0a-124">Cliquez sur **créer une variable**.</span><span class="sxs-lookup"><span data-stu-id="b9d0a-124">Click **Create Variable**.</span></span>  
  
    > [!TIP]
    > <span data-ttu-id="b9d0a-125">Si aucune zone **créer une variable** n’est affichée, cliquez sur l’activité <xref:System.Activities.Statements.Flowchart> sur l’aire du concepteur de flux de travail pour la sélectionner.</span><span class="sxs-lookup"><span data-stu-id="b9d0a-125">If no **Create Variable** box is displayed, click the <xref:System.Activities.Statements.Flowchart> activity on the workflow designer surface to select it.</span></span>  
  
10. <span data-ttu-id="b9d0a-126">Tapez `Guess` dans la zone **nom** , sélectionnez **Int32** dans la liste déroulante **type de variable** , puis appuyez sur entrée pour enregistrer la variable.</span><span class="sxs-lookup"><span data-stu-id="b9d0a-126">Type `Guess` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
11. <span data-ttu-id="b9d0a-127">Cliquez sur **créer une variable**.</span><span class="sxs-lookup"><span data-stu-id="b9d0a-127">Click **Create Variable**.</span></span>  
  
12. <span data-ttu-id="b9d0a-128">Tapez `Target` dans la zone **nom** , sélectionnez **Int32** dans la liste déroulante **type de variable** , puis appuyez sur entrée pour enregistrer la variable.</span><span class="sxs-lookup"><span data-stu-id="b9d0a-128">Type `Target` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
13. <span data-ttu-id="b9d0a-129">Cliquez sur **variables** dans la partie inférieure gauche du concepteur d’activités pour fermer le volet **variables** .</span><span class="sxs-lookup"><span data-stu-id="b9d0a-129">Click **Variables** in the lower-left side of the activity designer to close the **Variables** pane.</span></span>  
  
### <a name="to-add-the-workflow-activities"></a><span data-ttu-id="b9d0a-130">Pour ajouter les activités de flux de travail</span><span class="sxs-lookup"><span data-stu-id="b9d0a-130">To add the workflow activities</span></span>  
  
1. <span data-ttu-id="b9d0a-131">Faites glisser une activité **Assign** de la section **primitives** de la **boîte à outils** et placez-la sur le nœud de **départ** , qui se trouve en haut de l’organigramme.</span><span class="sxs-lookup"><span data-stu-id="b9d0a-131">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and hover it over the **Start** node, which is at the top of the flowchart.</span></span> <span data-ttu-id="b9d0a-132">Lorsque l’activité **Assign** se trouve sur le nœud de **départ** , trois triangles apparaissent autour du nœud de **démarrage** .</span><span class="sxs-lookup"><span data-stu-id="b9d0a-132">When the **Assign** activity is over the **Start** node, three triangles will appear around the **Start** node.</span></span> <span data-ttu-id="b9d0a-133">Déposez l’activité **Assign** sur le triangle qui est directement sous le nœud **Start** .</span><span class="sxs-lookup"><span data-stu-id="b9d0a-133">Drop the **Assign** activity on the triangle that is directly below the **Start** node.</span></span> <span data-ttu-id="b9d0a-134">Cela permet de lier les deux éléments ensemble et de désigner l’activité **Assign** comme première activité dans l’organigramme.</span><span class="sxs-lookup"><span data-stu-id="b9d0a-134">This will link the two items together and designates the **Assign** activity as the first activity in the flowchart.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="b9d0a-135">Les activités peuvent également être définies comme activité de départ dans le workflow en les liant manuellement au nœud de démarrage.</span><span class="sxs-lookup"><span data-stu-id="b9d0a-135">Activities can also be indicated as the starting activity in the workflow by manually linking them activity to the start node.</span></span> <span data-ttu-id="b9d0a-136">Pour ce faire, placez le curseur de la souris sur le nœud de **démarrage** , cliquez sur l’un des rectangles qui s’affichent lorsque la souris se trouve sur le nœud de **départ** , puis faites glisser la ligne de connexion vers le bas jusqu’à l’activité souhaitée et déposez-la sur l’un des rectangles qui s’affichent.</span><span class="sxs-lookup"><span data-stu-id="b9d0a-136">To do this, hover the mouse over the **Start** node, click one of the rectangles that appear when the mouse is over the **Start** node, and drag the connecting line down to the desired activity and drop it on one of the rectangles that appear.</span></span> <span data-ttu-id="b9d0a-137">Vous pouvez également désigner une activité comme activité de départ en cliquant dessus avec le bouton droit, puis en choisissant **définir comme nœud de démarrage**.</span><span class="sxs-lookup"><span data-stu-id="b9d0a-137">You can also designate an activity as the starting activity by right-clicking the it and choosing **Set as Start Node**.</span></span>  
  
2. <span data-ttu-id="b9d0a-138">Tapez `Target` dans la zone **à** et l’expression suivante dans la zone **entrer C# une expression** ou **entrer une expression VB** .</span><span class="sxs-lookup"><span data-stu-id="b9d0a-138">Type `Target` into the **To** box and the following expression into the **Enter a C# Expression** or **Enter a VB expression** box.</span></span>  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    > <span data-ttu-id="b9d0a-139">Si la fenêtre **boîte à outils** n’est pas affichée, sélectionnez **boîte à outils** dans le menu **affichage** .</span><span class="sxs-lookup"><span data-stu-id="b9d0a-139">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>  
  
3. <span data-ttu-id="b9d0a-140">Faites glisser une activité **prompt** de la section **NumberGuessWorkflowActivities** de la **boîte à outils**, déposez-la en dessous de l’activité **Assign** de l’étape précédente, puis connectez l’activité **prompt** à l’activité **Assign** .</span><span class="sxs-lookup"><span data-stu-id="b9d0a-140">Drag a **Prompt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox**, drop it below the **Assign** activity from the previous step, and connect the **Prompt** activity to the **Assign** activity.</span></span> <span data-ttu-id="b9d0a-141">Il existe trois façons de connecter les deux activités.</span><span class="sxs-lookup"><span data-stu-id="b9d0a-141">There are three ways to connect the two activities.</span></span> <span data-ttu-id="b9d0a-142">La première consiste à les connecter lorsque vous déposez l’activité **prompt** sur le Workflow.</span><span class="sxs-lookup"><span data-stu-id="b9d0a-142">The first way is to connect them as you drop the **Prompt** activity on the workflow.</span></span> <span data-ttu-id="b9d0a-143">Lorsque vous faites glisser l’activité **prompt** vers le workflow, placez-la sur l’activité **Assign** et déposez-la sur l’un des quatre triangles qui s’affiche lorsque l’activité **prompt** est positionnée sur l’activité **Assign** .</span><span class="sxs-lookup"><span data-stu-id="b9d0a-143">As you are dragging the **Prompt** activity to the workflow, hover it over the **Assign** activity and drop it onto one of the four triangles that appear when the **Prompt** activity is over the **Assign** activity.</span></span> <span data-ttu-id="b9d0a-144">La seconde consiste à déposer l’activité **prompt** sur le workflow à l’emplacement souhaité.</span><span class="sxs-lookup"><span data-stu-id="b9d0a-144">The second way is to drop the **Prompt** activity onto the workflow at the desired location.</span></span> <span data-ttu-id="b9d0a-145">Ensuite, placez le pointeur de la souris sur l’activité **Assign** et faites glisser l’un des rectangles qui s’affichent vers le bas de l’activité **prompt** .</span><span class="sxs-lookup"><span data-stu-id="b9d0a-145">Then, hover the mouse over the **Assign** activity and drag one of the rectangles that appears down to the **Prompt** activity.</span></span> <span data-ttu-id="b9d0a-146">Faites glisser la souris de sorte que la ligne de connexion de l’activité **Assign** se connecte à l’un des rectangles de l’activité **prompt** , puis relâchez le bouton de la souris.</span><span class="sxs-lookup"><span data-stu-id="b9d0a-146">Drag the mouse so that the connecting line from the **Assign** activity connects to one of the rectangles of the **Prompt** activity, and then release the mouse button.</span></span> <span data-ttu-id="b9d0a-147">La troisième méthode est très similaire à la première, mais au lieu de faire glisser l’activité **prompt** à partir de la **boîte à outils**, vous la faites glisser à partir de son emplacement sur l’aire de conception de workflow, vous la Positionnez sur l’activité **Assign** et vous la déposez sur l’un des triangles qui s’affiche.</span><span class="sxs-lookup"><span data-stu-id="b9d0a-147">The third way is very similar to the first way, except that instead of dragging the **Prompt** activity from the **Toolbox**, you drag it from its location on the workflow design surface, hover it over the **Assign** activity, and drop it onto one of the triangles that appears.</span></span>  
  
4. <span data-ttu-id="b9d0a-148">Dans la **fenêtre Propriétés** de l’activité **Prompt** , tapez `"EnterGuess"` y compris les guillemets dans la zone valeur de la propriété **NomSignet** .</span><span class="sxs-lookup"><span data-stu-id="b9d0a-148">In the **Properties Window** for the **Prompt** activity, type `"EnterGuess"` including the quotes into the **BookmarkName** property value box.</span></span> <span data-ttu-id="b9d0a-149">Tapez `Guess` dans la zone valeur de la propriété de **résultat** , puis tapez l’expression suivante dans la zone de propriété **texte** .</span><span class="sxs-lookup"><span data-stu-id="b9d0a-149">Type `Guess` into the **Result** property value box, and type the following expression into the **Text** property box.</span></span>  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
    > [!TIP]
    > <span data-ttu-id="b9d0a-150">Si la **fenêtre Propriétés** n’est pas affichée, sélectionnez **fenêtre Propriétés** dans le menu **affichage** .</span><span class="sxs-lookup"><span data-stu-id="b9d0a-150">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>  
  
5. <span data-ttu-id="b9d0a-151">Faites glisser une activité **Assign** de la section **primitives** de la **boîte à outils** et connectez-la à l’aide de l’une des méthodes décrites à l’étape précédente afin qu’elle soit en dessous de l’activité **prompt** .</span><span class="sxs-lookup"><span data-stu-id="b9d0a-151">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and connect it using one of the methods described in the previous step so that it is below the **Prompt** activity.</span></span>  
  
6. <span data-ttu-id="b9d0a-152">Tapez `Turns` dans la zone **à** et `Turns + 1` dans la zone **entrer C# une expression** ou **entrer une expression VB** .</span><span class="sxs-lookup"><span data-stu-id="b9d0a-152">Type `Turns` into the **To** box and `Turns + 1` into the **Enter a C# expression**  or **Enter a VB expression** box.</span></span>  
  
7. <span data-ttu-id="b9d0a-153">Faites glisser un **FlowDecision** à partir de la section **Flowchart** de la **boîte à outils** et connectez-le sous l’activité **Assign** .</span><span class="sxs-lookup"><span data-stu-id="b9d0a-153">Drag a **FlowDecision** from the **Flowchart** section of the **Toolbox** and connect it below the **Assign** activity.</span></span> <span data-ttu-id="b9d0a-154">Dans la **fenêtre Propriétés**, tapez l’expression suivante dans la zone valeur de la propriété **condition** .</span><span class="sxs-lookup"><span data-stu-id="b9d0a-154">In the **Properties Window**, type the following expression into the **Condition** property value box.</span></span>  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
8. <span data-ttu-id="b9d0a-155">Faites glisser une autre activité **FlowDecision** de la **boîte à outils** et déposez-la en dessous de la première.</span><span class="sxs-lookup"><span data-stu-id="b9d0a-155">Drag another **FlowDecision** activity from the **Toolbox** and drop it below the first one.</span></span> <span data-ttu-id="b9d0a-156">Connectez les deux activités en faisant glisser le rectangle qui est étiqueté **false** sur l’activité **FlowDecision** supérieure vers le rectangle situé en haut de la deuxième activité **FlowDecision** .</span><span class="sxs-lookup"><span data-stu-id="b9d0a-156">Connect the two activities by dragging from the rectangle that is labeled **False** on the top **FlowDecision** activity to the rectangle at the top of the second **FlowDecision** activity.</span></span>  
  
    > [!TIP]
    > <span data-ttu-id="b9d0a-157">Si vous ne voyez pas les étiquettes **true** et **false** sur le **FlowDecision**, pointez la souris sur **FlowDecision**.</span><span class="sxs-lookup"><span data-stu-id="b9d0a-157">If you do not see the **True** and **False** labels on the **FlowDecision**, hover the mouse over the **FlowDecision**.</span></span>  
  
9. <span data-ttu-id="b9d0a-158">Cliquez sur la deuxième activité **FlowDecision** pour la sélectionner.</span><span class="sxs-lookup"><span data-stu-id="b9d0a-158">Click the second **FlowDecision** activity to select it.</span></span> <span data-ttu-id="b9d0a-159">Dans la **fenêtre Propriétés**, tapez l’expression suivante dans la zone valeur de la propriété **condition** .</span><span class="sxs-lookup"><span data-stu-id="b9d0a-159">In the **Properties Window**, type the following expression into the **Condition** property value box.</span></span>  
  
    ```text
    Guess < Target
    ```  
  
10. <span data-ttu-id="b9d0a-160">Faites glisser deux activités **WriteLine** de la section **primitives** de la **boîte à outils** et déposez-les afin qu’elles soient côte à côte en dessous des deux activités **FlowDecision** .</span><span class="sxs-lookup"><span data-stu-id="b9d0a-160">Drag two **WriteLine** activities from the **Primitives** section of the **Toolbox** and drop them so that they are side by side below the two **FlowDecision** activities.</span></span> <span data-ttu-id="b9d0a-161">Connectez l’action **true** de l’activité **FlowDecision** inférieure à l’activité **WriteLine** la plus à gauche et l’action **false** à l’activité **WriteLine** la plus à droite.</span><span class="sxs-lookup"><span data-stu-id="b9d0a-161">Connect the **True** action of the bottom **FlowDecision** activity to the leftmost **WriteLine** activity, and the **False** action to the rightmost **WriteLine** activity.</span></span>  
  
11. <span data-ttu-id="b9d0a-162">Cliquez sur l’activité **WriteLine** la plus à gauche pour la sélectionner, puis tapez l’expression suivante dans la zone de valeur de propriété **texte** de la **fenêtre Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="b9d0a-162">Click the leftmost **WriteLine** activity to select it, and type the following expression into the **Text** property value box in the **Properties Window**.</span></span>  
  
    ```text
    "Your guess is too low."  
    ```  
  
12. <span data-ttu-id="b9d0a-163">Connectez le **WriteLine** à la partie gauche de l’activité **prompt** qui se trouve au-dessus de lui.</span><span class="sxs-lookup"><span data-stu-id="b9d0a-163">Connect the **WriteLine** to the left side of the **Prompt** activity that is above it.</span></span>  
  
13. <span data-ttu-id="b9d0a-164">Cliquez sur l’activité **WriteLine** la plus à droite pour la sélectionner, puis tapez l’expression suivante dans la zone de valeur de propriété **texte** de la **fenêtre Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="b9d0a-164">Click the rightmost **WriteLine** activity to select it, and type the following expression into the **Text** property value box in the **Properties Window**.</span></span>  
  
    ```text
    "Your guess is too high."  
    ```  
  
14. <span data-ttu-id="b9d0a-165">Connectez l’activité **WriteLine** au côté droit de l’activité **prompt** située au-dessus de celle-ci.</span><span class="sxs-lookup"><span data-stu-id="b9d0a-165">Connect the **WriteLine** activity to the right side of the **Prompt** activity above it.</span></span>  
  
     <span data-ttu-id="b9d0a-166">L'exemple suivant illustre le flux de travail terminé.</span><span class="sxs-lookup"><span data-stu-id="b9d0a-166">The following example illustrates the completed workflow.</span></span>  
  
     ![Diagramme qui affiche un organigramme Windows Workflow Foundation terminé.](./media/how-to-create-a-flowchart-workflow/completed-windows-workflow-flowchart.png)  
  
### <a name="to-build-the-workflow"></a><span data-ttu-id="b9d0a-168">Pour générer le flux de travail</span><span class="sxs-lookup"><span data-stu-id="b9d0a-168">To build the workflow</span></span>  
  
1. <span data-ttu-id="b9d0a-169">Appuyez sur Ctrl+Maj+B pour générer la solution.</span><span class="sxs-lookup"><span data-stu-id="b9d0a-169">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
     <span data-ttu-id="b9d0a-170">Pour obtenir des instructions sur l’exécution du flux de travail, consultez la rubrique suivante, [procédure: Exécutez un](how-to-run-a-workflow.md)de Workflow.</span><span class="sxs-lookup"><span data-stu-id="b9d0a-170">For instructions on how to run the workflow, please see the next topic, [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span> <span data-ttu-id="b9d0a-171">Si vous avez déjà effectué les [procédure: Exécuter un flux de travail](how-to-run-a-workflow.md) étape avec un style différent de workflow et souhaitez l’exécuter à l’aide du flux de travail de l’organigramme à partir de cette étape, passez à la section [pour générer et exécuter l’application](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) de [procédure: Exécutez un de Workflow.](how-to-run-a-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="b9d0a-171">If you have already completed the [How to: Run a Workflow](how-to-run-a-workflow.md) step with a different style of workflow and wish to run it using the flowchart workflow from this step, skip ahead to the [To build and run the application](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) section of [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9d0a-172">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b9d0a-172">See also</span></span>

- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [<span data-ttu-id="b9d0a-173">Programmation Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="b9d0a-173">Windows Workflow Foundation Programming</span></span>](programming.md)
- [<span data-ttu-id="b9d0a-174">Conception des workflows</span><span class="sxs-lookup"><span data-stu-id="b9d0a-174">Designing Workflows</span></span>](designing-workflows.md)
- [<span data-ttu-id="b9d0a-175">Didacticiel Bien démarrer</span><span class="sxs-lookup"><span data-stu-id="b9d0a-175">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
- [<span data-ttu-id="b9d0a-176">Guide pratique: Créer une activité</span><span class="sxs-lookup"><span data-stu-id="b9d0a-176">How to: Create an Activity</span></span>](how-to-create-an-activity.md)
- [<span data-ttu-id="b9d0a-177">Guide pratique: Exécuter un flux de travail</span><span class="sxs-lookup"><span data-stu-id="b9d0a-177">How to: Run a Workflow</span></span>](how-to-run-a-workflow.md)

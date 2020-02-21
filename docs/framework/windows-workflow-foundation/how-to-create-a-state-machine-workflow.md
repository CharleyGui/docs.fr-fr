---
title: 'Procédure : créer un flux de travail de machine à états'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3ec60e8f-fad4-493e-a426-e7962d7aee8c
ms.openlocfilehash: e93f84f0bacf7ac205294c12c55afcab8d7319b7
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989809"
---
# <a name="how-to-create-a-state-machine-workflow"></a><span data-ttu-id="223e4-102">Procédure : créer un flux de travail de machine à états</span><span class="sxs-lookup"><span data-stu-id="223e4-102">How to: Create a State Machine Workflow</span></span>
<span data-ttu-id="223e4-103">Les workflows peuvent être construits aussi bien à partir d'activités intégrées que d'activités personnalisées.</span><span class="sxs-lookup"><span data-stu-id="223e4-103">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="223e4-104">Cette rubrique décrit comment créer un workflow qui utilise à la fois des activités intégrées, telles que l’activité <xref:System.Activities.Statements.StateMachine>, et les activités personnalisées de la [précédente Comment : Créer une activité](how-to-create-an-activity.md) rubrique.</span><span class="sxs-lookup"><span data-stu-id="223e4-104">This topic steps through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.StateMachine> activity, and the custom activities from the previous [How to: Create an Activity](how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="223e4-105">Le workflow modélise un jeu d'estimation de nombre.</span><span class="sxs-lookup"><span data-stu-id="223e4-105">The workflow models a number guessing game.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="223e4-106">Chaque rubrique du didacticiel de mise en route dépend des rubriques précédentes.</span><span class="sxs-lookup"><span data-stu-id="223e4-106">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="223e4-107">Pour effectuer cette rubrique, vous devez d’abord terminer [procédure : Créer une](how-to-create-an-activity.md)d’activité.</span><span class="sxs-lookup"><span data-stu-id="223e4-107">To complete this topic, you must first complete [How to: Create an Activity](how-to-create-an-activity.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="223e4-108">Pour télécharger une version complète du didacticiel, consultez [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976)(Windows Workflow Foundation (WF45) - Didacticiel de mise en route).</span><span class="sxs-lookup"><span data-stu-id="223e4-108">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
### <a name="to-create-the-workflow"></a><span data-ttu-id="223e4-109">Pour créer le flux de travail</span><span class="sxs-lookup"><span data-stu-id="223e4-109">To create the workflow</span></span>  
  
1. <span data-ttu-id="223e4-110">Cliquez avec le bouton droit sur **NumberGuessWorkflowActivities** dans **Explorateur de solutions** , puis sélectionnez **Ajouter**, **nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="223e4-110">Right-click **NumberGuessWorkflowActivities** in **Solution Explorer** and select **Add**, **New Item**.</span></span>  
  
2. <span data-ttu-id="223e4-111">Dans le nœud **éléments communs** **installés**, sélectionnez **flux de travail**.</span><span class="sxs-lookup"><span data-stu-id="223e4-111">In the **Installed**, **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="223e4-112">Sélectionnez **activité** dans la liste **flux de travail** .</span><span class="sxs-lookup"><span data-stu-id="223e4-112">Select **Activity** from the **Workflow** list.</span></span>  
  
3. <span data-ttu-id="223e4-113">Tapez `StateMachineNumberGuessWorkflow` dans la zone **nom** , puis cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="223e4-113">Type `StateMachineNumberGuessWorkflow` into the **Name** box and click **Add**.</span></span>  
  
4. <span data-ttu-id="223e4-114">Faites glisser une activité **StateMachine** de la section **machine à États** de la **boîte à outils** et déposez-la sur l’étiquette **déposer l’activité ici** sur l’aire de conception de Workflow.</span><span class="sxs-lookup"><span data-stu-id="223e4-114">Drag a **StateMachine** activity from the **State Machine** section of the **Toolbox** and drop it onto the **Drop activity here** label on the workflow design surface.</span></span>  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a><span data-ttu-id="223e4-115">Pour créer les variables et arguments du flux de travail</span><span class="sxs-lookup"><span data-stu-id="223e4-115">To create the workflow variables and arguments</span></span>  
  
1. <span data-ttu-id="223e4-116">Double-cliquez sur **StateMachineNumberGuessWorkflow. Xaml** dans **Explorateur de solutions** pour afficher le flux de travail dans le concepteur, s’il n’est pas déjà affiché.</span><span class="sxs-lookup"><span data-stu-id="223e4-116">Double-click **StateMachineNumberGuessWorkflow.xaml** in **Solution Explorer** to display the workflow in the designer, if it is not already displayed.</span></span>  
  
2. <span data-ttu-id="223e4-117">Cliquez sur **arguments** dans la partie inférieure gauche du concepteur de flux de travail pour afficher le volet **arguments** .</span><span class="sxs-lookup"><span data-stu-id="223e4-117">Click **Arguments** in the lower-left side of the workflow designer to display the **Arguments** pane.</span></span>  
  
3. <span data-ttu-id="223e4-118">Cliquez sur **créer un argument**.</span><span class="sxs-lookup"><span data-stu-id="223e4-118">Click **Create Argument**.</span></span>  
  
4. <span data-ttu-id="223e4-119">Tapez `MaxNumber` dans la zone **nom** , sélectionnez **in** dans la liste déroulante **direction** , sélectionnez **Int32** dans la liste déroulante **type d’argument** , puis appuyez sur entrée pour enregistrer l’argument.</span><span class="sxs-lookup"><span data-stu-id="223e4-119">Type `MaxNumber` into the **Name** box, select **In** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER to save the argument.</span></span>  
  
5. <span data-ttu-id="223e4-120">Cliquez sur **créer un argument**.</span><span class="sxs-lookup"><span data-stu-id="223e4-120">Click **Create Argument**.</span></span>  
  
6. <span data-ttu-id="223e4-121">Tapez `Turns` dans la zone **nom** située sous l’argument `MaxNumber` récemment ajouté, sélectionnez **out** dans la liste déroulante **direction** , sélectionnez **Int32** dans la liste déroulante **type d’argument** , puis appuyez sur entrée.</span><span class="sxs-lookup"><span data-stu-id="223e4-121">Type `Turns` into the **Name** box that is below the newly added `MaxNumber` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER.</span></span>  
  
7. <span data-ttu-id="223e4-122">Cliquez sur **arguments** dans la partie inférieure gauche du concepteur d’activités pour fermer le volet **arguments** .</span><span class="sxs-lookup"><span data-stu-id="223e4-122">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>  
  
8. <span data-ttu-id="223e4-123">Cliquez sur **variables** dans la partie inférieure gauche du concepteur de flux de travail pour afficher le volet **variables** .</span><span class="sxs-lookup"><span data-stu-id="223e4-123">Click **Variables** in the lower-left side of the workflow designer to display the **Variables** pane.</span></span>  
  
9. <span data-ttu-id="223e4-124">Cliquez sur **créer une variable**.</span><span class="sxs-lookup"><span data-stu-id="223e4-124">Click **Create Variable**.</span></span>  
  
    > [!TIP]
    > <span data-ttu-id="223e4-125">Si aucune zone **créer une variable** n’est affichée, cliquez sur l’activité <xref:System.Activities.Statements.StateMachine> sur l’aire du concepteur de flux de travail pour la sélectionner.</span><span class="sxs-lookup"><span data-stu-id="223e4-125">If no **Create Variable** box is displayed, click the <xref:System.Activities.Statements.StateMachine> activity on the workflow designer surface to select it.</span></span>  
  
10. <span data-ttu-id="223e4-126">Tapez `Guess` dans la zone **nom** , sélectionnez **Int32** dans la liste déroulante **type de variable** , puis appuyez sur entrée pour enregistrer la variable.</span><span class="sxs-lookup"><span data-stu-id="223e4-126">Type `Guess` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
11. <span data-ttu-id="223e4-127">Cliquez sur **créer une variable**.</span><span class="sxs-lookup"><span data-stu-id="223e4-127">Click **Create Variable**.</span></span>  
  
12. <span data-ttu-id="223e4-128">Tapez `Target` dans la zone **nom** , sélectionnez **Int32** dans la liste déroulante **type de variable** , puis appuyez sur entrée pour enregistrer la variable.</span><span class="sxs-lookup"><span data-stu-id="223e4-128">Type `Target` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
13. <span data-ttu-id="223e4-129">Cliquez sur **variables** dans la partie inférieure gauche du concepteur d’activités pour fermer le volet **variables** .</span><span class="sxs-lookup"><span data-stu-id="223e4-129">Click **Variables** in the lower-left side of the activity designer to close the **Variables** pane.</span></span>  
  
### <a name="to-add-the-workflow-activities"></a><span data-ttu-id="223e4-130">Pour ajouter les activités de flux de travail</span><span class="sxs-lookup"><span data-stu-id="223e4-130">To add the workflow activities</span></span>  
  
1. <span data-ttu-id="223e4-131">Cliquez sur **State1** pour le sélectionner.</span><span class="sxs-lookup"><span data-stu-id="223e4-131">Click **State1** to select it.</span></span> <span data-ttu-id="223e4-132">Dans la **fenêtre Propriétés**, remplacez **DisplayName** par `Initialize Target`.</span><span class="sxs-lookup"><span data-stu-id="223e4-132">In the **Properties Window**, change the **DisplayName** to `Initialize Target`.</span></span>  
  
    > [!TIP]
    > <span data-ttu-id="223e4-133">Si la **fenêtre Propriétés** n’est pas affichée, sélectionnez **fenêtre Propriétés** dans le menu **affichage** .</span><span class="sxs-lookup"><span data-stu-id="223e4-133">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>  
  
2. <span data-ttu-id="223e4-134">Double-cliquez sur l’état **initialiser l’initialisation** de la cible dans le concepteur de workflow pour la développer.</span><span class="sxs-lookup"><span data-stu-id="223e4-134">Double-click the newly renamed **Initialize Target** state in the workflow designer to expand it.</span></span>  
  
3. <span data-ttu-id="223e4-135">Faites glisser une activité **Assign** de la section **primitives** de la **boîte à outils** et déposez-la dans la section d' **entrée** de l’État.</span><span class="sxs-lookup"><span data-stu-id="223e4-135">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Entry** section of the state.</span></span> <span data-ttu-id="223e4-136">Tapez `Target` dans la zone **à** et l’expression suivante dans la zone **entrer C# une expression** ou **entrer une expression VB** .</span><span class="sxs-lookup"><span data-stu-id="223e4-136">Type `Target` into the **To** box and the following expression into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    > <span data-ttu-id="223e4-137">Si la fenêtre **boîte à outils** n’est pas affichée, sélectionnez **boîte à outils** dans le menu **affichage** .</span><span class="sxs-lookup"><span data-stu-id="223e4-137">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>  
  
4. <span data-ttu-id="223e4-138">Revenez à la vue globale de l’ordinateur d’État dans le concepteur de flux de travail en cliquant sur **StateMachine** dans l’affichage de navigation en haut du concepteur de Workflow.</span><span class="sxs-lookup"><span data-stu-id="223e4-138">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
5. <span data-ttu-id="223e4-139">Faites glisser une activité **State** de la section **machine à États** de la **boîte à outils** vers le concepteur de flux de travail et placez-la sur l’état **initialiser la cible** .</span><span class="sxs-lookup"><span data-stu-id="223e4-139">Drag a **State** activity from the **State Machine** section of the **Toolbox** onto the workflow designer and hover it over the **Initialize Target** state.</span></span> <span data-ttu-id="223e4-140">Notez que quatre triangles apparaissent autour de l’état **initialiser la cible** lorsque le nouvel État est sur celui-ci.</span><span class="sxs-lookup"><span data-stu-id="223e4-140">Note that four triangles will appear around the **Initialize Target** state when the new state is over it.</span></span> <span data-ttu-id="223e4-141">Déposez le nouvel État sur le triangle qui est immédiatement en dessous de l’état **initialiser la cible** .</span><span class="sxs-lookup"><span data-stu-id="223e4-141">Drop the new state on the triangle that is immediately below the **Initialize Target** state.</span></span> <span data-ttu-id="223e4-142">Cela place le nouvel État sur le workflow et crée une transition de l’état d’initialisation de la **cible** vers le nouvel État.</span><span class="sxs-lookup"><span data-stu-id="223e4-142">This places the new state onto the workflow and creates a transition from the **Initialize Target** state to the new state.</span></span>  
  
6. <span data-ttu-id="223e4-143">Cliquez sur **State1** pour le sélectionner, remplacez **DisplayName** par `Enter Guess`, puis double-cliquez sur l’État dans le concepteur de workflow pour le développer.</span><span class="sxs-lookup"><span data-stu-id="223e4-143">Click **State1** to select it, change the **DisplayName** to `Enter Guess`, and then double-click the state in the workflow designer to expand it.</span></span>  
  
7. <span data-ttu-id="223e4-144">Faites glisser une activité **WriteLine** de la section **primitives** de la **boîte à outils** et déposez-la dans la section d' **entrée** de l’État.</span><span class="sxs-lookup"><span data-stu-id="223e4-144">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Entry** section of the state.</span></span>  
  
8. <span data-ttu-id="223e4-145">Tapez l’expression suivante dans la zone de propriété **Text** de **WriteLine**.</span><span class="sxs-lookup"><span data-stu-id="223e4-145">Type the following expression into the **Text** property box of the **WriteLine**.</span></span>  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
9. <span data-ttu-id="223e4-146">Faites glisser une activité **Assign** de la section **primitives** de la **boîte à outils** et déposez-la sur la section **Exit** de l’État.</span><span class="sxs-lookup"><span data-stu-id="223e4-146">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop onto the **Exit** section of the state.</span></span>  
  
10. <span data-ttu-id="223e4-147">Tapez `Turns` dans la zone **à** et `Turns + 1` dans la zone **entrer C# une expression** ou **entrer une expression VB** .</span><span class="sxs-lookup"><span data-stu-id="223e4-147">Type `Turns` into the **To** box and `Turns + 1` into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>  
  
11. <span data-ttu-id="223e4-148">Revenez à la vue globale de l’ordinateur d’État dans le concepteur de flux de travail en cliquant sur **StateMachine** dans l’affichage de navigation en haut du concepteur de Workflow.</span><span class="sxs-lookup"><span data-stu-id="223e4-148">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
12. <span data-ttu-id="223e4-149">Faites glisser une activité **FinalState** de la section **machine à États** de la **boîte à outils**, placez-la sur l’état **Enter Guess** et déposez-la sur le triangle qui apparaît à droite de l’état **Enter Guess** afin qu’une transition soit créée entre **Enter Guess** et **FinalState**.</span><span class="sxs-lookup"><span data-stu-id="223e4-149">Drag a **FinalState** activity from the **State Machine** section of the **Toolbox**, hover it over the **Enter Guess** state, and drop it onto the triangle that appears to the right of the **Enter Guess** state so that a transition is created between **Enter Guess** and **FinalState**.</span></span>  
  
13. <span data-ttu-id="223e4-150">Le nom par défaut de la transition est **T2**.</span><span class="sxs-lookup"><span data-stu-id="223e4-150">The default name of the transition is **T2**.</span></span> <span data-ttu-id="223e4-151">Cliquez sur la transition dans le concepteur de flux de travail pour la sélectionner et définissez **DisplayName** sur **estimation correcte**.</span><span class="sxs-lookup"><span data-stu-id="223e4-151">Click the transition in the workflow designer to select it, and set its **DisplayName** to **Guess Correct**.</span></span> <span data-ttu-id="223e4-152">Cliquez ensuite sur le **FinalState**et sélectionnez-le, puis faites-le glisser vers la droite afin qu’il y ait de la place pour que le nom de la transition complète s’affiche sans superposer l’un des deux États.</span><span class="sxs-lookup"><span data-stu-id="223e4-152">Then click and select the **FinalState**, and drag it to the right so that there is room for the full transition name to be displayed without overlaying either of the two states.</span></span> <span data-ttu-id="223e4-153">Cela facilitera l'exécution des autres étapes du didacticiel.</span><span class="sxs-lookup"><span data-stu-id="223e4-153">This will make it easier to complete the remaining steps in the tutorial.</span></span>  
  
14. <span data-ttu-id="223e4-154">Double-cliquez sur la transition **estimation correcte** renommée dans le concepteur de workflow pour la développer.</span><span class="sxs-lookup"><span data-stu-id="223e4-154">Double-click the newly renamed **Guess Correct** transition in the workflow designer to expand it.</span></span>  
  
15. <span data-ttu-id="223e4-155">Faites glisser une activité **ReadInt** de la section **NumberGuessWorkflowActivities** de la **boîte à outils** et déposez-la dans la section **Trigger** de la transition.</span><span class="sxs-lookup"><span data-stu-id="223e4-155">Drag a **ReadInt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox** and drop it in the **Trigger** section of the transition.</span></span>  
  
16. <span data-ttu-id="223e4-156">Dans la **fenêtre Propriétés** de l’activité **ReadInt** , tapez `"EnterGuess"` y compris les guillemets dans la zone valeur de la propriété **NomSignet** , puis tapez `Guess` dans la zone valeur de la propriété **result** .</span><span class="sxs-lookup"><span data-stu-id="223e4-156">In the **Properties Window** for the **ReadInt** activity, type `"EnterGuess"` including the quotes into the **BookmarkName** property value box, and type `Guess` into the **Result** property value box</span></span>  
  
17. <span data-ttu-id="223e4-157">Tapez l’expression suivante dans la zone de valeur de propriété **condition** de la transition de l' **estimation correcte** .</span><span class="sxs-lookup"><span data-stu-id="223e4-157">Type the following expression into the **Guess Correct** transition’s **Condition** property value box.</span></span>  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
18. <span data-ttu-id="223e4-158">Revenez à la vue globale de l’ordinateur d’État dans le concepteur de flux de travail en cliquant sur **StateMachine** dans l’affichage de navigation en haut du concepteur de Workflow.</span><span class="sxs-lookup"><span data-stu-id="223e4-158">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="223e4-159">Une transition se produit lorsque l'événement déclencheur est reçu et <xref:System.Activities.Statements.Transition.Condition%2A>, s'il est présent, prend la valeur `True`.</span><span class="sxs-lookup"><span data-stu-id="223e4-159">A transition occurs when the trigger event is received and the <xref:System.Activities.Statements.Transition.Condition%2A>, if present, evaluates to `True`.</span></span> <span data-ttu-id="223e4-160">Pour cette transition, si la `Guess` de l’utilisateur correspond à la `Target`générée de façon aléatoire, le contrôle passe à **FinalState** et le flux de travail se termine.</span><span class="sxs-lookup"><span data-stu-id="223e4-160">For this transition, if the user’s `Guess` matches the randomly generated `Target`, then control passes to the **FinalState** and the workflow completes.</span></span>  
  
19. <span data-ttu-id="223e4-161">Selon que l’estimation est correcte ou non, le flux de travail doit passer au **FinalState** ou revenir à l’état **Enter Guess** pour une autre tentative.</span><span class="sxs-lookup"><span data-stu-id="223e4-161">Depending on whether the guess is correct, the workflow should transition either to the **FinalState** or back to the **Enter Guess** state for another try.</span></span> <span data-ttu-id="223e4-162">Les deux transitions partagent le même déclencheur que l’attente de la réception de l’utilisateur par le biais de l’activité **ReadInt** .</span><span class="sxs-lookup"><span data-stu-id="223e4-162">Both transitions share the same trigger of waiting for the user’s guess to be received via the **ReadInt** activity.</span></span> <span data-ttu-id="223e4-163">Il s'agit d'une transition partagée.</span><span class="sxs-lookup"><span data-stu-id="223e4-163">This is called a shared transition.</span></span> <span data-ttu-id="223e4-164">Pour créer une transition partagée, cliquez sur le cercle qui indique le début de la transition de **estimation correcte** et faites-la glisser vers l’état souhaité.</span><span class="sxs-lookup"><span data-stu-id="223e4-164">To create a shared transition, click the circle that indicates the start of the **Guess Correct** transition and drag it to the desired state.</span></span> <span data-ttu-id="223e4-165">Dans ce cas, la transition est une transition automatique. par conséquent, faites glisser le point de départ de la transition **estimation correcte** , puis déposez-la sur le bas de l’état **Enter Guess** .</span><span class="sxs-lookup"><span data-stu-id="223e4-165">In this case the transition is a self-transition, so drag the start point of the **Guess Correct** transition and drop it back onto the bottom of the **Enter Guess** state.</span></span> <span data-ttu-id="223e4-166">Une fois la transition créée, sélectionnez-la dans le concepteur de flux de travail et définissez sa propriété **DisplayName** sur **deviner incorrect**.</span><span class="sxs-lookup"><span data-stu-id="223e4-166">After creating the transition, select it in the workflow designer and set its **DisplayName** property to **Guess Incorrect**.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="223e4-167">Des transitions partagées peuvent également être créées à partir du concepteur de transition en cliquant sur **Ajouter une transition de déclencheur partagée** en bas du concepteur de transition, puis en sélectionnant l’État cible souhaité dans la liste déroulante **États disponibles pour la connexion** .</span><span class="sxs-lookup"><span data-stu-id="223e4-167">Shared transitions can also be created from within the transition designer by clicking **Add shared trigger transition** at the bottom of the transition designer, and then selecting the desired target state from the **Available states to connect** drop-down.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="223e4-168">Notez que si la condition <xref:System.Activities.Statements.Transition.Condition%2A> d'une transition a pour valeur `false` (ou si toutes les conditions d'une transition de déclencheur partagée ont la valeur `false`), la transition n'a pas lieu et tous les déclencheurs de toutes les transitions de l'état sont replanifiés.</span><span class="sxs-lookup"><span data-stu-id="223e4-168">Note that if the <xref:System.Activities.Statements.Transition.Condition%2A> of a transition evaluates to `false` (or all of the conditions of a shared trigger transition evaluate to `false`), the transition will not occur and all triggers for all the transitions from the state will be rescheduled.</span></span> <span data-ttu-id="223e4-169">Dans ce didacticiel, cette situation ne peut pas se produire en raison de la façon dont les conditions sont configurées (il existe des actions spécifiques lorsque l'estimation est correcte ou incorrecte).</span><span class="sxs-lookup"><span data-stu-id="223e4-169">In this tutorial, this situation cannot happen because of the way the conditions are configured (we have specific actions for whether the guess is correct or incorrect).</span></span>  
  
20. <span data-ttu-id="223e4-170">Double-cliquez sur la transition **Guess incorrect** dans le concepteur de flux de travail pour la développer.</span><span class="sxs-lookup"><span data-stu-id="223e4-170">Double-click the **Guess Incorrect** transition in the workflow designer to expand it.</span></span> <span data-ttu-id="223e4-171">Notez que le **déclencheur** est déjà défini sur la même activité **ReadInt** que celle utilisée par la transition **estimation correcte** .</span><span class="sxs-lookup"><span data-stu-id="223e4-171">Note that the **Trigger** is already set to the same **ReadInt** activity that was used by the **Guess Correct** transition.</span></span>  
  
21. <span data-ttu-id="223e4-172">Tapez l’expression suivante dans la zone de valeur de propriété **condition** .</span><span class="sxs-lookup"><span data-stu-id="223e4-172">Type the following expression into the **Condition** property value box.</span></span>  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
22. <span data-ttu-id="223e4-173">Faites glisser une activité **If** de la section **Control Flow** de la **boîte à outils** et déposez-la dans la section **action** de la transition.</span><span class="sxs-lookup"><span data-stu-id="223e4-173">Drag an **If** activity from the **Control Flow** section of the **Toolbox** and drop it in the **Action** section of the transition.</span></span>  
  
23. <span data-ttu-id="223e4-174">Tapez l’expression suivante dans la zone de valeur de propriété **condition** de l’activité **If** .</span><span class="sxs-lookup"><span data-stu-id="223e4-174">Type the following expression into the **If** activity’s **Condition** property value box.</span></span>  
  
    ```text
    Guess < Target
    ```  
  
24. <span data-ttu-id="223e4-175">Faites glisser deux activités **WriteLine** de la section **primitives** de **la boîte à outils** et déposez-les de façon à ce qu’elles se trouvent dans la section **Then** de l’activité **If** , et l’autre dans la section **else** .</span><span class="sxs-lookup"><span data-stu-id="223e4-175">Drag two **WriteLine** activities from the **Primitives** section of the **Toolbox** and drop them so that one is in the **Then** section of the **If** activity, and one is in the **Else** section.</span></span>  
  
25. <span data-ttu-id="223e4-176">Cliquez sur l’activité **WriteLine** dans la section **Then** pour la sélectionner, puis tapez l’expression suivante dans la zone de valeur de propriété **Text** .</span><span class="sxs-lookup"><span data-stu-id="223e4-176">Click the **WriteLine** activity in the **Then** section to select it, and type the following expression into the **Text** property value box.</span></span>  
  
    ```text
    "Your guess is too low."  
    ```  
  
26. <span data-ttu-id="223e4-177">Cliquez sur l’activité **WriteLine** dans la section **sinon** pour la sélectionner, puis tapez l’expression suivante dans la zone de valeur de propriété **texte** .</span><span class="sxs-lookup"><span data-stu-id="223e4-177">Click the **WriteLine** activity in the **Else** section to select it, and type the following expression into the **Text** property value box.</span></span>  
  
    ```text
    "Your guess is too high."  
    ```  
  
27. <span data-ttu-id="223e4-178">Revenez à la vue globale de l’ordinateur d’État dans le concepteur de flux de travail en cliquant sur **StateMachine** dans l’affichage de navigation en haut du concepteur de Workflow.</span><span class="sxs-lookup"><span data-stu-id="223e4-178">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
     <span data-ttu-id="223e4-179">L'exemple suivant illustre le flux de travail terminé.</span><span class="sxs-lookup"><span data-stu-id="223e4-179">The following example illustrates the completed workflow.</span></span>  
  
     ![Illustration qui montre le flux de travail de l’ordinateur d’état terminé.](./media/how-to-create-a-state-machine-workflow/complete-state-machine-workflow.jpg)  
  
### <a name="to-build-the-workflow"></a><span data-ttu-id="223e4-181">Pour générer le flux de travail</span><span class="sxs-lookup"><span data-stu-id="223e4-181">To build the workflow</span></span>  
  
1. <span data-ttu-id="223e4-182">Appuyez sur Ctrl+Maj+B pour générer la solution.</span><span class="sxs-lookup"><span data-stu-id="223e4-182">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
     <span data-ttu-id="223e4-183">Pour obtenir des instructions sur l’exécution du flux de travail, consultez la rubrique suivante, [procédure : Exécutez un](how-to-run-a-workflow.md)de Workflow.</span><span class="sxs-lookup"><span data-stu-id="223e4-183">For instructions on how to run the workflow, please see the next topic, [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span> <span data-ttu-id="223e4-184">Si vous avez déjà effectué les [procédure : Exécuter un flux de travail](how-to-run-a-workflow.md) étape avec un style de flux de travail différent et souhaitez l’exécuter à l’aide du flux de travail de l’ordinateur d’État à partir de cette étape, passez à la section [pour générer et exécuter l’application](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) de [procédure : Exécutez un de Workflow.](how-to-run-a-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="223e4-184">If you have already completed the [How to: Run a Workflow](how-to-run-a-workflow.md) step with a different style of workflow and wish to run it using the state machine workflow from this step, skip ahead to the [To build and run the application](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) section of [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="223e4-185">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="223e4-185">See also</span></span>

- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [<span data-ttu-id="223e4-186">Programmation Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="223e4-186">Windows Workflow Foundation Programming</span></span>](programming.md)
- [<span data-ttu-id="223e4-187">Conception des workflows</span><span class="sxs-lookup"><span data-stu-id="223e4-187">Designing Workflows</span></span>](designing-workflows.md)
- [<span data-ttu-id="223e4-188">Didacticiel Bien démarrer</span><span class="sxs-lookup"><span data-stu-id="223e4-188">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
- [<span data-ttu-id="223e4-189">Guide pratique: Créer une activité</span><span class="sxs-lookup"><span data-stu-id="223e4-189">How to: Create an Activity</span></span>](how-to-create-an-activity.md)
- [<span data-ttu-id="223e4-190">Guide pratique: Exécuter un flux de travail</span><span class="sxs-lookup"><span data-stu-id="223e4-190">How to: Run a Workflow</span></span>](how-to-run-a-workflow.md)

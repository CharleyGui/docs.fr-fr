---
title: 'Procédure : créer une activité'
description: 'Cet article vous montre comment créer deux activités dans Workflow Foundation : une qui utilise du code pour implémenter sa logique et une autre définie à l’aide d’autres activités.'
ms.date: 09/14/2018
dev_langs:
- csharp
- vb
ms.assetid: c09b1e99-21b5-4d96-9c04-ec31db3f4436
ms.openlocfilehash: c7610d8612eb944afa9c23e1bf2abceeb3a6d38b
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98190765"
---
# <a name="how-to-create-an-activity"></a><span data-ttu-id="eb264-103">Procédure : créer une activité</span><span class="sxs-lookup"><span data-stu-id="eb264-103">How to: Create an Activity</span></span>

<span data-ttu-id="eb264-104">Les activités sont l'unité principale de comportement dans [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="eb264-104">Activities are the core unit of behavior in [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span></span> <span data-ttu-id="eb264-105">La logique d'exécution d'une activité peut être implémentée en code managé ou à l'aide d'autres activités.</span><span class="sxs-lookup"><span data-stu-id="eb264-105">The execution logic of an activity can be implemented in managed code or it can be implemented by using other activities.</span></span> <span data-ttu-id="eb264-106">Cette rubrique indique comment créer deux activités.</span><span class="sxs-lookup"><span data-stu-id="eb264-106">This topic demonstrates how to create two activities.</span></span> <span data-ttu-id="eb264-107">La première activité est une activité simple qui utilise le code pour implémenter la logique d'exécution.</span><span class="sxs-lookup"><span data-stu-id="eb264-107">The first activity is a simple activity that uses code to implement its execution logic.</span></span> <span data-ttu-id="eb264-108">L'implémentation de la deuxième activité est définie à l'aide d'autres activités.</span><span class="sxs-lookup"><span data-stu-id="eb264-108">The implementation of the second activity is defined by using other activities.</span></span> <span data-ttu-id="eb264-109">Ces activités sont utilisées dans les procédures du didacticiel.</span><span class="sxs-lookup"><span data-stu-id="eb264-109">These activities are used in following steps in the tutorial.</span></span>

## <a name="create-the-activity-library-project"></a><span data-ttu-id="eb264-110">Créer le projet de bibliothèque d’activités</span><span class="sxs-lookup"><span data-stu-id="eb264-110">Create the activity library project</span></span>

1. <span data-ttu-id="eb264-111">Ouvrez Visual Studio et choisissez **nouveau**  >  **projet** dans le menu **fichier** .</span><span class="sxs-lookup"><span data-stu-id="eb264-111">Open Visual Studio and choose **New** > **Project** from the **File** menu.</span></span>

2. <span data-ttu-id="eb264-112">Dans la boîte de dialogue **nouveau projet** , sous la catégorie **installé** , sélectionnez flux de travail **Visual C#**  >   (ou **Visual Basic**  >  **Workflow**).</span><span class="sxs-lookup"><span data-stu-id="eb264-112">In the **New Project** dialog, under the **Installed** category, select **Visual C#** > **Workflow** (or **Visual Basic** > **Workflow**).</span></span>

    > [!NOTE]
    > <span data-ttu-id="eb264-113">Si vous ne voyez pas la catégorie de modèle de **flux de travail** , vous devrez peut-être installer le composant **Windows Workflow Foundation** de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="eb264-113">If you don't see the **Workflow** template category, you may need to install the **Windows Workflow Foundation** component of Visual Studio.</span></span> <span data-ttu-id="eb264-114">Choisissez le lien **ouvrir le Visual Studio installer** sur le côté gauche de la boîte de dialogue **nouveau projet** .</span><span class="sxs-lookup"><span data-stu-id="eb264-114">Choose the **Open Visual Studio Installer** link on the left-hand side of the **New Project** dialog.</span></span> <span data-ttu-id="eb264-115">Dans Visual Studio Installer, sélectionnez l’onglet **composants individuels** . Ensuite, sous la catégorie **activités de développement** , sélectionnez le composant **Windows Workflow Foundation** .</span><span class="sxs-lookup"><span data-stu-id="eb264-115">In Visual Studio Installer, select the **Individual components** tab. Then, under the **Development activities** category, select the **Windows Workflow Foundation** component.</span></span> <span data-ttu-id="eb264-116">Choisissez **modifier** pour installer le composant.</span><span class="sxs-lookup"><span data-stu-id="eb264-116">Choose **Modify** to install the component.</span></span>

3. <span data-ttu-id="eb264-117">Sélectionnez le modèle de projet **bibliothèque d’activités** .</span><span class="sxs-lookup"><span data-stu-id="eb264-117">Select the **Activity Library** project template.</span></span> <span data-ttu-id="eb264-118">Entrez `NumberGuessWorkflowActivities` dans la zone **Nom**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="eb264-118">Type `NumberGuessWorkflowActivities` in the **Name** box and then click **OK**.</span></span>

4. <span data-ttu-id="eb264-119">Cliquez avec le bouton droit sur **Activity1.xaml** dans l'**Explorateur de solutions**, puis choisissez **Supprimer**.</span><span class="sxs-lookup"><span data-stu-id="eb264-119">Right-click **Activity1.xaml** in **Solution Explorer** and choose **Delete**.</span></span> <span data-ttu-id="eb264-120">Cliquez sur **OK** pour confirmer.</span><span class="sxs-lookup"><span data-stu-id="eb264-120">Click **OK** to confirm.</span></span>

## <a name="create-the-readint-activity"></a><span data-ttu-id="eb264-121">Créer l’activité ReadInt</span><span class="sxs-lookup"><span data-stu-id="eb264-121">Create the ReadInt activity</span></span>

1. <span data-ttu-id="eb264-122">Choisissez **Ajouter un nouvel élément** dans le menu **projet** .</span><span class="sxs-lookup"><span data-stu-id="eb264-122">Choose **Add New Item** from the **Project** menu.</span></span>

2. <span data-ttu-id="eb264-123">Dans le   >  nœud **éléments communs** installés, sélectionnez **flux de travail**.</span><span class="sxs-lookup"><span data-stu-id="eb264-123">In the **Installed** > **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="eb264-124">Sélectionnez **activité du code** dans la liste **flux de travail** .</span><span class="sxs-lookup"><span data-stu-id="eb264-124">Select **Code Activity** from the **Workflow** list.</span></span>

3. <span data-ttu-id="eb264-125">Entrez `ReadInt` dans la zone **Nom**, puis cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="eb264-125">Type `ReadInt` into the **Name** box and then click **Add**.</span></span>

4. <span data-ttu-id="eb264-126">Remplacez la définition `ReadInt` existante par la définition suivante.</span><span class="sxs-lookup"><span data-stu-id="eb264-126">Replace the existing `ReadInt` definition with the following definition.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#1](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/readint.cs#1)]
     [!code-vb[CFX_WF_GettingStarted#1](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/readint.vb#1)]

    > [!NOTE]
    > <span data-ttu-id="eb264-127">L'activité `ReadInt` dérive de <xref:System.Activities.NativeActivity%601> au lieu de <xref:System.Activities.CodeActivity>, qui est la valeur par défaut pour le modèle d'activité de code.</span><span class="sxs-lookup"><span data-stu-id="eb264-127">The `ReadInt` activity derives from <xref:System.Activities.NativeActivity%601> instead of <xref:System.Activities.CodeActivity>, which is the default for the code activity template.</span></span> <span data-ttu-id="eb264-128"><xref:System.Activities.CodeActivity%601> peut être utilisé si l'activité fournit un résultat unique, exposé via l'argument <xref:System.Activities.Activity%601.Result%2A>, mais <xref:System.Activities.CodeActivity%601> ne prenant pas en charge l'utilisation de signets, <xref:System.Activities.NativeActivity%601> est utilisé.</span><span class="sxs-lookup"><span data-stu-id="eb264-128"><xref:System.Activities.CodeActivity%601> can be used if the activity provides a single result, which is exposed through the <xref:System.Activities.Activity%601.Result%2A> argument, but <xref:System.Activities.CodeActivity%601> does not support the use of bookmarks, so <xref:System.Activities.NativeActivity%601> is used.</span></span>

## <a name="create-the-prompt-activity"></a><span data-ttu-id="eb264-129">Créer l’activité Prompt</span><span class="sxs-lookup"><span data-stu-id="eb264-129">Create the Prompt activity</span></span>

1. <span data-ttu-id="eb264-130">Appuyez sur **CTRL** + **MAJ** + **B** pour générer le projet.</span><span class="sxs-lookup"><span data-stu-id="eb264-130">Press **Ctrl**+**Shift**+**B** to build the project.</span></span> <span data-ttu-id="eb264-131">La génération du projet permet d'utiliser l'activité `ReadInt` dans ce projet pour générer l'activité personnalisée de cette étape.</span><span class="sxs-lookup"><span data-stu-id="eb264-131">Building the project enables the `ReadInt` activity in this project to be used to build the custom activity from this step.</span></span>

2. <span data-ttu-id="eb264-132">Choisissez **Ajouter un nouvel élément** dans le menu **projet** .</span><span class="sxs-lookup"><span data-stu-id="eb264-132">Choose **Add New Item** from the **Project** menu.</span></span>

3. <span data-ttu-id="eb264-133">Dans le   >  nœud **éléments communs** installés, sélectionnez **flux de travail**.</span><span class="sxs-lookup"><span data-stu-id="eb264-133">In the **Installed** > **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="eb264-134">Sélectionnez **Activité** dans la liste **Flux de travail**.</span><span class="sxs-lookup"><span data-stu-id="eb264-134">Select **Activity** from the **Workflow** list.</span></span>

4. <span data-ttu-id="eb264-135">Entrez `Prompt` dans la zone **Nom**, puis cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="eb264-135">Type `Prompt` into the **Name** box and then click **Add**.</span></span>

5. <span data-ttu-id="eb264-136">Double-cliquez sur **prompt. Xaml** dans **Explorateur de solutions** pour l’afficher dans le concepteur s’il n’est pas déjà affiché.</span><span class="sxs-lookup"><span data-stu-id="eb264-136">Double-click **Prompt.xaml** in **Solution Explorer** to display it in the designer if it is not already displayed.</span></span>

6. <span data-ttu-id="eb264-137">Cliquez sur **Arguments** dans la partie inférieure gauche du concepteur d'activités pour afficher le volet **Arguments**.</span><span class="sxs-lookup"><span data-stu-id="eb264-137">Click **Arguments** in the lower-left side of the activity designer to display the **Arguments** pane.</span></span>

7. <span data-ttu-id="eb264-138">Cliquez sur **Créer un argument**.</span><span class="sxs-lookup"><span data-stu-id="eb264-138">Click **Create Argument**.</span></span>

8. <span data-ttu-id="eb264-139">Tapez `BookmarkName` dans la zone **nom** , sélectionnez **in** dans la liste déroulante **direction** , sélectionnez **String** dans la liste déroulante **type d’argument** , puis appuyez sur **entrée** pour enregistrer l’argument.</span><span class="sxs-lookup"><span data-stu-id="eb264-139">Type `BookmarkName` into the **Name** box, select **In** from the **Direction** drop-down list, select **String** from the **Argument type** drop-down list, and then press **Enter** to save the argument.</span></span>

9. <span data-ttu-id="eb264-140">Cliquez sur **Créer un argument**.</span><span class="sxs-lookup"><span data-stu-id="eb264-140">Click **Create Argument**.</span></span>

10. <span data-ttu-id="eb264-141">Tapez `Result` dans la zone **nom** située sous l’argument nouvellement ajouté `BookmarkName` , sélectionnez **out** dans la liste déroulante **direction** , sélectionnez **Int32** dans la liste déroulante **type d’argument** , puis appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="eb264-141">Type `Result` into the **Name** box that is underneath the newly added `BookmarkName` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press **Enter**.</span></span>

11. <span data-ttu-id="eb264-142">Cliquez sur **Créer un argument**.</span><span class="sxs-lookup"><span data-stu-id="eb264-142">Click **Create Argument**.</span></span>

12. <span data-ttu-id="eb264-143">Tapez `Text` dans la zone **nom** , sélectionnez **in** dans la liste déroulante **direction** , sélectionnez **String** dans la liste déroulante **type d’argument** , puis appuyez sur **entrée** pour enregistrer l’argument.</span><span class="sxs-lookup"><span data-stu-id="eb264-143">Type `Text` into the **Name** box, select **In** from the **Direction** drop-down list, select **String** from the **Argument type** drop-down list, and then press **Enter** to save the argument.</span></span>

     <span data-ttu-id="eb264-144">Ces trois arguments sont liés aux arguments correspondants des activités <xref:System.Activities.Statements.WriteLine> et `ReadInt` ajoutées à l'activité `Prompt` dans les étapes suivantes.</span><span class="sxs-lookup"><span data-stu-id="eb264-144">These three arguments are bound to the corresponding arguments of the <xref:System.Activities.Statements.WriteLine> and `ReadInt` activities that are added to the `Prompt` activity in the following steps.</span></span>

13. <span data-ttu-id="eb264-145">Cliquez sur **Arguments** dans la partie inférieure gauche du concepteur d'activités pour fermer le volet **Arguments**.</span><span class="sxs-lookup"><span data-stu-id="eb264-145">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>

14. <span data-ttu-id="eb264-146">Faites glisser une activité **Sequence** de la section **Control Flow** de **la boîte à outils** et déposez-la sur l’étiquette **déposer l’activité ici** du concepteur d’activités **prompt** .</span><span class="sxs-lookup"><span data-stu-id="eb264-146">Drag a **Sequence** activity from the **Control Flow** section of the **Toolbox** and drop it onto the **Drop activity here** label of the **Prompt** activity designer.</span></span>

    > [!TIP]
    > <span data-ttu-id="eb264-147">Si la fenêtre **Boîte à outils** ne s'affiche pas, sélectionnez **Boîte à outils** dans le menu **Afficher**.</span><span class="sxs-lookup"><span data-stu-id="eb264-147">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>

15. <span data-ttu-id="eb264-148">Faites glisser une activité **WriteLine** de la section **primitives** de **la boîte à outils** et déposez-la sur l’étiquette **déposer l’activité ici** de l’activité **Sequence** .</span><span class="sxs-lookup"><span data-stu-id="eb264-148">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Drop activity here** label of the **Sequence** activity.</span></span>

16. <span data-ttu-id="eb264-149">Liez l' **argument Text** de l’activité **WriteLine** à l’argument **Text** de l’activité **prompt** en tapant `Text` dans la zone **entrer une expression C#** ou **entrer une expression VB** dans la fenêtre **Propriétés** , puis appuyez deux fois sur la touche **Tab** .</span><span class="sxs-lookup"><span data-stu-id="eb264-149">Bind the **Text** argument of the **WriteLine** activity to the **Text** argument of the **Prompt** activity by typing `Text` into the **Enter a C# expression** or **Enter a VB expression** box in the **Properties** window, and then press the **Tab** key two times.</span></span> <span data-ttu-id="eb264-150">Cela ferme la fenêtre de liste des membres IntelliSense et enregistre la valeur de propriété en déplaçant la sélection en dehors de la propriété.</span><span class="sxs-lookup"><span data-stu-id="eb264-150">This dismisses the IntelliSense list members window and saves the property value by moving the selection off the property.</span></span> <span data-ttu-id="eb264-151">Cette propriété peut également être définie en tapant `Text` dans la zone **entrer une expression C#** ou **entrer une expression VB** sur l’activité elle-même.</span><span class="sxs-lookup"><span data-stu-id="eb264-151">This property can also be set by typing `Text` into the **Enter a C# expression** or **Enter a VB expression** box on the activity itself.</span></span>

    > [!TIP]
    > <span data-ttu-id="eb264-152">Si la **fenêtre Propriétés** n’est pas affichée, sélectionnez **fenêtre Propriétés** dans le menu **affichage** .</span><span class="sxs-lookup"><span data-stu-id="eb264-152">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>

17. <span data-ttu-id="eb264-153">Faites glisser une activité **ReadInt** de la section **NumberGuessWorkflowActivities** de la **boîte à outils** et déposez-la dans l’activité **Sequence** afin qu’elle suive l’activité **WriteLine** .</span><span class="sxs-lookup"><span data-stu-id="eb264-153">Drag a **ReadInt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox** and drop it in the **Sequence** activity so that it follows the **WriteLine** activity.</span></span>

18. <span data-ttu-id="eb264-154">Liez l’argument **NomSignet** de l' **activité ReadInt** à l’argument **NomSignet** de l’activité **prompt** en tapant `BookmarkName` dans la zone **entrer une expression VB** à droite de l’argument **NomSignet** dans la **fenêtre Propriétés**, puis appuyez deux fois sur la touche **Tab** pour fermer la fenêtre des membres de la liste IntelliSense et enregistrer la propriété.</span><span class="sxs-lookup"><span data-stu-id="eb264-154">Bind the **BookmarkName** argument of the **ReadInt** activity to the **BookmarkName** argument of the **Prompt** activity by typing `BookmarkName` into the **Enter a VB expression** box to the right of the **BookmarkName** argument in the **Properties Window**, and then press the **Tab** key two times to close the IntelliSense list members window and save the property.</span></span>

19. <span data-ttu-id="eb264-155">Liez l’argument **result** de l' **activité ReadInt** à l’argument **result** de l’activité **prompt** en tapant `Result` dans la zone **entrer une expression VB** à droite de l’argument **result** dans la **fenêtre Propriétés**, puis appuyez deux fois sur la touche **Tab** .</span><span class="sxs-lookup"><span data-stu-id="eb264-155">Bind the **Result** argument of the **ReadInt** activity to the **Result** argument of the **Prompt** activity by typing `Result` into the **Enter a VB expression** box to the right of the **Result** argument in the **Properties Window**, and then press the **Tab** key two times.</span></span>

20. <span data-ttu-id="eb264-156">Appuyez sur **CTRL** + **MAJ** + **B** pour générer la solution.</span><span class="sxs-lookup"><span data-stu-id="eb264-156">Press **Ctrl**+**Shift**+**B** to build the solution.</span></span>

## <a name="next-steps"></a><span data-ttu-id="eb264-157">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="eb264-157">Next steps</span></span>

<span data-ttu-id="eb264-158">Pour obtenir des instructions sur la création d’un workflow à l’aide de ces activités, consultez l’étape suivante du didacticiel, [How to : Create a Workflow](how-to-create-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="eb264-158">For instructions on how to create a workflow by using these activities, see the next step in the tutorial, [How to: Create a Workflow](how-to-create-a-workflow.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="eb264-159">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eb264-159">See also</span></span>

- <xref:System.Activities.CodeActivity>
- <xref:System.Activities.NativeActivity%601>
- [<span data-ttu-id="eb264-160">Conception et implémentation d'activités personnalisées</span><span class="sxs-lookup"><span data-stu-id="eb264-160">Designing and Implementing Custom Activities</span></span>](designing-and-implementing-custom-activities.md)
- [<span data-ttu-id="eb264-161">Didacticiel de mise en route</span><span class="sxs-lookup"><span data-stu-id="eb264-161">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
- [<span data-ttu-id="eb264-162">Procédure : créer un workflow</span><span class="sxs-lookup"><span data-stu-id="eb264-162">How to: Create a Workflow</span></span>](how-to-create-a-workflow.md)
- [<span data-ttu-id="eb264-163">Utilisation d'ExpressionTextBox dans un concepteur d'activités personnalisées</span><span class="sxs-lookup"><span data-stu-id="eb264-163">Using the ExpressionTextBox in a Custom Activity Designer</span></span>](./samples/using-the-expressiontextbox-in-a-custom-activity-designer.md)

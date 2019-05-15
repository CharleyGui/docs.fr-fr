---
title: 'Procédure : créer une activité'
ms.date: 09/14/2018
dev_langs:
- csharp
- vb
ms.assetid: c09b1e99-21b5-4d96-9c04-ec31db3f4436
ms.openlocfilehash: 6d74af6af6cea0d65c33db67ecbfd71ac1d5c346
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65636954"
---
# <a name="how-to-create-an-activity"></a><span data-ttu-id="73181-102">Procédure : créer une activité</span><span class="sxs-lookup"><span data-stu-id="73181-102">How to: Create an Activity</span></span>

<span data-ttu-id="73181-103">Les activités sont l'unité principale de comportement dans [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="73181-103">Activities are the core unit of behavior in [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span></span> <span data-ttu-id="73181-104">La logique d'exécution d'une activité peut être implémentée en code managé ou à l'aide d'autres activités.</span><span class="sxs-lookup"><span data-stu-id="73181-104">The execution logic of an activity can be implemented in managed code or it can be implemented by using other activities.</span></span> <span data-ttu-id="73181-105">Cette rubrique indique comment créer deux activités.</span><span class="sxs-lookup"><span data-stu-id="73181-105">This topic demonstrates how to create two activities.</span></span> <span data-ttu-id="73181-106">La première activité est une activité simple qui utilise le code pour implémenter la logique d'exécution.</span><span class="sxs-lookup"><span data-stu-id="73181-106">The first activity is a simple activity that uses code to implement its execution logic.</span></span> <span data-ttu-id="73181-107">L'implémentation de la deuxième activité est définie à l'aide d'autres activités.</span><span class="sxs-lookup"><span data-stu-id="73181-107">The implementation of the second activity is defined by using other activities.</span></span> <span data-ttu-id="73181-108">Ces activités sont utilisées dans les procédures du didacticiel.</span><span class="sxs-lookup"><span data-stu-id="73181-108">These activities are used in following steps in the tutorial.</span></span>

> [!NOTE]
> <span data-ttu-id="73181-109">Pour télécharger une version complète du didacticiel, consultez [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976)(Windows Workflow Foundation (WF45) - Didacticiel de mise en route).</span><span class="sxs-lookup"><span data-stu-id="73181-109">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>

## <a name="create-the-activity-library-project"></a><span data-ttu-id="73181-110">Créer le projet de bibliothèque d’activités</span><span class="sxs-lookup"><span data-stu-id="73181-110">Create the activity library project</span></span>

1. <span data-ttu-id="73181-111">Ouvrez Visual Studio et choisissez **New** > **projet** à partir de la **fichier** menu.</span><span class="sxs-lookup"><span data-stu-id="73181-111">Open Visual Studio and choose **New** > **Project** from the **File** menu.</span></span>

2. <span data-ttu-id="73181-112">Dans le **nouveau projet** boîte de dialogue, sous le **installé** catégorie, sélectionnez **Visual C#** > **Workflow** (ou **Visual Basic** > **Workflow**).</span><span class="sxs-lookup"><span data-stu-id="73181-112">In the **New Project** dialog, under the **Installed** category, select **Visual C#** > **Workflow** (or **Visual Basic** > **Workflow**).</span></span>

    > [!NOTE]
    > <span data-ttu-id="73181-113">Si vous ne voyez pas le **Workflow** catégorie du modèle, vous devrez peut-être installer le **Windows Workflow Foundation** composant de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="73181-113">If you don't see the **Workflow** template category, you may need to install the **Windows Workflow Foundation** component of Visual Studio.</span></span> <span data-ttu-id="73181-114">Choisissez le **ouvrir Visual Studio Installer** lien sur le côté gauche de la **nouveau projet** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="73181-114">Choose the **Open Visual Studio Installer** link on the left-hand side of the **New Project** dialog.</span></span> <span data-ttu-id="73181-115">Dans le programme d’installation de Visual Studio, sélectionnez le **composants individuels** onglet. Ensuite, sous la **activités de développement** catégorie, sélectionnez le **Windows Workflow Foundation** composant.</span><span class="sxs-lookup"><span data-stu-id="73181-115">In Visual Studio Installer, select the **Individual components** tab. Then, under the **Development activities** category, select the **Windows Workflow Foundation** component.</span></span> <span data-ttu-id="73181-116">Choisissez **modifier** pour installer le composant.</span><span class="sxs-lookup"><span data-stu-id="73181-116">Choose **Modify** to install the component.</span></span>

3. <span data-ttu-id="73181-117">Sélectionnez le **bibliothèque d’activités** modèle de projet.</span><span class="sxs-lookup"><span data-stu-id="73181-117">Select the **Activity Library** project template.</span></span> <span data-ttu-id="73181-118">Type `NumberGuessWorkflowActivities` dans le **nom** , puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="73181-118">Type `NumberGuessWorkflowActivities` in the **Name** box and then click **OK**.</span></span>

4. <span data-ttu-id="73181-119">Avec le bouton droit **Activity1.xaml** dans **l’Explorateur de solutions** et choisissez **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="73181-119">Right-click **Activity1.xaml** in **Solution Explorer** and choose **Delete**.</span></span> <span data-ttu-id="73181-120">Pour confirmer, cliquez sur **OK** .</span><span class="sxs-lookup"><span data-stu-id="73181-120">Click **OK** to confirm.</span></span>

## <a name="create-the-readint-activity"></a><span data-ttu-id="73181-121">Création de l’activité ReadInt</span><span class="sxs-lookup"><span data-stu-id="73181-121">Create the ReadInt activity</span></span>

1. <span data-ttu-id="73181-122">Choisissez **ajouter un nouvel élément** à partir de la **projet** menu.</span><span class="sxs-lookup"><span data-stu-id="73181-122">Choose **Add New Item** from the **Project** menu.</span></span>

2. <span data-ttu-id="73181-123">Dans le **installé** > **éléments communs** nœud, sélectionnez **Workflow**.</span><span class="sxs-lookup"><span data-stu-id="73181-123">In the **Installed** > **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="73181-124">Sélectionnez **activité de Code** à partir de la **Workflow** liste.</span><span class="sxs-lookup"><span data-stu-id="73181-124">Select **Code Activity** from the **Workflow** list.</span></span>

3. <span data-ttu-id="73181-125">Type `ReadInt` dans le **nom** , puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="73181-125">Type `ReadInt` into the **Name** box and then click **Add**.</span></span>

4. <span data-ttu-id="73181-126">Remplacez la définition `ReadInt` existante par la définition suivante.</span><span class="sxs-lookup"><span data-stu-id="73181-126">Replace the existing `ReadInt` definition with the following definition.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#1](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/readint.cs#1)]
     [!code-vb[CFX_WF_GettingStarted#1](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/readint.vb#1)]

    > [!NOTE]
    > <span data-ttu-id="73181-127">L'activité `ReadInt` dérive de <xref:System.Activities.NativeActivity%601> au lieu de <xref:System.Activities.CodeActivity>, qui est la valeur par défaut pour le modèle d'activité de code.</span><span class="sxs-lookup"><span data-stu-id="73181-127">The `ReadInt` activity derives from <xref:System.Activities.NativeActivity%601> instead of <xref:System.Activities.CodeActivity>, which is the default for the code activity template.</span></span> <span data-ttu-id="73181-128"><xref:System.Activities.CodeActivity%601> peut être utilisé si l'activité fournit un résultat unique, exposé via l'argument <xref:System.Activities.Activity%601.Result%2A>, mais <xref:System.Activities.CodeActivity%601> ne prenant pas en charge l'utilisation de signets, <xref:System.Activities.NativeActivity%601> est utilisé.</span><span class="sxs-lookup"><span data-stu-id="73181-128"><xref:System.Activities.CodeActivity%601> can be used if the activity provides a single result, which is exposed through the <xref:System.Activities.Activity%601.Result%2A> argument, but <xref:System.Activities.CodeActivity%601> does not support the use of bookmarks, so <xref:System.Activities.NativeActivity%601> is used.</span></span>

## <a name="create-the-prompt-activity"></a><span data-ttu-id="73181-129">Créer l’activité Prompt</span><span class="sxs-lookup"><span data-stu-id="73181-129">Create the Prompt activity</span></span>

1. <span data-ttu-id="73181-130">Appuyez sur **Ctrl**+**MAJ**+**B** pour générer le projet.</span><span class="sxs-lookup"><span data-stu-id="73181-130">Press **Ctrl**+**Shift**+**B** to build the project.</span></span> <span data-ttu-id="73181-131">La génération du projet permet d'utiliser l'activité `ReadInt` dans ce projet pour générer l'activité personnalisée de cette étape.</span><span class="sxs-lookup"><span data-stu-id="73181-131">Building the project enables the `ReadInt` activity in this project to be used to build the custom activity from this step.</span></span>

2. <span data-ttu-id="73181-132">Choisissez **ajouter un nouvel élément** à partir de la **projet** menu.</span><span class="sxs-lookup"><span data-stu-id="73181-132">Choose **Add New Item** from the **Project** menu.</span></span>

3. <span data-ttu-id="73181-133">Dans le **installé** > **éléments communs** nœud, sélectionnez **Workflow**.</span><span class="sxs-lookup"><span data-stu-id="73181-133">In the **Installed** > **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="73181-134">Sélectionnez **activité** à partir de la **Workflow** liste.</span><span class="sxs-lookup"><span data-stu-id="73181-134">Select **Activity** from the **Workflow** list.</span></span>

4. <span data-ttu-id="73181-135">Type `Prompt` dans le **nom** , puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="73181-135">Type `Prompt` into the **Name** box and then click **Add**.</span></span>

5. <span data-ttu-id="73181-136">Double-cliquez sur **Prompt.xaml** dans **l’Explorateur de solutions** à afficher dans le concepteur si elle n’est pas déjà affichée.</span><span class="sxs-lookup"><span data-stu-id="73181-136">Double-click **Prompt.xaml** in **Solution Explorer** to display it in the designer if it is not already displayed.</span></span>

6. <span data-ttu-id="73181-137">Cliquez sur **Arguments** dans la partie inférieure gauche du Concepteur d’activités pour afficher le **Arguments** volet.</span><span class="sxs-lookup"><span data-stu-id="73181-137">Click **Arguments** in the lower-left side of the activity designer to display the **Arguments** pane.</span></span>

7. <span data-ttu-id="73181-138">Cliquez sur **créer un Argument**.</span><span class="sxs-lookup"><span data-stu-id="73181-138">Click **Create Argument**.</span></span>

8. <span data-ttu-id="73181-139">Type `BookmarkName` dans le **nom** boîte, sélectionnez **dans** à partir de la **Direction** liste déroulante, sélectionnez **chaîne** à partir de la **Type d’argument** liste déroulante, puis appuyez sur **entrée** pour enregistrer l’argument.</span><span class="sxs-lookup"><span data-stu-id="73181-139">Type `BookmarkName` into the **Name** box, select **In** from the **Direction** drop-down list, select **String** from the **Argument type** drop-down list, and then press **Enter** to save the argument.</span></span>

9. <span data-ttu-id="73181-140">Cliquez sur **créer un Argument**.</span><span class="sxs-lookup"><span data-stu-id="73181-140">Click **Create Argument**.</span></span>

10. <span data-ttu-id="73181-141">Type `Result` dans le **nom** boîte qui se trouve sous récemment ajouté `BookmarkName` argument, sélectionnez **Out** à partir de la **Direction** liste déroulante, sélectionnez **Int32** à partir de la **type d’Argument** liste déroulante, puis appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="73181-141">Type `Result` into the **Name** box that is underneath the newly added `BookmarkName` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press **Enter**.</span></span>

11. <span data-ttu-id="73181-142">Cliquez sur **créer un Argument**.</span><span class="sxs-lookup"><span data-stu-id="73181-142">Click **Create Argument**.</span></span>

12. <span data-ttu-id="73181-143">Type `Text` dans le **nom** boîte, sélectionnez **dans** à partir de la **Direction** liste déroulante, sélectionnez **chaîne** à partir de la **Type d’argument** liste déroulante, puis appuyez sur **entrée** pour enregistrer l’argument.</span><span class="sxs-lookup"><span data-stu-id="73181-143">Type `Text` into the **Name** box, select **In** from the **Direction** drop-down list, select **String** from the **Argument type** drop-down list, and then press **Enter** to save the argument.</span></span>

     <span data-ttu-id="73181-144">Ces trois arguments sont liés aux arguments correspondants des activités <xref:System.Activities.Statements.WriteLine> et `ReadInt` ajoutées à l'activité `Prompt` dans les étapes suivantes.</span><span class="sxs-lookup"><span data-stu-id="73181-144">These three arguments are bound to the corresponding arguments of the <xref:System.Activities.Statements.WriteLine> and `ReadInt` activities that are added to the `Prompt` activity in the following steps.</span></span>

13. <span data-ttu-id="73181-145">Cliquez sur **Arguments** dans la partie inférieure gauche du Concepteur d’activités pour fermer la **Arguments** volet.</span><span class="sxs-lookup"><span data-stu-id="73181-145">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>

14. <span data-ttu-id="73181-146">Faites glisser un **séquence** activité à partir de la **flux de contrôle** section de la **boîte à outils** et déposez-le sur le **déposer l’activité ici** étiquette de la **Invite** Concepteur d’activités.</span><span class="sxs-lookup"><span data-stu-id="73181-146">Drag a **Sequence** activity from the **Control Flow** section of the **Toolbox** and drop it onto the **Drop activity here** label of the **Prompt** activity designer.</span></span>

    > [!TIP]
    > <span data-ttu-id="73181-147">Si le **boîte à outils** fenêtre n’est pas affichée, sélectionnez **boîte à outils** à partir de la **vue** menu.</span><span class="sxs-lookup"><span data-stu-id="73181-147">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>

15. <span data-ttu-id="73181-148">Faites glisser un **WriteLine** activité à partir de la **Primitives** section de la **boîte à outils** et déposez-le sur le **déposer l’activité ici** étiquette de la **Séquence** activité.</span><span class="sxs-lookup"><span data-stu-id="73181-148">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Drop activity here** label of the **Sequence** activity.</span></span>

16. <span data-ttu-id="73181-149">Lier le **texte** argument de la **WriteLine** activité à la **texte** argument de la **invite** activité en tapant `Text` dans le **entrer une expression c#** ou **entrer une expression VB** zone le **propriétés** fenêtre et appuyez sur la **onglet** clé de deux fois.</span><span class="sxs-lookup"><span data-stu-id="73181-149">Bind the **Text** argument of the **WriteLine** activity to the **Text** argument of the **Prompt** activity by typing `Text` into the **Enter a C# expression** or **Enter a VB expression** box in the **Properties** window, and then press the **Tab** key two times.</span></span> <span data-ttu-id="73181-150">Cela ferme la fenêtre de liste des membres IntelliSense et enregistre la valeur de propriété en déplaçant la sélection en dehors de la propriété.</span><span class="sxs-lookup"><span data-stu-id="73181-150">This dismisses the IntelliSense list members window and saves the property value by moving the selection off the property.</span></span> <span data-ttu-id="73181-151">Cette propriété peut également être définie en tapant `Text` dans le **entrer une expression c#** ou **entrer une expression VB** boîte sur l’activité elle-même.</span><span class="sxs-lookup"><span data-stu-id="73181-151">This property can also be set by typing `Text` into the **Enter a C# expression** or **Enter a VB expression** box on the activity itself.</span></span>

    > [!TIP]
    > <span data-ttu-id="73181-152">Si le **fenêtre Propriétés** n’est pas affiché, sélectionnez **fenêtre Propriétés** à partir de la **vue** menu.</span><span class="sxs-lookup"><span data-stu-id="73181-152">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>

17. <span data-ttu-id="73181-153">Faites glisser un **ReadInt** activité à partir de la **NumberGuessWorkflowActivities** section de la **boîte à outils** et déposez-le dans la **séquence** activité afin qu’elle suive le **WriteLine** activité.</span><span class="sxs-lookup"><span data-stu-id="73181-153">Drag a **ReadInt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox** and drop it in the **Sequence** activity so that it follows the **WriteLine** activity.</span></span>

18. <span data-ttu-id="73181-154">Lier le **BookmarkName** argument de la **ReadInt** activité à la **BookmarkName** argument de la **invite** activité en tapant `BookmarkName` dans le **entrer une expression VB** zone à droite de la **BookmarkName** argument dans le **fenêtre Propriétés**, puis appuyez sur la **Onglet** deux reprises pour fermer la fenêtre de membres de liste IntelliSense et enregistrer la propriété de clé.</span><span class="sxs-lookup"><span data-stu-id="73181-154">Bind the **BookmarkName** argument of the **ReadInt** activity to the **BookmarkName** argument of the **Prompt** activity by typing `BookmarkName` into the **Enter a VB expression** box to the right of the **BookmarkName** argument in the **Properties Window**, and then press the **Tab** key two times to close the IntelliSense list members window and save the property.</span></span>

19. <span data-ttu-id="73181-155">Lier le **résultat** argument de la **ReadInt** activité à la **résultat** argument de la **invite** activité en tapant `Result` dans le **entrer une expression VB** zone à droite de la **résultat** argument dans le **fenêtre Propriétés**, puis appuyez sur la **onglet** deux fois la clé.</span><span class="sxs-lookup"><span data-stu-id="73181-155">Bind the **Result** argument of the **ReadInt** activity to the **Result** argument of the **Prompt** activity by typing `Result` into the **Enter a VB expression** box to the right of the **Result** argument in the **Properties Window**, and then press the **Tab** key two times.</span></span>

20. <span data-ttu-id="73181-156">Appuyez sur **Ctrl**+**MAJ**+**B** pour générer la solution.</span><span class="sxs-lookup"><span data-stu-id="73181-156">Press **Ctrl**+**Shift**+**B** to build the solution.</span></span>

## <a name="next-steps"></a><span data-ttu-id="73181-157">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="73181-157">Next steps</span></span>

<span data-ttu-id="73181-158">Pour obtenir des instructions sur la création d’un flux de travail à l’aide de ces activités, consultez l’étape suivante du didacticiel, [Comment : Créer un flux de travail](how-to-create-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="73181-158">For instructions on how to create a workflow by using these activities, see the next step in the tutorial, [How to: Create a Workflow](how-to-create-a-workflow.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="73181-159">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="73181-159">See also</span></span>

- <xref:System.Activities.CodeActivity>
- <xref:System.Activities.NativeActivity%601>
- [<span data-ttu-id="73181-160">Conception et implémentation d’activités personnalisées</span><span class="sxs-lookup"><span data-stu-id="73181-160">Designing and Implementing Custom Activities</span></span>](designing-and-implementing-custom-activities.md)
- [<span data-ttu-id="73181-161">Didacticiel Bien démarrer</span><span class="sxs-lookup"><span data-stu-id="73181-161">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
- [<span data-ttu-id="73181-162">Guide pratique pour Créer un flux de travail</span><span class="sxs-lookup"><span data-stu-id="73181-162">How to: Create a Workflow</span></span>](how-to-create-a-workflow.md)
- [<span data-ttu-id="73181-163">Utilisation d’ExpressionTextBox dans un concepteur d’activités personnalisées</span><span class="sxs-lookup"><span data-stu-id="73181-163">Using the ExpressionTextBox in a Custom Activity Designer</span></span>](./samples/using-the-expressiontextbox-in-a-custom-activity-designer.md)

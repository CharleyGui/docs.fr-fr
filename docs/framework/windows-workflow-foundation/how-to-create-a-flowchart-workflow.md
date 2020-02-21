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
# <a name="how-to-create-a-flowchart-workflow"></a>Procédure : créer un workflow d’organigramme
Les workflows peuvent être construits aussi bien à partir d'activités intégrées que d'activités personnalisées. Cette rubrique décrit comment créer un workflow qui utilise à la fois des activités intégrées, telles que l’activité <xref:System.Activities.Statements.Flowchart>, et les activités personnalisées de la [précédente Comment : Créer une activité](how-to-create-an-activity.md) rubrique. Le workflow modélise un jeu d'estimation de nombre.  
  
> [!NOTE]
> Chaque rubrique du didacticiel de mise en route dépend des rubriques précédentes. Pour effectuer cette rubrique, vous devez d’abord terminer [procédure : Créer une](how-to-create-an-activity.md)d’activité.  
  
> [!NOTE]
> Pour télécharger une version complète du didacticiel, consultez [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976)(Windows Workflow Foundation (WF45) - Didacticiel de mise en route).  
  
### <a name="to-create-the-workflow"></a>Pour créer le flux de travail  
  
1. Cliquez avec le bouton droit sur **NumberGuessWorkflowActivities** dans **Explorateur de solutions** , puis sélectionnez **Ajouter**, **nouvel élément**.  
  
2. Dans le nœud **éléments communs** **installés**, sélectionnez **flux de travail**. Sélectionnez **activité** dans la liste **flux de travail** .  
  
3. Tapez `FlowchartNumberGuessWorkflow` dans la zone **nom** , puis cliquez sur **Ajouter**.  
  
4. Faites glisser une activité **Flowchart** de la section **organigramme** de la **boîte à outils** et déposez-la sur l’étiquette déposer l' **activité ici** sur l’aire de conception de Workflow.  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a>Pour créer les variables et arguments du flux de travail  
  
1. Double-cliquez sur **FlowchartNumberGuessWorkflow. Xaml** dans **Explorateur de solutions** pour afficher le flux de travail dans le concepteur, s’il n’est pas déjà affiché.  
  
2. Cliquez sur **arguments** dans la partie inférieure gauche du concepteur de flux de travail pour afficher le volet **arguments** .  
  
3. Cliquez sur **créer un argument**.  
  
4. Tapez `MaxNumber` dans la zone **nom** , sélectionnez **in** dans la liste déroulante **direction** , sélectionnez **Int32** dans la liste déroulante **type d’argument** , puis appuyez sur entrée pour enregistrer l’argument.  
  
5. Cliquez sur **créer un argument**.  
  
6. Tapez `Turns` dans la zone **nom** située sous l’argument `MaxNumber` récemment ajouté, sélectionnez **out** dans la liste déroulante **direction** , sélectionnez **Int32** dans la liste déroulante **type d’argument** , puis appuyez sur entrée.  
  
7. Cliquez sur **arguments** dans la partie inférieure gauche du concepteur d’activités pour fermer le volet **arguments** .  
  
8. Cliquez sur **variables** dans la partie inférieure gauche du concepteur de flux de travail pour afficher le volet **variables** .  
  
9. Cliquez sur **créer une variable**.  
  
    > [!TIP]
    > Si aucune zone **créer une variable** n’est affichée, cliquez sur l’activité <xref:System.Activities.Statements.Flowchart> sur l’aire du concepteur de flux de travail pour la sélectionner.  
  
10. Tapez `Guess` dans la zone **nom** , sélectionnez **Int32** dans la liste déroulante **type de variable** , puis appuyez sur entrée pour enregistrer la variable.  
  
11. Cliquez sur **créer une variable**.  
  
12. Tapez `Target` dans la zone **nom** , sélectionnez **Int32** dans la liste déroulante **type de variable** , puis appuyez sur entrée pour enregistrer la variable.  
  
13. Cliquez sur **variables** dans la partie inférieure gauche du concepteur d’activités pour fermer le volet **variables** .  
  
### <a name="to-add-the-workflow-activities"></a>Pour ajouter les activités de flux de travail  
  
1. Faites glisser une activité **Assign** de la section **primitives** de la **boîte à outils** et placez-la sur le nœud de **départ** , qui se trouve en haut de l’organigramme. Lorsque l’activité **Assign** se trouve sur le nœud de **départ** , trois triangles apparaissent autour du nœud de **démarrage** . Déposez l’activité **Assign** sur le triangle qui est directement sous le nœud **Start** . Cela permet de lier les deux éléments ensemble et de désigner l’activité **Assign** comme première activité dans l’organigramme.  
  
    > [!NOTE]
    > Les activités peuvent également être définies comme activité de départ dans le workflow en les liant manuellement au nœud de démarrage. Pour ce faire, placez le curseur de la souris sur le nœud de **démarrage** , cliquez sur l’un des rectangles qui s’affichent lorsque la souris se trouve sur le nœud de **départ** , puis faites glisser la ligne de connexion vers le bas jusqu’à l’activité souhaitée et déposez-la sur l’un des rectangles qui s’affichent. Vous pouvez également désigner une activité comme activité de départ en cliquant dessus avec le bouton droit, puis en choisissant **définir comme nœud de démarrage**.  
  
2. Tapez `Target` dans la zone **à** et l’expression suivante dans la zone **entrer C# une expression** ou **entrer une expression VB** .  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    > Si la fenêtre **boîte à outils** n’est pas affichée, sélectionnez **boîte à outils** dans le menu **affichage** .  
  
3. Faites glisser une activité **prompt** de la section **NumberGuessWorkflowActivities** de la **boîte à outils**, déposez-la en dessous de l’activité **Assign** de l’étape précédente, puis connectez l’activité **prompt** à l’activité **Assign** . Il existe trois façons de connecter les deux activités. La première consiste à les connecter lorsque vous déposez l’activité **prompt** sur le Workflow. Lorsque vous faites glisser l’activité **prompt** vers le workflow, placez-la sur l’activité **Assign** et déposez-la sur l’un des quatre triangles qui s’affiche lorsque l’activité **prompt** est positionnée sur l’activité **Assign** . La seconde consiste à déposer l’activité **prompt** sur le workflow à l’emplacement souhaité. Ensuite, placez le pointeur de la souris sur l’activité **Assign** et faites glisser l’un des rectangles qui s’affichent vers le bas de l’activité **prompt** . Faites glisser la souris de sorte que la ligne de connexion de l’activité **Assign** se connecte à l’un des rectangles de l’activité **prompt** , puis relâchez le bouton de la souris. La troisième méthode est très similaire à la première, mais au lieu de faire glisser l’activité **prompt** à partir de la **boîte à outils**, vous la faites glisser à partir de son emplacement sur l’aire de conception de workflow, vous la Positionnez sur l’activité **Assign** et vous la déposez sur l’un des triangles qui s’affiche.  
  
4. Dans la **fenêtre Propriétés** de l’activité **Prompt** , tapez `"EnterGuess"` y compris les guillemets dans la zone valeur de la propriété **NomSignet** . Tapez `Guess` dans la zone valeur de la propriété de **résultat** , puis tapez l’expression suivante dans la zone de propriété **texte** .  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
    > [!TIP]
    > Si la **fenêtre Propriétés** n’est pas affichée, sélectionnez **fenêtre Propriétés** dans le menu **affichage** .  
  
5. Faites glisser une activité **Assign** de la section **primitives** de la **boîte à outils** et connectez-la à l’aide de l’une des méthodes décrites à l’étape précédente afin qu’elle soit en dessous de l’activité **prompt** .  
  
6. Tapez `Turns` dans la zone **à** et `Turns + 1` dans la zone **entrer C# une expression** ou **entrer une expression VB** .  
  
7. Faites glisser un **FlowDecision** à partir de la section **Flowchart** de la **boîte à outils** et connectez-le sous l’activité **Assign** . Dans la **fenêtre Propriétés**, tapez l’expression suivante dans la zone valeur de la propriété **condition** .  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
8. Faites glisser une autre activité **FlowDecision** de la **boîte à outils** et déposez-la en dessous de la première. Connectez les deux activités en faisant glisser le rectangle qui est étiqueté **false** sur l’activité **FlowDecision** supérieure vers le rectangle situé en haut de la deuxième activité **FlowDecision** .  
  
    > [!TIP]
    > Si vous ne voyez pas les étiquettes **true** et **false** sur le **FlowDecision**, pointez la souris sur **FlowDecision**.  
  
9. Cliquez sur la deuxième activité **FlowDecision** pour la sélectionner. Dans la **fenêtre Propriétés**, tapez l’expression suivante dans la zone valeur de la propriété **condition** .  
  
    ```text
    Guess < Target
    ```  
  
10. Faites glisser deux activités **WriteLine** de la section **primitives** de la **boîte à outils** et déposez-les afin qu’elles soient côte à côte en dessous des deux activités **FlowDecision** . Connectez l’action **true** de l’activité **FlowDecision** inférieure à l’activité **WriteLine** la plus à gauche et l’action **false** à l’activité **WriteLine** la plus à droite.  
  
11. Cliquez sur l’activité **WriteLine** la plus à gauche pour la sélectionner, puis tapez l’expression suivante dans la zone de valeur de propriété **texte** de la **fenêtre Propriétés**.  
  
    ```text
    "Your guess is too low."  
    ```  
  
12. Connectez le **WriteLine** à la partie gauche de l’activité **prompt** qui se trouve au-dessus de lui.  
  
13. Cliquez sur l’activité **WriteLine** la plus à droite pour la sélectionner, puis tapez l’expression suivante dans la zone de valeur de propriété **texte** de la **fenêtre Propriétés**.  
  
    ```text
    "Your guess is too high."  
    ```  
  
14. Connectez l’activité **WriteLine** au côté droit de l’activité **prompt** située au-dessus de celle-ci.  
  
     L'exemple suivant illustre le flux de travail terminé.  
  
     ![Diagramme qui affiche un organigramme Windows Workflow Foundation terminé.](./media/how-to-create-a-flowchart-workflow/completed-windows-workflow-flowchart.png)  
  
### <a name="to-build-the-workflow"></a>Pour générer le flux de travail  
  
1. Appuyez sur Ctrl+Maj+B pour générer la solution.  
  
     Pour obtenir des instructions sur l’exécution du flux de travail, consultez la rubrique suivante, [procédure: Exécutez un](how-to-run-a-workflow.md)de Workflow. Si vous avez déjà effectué les [procédure: Exécuter un flux de travail](how-to-run-a-workflow.md) étape avec un style différent de workflow et souhaitez l’exécuter à l’aide du flux de travail de l’organigramme à partir de cette étape, passez à la section [pour générer et exécuter l’application](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) de [procédure: Exécutez un de Workflow.](how-to-run-a-workflow.md)  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [Programmation Windows Workflow Foundation](programming.md)
- [Conception des workflows](designing-workflows.md)
- [Didacticiel Bien démarrer](getting-started-tutorial.md)
- [Guide pratique: Créer une activité](how-to-create-an-activity.md)
- [Guide pratique: Exécuter un flux de travail](how-to-run-a-workflow.md)

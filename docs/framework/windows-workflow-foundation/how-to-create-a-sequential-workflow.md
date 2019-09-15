---
title: 'Procédure : Créer un workflow séquentiel'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5280e816-ae17-48c4-8de0-a1e6895dd8f0
ms.openlocfilehash: 61e3f01b1259536ff15d71526e91aef42069722e
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989701"
---
# <a name="how-to-create-a-sequential-workflow"></a>Procédure : Créer un workflow séquentiel

Les workflows peuvent être construits aussi bien à partir d'activités intégrées que d'activités personnalisées. Cette rubrique explique comment créer un workflow qui utilise à la fois des activités intégrées telles que <xref:System.Activities.Statements.Sequence> l’activité, et les activités personnalisées de [la procédure précédente Comment : Créer une rubrique](how-to-create-an-activity.md) d’activité. Le workflow modélise un jeu d'estimation de nombre.

> [!NOTE]
> Chaque rubrique du didacticiel de mise en route dépend des rubriques précédentes. Pour effectuer cette rubrique, vous devez d’abord [effectuer les opérations suivantes : Créer une activité](how-to-create-an-activity.md).

> [!NOTE]
> Pour télécharger une version complète du didacticiel, consultez [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976)(Windows Workflow Foundation (WF45) - Didacticiel de mise en route).

## <a name="to-create-the-workflow"></a>Pour créer le flux de travail

1. Cliquez avec le bouton droit sur **NumberGuessWorkflowActivities** dans **Explorateur de solutions** , puis sélectionnez **Ajouter**, **nouvel élément**.

2. Dans le nœud **éléments communs** **installés**, sélectionnez **flux de travail**. Sélectionnez **activité** dans la liste **flux de travail** .

3. Tapez `SequentialNumberGuessWorkflow` dans la zone **nom** , puis cliquez sur **Ajouter**.

4. Faites glisser une activité **Sequence** de la section **flux de contrôle** de la **boîte à outils** et déposez-la sur l’étiquette **déposer l’activité ici** sur l’aire de conception de Workflow.

## <a name="to-create-the-workflow-variables-and-arguments"></a>Pour créer les variables et arguments du flux de travail

1. Double-cliquez sur **SequentialNumberGuessWorkflow. Xaml** dans **Explorateur de solutions** pour afficher le flux de travail dans le concepteur, s’il n’est pas déjà affiché.

2. Cliquez sur **arguments** dans la partie inférieure gauche du concepteur de flux de travail pour afficher le volet **arguments** .

3. Cliquez sur **créer un argument**.

4. Tapez `MaxNumber` dans la zone **nom** , sélectionnez **in** dans la liste déroulante **direction** , sélectionnez **Int32** dans la liste déroulante **type d’argument** , puis appuyez sur entrée pour enregistrer l’argument.

5. Cliquez sur **créer un argument**.

6. Tapez `Turns` dans la zone **nom** située sous l’argument nouvellement ajouté `MaxNumber` , sélectionnez **out** dans la liste déroulante **direction** , sélectionnez **Int32** dans la liste déroulante **type d’argument** , puis appuyez sur entrée.

7. Cliquez sur **arguments** dans la partie inférieure gauche du concepteur d’activités pour fermer le volet **arguments** .

8. Cliquez sur **variables** dans la partie inférieure gauche du concepteur de flux de travail pour afficher le volet **variables** .

9. Cliquez sur **créer une variable**.

    > [!TIP]
    > Si aucune zone **créer une variable** n’est affichée, cliquez sur l’activité **séquence** sur l’aire du concepteur de flux de travail pour la sélectionner.

10. Tapez `Guess` dans la zone **nom** , sélectionnez **Int32** dans la liste déroulante **type de variable** , puis appuyez sur entrée pour enregistrer la variable.

11. Cliquez sur **créer une variable**.

12. Tapez `Target` dans la zone **nom** , sélectionnez **Int32** dans la liste déroulante **type de variable** , puis appuyez sur entrée pour enregistrer la variable.

13. Cliquez sur **variables** dans la partie inférieure gauche du concepteur d’activités pour fermer le volet **variables** .

## <a name="to-add-the-workflow-activities"></a>Pour ajouter les activités de flux de travail

1. Faites glisser une activité **Assign** de la section **primitives** de la **boîte à outils** et déposez-la sur l’activité **Sequence** . Tapez `Target` dans la zone **à** et l’expression suivante dans la zone **entrer C# une expression** ou **entrer une expression VB** .

    ```vb
    New System.Random().Next(1, MaxNumber + 1)
    ```

    ```csharp
    new System.Random().Next(1, MaxNumber + 1)
    ```

    > [!TIP]
    > Si la fenêtre **boîte à outils** n’est pas affichée, sélectionnez **boîte à outils** dans le menu **affichage** .

2. Faites glisser une activité **while** à partir de la section **flux de contrôle** de la **boîte à outils** et déposez-la sur le workflow afin qu’elle soit en dessous de l’activité **Assign** .

3. Tapez l’expression suivante dans la zone de valeur de propriété **condition** de **l’activité de** l’activité.

    ```vb
    Guess <> Target
    ```

    ```csharp
    Guess != Target
    ```

     Une activité <xref:System.Activities.Statements.DoWhile> exécute ses activités enfants puis évalue son <xref:System.Activities.Statements.DoWhile.Condition%2A>. Si <xref:System.Activities.Statements.DoWhile.Condition%2A> a la valeur `True`, les activités dans <xref:System.Activities.Statements.DoWhile> s'exécutent encore. Dans cet exemple, l'estimation de l'utilisateur est évaluée et <xref:System.Activities.Statements.DoWhile> continue jusqu'à ce que l'estimation soit correcte.

4. Faites glisser une activité **prompt** de la section **NumberGuessWorkflowActivities** de la **boîte à outils** et déposez-la dans l’activité en **cours** à partir de l’étape précédente.

5. Dans la **fenêtre Propriétés**, tapez `"EnterGuess"` en incluant les guillemets dans la zone de valeur de propriété **NomSignet** pour l’activité **prompt** . Tapez `Guess` dans la zone valeur de la propriété de **résultat** , puis tapez l’expression suivante dans la zone de propriété **texte** .

    ```vb
    "Please enter a number between 1 and " & MaxNumber
    ```

    ```csharp
    "Please enter a number between 1 and " + MaxNumber
    ```

    > [!TIP]
    > Si la **fenêtre Propriétés** n’est pas affichée, sélectionnez **fenêtre Propriétés** dans le menu **affichage** .

6. Faites glisser une activité **Assign** de la section **primitives** de **la boîte à outils** et déposez-la dans **l’activité de** fait pour qu’elle suive l’activité **prompt** .

    > [!NOTE]
    > Lorsque vous déposez l’activité **Assign** , Notez comment le concepteur de workflow ajoute automatiquement une activité **Sequence** pour contenir à la fois l’activité **prompt** et l’activité Assign qui vient d' **être** ajoutée.

7. Tapez `Turns` dans la zone **à** , `Turns + 1` puis dans la zone **entrer une C# expression** ou **entrer une expression VB** .

8. Faites glisser une activité **If** de la section **Control Flow** de **la boîte à outils** et déposez-la dans l’activité **Sequence** afin qu’elle suive l’activité Assign qui vient d' **être** ajoutée.

9. Tapez l’expression suivante dans la zone de valeur de propriété **condition** de l’activité **If** .

    ```vb
    Guess <> Target
    ```

    ```csharp
    Guess != Target
    ```

10. Faites glisser une autre activité **If** de la section **Control Flow** de la **boîte à outils** et déposez-la dans la section **Then** de la première activité **If** .

11. Tapez l’expression suivante dans la zone de valeur de propriété **condition** de **l’activité nouvellement** ajoutée.

    ```text
    Guess < Target
    ```

12. Faites glisser deux activités **WriteLine** de la section **primitives** de **la boîte à outils** et déposez-les de façon à ce qu’elles se trouvent dans la section **Then** de l’activité **If** nouvellement ajoutée, et l’autre dans la section **else** .

13. Cliquez sur l’activité **WriteLine** dans la section **Then** pour la sélectionner, puis tapez l’expression suivante dans la zone de valeur de propriété **Text** .

    ```text
    "Your guess is too low."
    ```

14. Cliquez sur l’activité **WriteLine** dans la section **sinon** pour la sélectionner, puis tapez l’expression suivante dans la zone de valeur de propriété **texte** .

    ```text
    "Your guess is too high."
    ```

     L’exemple suivant illustre le flux de travail terminé :

     ![Capture d’écran montrant le flux de travail séquentiel terminé.](./media/how-to-create-a-sequential-workflow/complete-sequential-workflow.jpg)

## <a name="to-build-the-workflow"></a>Pour générer le flux de travail

1. Appuyez sur Ctrl+Maj+B pour générer la solution.

     Pour obtenir des instructions sur l’exécution du flux de travail, consultez la rubrique [suivante, comment : Exécuter un flux](how-to-run-a-workflow.md)de travail. Si vous avez déjà effectué les [opérations suivantes : Exécutez une étape](how-to-run-a-workflow.md) de workflow avec un style différent de workflow et souhaitez l’exécuter à l’aide du flux de travail séquentiel de cette étape, passez à la section [ [pour générer et exécuter l’application](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) dans How to : Exécuter un flux](how-to-run-a-workflow.md)de travail.

## <a name="see-also"></a>Voir aussi

- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [Programmation Windows Workflow Foundation](programming.md)
- [Conception des workflows](designing-workflows.md)
- [Didacticiel Bien démarrer](getting-started-tutorial.md)
- [Guide pratique pour Créer une activité](how-to-create-an-activity.md)
- [Guide pratique pour Exécuter un flux de travail](how-to-run-a-workflow.md)

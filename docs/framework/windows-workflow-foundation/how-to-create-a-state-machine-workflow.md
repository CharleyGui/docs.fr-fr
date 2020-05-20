---
title: "Procédure : créer un workflow d'ordinateur d'état"
description: Cet article crée un flux de travail qui utilise à la fois des activités intégrées, telles que l’activité StateMachine et des activités personnalisées.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3ec60e8f-fad4-493e-a426-e7962d7aee8c
ms.openlocfilehash: 8a9342c07c15d65df0310c0cb35b4b2c6f2ba686
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83419653"
---
# <a name="how-to-create-a-state-machine-workflow"></a>Procédure : créer un workflow d'ordinateur d'état
Les workflows peuvent être construits aussi bien à partir d'activités intégrées que d'activités personnalisées. Cette rubrique décrit comment créer un workflow qui utilise à la fois des activités intégrées, telles que l' <xref:System.Activities.Statements.StateMachine> activité, et les activités personnalisées de la rubrique précédente [Comment : créer une activité](how-to-create-an-activity.md) . Le workflow modélise un jeu d'estimation de nombre.  
  
> [!NOTE]
> Chaque rubrique du didacticiel de mise en route dépend des rubriques précédentes. Pour effectuer cette rubrique, vous devez d’abord terminer [la procédure : créer une activité](how-to-create-an-activity.md).  
  
> [!NOTE]
> Pour télécharger une version complète du didacticiel, consultez [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976)(Windows Workflow Foundation (WF45) - Didacticiel de mise en route).  
  
### <a name="to-create-the-workflow"></a>Pour créer le flux de travail  
  
1. Cliquez avec le bouton droit sur **NumberGuessWorkflowActivities** dans **Explorateur de solutions** , puis sélectionnez **Ajouter**, **nouvel élément**.  
  
2. Dans le nœud **éléments communs** **installés**, sélectionnez **flux de travail**. Sélectionnez **Activité** dans la liste **Flux de travail**.  
  
3. Tapez `StateMachineNumberGuessWorkflow` dans la zone **nom** , puis cliquez sur **Ajouter**.  
  
4. Faites glisser une activité **StateMachine** de la section **machine à États** de la **boîte à outils** et déposez-la sur l’étiquette **déposer l’activité ici** sur l’aire de conception de Workflow.  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a>Pour créer les variables et arguments du flux de travail  
  
1. Double-cliquez sur **StateMachineNumberGuessWorkflow. Xaml** dans **Explorateur de solutions** pour afficher le flux de travail dans le concepteur, s’il n’est pas déjà affiché.  
  
2. Cliquez sur **arguments** dans la partie inférieure gauche du concepteur de flux de travail pour afficher le volet **arguments** .  
  
3. Cliquez sur **Créer un argument**.  
  
4. Tapez dans `MaxNumber` la **zone Nom** , sélectionnez **in** dans la liste déroulante **direction** , sélectionnez **Int32** dans la liste déroulante type d' **argument** , puis appuyez sur entrée pour enregistrer l’argument.  
  
5. Cliquez sur **Créer un argument**.  
  
6. Tapez `Turns` dans la zone **nom** située sous l’argument nouvellement ajouté `MaxNumber` , sélectionnez **out** dans la liste déroulante **direction** , sélectionnez **Int32** dans la liste déroulante **type d’argument** , puis appuyez sur entrée.  
  
7. Cliquez sur **Arguments** dans la partie inférieure gauche du concepteur d'activités pour fermer le volet **Arguments**.  
  
8. Cliquez sur **variables** dans la partie inférieure gauche du concepteur de flux de travail pour afficher le volet **variables** .  
  
9. Cliquez sur **Créer une variable**.  
  
    > [!TIP]
    > Si aucune zone **créer une variable** n’est affichée, cliquez sur l' <xref:System.Activities.Statements.StateMachine> activité sur l’aire du concepteur de flux de travail pour la sélectionner.  
  
10. Tapez `Guess` dans la zone **nom** , sélectionnez **Int32** dans la liste déroulante **type de variable** , puis appuyez sur entrée pour enregistrer la variable.  
  
11. Cliquez sur **Créer une variable**.  
  
12. Tapez `Target` dans la zone **nom** , sélectionnez **Int32** dans la liste déroulante **type de variable** , puis appuyez sur entrée pour enregistrer la variable.  
  
13. Cliquez sur **Variables** dans la partie inférieure gauche du concepteur d'activités pour fermer le volet **Variables**.  
  
### <a name="to-add-the-workflow-activities"></a>Pour ajouter les activités de flux de travail  
  
1. Cliquez sur **State1** pour le sélectionner. Dans la **fenêtre Propriétés**, remplacez **DisplayName** par `Initialize Target` .  
  
    > [!TIP]
    > Si la **fenêtre Propriétés** n’est pas affichée, sélectionnez **fenêtre Propriétés** dans le menu **affichage** .  
  
2. Double-cliquez sur l’état **initialiser l’initialisation** de la cible dans le concepteur de workflow pour la développer.  
  
3. Faites glisser une activité **Assign** de la section **primitives** de la **boîte à outils** et déposez-la dans la section d' **entrée** de l’État. Tapez `Target` dans la zone **à** et l’expression suivante dans la zone **entrer une expression C#** ou **entrer une expression VB** .  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    > Si la fenêtre **Boîte à outils** ne s'affiche pas, sélectionnez **Boîte à outils** dans le menu **Afficher**.  
  
4. Revenez à la vue globale de l’ordinateur d’État dans le concepteur de flux de travail en cliquant sur **StateMachine** dans l’affichage de navigation en haut du concepteur de Workflow.  
  
5. Faites glisser une activité **State** de la section **machine à États** de la **boîte à outils** vers le concepteur de flux de travail et placez-la sur l’état **initialiser la cible** . Notez que quatre triangles apparaissent autour de l’état **initialiser la cible** lorsque le nouvel État est sur celui-ci. Déposez le nouvel État sur le triangle qui est immédiatement en dessous de l’état **initialiser la cible** . Cela place le nouvel État sur le workflow et crée une transition de l’état d’initialisation de la **cible** vers le nouvel État.  
  
6. Cliquez sur **State1** pour le sélectionner, remplacez **DisplayName** par `Enter Guess` , puis double-cliquez sur l’État dans le concepteur de workflow pour le développer.  
  
7. Faites glisser une activité **WriteLine** de la section **primitives** de la **boîte à outils** et déposez-la dans la section d' **entrée** de l’État.  
  
8. Tapez l’expression suivante dans la zone de propriété **Text** de **WriteLine**.  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
9. Faites glisser une activité **Assign** de la section **primitives** de la **boîte à outils** et déposez-la sur la section **Exit** de l’État.  
  
10. Tapez `Turns` dans la zone **à** , puis `Turns + 1` dans la zone **entrer une expression C#** ou **entrer une expression VB** .  
  
11. Revenez à la vue globale de l’ordinateur d’État dans le concepteur de flux de travail en cliquant sur **StateMachine** dans l’affichage de navigation en haut du concepteur de Workflow.  
  
12. Faites glisser une activité **FinalState** de la section **machine à États** de la **boîte à outils**, placez-la sur l’état **Enter Guess** et déposez-la sur le triangle qui apparaît à droite de l’état **Enter Guess** afin qu’une transition soit créée entre **Enter Guess** et **FinalState**.  
  
13. Le nom par défaut de la transition est **T2**. Cliquez sur la transition dans le concepteur de flux de travail pour la sélectionner et définissez **DisplayName** sur **estimation correcte**. Cliquez ensuite sur le **FinalState**et sélectionnez-le, puis faites-le glisser vers la droite afin qu’il y ait de la place pour que le nom de la transition complète s’affiche sans superposer l’un des deux États. Cela facilitera l'exécution des autres étapes du didacticiel.  
  
14. Double-cliquez sur la transition **estimation correcte** renommée dans le concepteur de workflow pour la développer.  
  
15. Faites glisser une activité **ReadInt** de la section **NumberGuessWorkflowActivities** de la **boîte à outils** et déposez-la dans la section **Trigger** de la transition.  
  
16. Dans la **fenêtre Propriétés** de l’activité **ReadInt** , tapez en `"EnterGuess"` incluant les guillemets dans la zone de valeur de propriété **NomSignet** , puis tapez `Guess` dans la zone de valeur de propriété **result** .  
  
17. Tapez l’expression suivante dans la zone de valeur de propriété **condition** de la transition de l' **estimation correcte** .  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
18. Revenez à la vue globale de l’ordinateur d’État dans le concepteur de flux de travail en cliquant sur **StateMachine** dans l’affichage de navigation en haut du concepteur de Workflow.  
  
    > [!NOTE]
    > Une transition se produit lorsque l'événement déclencheur est reçu et <xref:System.Activities.Statements.Transition.Condition%2A>, s'il est présent, prend la valeur `True`. Pour cette transition, si l’utilisateur `Guess` correspond au généré de manière aléatoire `Target` , le contrôle passe à **FinalState** et le workflow se termine.  
  
19. Selon que l’estimation est correcte ou non, le flux de travail doit passer au **FinalState** ou revenir à l’état **Enter Guess** pour une autre tentative. Les deux transitions partagent le même déclencheur que l’attente de la réception de l’utilisateur par le biais de l’activité **ReadInt** . Il s'agit d'une transition partagée. Pour créer une transition partagée, cliquez sur le cercle qui indique le début de la transition de **estimation correcte** et faites-la glisser vers l’état souhaité. Dans ce cas, la transition est une transition automatique. par conséquent, faites glisser le point de départ de la transition **estimation correcte** , puis déposez-la sur le bas de l’état **Enter Guess** . Une fois la transition créée, sélectionnez-la dans le concepteur de flux de travail et définissez sa propriété **DisplayName** sur **deviner incorrect**.  
  
    > [!NOTE]
    > Des transitions partagées peuvent également être créées à partir du concepteur de transition en cliquant sur **Ajouter une transition de déclencheur partagée** en bas du concepteur de transition, puis en sélectionnant l’État cible souhaité dans la liste déroulante **États disponibles pour la connexion** .  
  
    > [!NOTE]
    > Notez que si la condition <xref:System.Activities.Statements.Transition.Condition%2A> d'une transition a pour valeur `false` (ou si toutes les conditions d'une transition de déclencheur partagée ont la valeur `false`), la transition n'a pas lieu et tous les déclencheurs de toutes les transitions de l'état sont replanifiés. Dans ce didacticiel, cette situation ne peut pas se produire en raison de la façon dont les conditions sont configurées (il existe des actions spécifiques lorsque l'estimation est correcte ou incorrecte).  
  
20. Double-cliquez sur la transition **Guess incorrect** dans le concepteur de flux de travail pour la développer. Notez que le **déclencheur** est déjà défini sur la même activité **ReadInt** que celle utilisée par la transition **estimation correcte** .  
  
21. Tapez l’expression suivante dans la zone de valeur de propriété **condition** .  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
22. Faites glisser une activité **If** de la section **Control Flow** de la **boîte à outils** et déposez-la dans la section **action** de la transition.  
  
23. Tapez l’expression suivante dans la zone de valeur de propriété **condition** de l’activité **If** .  
  
    ```text
    Guess < Target
    ```  
  
24. Faites glisser deux activités **WriteLine** de la section **primitives** de **la boîte à outils** et déposez-les de façon à ce qu’elles se trouvent dans la section **Then** de l’activité **If** , et l’autre dans la section **else** .  
  
25. Cliquez sur l’activité **WriteLine** dans la section **Then** pour la sélectionner, puis tapez l’expression suivante dans la zone de valeur de propriété **Text** .  
  
    ```text
    "Your guess is too low."  
    ```  
  
26. Cliquez sur l’activité **WriteLine** dans la section **sinon** pour la sélectionner, puis tapez l’expression suivante dans la zone de valeur de propriété **texte** .  
  
    ```text
    "Your guess is too high."  
    ```  
  
27. Revenez à la vue globale de l’ordinateur d’État dans le concepteur de flux de travail en cliquant sur **StateMachine** dans l’affichage de navigation en haut du concepteur de Workflow.  
  
     L'exemple suivant illustre le flux de travail terminé.  
  
     ![Illustration qui montre le flux de travail de l’ordinateur d’état terminé.](./media/how-to-create-a-state-machine-workflow/complete-state-machine-workflow.jpg)  
  
### <a name="to-build-the-workflow"></a>Pour générer le flux de travail  
  
1. Appuyez sur Ctrl+Maj+B pour générer la solution.  
  
     Pour obtenir des instructions sur l’exécution du flux de travail, consultez la rubrique suivante, [Comment : exécuter un workflow](how-to-run-a-workflow.md). Si vous avez déjà effectué l’étape [Comment : exécuter un flux de travail](how-to-run-a-workflow.md) avec un style différent de workflow et que vous souhaitez l’exécuter à l’aide du flux de travail de l’ordinateur d’État à partir de cette étape, passez à la section [pour générer et exécuter l’application](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) dans [procédure : exécuter un workflow](how-to-run-a-workflow.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [Programmation Windows Workflow Foundation](programming.md)
- [Conception des workflows](designing-workflows.md)
- [Didacticiel Prise en main](getting-started-tutorial.md)
- [Guide pratique pour créer une activité](how-to-create-an-activity.md)
- [Guide pratique pour exécuter un workflow](how-to-run-a-workflow.md)

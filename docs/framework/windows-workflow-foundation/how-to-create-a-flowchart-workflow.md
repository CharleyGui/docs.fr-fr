---
title: 'Procédure : créer un workflow d’organigramme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 185d7aea-68a6-4bd8-adde-45050f33170a
ms.openlocfilehash: 10483c747e0f86816db6f03dd8df17472f31f15c
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063775"
---
# <a name="how-to-create-a-flowchart-workflow"></a>Procédure : créer un workflow d’organigramme
Les workflows peuvent être construits aussi bien à partir d'activités intégrées que d'activités personnalisées. Cette rubrique vous guide création d’un workflow qui utilise les deux activités intégrées telles que la <xref:System.Activities.Statements.Flowchart> activité et les activités personnalisées de la précédente [Comment : Créer une activité](how-to-create-an-activity.md) rubrique. Le workflow modélise un jeu d'estimation de nombre.  
  
> [!NOTE]
>  Chaque rubrique du didacticiel de mise en route dépend des rubriques précédentes. Pour effectuer cette rubrique, vous devez tout d’abord effectuer [Comment : Créer une activité](how-to-create-an-activity.md).  
  
> [!NOTE]
>  Pour télécharger une version complète du didacticiel, consultez [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976)(Windows Workflow Foundation (WF45) - Didacticiel de mise en route).  
  
### <a name="to-create-the-workflow"></a>Pour créer le flux de travail  
  
1. Avec le bouton droit **NumberGuessWorkflowActivities** dans **l’Explorateur de solutions** et sélectionnez **ajouter**, **un nouvel élément**.  
  
2. Dans le **installé**, **éléments communs** nœud, sélectionnez **Workflow**. Sélectionnez **activité** à partir de la **Workflow** liste.  
  
3. Type `FlowchartNumberGuessWorkflow` dans le **nom** , puis cliquez sur **ajouter**.  
  
4. Faites glisser un **organigramme** activité à partir de la **organigramme** section de la **boîte à outils** et déposez-le sur le **déposer l’activité ici** étiquette sur le aire de conception de workflow.  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a>Pour créer les variables et arguments du flux de travail  
  
1. Double-cliquez sur **FlowchartNumberGuessWorkflow.xaml** dans **l’Explorateur de solutions** pour afficher le flux de travail dans le concepteur, si ce n’est pas déjà fait.  
  
2. Cliquez sur **Arguments** dans la partie inférieure gauche du Concepteur de flux de travail pour afficher la **Arguments** volet.  
  
3. Cliquez sur **créer un Argument**.  
  
4. Type `MaxNumber` dans le **nom** boîte, sélectionnez **dans** à partir de la **Direction** liste déroulante, sélectionnez **Int32** à partir de la **Type d’argument** liste déroulante et appuyez sur ENTRÉE pour enregistrer l’argument.  
  
5. Cliquez sur **créer un Argument**.  
  
6. Type `Turns` dans le **nom** boîte qui se trouve sous récemment ajouté `MaxNumber` argument, sélectionnez **Out** à partir de la **Direction** liste déroulante, sélectionnez  **Int32** à partir de la **type d’Argument** liste déroulante et appuyez sur ENTRÉE.  
  
7. Cliquez sur **Arguments** dans la partie inférieure gauche du Concepteur d’activités pour fermer la **Arguments** volet.  
  
8. Cliquez sur **Variables** dans la partie inférieure gauche du Concepteur de flux de travail pour afficher la **Variables** volet.  
  
9. Cliquez sur **créer la Variable**.  
  
    > [!TIP]
    >  Si aucun **créer une Variable** s’affiche, cliquez sur le <xref:System.Activities.Statements.Flowchart> activité sur l’aire de Concepteur de flux de travail pour le sélectionner.  
  
10. Type `Guess` dans le **nom** boîte, sélectionnez **Int32** à partir de la **type de Variable** liste déroulante et appuyez sur ENTRÉE pour enregistrer la variable.  
  
11. Cliquez sur **créer la Variable**.  
  
12. Type `Target` dans le **nom** boîte, sélectionnez **Int32** à partir de la **type de Variable** liste déroulante et appuyez sur ENTRÉE pour enregistrer la variable.  
  
13. Cliquez sur **Variables** dans la partie inférieure gauche du Concepteur d’activités pour fermer la **Variables** volet.  
  
### <a name="to-add-the-workflow-activities"></a>Pour ajouter les activités de flux de travail  
  
1. Faites glisser un **affecter** activité à partir de la **Primitives** section de la **boîte à outils** et placez-la sur le **Démarrer** nœud, qui est en haut de la diagramme de flux. Lorsque le **affecter** activité se trouve sur le **Démarrer** nœud, trois triangles apparaissent autour de la **Démarrer** nœud. Supprimer le **affecter** activité sur le triangle qui est directement sous le **Démarrer** nœud. Cela sera relier les deux éléments et désigne la **affecter** activité comme première activité dans l’organigramme.  
  
    > [!NOTE]
    >  Les activités peuvent également être définies comme activité de départ dans le workflow en les liant manuellement au nœud de démarrage. Pour ce faire, pointez la souris sur le **Démarrer** nœud, cliquez sur un des rectangles qui apparaissent lorsque la souris est positionnée sur le **Démarrer** nœud, puis faites glisser la connexion de ligne à l’activité souhaitée et déposez-la sur l’un des les rectangles qui s’affichent. Vous pouvez également désigner une activité en tant que l’activité de départ en double-cliquant sur l’informatique et en choisissant **définir en tant que nœud début**.  
  
2. Type `Target` dans le **à** boîte et l’expression suivante dans le **entrer une Expression c#** ou **entrer une expression VB** boîte.  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  Si le **boîte à outils** fenêtre n’est pas affichée, sélectionnez **boîte à outils** à partir de la **vue** menu.  
  
3. Faites glisser un **invite** activité à partir de la **NumberGuessWorkflowActivities** section de la **boîte à outils**, déposez-la en dessous le **affecter** activité à partir de la précédente pas à pas et vous connecter le **invite** activité à la **affecter** activité. Il existe trois façons de connecter les deux activités. La première consiste à les connecter lorsque vous déposez le **invite** activité sur le flux de travail. Lorsque vous faites glisser le **invite** activité au workflow, placez-la sur le **affecter** activité et déposez-la sur un des quatre triangles qui s’affichent lorsque le **invite** activité se trouve sur le **affecter** activité. La deuxième méthode consiste à supprimer la **invite** activité sur le flux de travail à l’emplacement souhaité. Ensuite, pointez la souris sur le **affecter** activité et faites glisser un des rectangles qui apparaît sous le **invite** activité. Faites glisser la souris afin que la ligne de connexion le **affecter** activité se connecte à un des rectangles de la **invite** activité, puis relâchez le bouton de la souris. La troisième méthode est très similaire à la première, mais au lieu de faire glisser le **invite** activité à partir de la **boîte à outils**, vous faites glisser à partir de son emplacement sur l’aire de conception de workflow, placez-la sur le  **Affecter** activité et déposez-la sur un des triangles qui s’affiche.  
  
4. Dans le **fenêtre Propriétés** pour le **invite** activité, type `"EnterGuess"` oublier les guillemets le **BookmarkName** zone valeur de propriété. Type `Guess` dans le **résultat** propriété zone de valeur et tapez l’expression suivante dans le **texte** zone de propriété.  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
    > [!TIP]
    >  Si le **fenêtre Propriétés** n’est pas affiché, sélectionnez **fenêtre Propriétés** à partir de la **vue** menu.  
  
5. Faites glisser un **affecter** activité à partir de la **Primitives** section de la **boîte à outils** et connectez-le à l’aide d’une des méthodes décrites dans l’étape précédente, afin qu’il soit sous la  **Invite** activité.  
  
6. Type `Turns` dans le **à** boîte et `Turns + 1` dans le **entrer une expression c#** ou **entrer une expression VB** boîte.  
  
7. Faites glisser un **FlowDecision** à partir de la **organigramme** section de la **boîte à outils** et connectez-la en dessous le **affecter** activité. Dans le **fenêtre Propriétés**, tapez l’expression suivante dans le **Condition** zone valeur de propriété.  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
8. Faites glisser un autre **FlowDecision** activité à partir de la **boîte à outils** et déposez-le sous la première. Connectez les deux activités en faisant glisser du rectangle étiqueté **False** situé en haut **FlowDecision** activité vers le rectangle en haut de la seconde **FlowDecision**activité.  
  
    > [!TIP]
    >  Si vous ne voyez pas le **True** et **False** des étiquettes sur le **FlowDecision**, pointez la souris sur le **FlowDecision**.  
  
9. Cliquez sur le second **FlowDecision** activité pour le sélectionner. Dans le **fenêtre Propriétés**, tapez l’expression suivante dans le **Condition** zone valeur de propriété.  
  
    ```
    Guess < Target  
    ```  
  
10. Faites glisser deux **WriteLine** activités à partir de la **Primitives** section de la **boîte à outils** et déposez-les de sorte qu’ils soient côte à côte sous les deux **FlowDecision**  activités. Connecter le **True** action du bas **FlowDecision** activité le plus à gauche **WriteLine** activité et le **False** action à la à l’extrême droite **WriteLine** activité.  
  
11. Cliquez sur le plus à gauche **WriteLine** activité pour la sélectionner, puis tapez l’expression suivante dans le **texte** zone de valeur de propriété le **fenêtre Propriétés**.  
  
    ```
    "Your guess is too low."  
    ```  
  
12. Connecter le **WriteLine** vers le côté gauche de la **invite** activité qui est au-dessus de lui.  
  
13. Cliquez sur le plus à droite **WriteLine** activité pour la sélectionner, puis tapez l’expression suivante dans le **texte** zone de valeur de propriété le **fenêtre Propriétés**.  
  
    ```
    "Your guess is too high."  
    ```  
  
14. Connecter le **WriteLine** activité sur le côté droit de la **invite** activité au-dessus de lui.  
  
     L'exemple suivant illustre le flux de travail terminé.  
  
     ![Diagramme illustrant un organigramme de Windows Workflow Foundation terminé.](./media/how-to-create-a-flowchart-workflow/completed-windows-workflow-flowchart.png)  
  
### <a name="to-build-the-workflow"></a>Pour générer le flux de travail  
  
1. Appuyez sur Ctrl+Maj+B pour générer la solution.  
  
     Pour obtenir des instructions sur la façon d’exécuter le flux de travail, consultez la rubrique suivante, [Comment : Exécuter un Workflow](how-to-run-a-workflow.md). Si vous avez déjà effectué le [Comment : Exécuter un Workflow](how-to-run-a-workflow.md) étape avec un style différent de workflow et souhaitez l’exécuter en utilisant le workflow d’organigramme à partir de cette étape, passez directement à la [pour générer et exécuter l’application](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) section de [Comment : Exécuter un Workflow](how-to-run-a-workflow.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [Programmation Windows Workflow Foundation](programming.md)
- [Conception des workflows](designing-workflows.md)
- [Didacticiel Bien démarrer](getting-started-tutorial.md)
- [Guide pratique pour Créer une activité](how-to-create-an-activity.md)
- [Guide pratique pour Exécuter un Workflow](how-to-run-a-workflow.md)

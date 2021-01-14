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
# <a name="how-to-create-an-activity"></a>Procédure : créer une activité

Les activités sont l'unité principale de comportement dans [!INCLUDE[wf1](../../../includes/wf1-md.md)]. La logique d'exécution d'une activité peut être implémentée en code managé ou à l'aide d'autres activités. Cette rubrique indique comment créer deux activités. La première activité est une activité simple qui utilise le code pour implémenter la logique d'exécution. L'implémentation de la deuxième activité est définie à l'aide d'autres activités. Ces activités sont utilisées dans les procédures du didacticiel.

## <a name="create-the-activity-library-project"></a>Créer le projet de bibliothèque d’activités

1. Ouvrez Visual Studio et choisissez **nouveau**  >  **projet** dans le menu **fichier** .

2. Dans la boîte de dialogue **nouveau projet** , sous la catégorie **installé** , sélectionnez flux de travail **Visual C#**  >   (ou **Visual Basic**  >  **Workflow**).

    > [!NOTE]
    > Si vous ne voyez pas la catégorie de modèle de **flux de travail** , vous devrez peut-être installer le composant **Windows Workflow Foundation** de Visual Studio. Choisissez le lien **ouvrir le Visual Studio installer** sur le côté gauche de la boîte de dialogue **nouveau projet** . Dans Visual Studio Installer, sélectionnez l’onglet **composants individuels** . Ensuite, sous la catégorie **activités de développement** , sélectionnez le composant **Windows Workflow Foundation** . Choisissez **modifier** pour installer le composant.

3. Sélectionnez le modèle de projet **bibliothèque d’activités** . Entrez `NumberGuessWorkflowActivities` dans la zone **Nom**, puis cliquez sur **OK**.

4. Cliquez avec le bouton droit sur **Activity1.xaml** dans l'**Explorateur de solutions**, puis choisissez **Supprimer**. Cliquez sur **OK** pour confirmer.

## <a name="create-the-readint-activity"></a>Créer l’activité ReadInt

1. Choisissez **Ajouter un nouvel élément** dans le menu **projet** .

2. Dans le   >  nœud **éléments communs** installés, sélectionnez **flux de travail**. Sélectionnez **activité du code** dans la liste **flux de travail** .

3. Entrez `ReadInt` dans la zone **Nom**, puis cliquez sur **Ajouter**.

4. Remplacez la définition `ReadInt` existante par la définition suivante.

     [!code-csharp[CFX_WF_GettingStarted#1](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/readint.cs#1)]
     [!code-vb[CFX_WF_GettingStarted#1](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/readint.vb#1)]

    > [!NOTE]
    > L'activité `ReadInt` dérive de <xref:System.Activities.NativeActivity%601> au lieu de <xref:System.Activities.CodeActivity>, qui est la valeur par défaut pour le modèle d'activité de code. <xref:System.Activities.CodeActivity%601> peut être utilisé si l'activité fournit un résultat unique, exposé via l'argument <xref:System.Activities.Activity%601.Result%2A>, mais <xref:System.Activities.CodeActivity%601> ne prenant pas en charge l'utilisation de signets, <xref:System.Activities.NativeActivity%601> est utilisé.

## <a name="create-the-prompt-activity"></a>Créer l’activité Prompt

1. Appuyez sur **CTRL** + **MAJ** + **B** pour générer le projet. La génération du projet permet d'utiliser l'activité `ReadInt` dans ce projet pour générer l'activité personnalisée de cette étape.

2. Choisissez **Ajouter un nouvel élément** dans le menu **projet** .

3. Dans le   >  nœud **éléments communs** installés, sélectionnez **flux de travail**. Sélectionnez **Activité** dans la liste **Flux de travail**.

4. Entrez `Prompt` dans la zone **Nom**, puis cliquez sur **Ajouter**.

5. Double-cliquez sur **prompt. Xaml** dans **Explorateur de solutions** pour l’afficher dans le concepteur s’il n’est pas déjà affiché.

6. Cliquez sur **Arguments** dans la partie inférieure gauche du concepteur d'activités pour afficher le volet **Arguments**.

7. Cliquez sur **Créer un argument**.

8. Tapez `BookmarkName` dans la zone **nom** , sélectionnez **in** dans la liste déroulante **direction** , sélectionnez **String** dans la liste déroulante **type d’argument** , puis appuyez sur **entrée** pour enregistrer l’argument.

9. Cliquez sur **Créer un argument**.

10. Tapez `Result` dans la zone **nom** située sous l’argument nouvellement ajouté `BookmarkName` , sélectionnez **out** dans la liste déroulante **direction** , sélectionnez **Int32** dans la liste déroulante **type d’argument** , puis appuyez sur **entrée**.

11. Cliquez sur **Créer un argument**.

12. Tapez `Text` dans la zone **nom** , sélectionnez **in** dans la liste déroulante **direction** , sélectionnez **String** dans la liste déroulante **type d’argument** , puis appuyez sur **entrée** pour enregistrer l’argument.

     Ces trois arguments sont liés aux arguments correspondants des activités <xref:System.Activities.Statements.WriteLine> et `ReadInt` ajoutées à l'activité `Prompt` dans les étapes suivantes.

13. Cliquez sur **Arguments** dans la partie inférieure gauche du concepteur d'activités pour fermer le volet **Arguments**.

14. Faites glisser une activité **Sequence** de la section **Control Flow** de **la boîte à outils** et déposez-la sur l’étiquette **déposer l’activité ici** du concepteur d’activités **prompt** .

    > [!TIP]
    > Si la fenêtre **Boîte à outils** ne s'affiche pas, sélectionnez **Boîte à outils** dans le menu **Afficher**.

15. Faites glisser une activité **WriteLine** de la section **primitives** de **la boîte à outils** et déposez-la sur l’étiquette **déposer l’activité ici** de l’activité **Sequence** .

16. Liez l' **argument Text** de l’activité **WriteLine** à l’argument **Text** de l’activité **prompt** en tapant `Text` dans la zone **entrer une expression C#** ou **entrer une expression VB** dans la fenêtre **Propriétés** , puis appuyez deux fois sur la touche **Tab** . Cela ferme la fenêtre de liste des membres IntelliSense et enregistre la valeur de propriété en déplaçant la sélection en dehors de la propriété. Cette propriété peut également être définie en tapant `Text` dans la zone **entrer une expression C#** ou **entrer une expression VB** sur l’activité elle-même.

    > [!TIP]
    > Si la **fenêtre Propriétés** n’est pas affichée, sélectionnez **fenêtre Propriétés** dans le menu **affichage** .

17. Faites glisser une activité **ReadInt** de la section **NumberGuessWorkflowActivities** de la **boîte à outils** et déposez-la dans l’activité **Sequence** afin qu’elle suive l’activité **WriteLine** .

18. Liez l’argument **NomSignet** de l' **activité ReadInt** à l’argument **NomSignet** de l’activité **prompt** en tapant `BookmarkName` dans la zone **entrer une expression VB** à droite de l’argument **NomSignet** dans la **fenêtre Propriétés**, puis appuyez deux fois sur la touche **Tab** pour fermer la fenêtre des membres de la liste IntelliSense et enregistrer la propriété.

19. Liez l’argument **result** de l' **activité ReadInt** à l’argument **result** de l’activité **prompt** en tapant `Result` dans la zone **entrer une expression VB** à droite de l’argument **result** dans la **fenêtre Propriétés**, puis appuyez deux fois sur la touche **Tab** .

20. Appuyez sur **CTRL** + **MAJ** + **B** pour générer la solution.

## <a name="next-steps"></a>Étapes suivantes

Pour obtenir des instructions sur la création d’un workflow à l’aide de ces activités, consultez l’étape suivante du didacticiel, [How to : Create a Workflow](how-to-create-a-workflow.md).

## <a name="see-also"></a>Voir aussi

- <xref:System.Activities.CodeActivity>
- <xref:System.Activities.NativeActivity%601>
- [Conception et implémentation d'activités personnalisées](designing-and-implementing-custom-activities.md)
- [Didacticiel de mise en route](getting-started-tutorial.md)
- [Procédure : créer un workflow](how-to-create-a-workflow.md)
- [Utilisation d'ExpressionTextBox dans un concepteur d'activités personnalisées](./samples/using-the-expressiontextbox-in-a-custom-activity-designer.md)

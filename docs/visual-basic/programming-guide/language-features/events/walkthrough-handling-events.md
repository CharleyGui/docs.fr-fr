---
title: Gestion des événements
ms.date: 07/20/2015
helpviewer_keywords:
- event handling [Visual Basic], walkthroughs
- walkthroughs [Visual Basic], event handling
- variables [Visual Basic], WithEvents
- events [Visual Basic], walkthroughs
- WithEvents keyword [Visual Basic], walkthroughs
- event handlers [Visual Basic], walkthroughs
ms.assetid: f145b3fc-5ae0-4509-a2aa-1ff6934706bd
ms.openlocfilehash: cb42f2e41e366cf8765cb9395d1a5641434bab40
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345082"
---
# <a name="walkthrough-handling-events-visual-basic"></a>Procédure pas à pas : gestion des événements (Visual Basic)
Il s’agit de la deuxième des deux rubriques qui montrent comment utiliser les événements. La première rubrique, [procédure pas à pas : déclaration et déclenchement d’événements](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md), montre comment déclarer et déclencher des événements. Cette section utilise le formulaire et la classe de cette procédure pas à pas pour montrer comment gérer les événements lorsqu’ils se produisent.  
  
 L’exemple de classe `Widget` utilise des instructions de gestion des événements traditionnelles. Visual Basic fournit d’autres techniques pour l’utilisation des événements. En guise d’exercice, vous pouvez modifier cet exemple pour utiliser les instructions `AddHandler` et `Handles`.  
  
### <a name="to-handle-the-percentdone-event-of-the-widget-class"></a>Pour gérer l’événement PercentDone de la classe widget  
  
1. Placez le code suivant dans `Form1`:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#4)]  
  
     Le mot clé `WithEvents` spécifie que la variable `mWidget` est utilisée pour gérer les événements d’un objet. Vous spécifiez le type d’objet en fournissant le nom de la classe à partir de laquelle l’objet sera créé.  
  
     La variable `mWidget` est déclarée dans `Form1`, car `WithEvents` variables doivent être au niveau de la classe. Cela est vrai quel que soit le type de classe dans lequel vous les placez.  
  
     La variable `mblnCancel` est utilisée pour annuler la méthode `LongTask`.  
  
## <a name="writing-code-to-handle-an-event"></a>Écriture de code pour gérer un événement  
 Dès que vous déclarez une variable à l’aide de `WithEvents`, le nom de la variable apparaît dans la liste déroulante de gauche de l' **éditeur de code**de la classe. Lorsque vous sélectionnez `mWidget`, les événements de la classe `Widget` s’affichent dans la liste déroulante de droite. La sélection d’un événement affiche la procédure d’événement correspondante, avec le préfixe `mWidget` et un trait de soulignement. Toutes les procédures événementielles associées à une variable `WithEvents` reçoivent le nom de la variable en tant que préfixe.  
  
#### <a name="to-handle-an-event"></a>Pour gérer un événement  
  
1. Sélectionnez `mWidget` dans la liste déroulante de gauche dans l' **éditeur de code**.  
  
2. Sélectionnez l’événement `PercentDone` dans la liste déroulante de droite. L' **éditeur de code** ouvre la procédure d’événement `mWidget_PercentDone`.  
  
    > [!NOTE]
    > L' **éditeur de code** est utile, mais pas obligatoire, pour l’insertion de nouveaux gestionnaires d’événements. Dans cette procédure pas à pas, il est plus direct de copier uniquement les gestionnaires d’événements directement dans votre code.  
  
3. Ajoutez le code suivant au gestionnaire d'événements `mWidget_PercentDone` :  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#5)]  
  
     Chaque fois que l’événement `PercentDone` est déclenché, la procédure événementielle affiche le pourcentage effectué dans un contrôle `Label`. La méthode `DoEvents` permet à l’étiquette de repeindre, et donne également à l’utilisateur la possibilité de cliquer sur le bouton **Annuler** .  
  
4. Ajoutez le code suivant pour le gestionnaire d’événements `Button2_Click` :  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#6)]  
  
 Si l’utilisateur clique sur le bouton **Annuler** pendant que `LongTask` est en cours d’exécution, l’événement `Button2_Click` est exécuté dès que l’instruction `DoEvents` permet au traitement des événements de se produire. La variable de niveau classe `mblnCancel` est définie sur `True`, et l’événement `mWidget_PercentDone` le teste et définit l’argument `ByRef Cancel` sur `True`.  
  
## <a name="connecting-a-withevents-variable-to-an-object"></a>Connexion d’une variable WithEvents à un objet  
 `Form1` est maintenant configuré pour gérer les événements d’un objet `Widget`. Il ne reste plus qu’à trouver un `Widget` quelque part.  
  
 Quand vous déclarez une variable `WithEvents` au moment de la conception, aucun objet n’est associé à celle-ci. Une variable `WithEvents` se présente comme n’importe quelle autre variable objet. Vous devez créer un objet et lui assigner une référence avec la variable `WithEvents`.  
  
#### <a name="to-create-an-object-and-assign-a-reference-to-it"></a>Pour créer un objet et lui assigner une référence  
  
1. Sélectionnez **(événements Form1)** dans la liste déroulante de gauche de l' **éditeur de code**.  
  
2. Sélectionnez l’événement `Load` dans la liste déroulante de droite. L' **éditeur de code** ouvre la procédure d’événement `Form1_Load`.  
  
3. Ajoutez le code suivant pour la procédure d’événement `Form1_Load` pour créer l' `Widget`:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#7)]  
  
 Lorsque ce code s’exécute, Visual Basic crée un objet `Widget` et connecte ses événements aux procédures d’événements associées à `mWidget`. À partir de là, chaque fois que le `Widget` déclenche son événement `PercentDone`, la procédure d’événement `mWidget_PercentDone` est exécutée.  
  
#### <a name="to-call-the-longtask-method"></a>Pour appeler la méthode LongTask  
  
- Ajoutez le code suivant au gestionnaire d'événements `Button1_Click` :  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#8)]  
  
 Avant que la méthode `LongTask` soit appelée, l’étiquette qui affiche le pourcentage d’achèvement doit être initialisée et l’indicateur de `Boolean` au niveau de la classe pour annuler la méthode doit avoir la valeur `False`.  
  
 `LongTask` est appelée avec une durée de tâche de 12,2 secondes. L’événement `PercentDone` est déclenché une fois tous les tiers d’une seconde. Chaque fois que l’événement est déclenché, la procédure d’événement `mWidget_PercentDone` est exécutée.  
  
 Une fois `LongTask` terminé, `mblnCancel` est testé pour vérifier si `LongTask` s’est terminé normalement, ou s’il s’est arrêté en raison de l' `mblnCancel` a été défini sur `True`. Le pourcentage d’achèvement est mis à jour uniquement dans le cas précédent.  
  
#### <a name="to-run-the-program"></a>Pour exécuter le programme  
  
1. Appuyez sur F5 pour mettre le projet en mode exécution.  
  
2. Cliquez sur le bouton **Démarrer la tâche** . Chaque fois que l’événement `PercentDone` est déclenché, l’étiquette est mise à jour avec le pourcentage de la tâche qui est terminé.  
  
3. Cliquez sur le bouton **Annuler** pour arrêter la tâche. Notez que l’apparence du bouton **Annuler** ne change pas immédiatement lorsque vous cliquez dessus. L’événement `Click` ne peut pas se produire tant que l’instruction `My.Application.DoEvents` autorise le traitement des événements.  
  
    > [!NOTE]
    > La méthode `My.Application.DoEvents` ne traite pas les événements exactement de la même façon que le formulaire. Par exemple, dans cette procédure pas à pas, vous devez cliquer deux fois sur le bouton **Annuler** . Pour permettre au formulaire de gérer directement les événements, vous pouvez utiliser le multithreading. Pour plus d’informations, consultez [threads managés](../../../../standard/threading/index.md).
  
 Il peut être intéressant d’exécuter le programme avec F11 et de parcourir le code une ligne à la fois. Vous pouvez voir clairement la façon dont l’exécution entre `LongTask`, puis entre rapidement `Form1` chaque fois que l’événement `PercentDone` est déclenché.  
  
 Que se passerait-il si, alors que l’exécution était de retour dans le code de `Form1`, la méthode `LongTask` était appelée à nouveau ? Au pire, un dépassement de capacité de la pile peut se produire si `LongTask` ont été appelées chaque fois que l’événement a été déclenché.  
  
 Vous pouvez faire en sorte que la variable `mWidget` gérer les événements d’un autre objet `Widget` en affectant une référence au nouveau `Widget` à `mWidget`. En fait, vous pouvez créer le code dans `Button1_Click` effectuer cette opération chaque fois que vous cliquez sur le bouton.  
  
#### <a name="to-handle-events-for-a-different-widget"></a>Pour gérer les événements d’un autre widget  
  
- Ajoutez la ligne de code suivante à la procédure `Button1_Click`, juste avant la ligne qui lit `mWidget.LongTask(12.2, 0.33)`:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#9)]  
  
 Le code ci-dessus crée un `Widget` chaque fois que l’utilisateur clique sur le bouton. Dès que la méthode `LongTask` se termine, la référence à la `Widget` est libérée et la `Widget` est détruite.  
  
 Une variable `WithEvents` ne peut contenir qu’une seule référence d’objet à la fois. par conséquent, si vous assignez un autre objet `Widget` à `mWidget`, les événements de l’objet `Widget` précédent ne seront plus gérés. Si `mWidget` est la seule variable objet contenant une référence à l’ancienne `Widget`, l’objet est détruit. Si vous souhaitez gérer les événements de plusieurs objets `Widget`, utilisez l’instruction `AddHandler` pour traiter les événements de chaque objet séparément.  
  
> [!NOTE]
> Vous pouvez déclarer autant de variables `WithEvents` que vous le souhaitez, mais les tableaux de variables `WithEvents` ne sont pas pris en charge.  
  
## <a name="see-also"></a>Voir aussi

- [Procédure pas à pas : déclaration et déclenchement des événements](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)
- [Événements](../../../../visual-basic/programming-guide/language-features/events/index.md)

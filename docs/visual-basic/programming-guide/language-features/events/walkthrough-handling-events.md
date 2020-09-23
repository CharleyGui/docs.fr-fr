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
ms.openlocfilehash: 4489f75e50a783a9b1acfb9c30568fdec6614488
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91057908"
---
# <a name="walkthrough-handling-events-visual-basic"></a>Procédure pas à pas : gestion des événements (Visual Basic)

Il s’agit de la deuxième des deux rubriques qui montrent comment utiliser les événements. La première rubrique, [procédure pas à pas : déclaration et déclenchement d’événements](walkthrough-declaring-and-raising-events.md), montre comment déclarer et déclencher des événements. Cette section utilise le formulaire et la classe de cette procédure pas à pas pour montrer comment gérer les événements lorsqu’ils se produisent.  
  
 L' `Widget` exemple de classe utilise des instructions de gestion des événements traditionnelles. Visual Basic fournit d’autres techniques pour l’utilisation des événements. En guise d’exercice, vous pouvez modifier cet exemple pour utiliser les `AddHandler` `Handles` instructions et.  
  
### <a name="to-handle-the-percentdone-event-of-the-widget-class"></a>Pour gérer l’événement PercentDone de la classe widget  
  
1. Placez le code suivant dans `Form1` :  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#4)]  
  
     Le `WithEvents` mot clé spécifie que la variable `mWidget` est utilisée pour gérer les événements d’un objet. Vous spécifiez le type d’objet en fournissant le nom de la classe à partir de laquelle l’objet sera créé.  
  
     La variable `mWidget` est déclarée dans `Form1` , car les `WithEvents` variables doivent être au niveau de la classe. Cela est vrai quel que soit le type de classe dans lequel vous les placez.  
  
     La variable `mblnCancel` est utilisée pour annuler la `LongTask` méthode.  
  
## <a name="writing-code-to-handle-an-event"></a>Écriture de code pour gérer un événement  

 Dès que vous déclarez une variable à l’aide `WithEvents` de, le nom de la variable apparaît dans la liste déroulante de gauche de l' **éditeur de code**de la classe. Lorsque vous sélectionnez `mWidget` , les `Widget` événements de la classe s’affichent dans la liste déroulante de droite. La sélection d’un événement affiche la procédure d’événement correspondante, avec le préfixe `mWidget` et un trait de soulignement. Toutes les procédures d’événement associées à une `WithEvents` variable reçoivent le nom de la variable en tant que préfixe.  
  
#### <a name="to-handle-an-event"></a>Pour gérer un événement  
  
1. Sélectionnez dans `mWidget` la liste déroulante de gauche dans l' **éditeur de code**.  
  
2. Sélectionnez l' `PercentDone` événement dans la liste déroulante de droite. L' **éditeur de code** ouvre la `mWidget_PercentDone` procédure événementielle.  
  
    > [!NOTE]
    > L' **éditeur de code** est utile, mais pas obligatoire, pour l’insertion de nouveaux gestionnaires d’événements. Dans cette procédure pas à pas, il est plus direct de copier uniquement les gestionnaires d’événements directement dans votre code.  
  
3. Ajoutez le code suivant au gestionnaire d'événements `mWidget_PercentDone` :  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#5)]  
  
     Chaque fois que l' `PercentDone` événement est déclenché, la procédure événementielle affiche le pourcentage effectué dans un `Label` contrôle. La `DoEvents` méthode permet à l’étiquette de repeindre et donne également à l’utilisateur la possibilité de cliquer sur le bouton **Annuler** .  
  
4. Ajoutez le code suivant pour le `Button2_Click` Gestionnaire d’événements :  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#6)]  
  
 Si l’utilisateur clique sur le bouton **Annuler** pendant que `LongTask` est en cours d’exécution, l' `Button2_Click` événement est exécuté dès que l' `DoEvents` instruction autorise le traitement de l’événement. La variable au niveau de la classe `mblnCancel` a la valeur `True` , et l' `mWidget_PercentDone` événement la teste, puis définit l' `ByRef Cancel` argument sur `True` .  
  
## <a name="connecting-a-withevents-variable-to-an-object"></a>Connexion d’une variable WithEvents à un objet  

 `Form1` est maintenant configuré pour gérer les `Widget` événements d’un objet. Il ne reste plus qu’à trouver `Widget` quelque part.  
  
 Quand vous déclarez une variable `WithEvents` au moment de la conception, aucun objet n’est associé à celle-ci. Une `WithEvents` variable est semblable à toute autre variable objet. Vous devez créer un objet et lui assigner une référence avec la `WithEvents` variable.  
  
#### <a name="to-create-an-object-and-assign-a-reference-to-it"></a>Pour créer un objet et lui assigner une référence  
  
1. Sélectionnez **(événements Form1)** dans la liste déroulante de gauche de l' **éditeur de code**.  
  
2. Sélectionnez l' `Load` événement dans la liste déroulante de droite. L' **éditeur de code** ouvre la `Form1_Load` procédure événementielle.  
  
3. Ajoutez le code suivant pour la `Form1_Load` procédure événementielle afin de créer le `Widget` :  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#7)]  
  
 Lorsque ce code s’exécute, Visual Basic crée un `Widget` objet et connecte ses événements aux procédures d’événement associées à `mWidget` . À partir de là, chaque fois que le `Widget` déclenche son `PercentDone` événement, la `mWidget_PercentDone` procédure événementielle est exécutée.  
  
#### <a name="to-call-the-longtask-method"></a>Pour appeler la méthode LongTask  
  
- Ajoutez le code suivant au gestionnaire d'événements `Button1_Click` :  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#8)]  
  
 Avant que la `LongTask` méthode ne soit appelée, l’étiquette qui affiche le pourcentage d’achèvement doit être initialisée et l' `Boolean` indicateur de niveau classe pour annuler la méthode doit avoir la valeur `False` .  
  
 `LongTask` est appelé avec une durée de tâche de 12,2 secondes. L' `PercentDone` événement est déclenché une fois tous les tiers un seconde. Chaque fois que l’événement est déclenché, la `mWidget_PercentDone` procédure événementielle est exécutée.  
  
 Lorsque `LongTask` est terminé, `mblnCancel` est testé pour voir si l’opération s’est `LongTask` terminée normalement ou si elle s’est arrêtée car `mblnCancel` a la valeur `True` . Le pourcentage d’achèvement est mis à jour uniquement dans le cas précédent.  
  
#### <a name="to-run-the-program"></a>Pour exécuter le programme  
  
1. Appuyez sur F5 pour mettre le projet en mode exécution.  
  
2. Cliquez sur le bouton **Démarrer la tâche** . Chaque fois `PercentDone` que l’événement est déclenché, l’étiquette est mise à jour avec le pourcentage de la tâche qui est terminé.  
  
3. Cliquez sur le bouton **Annuler** pour arrêter la tâche. Notez que l’apparence du bouton **Annuler** ne change pas immédiatement lorsque vous cliquez dessus. L' `Click` événement ne peut pas se produire tant que l’instruction n’autorise pas le `My.Application.DoEvents` traitement des événements.  
  
    > [!NOTE]
    > La `My.Application.DoEvents` méthode ne traite pas les événements exactement de la même façon que le formulaire. Par exemple, dans cette procédure pas à pas, vous devez cliquer deux fois sur le bouton **Annuler** . Pour permettre au formulaire de gérer directement les événements, vous pouvez utiliser le multithreading. Pour plus d’informations, consultez [threads managés](../../../../standard/threading/index.md).
  
 Il peut être intéressant d’exécuter le programme avec F11 et de parcourir le code une ligne à la fois. Vous pouvez voir clairement la façon dont l’exécution entre `LongTask` en vigueur, puis entrer brièvement `Form1` chaque fois que l' `PercentDone` événement est déclenché.  
  
 Que se passerait-il si, alors que l’exécution était de retour dans le code de `Form1` , la `LongTask` méthode était appelée à nouveau ? Au pire, un dépassement de capacité de la pile peut se produire si `LongTask` a été appelé chaque fois que l’événement a été déclenché.  
  
 Vous pouvez faire en sorte que la variable `mWidget` gère les événements d’un autre `Widget` objet en affectant une référence au nouveau `Widget` à `mWidget` . En fait, vous pouvez faire en sorte que le code effectue `Button1_Click` cette opération chaque fois que vous cliquez sur le bouton.  
  
#### <a name="to-handle-events-for-a-different-widget"></a>Pour gérer les événements d’un autre widget  
  
- Ajoutez la ligne de code suivante à la `Button1_Click` procédure, juste avant la ligne qui indique `mWidget.LongTask(12.2, 0.33)` :  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#9)]  
  
 Le code ci-dessus crée un nouveau `Widget` chaque fois que l’utilisateur clique sur le bouton. Dès que la `LongTask` méthode se termine, la référence à `Widget` est libérée et `Widget` est détruite.  
  
 Une `WithEvents` variable ne peut contenir qu’une seule référence d’objet à la fois. par conséquent, si vous assignez un autre `Widget` objet à `mWidget` , les `Widget` événements de l’objet précédent ne seront plus gérés. Si `mWidget` est la seule variable objet contenant une référence à l’ancien `Widget` , l’objet est détruit. Si vous souhaitez gérer les événements de plusieurs `Widget` objets, utilisez l' `AddHandler` instruction pour traiter les événements de chaque objet séparément.  
  
> [!NOTE]
> Vous pouvez déclarer autant `WithEvents` de variables que vous le souhaitez, mais les tableaux de `WithEvents` variables ne sont pas pris en charge.  
  
## <a name="see-also"></a>Voir aussi

- [Procédure pas à pas : déclaration et déclenchement des événements](walkthrough-declaring-and-raising-events.md)
- [Événements](index.md)

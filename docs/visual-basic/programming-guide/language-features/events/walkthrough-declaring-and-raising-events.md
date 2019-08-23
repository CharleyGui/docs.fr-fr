---
title: Déclaration et déclenchement d’événements (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], events
- events [Visual Basic], walkthroughs
- declaring events [Visual Basic], walkthroughs
- events [Visual Basic], declaring
- events [Visual Basic], raising
- raising events [Visual Basic], walkthroughs
ms.assetid: 8ffb3be8-097d-4d3c-b71e-04555ebda2a2
ms.openlocfilehash: 20e2b0efbf40597049c515134f408927f18d5603
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956339"
---
# <a name="walkthrough-declaring-and-raising-events-visual-basic"></a>Procédure pas à pas : Déclaration et déclenchement d’événements (Visual Basic)
Cette procédure pas à pas montre comment déclarer et déclencher des événements pour `Widget`une classe nommée. Une fois les étapes terminées, vous souhaiterez peut-être lire la [rubrique d’accompagnement, procédure pas à pas: Gestion des](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)événements, qui montre comment utiliser des événements `Widget` d’objets pour fournir des informations d’État dans une application.  
  
## <a name="the-widget-class"></a>Classe widget  
 Supposons que vous ayez une `Widget` classe. Votre `Widget` classe a une méthode qui peut prendre beaucoup de temps pour s’exécuter, et vous souhaitez que votre application puisse mettre en place un type d’indicateur d’achèvement.  
  
 Bien entendu, vous pouvez faire en `Widget` sorte que l’objet affiche une boîte de dialogue de pourcentage de réalisation, mais vous serez alors bloqué avec cette boîte de dialogue dans chaque projet `Widget` dans lequel vous avez utilisé la classe. Un bon principe de la conception d’objets est de permettre à l’application qui utilise un objet de gérer l’interface utilisateur, à moins que l’objectif entier de l’objet ne soit de gérer un formulaire ou une boîte de dialogue.  
  
 L’objectif de `Widget` est d’effectuer d’autres tâches. il est donc préférable d’ajouter `PercentDone` un événement et de laisser la procédure `Widget`qui appelle les méthodes pour gérer cet événement et afficher les mises à jour de l’État. L' `PercentDone` événement peut également fournir un mécanisme d’annulation de la tâche.  
  
#### <a name="to-build-the-code-example-for-this-topic"></a>Pour générer l’exemple de code pour cette rubrique  
  
1. Ouvrez un nouveau Visual Basic projet d’application Windows et créez un formulaire `Form1`nommé.  
  
2. Ajoutez deux boutons et une étiquette à `Form1`.  
  
3. Nommez les objets de la façon indiquée dans le tableau suivant.  
  
    |Objet|Propriété|Paramètre|  
    |------------|--------------|-------------|  
    |`Button1`|`Text`|Démarrer la tâche|  
    |`Button2`|`Text`|Annuler|  
    |`Label`|`(Name)`, `Text`|lblPercentDone, 0|  
  
4. Dans le menu **projet** , choisissez **Ajouter une classe** pour ajouter une classe `Widget.vb` nommée au projet.  
  
#### <a name="to-declare-an-event-for-the-widget-class"></a>Pour déclarer un événement pour la classe widget  
  
- Utilisez le `Event` mot clé pour déclarer un événement dans `Widget` la classe. Notez qu’un événement peut avoir `ByVal` des `ByRef` arguments et, `Widget`comme `PercentDone` le montre l’événement de:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#1)]  
  
 Lorsque l’objet appelant reçoit un `PercentDone` événement, l' `Percent` argument contient le pourcentage de la tâche qui est terminé. L' `Cancel` argument peut avoir la `True` valeur pour annuler la méthode qui a déclenché l’événement.  
  
> [!NOTE]
> Vous pouvez déclarer des arguments d’événement de la même façon que des arguments de procédures, avec les exceptions suivantes: Les événements ne `Optional` peuvent `ParamArray` pas avoir d’arguments ou, et les événements n’ont pas de valeurs de retour.  
  
 L' `PercentDone` événement est déclenché par la `LongTask` méthode de la `Widget` classe. `LongTask`accepte deux arguments: la durée pendant laquelle la méthode prétend exécuter le travail, et l’intervalle de temps minimal avant `LongTask` les pauses pour déclencher l' `PercentDone` événement.  
  
#### <a name="to-raise-the-percentdone-event"></a>Pour déclencher l’événement PercentDone  
  
1. Pour simplifier l’accès à `Timer` la propriété utilisée par cette classe, ajoutez `Imports` une instruction en haut de la section déclarations de votre module de classe, au `Class Widget` -dessus de l’instruction.  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#2)]  
  
2. Ajoutez le code suivant à la classe `Widget` :  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#3)]  
  
 Lorsque votre application appelle la `LongTask` méthode, la `Widget` classe déclenche l' `PercentDone` événement toutes `MinimumInterval` les secondes. Lorsque l’événement est retourné `LongTask` , vérifie si l’argument `Cancel` a la valeur `True`.  
  
 Quelques exclusions de responsabilité sont nécessaires ici. Par souci de simplicité `LongTask` , la procédure suppose que vous savez à l’avance le temps nécessaire à la tâche. Ce n’est presque jamais le cas. La Division des tâches en segments de taille égale peut être difficile, et souvent ce qui est le plus important pour les utilisateurs est simplement le temps qui s’écoule avant qu’ils ne reçoivent une indication qu’un événement se produit.  
  
 Vous avez peut-être repéré un autre défaut dans cet exemple. La `Timer` propriété retourne le nombre de secondes qui se sont écoulées depuis minuit; par conséquent, l’application est bloquée si elle est démarrée juste avant minuit. Une approche plus prudente de la mesure du temps consisterait à prendre en considération des conditions de limites, ou à les éviter, à `Now`l’aide de propriétés telles que.  
  
 Maintenant que la `Widget` classe peut déclencher des événements, vous pouvez passer à la procédure pas à pas suivante. [Procédure pas à pas : La gestion](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md) des événements montre comment `WithEvents` utiliser pour associer un gestionnaire d’événements `PercentDone` à l’événement.  
  
## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.DateAndTime.Timer%2A>
- <xref:Microsoft.VisualBasic.DateAndTime.Now%2A>
- [Procédure pas à pas : Gestion des événements](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)
- [Événements](../../../../visual-basic/programming-guide/language-features/events/index.md)

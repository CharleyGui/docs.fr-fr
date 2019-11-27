---
title: Déclaration et déclenchement des événements
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], events
- events [Visual Basic], walkthroughs
- declaring events [Visual Basic], walkthroughs
- events [Visual Basic], declaring
- events [Visual Basic], raising
- raising events [Visual Basic], walkthroughs
ms.assetid: 8ffb3be8-097d-4d3c-b71e-04555ebda2a2
ms.openlocfilehash: 6f4c303604f9cf55b4ecd500636e0d2772b6234c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345085"
---
# <a name="walkthrough-declaring-and-raising-events-visual-basic"></a>Procédure pas à pas : déclaration et déclenchement des événements (Visual Basic)
Cette procédure pas à pas montre comment déclarer et déclencher des événements pour une classe nommée `Widget`. Une fois les étapes terminées, vous souhaiterez peut-être lire la rubrique d’accompagnement, [procédure pas à pas : gestion des événements](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md), qui montre comment utiliser des événements de `Widget` objets pour fournir des informations d’État dans une application.  
  
## <a name="the-widget-class"></a>Classe widget  
 Supposons que vous ayez une classe `Widget`. Votre classe `Widget` a une méthode qui peut prendre beaucoup de temps pour s’exécuter, et vous souhaitez que votre application puisse mettre en place un type d’indicateur d’achèvement.  
  
 Bien entendu, vous pouvez faire en sorte que l’objet `Widget` affiche une boîte de dialogue de pourcentage de réalisation, mais vous serez alors bloqué avec cette boîte de dialogue dans chaque projet dans lequel vous avez utilisé la classe `Widget`. Un bon principe de la conception d’objets est de permettre à l’application qui utilise un objet de gérer l’interface utilisateur, à moins que l’objectif entier de l’objet ne soit de gérer un formulaire ou une boîte de dialogue.  
  
 L’objectif de `Widget` est d’effectuer d’autres tâches. il est donc préférable d’ajouter un événement `PercentDone` et de laisser la procédure qui appelle les méthodes de `Widget`gérer cet événement et afficher les mises à jour de l’État. L’événement `PercentDone` peut également fournir un mécanisme d’annulation de la tâche.  
  
#### <a name="to-build-the-code-example-for-this-topic"></a>Pour générer l’exemple de code pour cette rubrique  
  
1. Ouvrez un nouveau Visual Basic projet d’application Windows et créez un formulaire nommé `Form1`.  
  
2. Ajoutez deux boutons et une étiquette pour `Form1`.  
  
3. Nommez les objets de la façon indiquée dans le tableau suivant.  
  
    |Object|Propriété|Paramètre|  
    |------------|--------------|-------------|  
    |`Button1`|`Text`|Tâche de démarrage|  
    |`Button2`|`Text`|Annuler|  
    |`Label`|`(Name)`, `Text`|lblPercentDone, 0|  
  
4. Dans le menu **projet** , choisissez **Ajouter une classe** pour ajouter une classe nommée `Widget.vb` au projet.  
  
#### <a name="to-declare-an-event-for-the-widget-class"></a>Pour déclarer un événement pour la classe widget  
  
- Utilisez le mot clé `Event` pour déclarer un événement dans la classe `Widget`. Notez qu’un événement peut avoir des arguments `ByVal` et `ByRef`, comme le montre l’événement `PercentDone` de `Widget`:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#1)]  
  
 Lorsque l’objet appelant reçoit un événement `PercentDone`, l’argument `Percent` contient le pourcentage de la tâche qui est terminé. L’argument `Cancel` peut avoir la valeur `True` pour annuler la méthode qui a déclenché l’événement.  
  
> [!NOTE]
> Vous pouvez déclarer des arguments d’événement de la même façon que des arguments de procédures, avec les exceptions suivantes : les événements ne peuvent pas avoir d’arguments `Optional` ou `ParamArray`, et les événements n’ont pas de valeurs de retour.  
  
 L’événement `PercentDone` est déclenché par la méthode `LongTask` de la classe `Widget`. `LongTask` accepte deux arguments : la durée pendant laquelle la méthode prétend faire fonctionner et l’intervalle de temps minimal avant `LongTask` s’interrompt pour déclencher l’événement `PercentDone`.  
  
#### <a name="to-raise-the-percentdone-event"></a>Pour déclencher l’événement PercentDone  
  
1. Pour simplifier l’accès à la propriété `Timer` utilisée par cette classe, ajoutez une instruction `Imports` en haut de la section déclarations de votre module de classe, au-dessus de l’instruction `Class Widget`.  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#2)]  
  
2. Ajoutez le code suivant à la classe `Widget` :  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#3)]  
  
 Lorsque votre application appelle la méthode `LongTask`, la classe `Widget` déclenche l’événement `PercentDone` toutes les `MinimumInterval` secondes. Lorsque l’événement est retourné, `LongTask` vérifie si l’argument `Cancel` a été défini sur `True`.  
  
 Quelques exclusions de responsabilité sont nécessaires ici. Par souci de simplicité, la procédure `LongTask` suppose que vous savez à l’avance le temps nécessaire à la tâche. Ce n’est presque jamais le cas. La Division des tâches en segments de taille égale peut être difficile, et souvent ce qui est le plus important pour les utilisateurs est simplement le temps qui s’écoule avant qu’ils ne reçoivent une indication qu’un événement se produit.  
  
 Vous avez peut-être repéré un autre défaut dans cet exemple. La propriété `Timer` retourne le nombre de secondes qui se sont écoulées depuis minuit ; par conséquent, l’application est bloquée si elle est démarrée juste avant minuit. Une approche plus prudente de la mesure du temps consisterait à prendre en considération des conditions de limites, ou à les éviter, à l’aide de propriétés telles que `Now`.  
  
 Maintenant que la classe `Widget` peut déclencher des événements, vous pouvez passer à la procédure pas à pas suivante. [Procédure pas à pas : gestion des événements](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md) montre comment utiliser `WithEvents` pour associer un gestionnaire d’événements à l’événement `PercentDone`.  
  
## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.DateAndTime.Timer%2A>
- <xref:Microsoft.VisualBasic.DateAndTime.Now%2A>
- [Procédure pas à pas : gestion des événements](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)
- [Événements](../../../../visual-basic/programming-guide/language-features/events/index.md)

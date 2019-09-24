---
title: 'Procédure : Appeler un gestionnaire d’événements dans Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- event handlers [Visual Basic], calling
- event handlers
- procedures [Visual Basic], event handlers
- procedures [Visual Basic], calling
ms.assetid: 72e18ef8-144e-40df-a1f4-066a57271e28
ms.openlocfilehash: a9e090e83b180686ccb832aa6efb314c7e0fcc9a
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216617"
---
# <a name="how-to-call-an-event-handler-in-visual-basic"></a>Procédure : Appeler un gestionnaire d’événements dans Visual Basic

Un *événement* est une action ou une occurrence, telle qu’un clic de souris ou une limite de crédit dépassée, qui est reconnue par un composant de programme et pour laquelle vous pouvez écrire du code pour répondre. Un *Gestionnaire d’événements* est le code que vous écrivez pour répondre à un événement.

 Un gestionnaire d’événements dans Visual Basic est `Sub` une procédure. Toutefois, vous ne l’appelez pas normalement de la même façon que `Sub` les autres procédures. Au lieu de cela, vous identifiez la procédure en tant que gestionnaire de l’événement. Vous pouvez le faire avec une clause [Handles](../../../language-reference/statements/handles-clause.md) et une variable [WithEvents](../../../language-reference/modifiers/withevents.md) , ou avec une [instruction AddHandler](../../../language-reference/statements/addhandler-statement.md). L’utilisation `Handles` d’une clause est la manière par défaut de déclarer un gestionnaire d’événements dans Visual Basic. C’est la façon dont les gestionnaires d’événements sont écrits par les concepteurs lorsque vous programmez dans l’environnement de développement intégré (IDE). L' `AddHandler` instruction est appropriée pour déclencher des événements de manière dynamique au moment de l’exécution.

 Lorsque l’événement se produit, Visual Basic appelle automatiquement la procédure du gestionnaire d’événements. Tout code qui a accès à l’événement peut le faire en exécutant une [instruction RaiseEvent](../../../language-reference/statements/raiseevent-statement.md).

 Vous pouvez associer plusieurs gestionnaires d’événements à un même événement. Dans certains cas, vous pouvez dissocier un gestionnaire d’un événement. Pour plus d’informations, consultez [Événements](../events/index.md).

### <a name="to-call-an-event-handler-using-handles-and-withevents"></a>Pour appeler un gestionnaire d’événements à l’aide de handles et de WithEvents

1. Assurez-vous que l’événement est déclaré avec une [instruction Event](../../../language-reference/statements/event-statement.md).

2. Déclarez une variable objet au niveau du module ou de la classe, à l’aide du mot clé [WithEvents](../../../language-reference/modifiers/withevents.md) . La `As` clause de cette variable doit spécifier la classe qui déclenche l’événement.

3. Dans la déclaration de la procédure de gestion `Sub` des événements, ajoutez une clause [Handles](../../../language-reference/statements/handles-clause.md) qui `WithEvents` spécifie la variable et le nom de l’événement.

4. Lorsque l’événement se produit, Visual Basic appelle automatiquement `Sub` la procédure. Votre code peut utiliser une `RaiseEvent` instruction pour faire en sorte que l’événement se produise.

     L’exemple suivant définit un événement et une `WithEvents` variable qui fait référence à la classe qui déclenche l’événement. La procédure de gestion `Sub` des événements utilise `Handles` une clause pour spécifier la classe et l’événement qu’elle gère.

     [!code-vb[VbVbcnProcedures#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#4)]

### <a name="to-call-an-event-handler-using-addhandler"></a>Pour appeler un gestionnaire d’événements à l’aide d’AddHandler

1. Assurez-vous que l’événement est `Event` déclaré avec une instruction.

2. Exécutez une [instruction AddHandler](../../../language-reference/statements/addhandler-statement.md) pour connecter dynamiquement la procédure de gestion `Sub` des événements avec l’événement.

3. Lorsque l’événement se produit, Visual Basic appelle automatiquement `Sub` la procédure. Votre code peut utiliser une `RaiseEvent` instruction pour faire en sorte que l’événement se produise.

     L’exemple suivant définit une `Sub` procédure pour gérer l' <xref:System.Windows.Forms.Form.Closing> événement d’un formulaire. Il utilise ensuite l' [instruction AddHandler](../../../language-reference/statements/addhandler-statement.md) pour associer la `catchClose` procédure en tant que gestionnaire d' <xref:System.Windows.Forms.Form.Closing>événements pour.

     [!code-vb[VbVbcnProcedures#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#5)]

     Vous pouvez dissocier un gestionnaire d’événements d’un événement en exécutant l' [instruction RemoveHandler](../../../language-reference/statements/removehandler-statement.md).

## <a name="see-also"></a>Voir aussi

- [Procédures](index.md)
- [Procédures Sub](sub-procedures.md)
- [Sub (instruction)](../../../language-reference/statements/sub-statement.md)
- [AddressOf (opérateur)](../../../language-reference/operators/addressof-operator.md)
- [Guide pratique pour Créer une procédure](how-to-create-a-procedure.md)
- [Guide pratique pour Appeler une procédure qui ne retourne pas de valeur](how-to-call-a-procedure-that-does-not-return-a-value.md)

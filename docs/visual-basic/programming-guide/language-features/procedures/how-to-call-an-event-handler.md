---
title: 'Comment : appeler un gestionnaire d’événements'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- event handlers [Visual Basic], calling
- event handlers
- procedures [Visual Basic], event handlers
- procedures [Visual Basic], calling
ms.assetid: 72e18ef8-144e-40df-a1f4-066a57271e28
ms.openlocfilehash: 0c626a9ad92fe2cd0ea117a9abdd2965a09df2ea
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74340430"
---
# <a name="how-to-call-an-event-handler-in-visual-basic"></a>Comment : appeler un gestionnaire d'événements en Visual Basic

Un *événement* est une action ou une occurrence, telle qu’un clic de souris ou une limite de crédit dépassée, qui est reconnue par un composant de programme et pour laquelle vous pouvez écrire du code pour répondre. Un *Gestionnaire d’événements* est le code que vous écrivez pour répondre à un événement.

 Un gestionnaire d’événements dans Visual Basic est une procédure `Sub`. Toutefois, vous ne l’appelez pas normalement de la même façon que les autres procédures de `Sub`. Au lieu de cela, vous identifiez la procédure en tant que gestionnaire de l’événement. Vous pouvez le faire avec une clause [Handles](../../../language-reference/statements/handles-clause.md) et une variable [WithEvents](../../../language-reference/modifiers/withevents.md) , ou avec une [instruction AddHandler](../../../language-reference/statements/addhandler-statement.md). L’utilisation d’une clause `Handles` est la manière par défaut de déclarer un gestionnaire d’événements dans Visual Basic. C’est la façon dont les gestionnaires d’événements sont écrits par les concepteurs lorsque vous programmez dans l’environnement de développement intégré (IDE). L’instruction `AddHandler` est appropriée pour déclencher des événements de manière dynamique au moment de l’exécution.

 Lorsque l’événement se produit, Visual Basic appelle automatiquement la procédure du gestionnaire d’événements. Tout code qui a accès à l’événement peut le faire en exécutant une [instruction RaiseEvent](../../../language-reference/statements/raiseevent-statement.md).

 Vous pouvez associer plusieurs gestionnaires d’événements à un même événement. Dans certains cas, vous pouvez dissocier un gestionnaire d’un événement. Pour plus d'informations, consultez [Events](../events/index.md).

### <a name="to-call-an-event-handler-using-handles-and-withevents"></a>Pour appeler un gestionnaire d’événements à l’aide de handles et de WithEvents

1. Assurez-vous que l’événement est déclaré avec une [instruction Event](../../../language-reference/statements/event-statement.md).

2. Déclarez une variable objet au niveau du module ou de la classe, à l’aide du mot clé [WithEvents](../../../language-reference/modifiers/withevents.md) . La clause `As` pour cette variable doit spécifier la classe qui déclenche l’événement.

3. Dans la déclaration de la procédure de gestion des événements `Sub`, ajoutez une clause [Handles](../../../language-reference/statements/handles-clause.md) qui spécifie la variable `WithEvents` et le nom de l’événement.

4. Lorsque l’événement se produit, Visual Basic appelle automatiquement la procédure `Sub`. Votre code peut utiliser une instruction `RaiseEvent` pour faire en sorte que l’événement se produise.

     L’exemple suivant définit un événement et une variable `WithEvents` qui fait référence à la classe qui déclenche l’événement. La procédure de `Sub` de gestion des événements utilise une clause `Handles` pour spécifier la classe et l’événement qu’elle gère.

     [!code-vb[VbVbcnProcedures#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#4)]

### <a name="to-call-an-event-handler-using-addhandler"></a>Pour appeler un gestionnaire d’événements à l’aide d’AddHandler

1. Assurez-vous que l’événement est déclaré avec une instruction `Event`.

2. Exécutez une [instruction AddHandler](../../../language-reference/statements/addhandler-statement.md) pour connecter dynamiquement la procédure `Sub` de gestion des événements avec l’événement.

3. Lorsque l’événement se produit, Visual Basic appelle automatiquement la procédure `Sub`. Votre code peut utiliser une instruction `RaiseEvent` pour faire en sorte que l’événement se produise.

     L’exemple suivant définit une procédure `Sub` pour gérer l’événement <xref:System.Windows.Forms.Form.Closing> d’un formulaire. Il utilise ensuite l' [instruction AddHandler](../../../language-reference/statements/addhandler-statement.md) pour associer la procédure `catchClose` en tant que gestionnaire d’événements pour <xref:System.Windows.Forms.Form.Closing>.

     [!code-vb[VbVbcnProcedures#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#5)]

     Vous pouvez dissocier un gestionnaire d’événements d’un événement en exécutant l' [instruction RemoveHandler](../../../language-reference/statements/removehandler-statement.md).

## <a name="see-also"></a>Voir aussi

- [Procédures](index.md)
- [Procédures Sub](sub-procedures.md)
- [Sub (instruction)](../../../language-reference/statements/sub-statement.md)
- [AddressOf (opérateur)](../../../language-reference/operators/addressof-operator.md)
- [Guide pratique : créer une procédure](how-to-create-a-procedure.md)
- [Guide pratique : appeler une procédure qui ne retourne pas de valeur](how-to-call-a-procedure-that-does-not-return-a-value.md)

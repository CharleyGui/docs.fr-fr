---
title: Comment appeler un gestionnaire d’événements
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- event handlers [Visual Basic], calling
- event handlers
- procedures [Visual Basic], event handlers
- procedures [Visual Basic], calling
no-loc:
- WithEvents
ms.assetid: 72e18ef8-144e-40df-a1f4-066a57271e28
ms.openlocfilehash: 3762c79dd3d883ae2ccfe76b335cf98ac87d4246
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2020
ms.locfileid: "89464959"
---
# <a name="how-to-call-an-event-handler-in-visual-basic"></a>Comment appeler un gestionnaire d’événements dans Visual Basic

Un *événement* est une action ou une occurrence, telle qu’un clic de souris ou une limite de crédit dépassée, qui est reconnue par un composant de programme et pour laquelle vous pouvez écrire du code pour répondre. Un *Gestionnaire d’événements* est le code que vous écrivez pour répondre à un événement.

Un gestionnaire d’événements dans Visual Basic est une `Sub` procédure. Toutefois, vous ne l’appelez pas normalement de la même façon que les autres `Sub` procédures. Au lieu de cela, vous identifiez la procédure en tant que gestionnaire de l’événement. Vous pouvez le faire soit avec une [`Handles`](../../../language-reference/statements/handles-clause.md) clause et une [`WithEvents`](../../../language-reference/modifiers/withevents.md) variable, soit avec une [instruction AddHandler](../../../language-reference/statements/addhandler-statement.md). L’utilisation d’une `Handles` clause est la manière par défaut de déclarer un gestionnaire d’événements dans Visual Basic. C’est la façon dont les gestionnaires d’événements sont écrits par les concepteurs lorsque vous programmez dans l’environnement de développement intégré (IDE). L' `AddHandler` instruction est appropriée pour déclencher des événements de manière dynamique au moment de l’exécution.

Lorsque l’événement se produit, Visual Basic appelle automatiquement la procédure du gestionnaire d’événements. Tout code qui a accès à l’événement peut le faire en exécutant une [instruction RaiseEvent](../../../language-reference/statements/raiseevent-statement.md).

Vous pouvez associer plusieurs gestionnaires d’événements à un même événement. Dans certains cas, vous pouvez dissocier un gestionnaire d’un événement. Pour plus d’informations, consultez [Événements](../events/index.md).

## <a name="call-an-event-handler-using-no-loc-texthandles-and-no-locwithevents"></a>Appeler un gestionnaire d’événements à l’aide :::no-loc text="Handles"::: de et WithEvents

1. Assurez-vous que l’événement est déclaré avec une [instruction Event](../../../language-reference/statements/event-statement.md).

2. Déclarez une variable objet au niveau du module ou de la classe, à l’aide du [`WithEvents`](../../../language-reference/modifiers/withevents.md) mot clé. La `As` clause de cette variable doit spécifier la classe qui déclenche l’événement.

3. Dans la déclaration de la procédure de gestion des événements `Sub` , ajoutez une [`Handles`](../../../language-reference/statements/handles-clause.md) clause qui spécifie la `WithEvents` variable et le nom de l’événement.

4. Lorsque l’événement se produit, Visual Basic appelle automatiquement la `Sub` procédure. Votre code peut utiliser une `RaiseEvent` instruction pour faire en sorte que l’événement se produise.

    L’exemple suivant définit un événement et une `WithEvents` variable qui fait référence à la classe qui déclenche l’événement. La procédure de gestion des événements `Sub` utilise une `Handles` clause pour spécifier la classe et l’événement qu’elle gère.

    :::code language="vb" source="snippets/how-to-call-an-event-handler/SpecialForm.vb" id="4":::

## <a name="call-an-event-handler-using-addhandler"></a>Appeler un gestionnaire d’événements à l’aide de AddHandler

1. Assurez-vous que l’événement est déclaré avec une `Event` instruction.

2. Exécutez une [instruction AddHandler](../../../language-reference/statements/addhandler-statement.md) pour connecter dynamiquement la procédure de gestion des événements `Sub` avec l’événement.

3. Lorsque l’événement se produit, Visual Basic appelle automatiquement la `Sub` procédure. Votre code peut utiliser une `RaiseEvent` instruction pour faire en sorte que l’événement se produise.

    L’exemple suivant utilise l' [instruction AddHandler](../../../language-reference/statements/addhandler-statement.md) dans le constructeur pour associer la `OnFormClosing` procédure en tant que gestionnaire d’événements pour <xref:System.Windows.Forms.Form.FormClosing> .

    :::code language="vb" source="snippets/how-to-call-an-event-handler/SpecialForm.vb" id="5":::

    Vous pouvez dissocier un gestionnaire d’événements d’un événement en exécutant l' [instruction RemoveHandler](../../../language-reference/statements/removehandler-statement.md).

## <a name="see-also"></a>Voir aussi

- [Procédures](index.md)
- [Sub, procédures](sub-procedures.md)
- [Sub (instruction)](../../../language-reference/statements/sub-statement.md)
- [AddressOf, opérateur](../../../language-reference/operators/addressof-operator.md)
- [Guide pratique : créer une procédure](how-to-create-a-procedure.md)
- [Comment : appeler une procédure qui ne retourne pas de valeur](how-to-call-a-procedure-that-does-not-return-a-value.md)

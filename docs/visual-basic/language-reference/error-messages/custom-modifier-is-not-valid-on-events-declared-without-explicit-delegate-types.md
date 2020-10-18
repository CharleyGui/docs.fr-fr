---
title: Le modificateur 'Custom' n'est pas valide pour les événements déclarés sans types délégués explicites
ms.date: 07/20/2015
f1_keywords:
- vbc31122
- bc31122
helpviewer_keywords:
- BC31122
ms.assetid: 6911f0d1-641a-473b-906d-8ee5681194be
ms.openlocfilehash: a2277e3778c2c252fd4b1eaeb033d549f041c15c
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160631"
---
# <a name="bc31122-custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types"></a>BC31122 : le modificateur’Custom’n’est pas valide pour les événements déclarés sans types délégués explicites

Contrairement à un événement non personnalisé, une `Custom Event` déclaration requiert une `As` clause qui suit le nom de l’événement qui spécifie explicitement le type délégué de l’événement.

 Les événements non personnalisés peuvent être définis à l’aide d’une `As` clause et d’un type délégué explicite, ou avec une liste de paramètres qui suit immédiatement le nom de l’événement.

 **ID d’erreur :** BC31122

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. Définissez un délégué avec la même liste de paramètres que l’événement personnalisé.

     Par exemple, si le `Custom Event` a été défini par `Custom Event Test(ByVal sender As Object, ByVal i As Integer)` , le délégué correspondant est le suivant.

     [!code-vb[VbVbalrEventError#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEventError/VB/VbVbalrEventError.vb#18)]

2. Remplacez la liste de paramètres de l’événement personnalisé par une `As` clause qui spécifie le type délégué.

     Pour continuer avec l’exemple, la `Custom Event` déclaration est réécrite comme suit.

     [!code-vb[VbVbalrEventError#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEventError/VB/VbVbalrEventError.vb#19)]

## <a name="example"></a> Exemple

 Cet exemple déclare un `Custom Event` et spécifie la `As` clause requise avec un type délégué.

 [!code-vb[VbVbalrEventError#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEventError/VB/VbVbalrEventError.vb#2)]

## <a name="see-also"></a>Voir aussi

- [Event, instruction](../statements/event-statement.md)
- [Delegate, instruction](../statements/delegate-statement.md)
- [Événements](../../programming-guide/language-features/events/index.md)

---
title: 'Comment : créer une variable qui ne change pas de valeur'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], read-only
- variables [Visual Basic], constant value
ms.assetid: 86b59266-25df-4635-ae15-9b59c411d036
ms.openlocfilehash: 04e08784b5cfbdeb6db73b9b00fe9afa201bd06d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410514"
---
# <a name="how-to-create-a-variable-that-does-not-change-in-value-visual-basic"></a>Comment : créer une variable qui ne change pas de valeur (Visual Basic)

La notion d’une variable qui ne change pas sa valeur peut sembler contradictoire. Toutefois, il existe des situations où une constante n’est pas possible et il est utile d’avoir une variable avec une valeur fixe. Dans ce cas, vous pouvez définir une variable membre avec le mot clé [ReadOnly](../../../language-reference/modifiers/readonly.md) .

Vous ne pouvez pas utiliser l' [instruction Const](../../../language-reference/statements/const-statement.md) pour déclarer et assigner une valeur constante dans les circonstances suivantes :

- L' `Const` instruction n’accepte pas le type de données que vous souhaitez utiliser

- Vous ne connaissez pas la valeur au moment de la compilation

- Vous ne parvenez pas à calculer la valeur constante au moment de la compilation

### <a name="to-create-a-variable-that-does-not-change-in-value"></a>Pour créer une variable qui ne change pas de valeur

1. Au niveau du module, déclarez une variable membre avec l' [instruction Dim](../../../language-reference/statements/dim-statement.md)et incluez le mot clé [ReadOnly](../../../language-reference/modifiers/readonly.md) .

    ```vb
    Dim ReadOnly timeStarted
    ```

    Vous pouvez spécifier `ReadOnly` uniquement sur une variable membre. Cela signifie que vous devez définir la variable au niveau du module, en dehors de toute procédure.

2. Si vous pouvez calculer la valeur dans une seule instruction au moment de la compilation, utilisez une clause d’initialisation dans l' `Dim` instruction. Faites suivre la clause [As](../../../language-reference/statements/as-clause.md) d’un signe égal ( `=` ), puis d’une expression. Assurez-vous que le compilateur peut évaluer cette expression sur une valeur constante.

    ```vb
    Dim ReadOnly timeStarted As Date = Now
    ```

    Vous ne pouvez assigner une valeur à une `ReadOnly` variable qu’une seule fois. Une fois cela fait, aucun code ne peut modifier sa valeur.

    Si vous ne connaissez pas la valeur au moment de la compilation ou si vous ne pouvez pas la calculer au moment de la compilation dans une instruction unique, vous pouvez toujours l’assigner au moment de l’exécution dans un constructeur. Pour ce faire, vous devez déclarer la `ReadOnly` variable au niveau de la classe ou de la structure. Dans le constructeur de cette classe ou de cette structure, calculez la valeur fixe de la variable et assignez-la à la variable avant de retourner le constructeur.

## <a name="see-also"></a>Voir aussi

- [WriteOnly](../../../language-reference/modifiers/writeonly.md)
- [Const (instruction)](../../../language-reference/statements/const-statement.md)

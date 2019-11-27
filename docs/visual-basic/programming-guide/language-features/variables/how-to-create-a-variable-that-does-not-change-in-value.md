---
title: 'Comment : créer une variable qui ne change pas de valeur'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], read-only
- variables [Visual Basic], constant value
ms.assetid: 86b59266-25df-4635-ae15-9b59c411d036
ms.openlocfilehash: d5d8a6b066ae7e8795afd2f788b60823d8efdafa
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348642"
---
# <a name="how-to-create-a-variable-that-does-not-change-in-value-visual-basic"></a>Comment : créer une variable qui ne change pas de valeur (Visual Basic)

La notion d’une variable qui ne change pas sa valeur peut sembler contradictoire. Toutefois, il existe des situations où une constante n’est pas possible et il est utile d’avoir une variable avec une valeur fixe. Dans ce cas, vous pouvez définir une variable membre avec le mot clé [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md) .

Vous ne pouvez pas utiliser l' [instruction Const](../../../../visual-basic/language-reference/statements/const-statement.md) pour déclarer et assigner une valeur constante dans les circonstances suivantes :

- L’instruction `Const` n’accepte pas le type de données que vous souhaitez utiliser

- Vous ne connaissez pas la valeur au moment de la compilation

- Vous ne parvenez pas à calculer la valeur constante au moment de la compilation

### <a name="to-create-a-variable-that-does-not-change-in-value"></a>Pour créer une variable qui ne change pas de valeur

1. Au niveau du module, déclarez une variable membre avec l' [instruction Dim](../../../../visual-basic/language-reference/statements/dim-statement.md)et incluez le mot clé [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md) .

    ```vb
    Dim ReadOnly timeStarted
    ```

    Vous pouvez spécifier `ReadOnly` uniquement sur une variable membre. Cela signifie que vous devez définir la variable au niveau du module, en dehors de toute procédure.

2. Si vous pouvez calculer la valeur dans une seule instruction au moment de la compilation, utilisez une clause d’initialisation dans l’instruction `Dim`. Faites suivre la clause [As](../../../../visual-basic/language-reference/statements/as-clause.md) d’un signe égal (`=`), puis d’une expression. Assurez-vous que le compilateur peut évaluer cette expression sur une valeur constante.

    ```vb
    Dim ReadOnly timeStarted As Date = Now
    ```

    Vous ne pouvez affecter une valeur à une variable `ReadOnly` qu’une seule fois. Une fois cela fait, aucun code ne peut modifier sa valeur.

    Si vous ne connaissez pas la valeur au moment de la compilation ou si vous ne pouvez pas la calculer au moment de la compilation dans une instruction unique, vous pouvez toujours l’assigner au moment de l’exécution dans un constructeur. Pour ce faire, vous devez déclarer la variable `ReadOnly` au niveau de la classe ou de la structure. Dans le constructeur de cette classe ou de cette structure, calculez la valeur fixe de la variable et assignez-la à la variable avant de retourner le constructeur.

## <a name="see-also"></a>Voir aussi

- [WriteOnly](../../../../visual-basic/language-reference/modifiers/writeonly.md)
- [Const (instruction)](../../../../visual-basic/language-reference/statements/const-statement.md)

---
title: procédures Function
ms.date: 07/20/2015
helpviewer_keywords:
- Function procedures
- return values [Visual Basic], function procedures
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], Function procedures
- syntax [Visual Basic], function procedures
ms.assetid: 1b9f632c-553b-4cb6-920a-ded117ead8c0
ms.openlocfilehash: b0ba96a875fd8785e45eee565beefe4b961ffc9d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388749"
---
# <a name="function-procedures-visual-basic"></a>Function procedures (Visual Basic)

Une `Function` procédure est une série d’instructions Visual Basic délimitées par les `Function` `End Function` instructions et. La `Function` procédure effectue une tâche, puis retourne le contrôle au code appelant. Quand elle retourne le contrôle, elle retourne également une valeur au code appelant.

Chaque fois que la procédure est appelée, ses instructions sont exécutées, en commençant par la première instruction exécutable après l' `Function` instruction et en terminant par la première `End Function` `Exit Function` instruction, ou `Return` rencontrée.

Vous pouvez définir une `Function` procédure dans un module, une classe ou une structure. C’est `Public` par défaut le cas, ce qui signifie que vous pouvez l’appeler à partir de n’importe quel endroit de votre application ayant accès au module, à la classe ou à la structure dans laquelle vous l’avez défini.

Une `Function` procédure peut prendre des arguments, tels que des constantes, des variables ou des expressions, qui lui sont passés par le code appelant.

## <a name="declaration-syntax"></a>Syntaxe de déclaration

La syntaxe permettant de déclarer une `Function` procédure est la suivante :

```vb
[Modifiers] Function FunctionName [(ParameterList)] As ReturnType
    [Statements]
End Function
```

Les *modificateurs* peuvent spécifier le niveau d’accès et les informations relatives à la surcharge, au remplacement, au partage et à l’occultation. Pour plus d’informations, consultez [Function, instruction](../../../language-reference/statements/function-statement.md).

Vous déclarez chaque paramètre de la même façon que pour les [procédures Sub](./sub-procedures.md).

### <a name="data-type"></a>Type de données

Chaque `Function` procédure a un type de données, comme c’est le cas pour chaque variable. Ce type de données est spécifié par la `As` clause dans l' `Function` instruction et détermine le type de données de la valeur que la fonction retourne au code appelant. Les exemples de déclarations suivants illustrent cela.

```vb
Function Yesterday() As Date
End Function

Function FindSqrt(radicand As Single) As Single
End Function
```

Pour plus d’informations, consultez « parts » dans l' [instruction de fonction](../../../language-reference/statements/function-statement.md).

### <a name="returning-values"></a>Retour de valeurs

La valeur `Function` qu’une procédure renvoie au code appelant est appelée sa valeur de retour. La procédure retourne cette valeur de l’une des deux manières suivantes :

- Elle utilise l' `Return` instruction pour spécifier la valeur de retour et retourne immédiatement le contrôle au programme appelant. L'exemple suivant illustre ce comportement.

  ```vb
  Function FunctionName [(ParameterList)] As ReturnType
      ' The following statement immediately transfers control back
      ' to the calling code and returns the value of Expression.
      Return Expression
  End Function
  ```

- Elle assigne une valeur à son propre nom de fonction dans une ou plusieurs instructions de la procédure. Le contrôle ne retourne pas au programme appelant tant qu' `Exit Function` une `End Function` instruction ou n’est pas exécutée. L'exemple suivant illustre ce comportement.

  ```vb
  Function FunctionName [(ParameterList)] As ReturnType
      ' The following statement does not transfer control back to the calling code.
      FunctionName = Expression
      ' When control returns to the calling code, Expression is the return value.
  End Function
  ```

L’avantage de l’attribution de la valeur de retour au nom de la fonction est que le contrôle ne retourne pas de la procédure tant qu’il n’a pas rencontré une `Exit Function` `End Function` instruction ou. Cela vous permet d’attribuer une valeur préliminaire et de l’ajuster ultérieurement si nécessaire.

Pour plus d’informations sur le retour de valeurs, consultez [Function, instruction](../../../language-reference/statements/function-statement.md). Pour plus d’informations sur le retour de tableaux, consultez [tableaux](../arrays/index.md).

## <a name="calling-syntax"></a>Syntaxe d’appel

Pour appeler une procédure, vous devez `Function` inclure son nom et ses arguments sur le côté droit d’une instruction d’assignation ou dans une expression. Vous devez fournir des valeurs pour tous les arguments qui ne sont pas facultatifs, et vous devez placer la liste d’arguments entre parenthèses. Si aucun argument n’est fourni, vous pouvez éventuellement omettre les parenthèses.

La syntaxe d’un appel à une `Function` procédure est la suivante.

*lvalue* `=` *nomfonction* `[(` *argumentlist*    `)]`

`If ((`*nomfonction* `[(` *argumentlist* `)] / 3) <=` *expression*  `) Then`

Lorsque vous appelez une `Function` procédure, il n’est pas nécessaire d’utiliser sa valeur de retour. Si vous ne le faites pas, toutes les actions de la fonction sont exécutées, mais la valeur de retour est ignorée. <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>est souvent appelée de cette manière.

### <a name="illustration-of-declaration-and-call"></a>Illustration de la déclaration et de l’appel

La `Function` procédure suivante calcule le côté le plus long, ou hypoténuse, d’un triangle rectangle, en fonction des valeurs des deux autres côtés.

[!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]

L’exemple suivant montre un appel typique à `hypotenuse` .

[!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]

## <a name="see-also"></a>Voir aussi

- [Procédures](./index.md)
- [Sub, procédures](./sub-procedures.md)
- [Procédures Property](./property-procedures.md)
- [Procédures d'opérateur](./operator-procedures.md)
- [Paramètres et arguments d’une procédure](./procedure-parameters-and-arguments.md)
- [Function (instruction)](../../../language-reference/statements/function-statement.md)
- [Comment : créer une procédure qui retourne une valeur](./how-to-create-a-procedure-that-returns-a-value.md)
- [Comment : retourner une valeur d'une procédure](./how-to-return-a-value-from-a-procedure.md)
- [Comment : appeler une procédure qui retourne une valeur](./how-to-call-a-procedure-that-returns-a-value.md)

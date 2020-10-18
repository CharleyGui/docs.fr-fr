---
title: Le premier opérande d'une expression binaire 'If' doit être de type nullable ou référence
ms.date: 07/20/2015
f1_keywords:
- bc33107
- vbc33107
helpviewer_keywords:
- BC33107
ms.assetid: 493c8899-3f6b-4471-8eb6-9284e8492768
ms.openlocfilehash: bca9b74a68815b4e5a3bb2dc114b9031cdf24099
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162737"
---
# <a name="bc33107-first-operand-in-a-binary-if-expression-must-be-nullable-or-a-reference-type"></a>BC33107 : le premier opérande d’une expression binaire’If’doit être Nullable ou un type référence

Une `If` expression peut accepter deux ou trois arguments. Lorsque vous envoyez uniquement deux arguments, le premier argument doit être un type référence ou un type valeur Nullable. Si le premier argument est évalué à une valeur autre que `Nothing` , sa valeur est retournée. Si le premier argument a la valeur `Nothing` , le deuxième argument est évalué et retourné.

 Par exemple, le code suivant contient deux `If` expressions, une avec trois arguments et une avec deux arguments. Les expressions calculent et retournent la même valeur.

```vb
' firstChoice is a nullable value type.
Dim firstChoice? As Integer = Nothing
Dim secondChoice As Integer = 1128
' If expression with three arguments.
Console.WriteLine(If(firstChoice IsNot Nothing, firstChoice, secondChoice))
' If expression with two arguments.
Console.WriteLine(If(firstChoice, secondChoice))
```

 Les expressions suivantes provoquent cette erreur :

```vb
Dim choice1 = 4
Dim choice2 = 5
Dim booleanVar = True

' Not valid.
'Console.WriteLine(If(choice1 < choice2, 1))
' Not valid.
'Console.WriteLine(If(booleanVar, "Test returns True."))
```

 **ID d’erreur :** BC33107

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Si vous ne pouvez pas modifier le code afin que le premier argument soit un type valeur Nullable ou un type référence, envisagez d’effectuer la conversion en une expression à trois arguments `If` ou en une `If...Then...Else` instruction.

```vb
Console.WriteLine(If(choice1 < choice2, 1, 2))
Console.WriteLine(If(booleanVar, "Test returns True.", "Test returns False."))
```

## <a name="see-also"></a>Voir aussi

- [If, opérateur](../operators/if-operator.md)
- [If...Then...Else (instruction)](../statements/if-then-else-statement.md)
- [Types valeur Nullable](../../programming-guide/language-features/data-types/nullable-value-types.md)

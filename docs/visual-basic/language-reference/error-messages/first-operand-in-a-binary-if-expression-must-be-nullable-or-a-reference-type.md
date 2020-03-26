---
title: Le premier opérande d'une expression binaire 'If' doit être de type nullable ou référence
ms.date: 07/20/2015
f1_keywords:
- bc33107
- vbc33107
helpviewer_keywords:
- BC33107
ms.assetid: 493c8899-3f6b-4471-8eb6-9284e8492768
ms.openlocfilehash: 4b520949cb59b63ea39441632dc5e2c6d000d711
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249524"
---
# <a name="first-operand-in-a-binary-if-expression-must-be-nullable-or-a-reference-type"></a>Le premier opérande d'une expression binaire 'If' doit être de type nullable ou référence
Une `If` expression peut prendre deux ou trois arguments. Lorsque vous n’envoyez que deux arguments, le premier argument doit être un type de référence ou un type de valeur nul. Si le premier argument évalue `Nothing`autre chose que , sa valeur est retournée. Si le premier argument `Nothing`s’évalue à , le deuxième argument est évalué et retourné.  
  
 Par exemple, le code `If` suivant contient deux expressions, l’une avec trois arguments et l’autre avec deux arguments. Les expressions calculent et retournent la même valeur.  
  
```vb  
' firstChoice is a nullable value type.  
Dim firstChoice? As Integer = Nothing  
Dim secondChoice As Integer = 1128  
' If expression with three arguments.  
Console.WriteLine(If(firstChoice IsNot Nothing, firstChoice, secondChoice))  
' If expression with two arguments.  
Console.WriteLine(If(firstChoice, secondChoice))  
```  
  
 Les expressions suivantes causent cette erreur :  
  
```vb  
Dim choice1 = 4  
Dim choice2 = 5  
Dim booleanVar = True  
  
' Not valid.  
'Console.WriteLine(If(choice1 < choice2, 1))  
' Not valid.  
'Console.WriteLine(If(booleanVar, "Test returns True."))  
```  
  
 **ID erreur:** BC33107 (en)  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Si vous ne pouvez pas modifier le code de sorte que le premier argument est `If` un type `If...Then...Else` de valeur ou un type de référence annulable, envisagez de vous convertir à une expression à trois arguments ou à une déclaration.  
  
```vb  
Console.WriteLine(If(choice1 < choice2, 1, 2))  
Console.WriteLine(If(booleanVar, "Test returns True.", "Test returns False."))  
```  
  
## <a name="see-also"></a>Voir aussi

- [If (opérateur)](../../../visual-basic/language-reference/operators/if-operator.md)
- [If...Then...Else (instruction)](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [Types de valeur nuls](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)

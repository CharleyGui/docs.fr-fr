---
title: Do...Loop, instruction
ms.date: 07/20/2015
f1_keywords:
- vb.Do
- vb.Loop
- vb.Until
helpviewer_keywords:
- conditional statements [Visual Basic], Do�Loop
- while statement [Visual Basic], Do...Loop
- execution [Visual Basic], conditional
- Do loops
- Until keyword [Visual Basic], Do...Loop statement
- Do...Loop statement
- instructions, repeating
- Do statement [Visual Basic]
- Exit statement [Visual Basic], in Do...Loop statements
- loop structures [Visual Basic], Do�Loop statements
- do-while statements [Visual Basic]
- loops, exiting
- Loop keyword [Visual Basic], Do...Loop statement
ms.assetid: 892f9096-b3e2-4aee-834d-83bc4e2c379d
ms.openlocfilehash: 9384cbb355189be448fa4b8d274721b4a7ca6a20
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351252"
---
# <a name="doloop-statement-visual-basic"></a>Do...Loop, instruction (Visual Basic)
Repeats a block of statements while a `Boolean` condition is `True` or until the condition becomes `True`.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Do { While | Until } condition  
    [ statements ]  
    [ Continue Do ]  
    [ statements ]  
    [ Exit Do ]  
    [ statements ]  
Loop  
' -or-  
Do  
    [ statements ]  
    [ Continue Do ]  
    [ statements ]  
    [ Exit Do ]  
    [ statements ]  
Loop { While | Until } condition  
```  
  
## <a name="parts"></a>Composants  
  
|Terme|Définition|  
|---|---|  
|`Do`|Requis. Starts the definition of the `Do` loop.|  
|`While`|Requis, sauf si l'option `Until` est utilisée. Repeat the loop until `condition` is `False`.|  
|`Until`|Requis, sauf si l'option `While` est utilisée. Repeat the loop until `condition` is `True`.|  
|`condition`|Optionnel. `Boolean` expression. If `condition` is `Nothing`, Visual Basic treats it as `False`.|  
|`statements`|Optionnel. One or more statements that are repeated while, or until, `condition` is `True`.|  
|`Continue Do`|Optionnel. Transfers control to the next iteration of the `Do` loop.|  
|`Exit Do`|Optionnel. Transfers control out of the `Do` loop.|  
|`Loop`|Requis. Terminates the definition of the `Do` loop.|  
  
## <a name="remarks"></a>Notes  
 Use a `Do...Loop` structure when you want to repeat a set of statements an indefinite number of times, until a condition is satisfied. If you want to repeat the statements a set number of times, the [For...Next Statement](../../../visual-basic/language-reference/statements/for-next-statement.md) is usually a better choice.  
  
 You can use either `While` or `Until` to specify `condition`, but not both.  
  
 You can test `condition` only one time, at either the start or the end of the loop. If you test `condition` at the start of the loop (in the `Do` statement), the loop might not run even one time. If you test at the end of the loop (in the `Loop` statement), the loop always runs at least one time.  
  
 The condition usually results from a comparison of two values, but it can be any expression that evaluates to a [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md) value (`True` or `False`). This includes values of other data types, such as numeric types, that have been converted to `Boolean`.  
  
 You can nest `Do` loops by putting one loop within another. You can also nest different kinds of control structures within each other. For more information, see [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).  
  
> [!NOTE]
> The `Do...Loop` structure gives you more flexibility than the [While...End While Statement](../../../visual-basic/language-reference/statements/while-end-while-statement.md) because it enables you to decide whether to end the loop when `condition` stops being `True` or when it first becomes `True`. It also enables you to test `condition` at either the start or the end of the loop.  
  
## <a name="exit-do"></a>Exit Do  
 The [Exit Do](../../../visual-basic/language-reference/statements/exit-statement.md) statement can provide an alternative way to exit a `Do…Loop`. `Exit Do` transfers control immediately to the statement that follows the `Loop` statement.  
  
 `Exit Do` is often used after some condition is evaluated, for example in an `If...Then...Else` structure. You might want to exit a loop if you detect a condition that makes it unnecessary or impossible to continue iterating, such as an erroneous value or a termination request. One use of `Exit Do` is to test for a condition that could cause an *endless loop*, which is a loop that could run a large or even infinite number of times. You can use `Exit Do` to escape the loop.  
  
 You can include any number of `Exit Do` statements anywhere in a `Do…Loop`.  
  
 When used within nested `Do` loops, `Exit Do` transfers control out of the innermost loop and into the next higher level of nesting.  
  
## <a name="example"></a>Exemple  
 In the following example, the statements in the loop continue to run until the `index` variable is greater than 10. The `Until` clause is at the end of the loop.  
  
 [!code-vb[VbVbalrStatements#131](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#131)]  
  
## <a name="example"></a>Exemple  
 The following example uses a `While` clause instead of an `Until` clause, and `condition` is tested at the start of the loop instead of at the end.  
  
 [!code-vb[VbVbalrStatements#132](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#132)]  
  
## <a name="example"></a>Exemple  
 In the following example, `condition` stops the loop when the `index` variable is greater than 100. The `If` statement in the loop, however, causes the `Exit Do` statement to stop the loop when the index variable is greater than 10.  
  
 [!code-vb[VbVbalrStatements#133](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#133)]  
  
## <a name="example"></a>Exemple  
 The following example reads all lines in a text file. The <xref:System.IO.File.OpenText%2A> method opens the file and returns a <xref:System.IO.StreamReader> that reads the characters. In the `Do...Loop` condition, the <xref:System.IO.StreamReader.Peek%2A> method of the `StreamReader` determines whether there are any additional characters.  
  
 [!code-vb[VbVbalrStatements#134](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#134)]  
  
## <a name="see-also"></a>Voir aussi

- [Structures de boucle](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [For...Next (instruction)](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Booléen (type de données)](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [Structures de contrôle imbriquées](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Exit (instruction)](../../../visual-basic/language-reference/statements/exit-statement.md)
- [While...End While (instruction)](../../../visual-basic/language-reference/statements/while-end-while-statement.md)

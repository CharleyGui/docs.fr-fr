---
title: If...Then...Else, instruction
ms.date: 04/16/2018
f1_keywords:
- vb.ElseIf
- vb.Then
- vb.If
- vb.EndIf
helpviewer_keywords:
- ElseIf statement [Visual Basic], If...Then...Else
- Then statement [Visual Basic], If...Then...Else
- control flow [Visual Basic], branching
- execution [Visual Basic], conditional
- TypeOf...Is expression, and If...Then...Else statements
- If...Then...Else statements
- If statement [Visual Basic], If...Then...Else
- If statement [Visual Basic]
- Is operator [Visual Basic], in If...Then...Else statements
- If Operator [Visual Basic]
- branching [Visual Basic], conditional
- If function [Visual Basic], and If...Then...Else statements
- Else statement [Visual Basic]
ms.assetid: 790068a2-1307-4e28-8a72-be5ebda099e9
ms.openlocfilehash: f505755caeb9cc3cfeeb1ba83b6de15f48314103
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351161"
---
# <a name="ifthenelse-statement-visual-basic"></a>If...Then...Else, instruction (Visual Basic)

Exécute un groupe d'instructions soumises à une condition, en fonction de la valeur d'une expression.

## <a name="syntax"></a>Syntaxe

```vb
' Multiline syntax:
If condition [ Then ]
    [ statements ]
[ ElseIf elseifcondition [ Then ]
    [ elseifstatements ] ]
[ Else
    [ elsestatements ] ]
End If

' Single-line syntax:
If condition Then [ statements ] [ Else [ elsestatements ] ]
```

## <a name="quick-links-to-example-code"></a>Liens rapides vers l’exemple de code

Cet article contient plusieurs exemples qui illustrent l’utilisation de l’instruction `If`...`Then`...`Else` :

- [Exemple de syntaxe multiligne](#multi-line)
- [Exemple de syntaxe imbriquée](#nested)
- [Exemple de syntaxe sur une seule ligne](#single-line)

## <a name="parts"></a>Composants

`condition` \
Requis. Formule. Doit correspondre à `True` ou `False`, ou à un type de données implicitement convertible en `Boolean`.

Si l’expression est une variable `Boolean` [Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) qui prend la valeur [Nothing](../../../visual-basic/language-reference/nothing.md), la condition est traitée comme si l’expression était `False`, et les blocs `ElseIf` sont évalués s’ils existent, ou le bloc `Else` est exécuté s’il existe.

`Then` \
Obligatoire dans la syntaxe sur une seule ligne ; facultatif dans la syntaxe multiligne.

`statements` \
Ce paramètre est facultatif. Une ou plusieurs instructions qui suivent `If`...`Then` qui sont exécutées si `condition` prend la valeur `True`.

`elseifcondition` \
Obligatoire si `ElseIf` est présent. Formule. Doit correspondre à `True` ou `False`, ou à un type de données implicitement convertible en `Boolean`.

`elseifstatements` \
Ce paramètre est facultatif. Une ou plusieurs instructions qui suivent `ElseIf`...`Then` qui sont exécutées si `elseifcondition` prend la valeur `True`.

`elsestatements` \
Ce paramètre est facultatif. Une ou plusieurs instructions qui sont exécutées si aucune expression `condition` ou `elseifcondition` précédente ne prend la valeur `True`.

`End If` \
Met fin à la version multiligne du bloc `If`...`Then`...`Else`.

## <a name="remarks"></a>Notes

### <a name="multiline-syntax"></a>Syntaxe multiligne

Lorsqu’une `If`...`Then`instruction`Else` est rencontrée, `condition` est testé. Si `condition` est `True`, les instructions qui suivent `Then` sont exécutées. Si `condition` est `False`, chaque instruction `ElseIf` (le cas échéant) est évaluée dans l’ordre. Lorsqu’un `True` `elseifcondition` est trouvé, les instructions qui suivent immédiatement les `ElseIf` associées sont exécutées. Si aucun `elseifcondition` n’a la valeur `True`, ou s’il n’existe aucune instruction `ElseIf`, les instructions qui suivent `Else` sont exécutées. Après l’exécution des instructions qui suivent `Then`, `ElseIf`ou `Else`, l’exécution se poursuit avec l’instruction qui suit `End If`.

Les clauses `ElseIf` et `Else` sont toutes deux facultatives. Vous pouvez avoir autant de clauses de `ElseIf` que vous le souhaitez dans une instruction `If`...`Then`...`Else`, mais aucune clause `ElseIf` ne peut apparaître après une clause `Else`. les instructions `If`...`Then`...`Else` peuvent être imbriquées les unes dans les autres.

Dans la syntaxe multiligne, l’instruction `If` doit être la seule instruction sur la première ligne. Les instructions `ElseIf`, `Else`et `End If` peuvent être précédées uniquement d’une étiquette de ligne. Le bloc `If`...`Then`...`Else` doit se terminer par une instruction `End If`.

> [!TIP]
> L' [option Select... L’instruction case](../../../visual-basic/language-reference/statements/select-case-statement.md) peut être plus utile lorsque vous évaluez une expression unique qui a plusieurs valeurs possibles.

### <a name="single-line-syntax"></a>Syntaxe sur une seule ligne

Vous pouvez utiliser la syntaxe sur une seule ligne pour une seule condition avec le code à exécuter si elle est vraie. Toutefois, la syntaxe sur plusieurs lignes offre davantage de structure et de flexibilité, et est plus facile à lire, à gérer et à déboguer.

Ce qui suit le mot clé `Then` est examiné pour déterminer si une instruction est un `If`à une seule ligne. Si tout autre chose qu’un commentaire apparaît après `Then` sur la même ligne, l’instruction est traitée comme une instruction de `If` à une seule ligne. Si `Then` est absent, il doit s’agir du début d’un `If`à plusieurs lignes...`Then`...`Else`.

Dans la syntaxe d’une seule ligne, vous pouvez exécuter plusieurs instructions à la suite d’une `If`...`Then` décision. Toutes les instructions doivent se trouver sur la même ligne et être séparées par deux-points.

## <a name="multiline-syntax-example"></a>Exemple de syntaxe multiligne

<a name="multi-line"></a>

L’exemple suivant illustre l’utilisation de la syntaxe multiligne de l’instruction `If`...`Then`...`Else`.

[!code-vb[VbVbalrStatements#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#101)]

## <a name="nested-syntax-example"></a>Exemple de syntaxe imbriquée

<a name="nested"></a>

L’exemple suivant contient des instructions `If`...`Then`...`Else` imbriquées.

[!code-vb[VbVbalrStatements#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#102)]

## <a name="single-line-syntax-example"></a>Exemple de syntaxe sur une seule ligne

<a name="single-line"></a>L’exemple suivant illustre l’utilisation de la syntaxe sur une seule ligne.

[!code-vb[VbVbalrStatements#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#103)]

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.Interaction.Choose%2A>
- <xref:Microsoft.VisualBasic.Interaction.Switch%2A>
- [#If...Then...#Else, directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [Select...Case (instruction)](../../../visual-basic/language-reference/statements/select-case-statement.md)
- [Structures de contrôle imbriquées](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Structures de décision](../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [Opérateurs logiques et au niveau du bit dans Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
- [If (opérateur)](../../../visual-basic/language-reference/operators/if-operator.md)

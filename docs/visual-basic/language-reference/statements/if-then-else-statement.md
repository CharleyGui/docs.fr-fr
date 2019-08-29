---
title: If...Then...Else, instruction (Visual Basic)
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
ms.openlocfilehash: e0b365afaa8cf7dff130cf01d2937be629e5f7a8
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106516"
---
# <a name="ifthenelse-statement-visual-basic"></a>If...Then...Else, instruction (Visual Basic)

Exécute un groupe d'instructions soumises à une condition, en fonction de la valeur d'une expression.

## <a name="syntax"></a>Syntaxe

```
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

Cet article contient plusieurs exemples qui illustrent les `If`utilisations de... `Then`... `Else` instruction:

- [Exemple de syntaxe multiligne](#multi-line)
- [Exemple de syntaxe imbriquée](#nested)
- [Exemple de syntaxe sur une seule ligne](#single-line)

## <a name="parts"></a>Composants

`condition` \
Requis. Formule. Doit correspondre à `True` ou `False`à, ou à un type de données qui est implicitement `Boolean`convertible en.

Si l’expression est une variable [Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) `Boolean` qui prend la valeur [Nothing](../../../visual-basic/language-reference/nothing.md), la condition est traitée comme si l’expression était `False` et le `Else` bloc est exécuté.

`Then` \
Obligatoire dans la syntaxe sur une seule ligne; facultatif dans la syntaxe multiligne.

`statements` \
facultatif. Une ou plusieurs instructions qui `If`suivent... qui sont exécutés `condition` si prend la `True`valeur. `Then`

`elseifcondition` \
Obligatoire si `ElseIf` est présent. Formule. Doit correspondre à `True` ou `False`à, ou à un type de données qui est implicitement `Boolean`convertible en.

`elseifstatements` \
facultatif. Une ou plusieurs instructions qui `ElseIf`suivent... qui sont exécutés `elseifcondition` si prend la `True`valeur. `Then`

`elsestatements` \
facultatif. Une ou plusieurs instructions qui sont exécutées si aucune `condition` expression `elseifcondition` ou précédente n’a `True`la valeur.

`End If` \
Met fin à la version multiligne `If`de... `Then`... `Else` bloquer.

## <a name="remarks"></a>Notes

### <a name="multiline-syntax"></a>Syntaxe multiligne

Quand un `If`... `Then`... `Else` l'`condition` instruction est testée. Si `condition` `Then` est `True`, les instructions suivantes sont exécutées. Si `condition` est `False`, chaque`ElseIf` instruction (le cas échéant) est évaluée dans l’ordre. Lorsqu’un `True` `elseifcondition` est trouvé, les instructions qui suivent immédiatement le `ElseIf` associé sont exécutées. Si la `elseifcondition` valeur de `True`n’est pas, ou s’il `ElseIf` n’y a aucune instruction `Else` , les instructions suivantes sont exécutées. Après l’exécution des instructions qui `Then`suivent `ElseIf`, ou `Else`, l’exécution se poursuit avec l' `End If`instruction qui suit.

Les `ElseIf` clauses et `Else` sont toutes deux facultatives. Vous pouvez avoir `ElseIf` autant de clauses que vous le souhaitez dans `If`une... `Then`... , mais aucune clause `ElseIf` ne peut apparaître après une `Else` clause. `Else` `If`... `Then`... `Else` les instructions peuvent être imbriquées les unes dans les autres.

Dans la syntaxe multiligne, l' `If` instruction doit être la seule instruction sur la première ligne. Les `ElseIf`instructions `Else`, et`End If` ne peuvent être précédées que d’une étiquette de ligne. `If`... `Then`... le bloc doit se terminer `End If` par une instruction. `Else`

> [!TIP]
> L' [option Select... L’instruction case](../../../visual-basic/language-reference/statements/select-case-statement.md) peut être plus utile lorsque vous évaluez une expression unique qui a plusieurs valeurs possibles.

### <a name="single-line-syntax"></a>Syntaxe sur une seule ligne

Vous pouvez utiliser la syntaxe sur une seule ligne pour une seule condition avec le code à exécuter si elle est vraie. Toutefois, la syntaxe sur plusieurs lignes offre davantage de structure et de flexibilité, et est plus facile à lire, à gérer et à déboguer.

Ce qui suit `Then` le mot clé est examiné pour déterminer si une instruction est une seule `If`ligne. Si tout autre chose qu’un commentaire apparaît `Then` après sur la même ligne, l’instruction est traitée comme une instruction sur `If` une seule ligne. Si `Then` est absent, il doit s’agir du début d’une ligne `If`multiple... `Then`... `Else`.

Dans la syntaxe d’une seule ligne, vous pouvez avoir plusieurs instructions exécutées en tant que `If`résultat d’un... `Then` décision. Toutes les instructions doivent se trouver sur la même ligne et être séparées par deux-points.

## <a name="multiline-syntax-example"></a>Exemple de syntaxe multiligne

<a name="multi-line"></a>

L’exemple suivant illustre l’utilisation de la syntaxe multiligne de `If`... `Then`... `Else` instruction.

[!code-vb[VbVbalrStatements#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#101)]

## <a name="nested-syntax-example"></a>Exemple de syntaxe imbriquée

<a name="nested"></a>

L’exemple suivant contient `If`des... `Then`... `Else` instructions.

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

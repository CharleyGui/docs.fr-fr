---
title: If...Then...Else (instruction)
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
ms.openlocfilehash: 0884b71c24742286e695e720add9d00dd4bfe52b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404587"
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

Cet article contient plusieurs exemples qui illustrent les utilisations de `If` ... `Then` ...`Else` gestion

- [Exemple de syntaxe multiligne](#multi-line)
- [Exemple de syntaxe imbriquée](#nested)
- [Exemple de syntaxe sur une seule ligne](#single-line)

## <a name="parts"></a>Éléments

`condition` \
Obligatoire. Expression. Doit correspondre à `True` ou `False` à, ou à un type de données qui est implicitement convertible en `Boolean` .

Si l’expression est une [Nullable](../../programming-guide/language-features/data-types/nullable-value-types.md) `Boolean` variable Nullable qui prend la valeur [Nothing](../nothing.md), la condition est traitée comme si l’expression était `False` , et les `ElseIf` blocs sont évalués s’ils existent, ou le `Else` bloc est exécuté s’il existe.

`Then` \
Obligatoire dans la syntaxe sur une seule ligne ; facultatif dans la syntaxe multiligne.

`statements` \
Facultatif. Une ou plusieurs instructions `If` qui suivent... `Then` qui sont exécutées si `condition` prend la valeur `True` .

`elseifcondition` \
Obligatoire si `ElseIf` est présent. Expression. Doit correspondre à `True` ou `False` à, ou à un type de données qui est implicitement convertible en `Boolean` .

`elseifstatements` \
Facultatif. Une ou plusieurs instructions `ElseIf` qui suivent... `Then` qui sont exécutées si `elseifcondition` prend la valeur `True` .

`elsestatements` \
Facultatif. Une ou plusieurs instructions qui sont exécutées si aucune expression ou précédente n’a la `condition` `elseifcondition` valeur `True` .

`End If` \
Met fin à la version multiligne de `If` ... `Then` ...`Else` plage.

## <a name="remarks"></a>Notes

### <a name="multiline-syntax"></a>Syntaxe multiligne

Quand un `If` ... `Then` ...`Else` l’instruction est `condition` testée. Si `condition` est `True` , les instructions suivantes `Then` sont exécutées. Si `condition` est `False` , chaque `ElseIf` instruction (le cas échéant) est évaluée dans l’ordre. Lorsqu’un `True` `elseifcondition` est trouvé, les instructions qui suivent immédiatement le associé `ElseIf` sont exécutées. Si `elseifcondition` la valeur de n' `True` est pas, ou s’il n’y a aucune `ElseIf` instruction, les instructions suivantes `Else` sont exécutées. Après l’exécution des instructions qui suivent `Then` , `ElseIf` ou `Else` , l’exécution se poursuit avec l’instruction qui suit `End If` .

Les `ElseIf` `Else` clauses et sont toutes deux facultatives. Vous pouvez avoir autant `ElseIf` de clauses que vous le souhaitez dans une `If` ... `Then` ...`Else` , mais aucune `ElseIf` clause ne peut apparaître après une `Else` clause. `If`...`Then` ...`Else` les instructions peuvent être imbriquées les unes dans les autres.

Dans la syntaxe multiligne, l' `If` instruction doit être la seule instruction sur la première ligne. Les `ElseIf` `Else` instructions, et `End If` ne peuvent être précédées que d’une étiquette de ligne. `If`... `Then` ...`Else` le bloc doit se terminer par une `End If` instruction.

> [!TIP]
> L' [option Select... L’instruction case](select-case-statement.md) peut être plus utile lorsque vous évaluez une expression unique qui a plusieurs valeurs possibles.

### <a name="single-line-syntax"></a>Syntaxe sur une seule ligne

Vous pouvez utiliser la syntaxe sur une seule ligne pour une seule condition avec le code à exécuter si elle est vraie. Toutefois, la syntaxe sur plusieurs lignes offre davantage de structure et de flexibilité, et est plus facile à lire, à gérer et à déboguer.

Ce qui suit le `Then` mot clé est examiné pour déterminer si une instruction est une seule ligne `If` . Si tout autre chose qu’un commentaire apparaît après `Then` sur la même ligne, l’instruction est traitée comme une instruction sur une seule ligne `If` . Si `Then` est absent, il doit s’agir du début d’une ligne multiple `If` ... `Then` ...`Else`.

Dans la syntaxe d’une seule ligne, vous pouvez avoir plusieurs instructions exécutées en tant que résultat d’une `If` décision... `Then` . Toutes les instructions doivent se trouver sur la même ligne et être séparées par deux-points.

## <a name="multiline-syntax-example"></a>Exemple de syntaxe multiligne

<a name="multi-line"></a>

L’exemple suivant illustre l’utilisation de la syntaxe multiligne de `If` ... `Then` ...`Else` gestion.

[!code-vb[VbVbalrStatements#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#101)]

## <a name="nested-syntax-example"></a>Exemple de syntaxe imbriquée

<a name="nested"></a>

L’exemple suivant contient des `If` ... `Then` ...`Else` publication.

[!code-vb[VbVbalrStatements#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#102)]

## <a name="single-line-syntax-example"></a>Exemple de syntaxe sur une seule ligne

<a name="single-line"></a>L’exemple suivant illustre l’utilisation de la syntaxe sur une seule ligne.

[!code-vb[VbVbalrStatements#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#103)]

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.Interaction.Choose%2A>
- <xref:Microsoft.VisualBasic.Interaction.Switch%2A>
- [#If... Then... #Else directives](../directives/if-then-else-directives.md)
- [Select...Case (instruction)](select-case-statement.md)
- [Structures de contrôle imbriquées](../../programming-guide/language-features/control-flow/nested-control-structures.md)
- [Structures de décision](../../programming-guide/language-features/control-flow/decision-structures.md)
- [Opérateurs de bits et opérateurs logiques en Visual Basic](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
- [If, opérateur](../operators/if-operator.md)

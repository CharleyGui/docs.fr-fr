---
title: If, opérateur
ms.date: 07/20/2015
f1_keywords:
- vb.IfOperator
- IfOperator
helpviewer_keywords:
- ternary operators [Visual Basic]
- conditional execution
- If expressions [Visual Basic]
- conditional operator [Visual Basic]
- If Operator [Visual Basic]
ms.assetid: dd56c9df-7cd4-442c-9ba6-20c70ee44c8f
ms.openlocfilehash: 3b45a5afe331bd00c2b92f8c305351b77bc319cf
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249485"
---
# <a name="if-operator-visual-basic"></a>If, opérateur (Visual Basic)

Utilise l’évaluation des courts-circuits pour retourner conditionnellement l’une des deux valeurs. L’opérateur `If` peut être appelé avec trois arguments ou avec deux arguments.

## <a name="syntax"></a>Syntaxe

```vb
If( [argument1,] argument2, argument3 )
```

## <a name="if-operator-called-with-three-arguments"></a>Si l’opérateur a appelé avec trois arguments

Lorsqu’il `If` est appelé en utilisant trois arguments, le premier argument `Boolean`doit évaluer à une valeur qui peut être exprimée comme un . Cette `Boolean` valeur déterminera lequel des deux autres arguments est évalué et retourné. La liste suivante ne `If` s’applique que lorsque l’opérateur est appelé en utilisant trois arguments.

### <a name="parts"></a>Éléments

|Terme|Définition|
|---|---|
|`argument1`|Obligatoire. `Boolean`. Détermine lequel des autres arguments à évaluer et à retourner.|
|`argument2`|Obligatoire. `Object`. Évalué et retourné `argument1` si `True`l’évaluation à .|
|`argument3`|Obligatoire. `Object`. Évalué et retourné `argument1` si `False` évalue `argument1` ou s’il s’agit [d’une](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) `Boolean` variable Nullable qui n’évalue à [rien](../../../visual-basic/language-reference/nothing.md).|

Un `If` opérateur qui est appelé avec `IIf` trois arguments fonctionne comme une fonction, sauf qu’il utilise l’évaluation court-circuit. Une `IIf` fonction évalue toujours ses trois arguments, alors qu’un `If` opérateur qui a trois arguments n’en évalue que deux. Le `If` premier argument est évalué et le `Boolean` résultat `True` `False`est présenté comme une valeur, ou . Si la `True`valeur `argument2` est, est évaluée et `argument3` sa valeur est retournée, mais n’est pas évaluée. Si la valeur `Boolean` de `False` `argument3` l’expression est, est évalué `argument2` et sa valeur est retournée, mais n’est pas évaluée. Les exemples suivants `If` illustrent l’utilisation de trois arguments :

[!code-vb[VbVbalrOperators#100](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#100)]

L’exemple suivant illustre la valeur de l’évaluation en circuit court. L’exemple montre deux `number` tentatives `divisor` de `divisor` diviser variable par variable, sauf quand est nulle. Dans ce cas, un 0 devrait être retourné, et aucune tentative ne devrait être faite pour effectuer la division parce qu’une erreur de temps d’exécution en résulterait. Étant `If` donné que l’expression utilise l’évaluation en court-circuit, elle évalue soit le deuxième ou le troisième argument, selon la valeur du premier argument. Si le premier argument est vrai, le diviseur n’est pas nul et il est sécuritaire d’évaluer le deuxième argument et d’exécuter la division. Si le premier argument est faux, seul le troisième argument est évalué et un 0 est retourné. Par conséquent, lorsque le diviseur est 0, aucune tentative n’est faite pour effectuer la division et aucun résultat d’erreur. Toutefois, `IIf` parce qu’il n’utilise pas l’évaluation en court-circuit, le deuxième argument est évalué même lorsque le premier argument est faux. Cela provoque une erreur de division par zéro.

[!code-vb[VbVbalrOperators#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#101)]

## <a name="if-operator-called-with-two-arguments"></a>Si l’opérateur a appelé avec deux arguments

Le premier `If` argument à omettre. Cela permet à l’opérateur d’être appelé en utilisant seulement deux arguments. La liste suivante ne `If` s’applique que lorsque l’opérateur est appelé avec deux arguments.

### <a name="parts"></a>Éléments

|Terme|Définition|
|---|---|
|`argument2`|Obligatoire. `Object`. Doit être un type de référence ou de valeur nulle. Évalué et retourné quand il évalue `Nothing`à autre chose que .|
|`argument3`|Obligatoire. `Object`. Évalué et retourné `argument2` si `Nothing`l’évaluation à .|

Lorsque `Boolean` l’argument est omis, le premier argument doit être un type de référence ou de valeur nulle. Si le premier argument `Nothing`évalue à , la valeur du deuxième argument est retourné. Dans tous les autres cas, la valeur du premier argument est retournée. L’exemple suivant illustre le fonctionnement de cette évaluation :

[!code-vb[VbVbalrOperators#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#102)]

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.Interaction.IIf%2A>
- [Types de valeur nuls](../../programming-guide/language-features/data-types/nullable-value-types.md)
- [Rien](../nothing.md)

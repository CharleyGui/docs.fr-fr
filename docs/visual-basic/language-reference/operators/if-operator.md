---
title: If, opérateur (Visual Basic)
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
ms.openlocfilehash: 244c0598c65ba691decc09c36293799571211a40
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701154"
---
# <a name="if-operator-visual-basic"></a>If, opérateur (Visual Basic)
Utilise l’évaluation de court-circuit pour retourner de manière conditionnelle l’une des deux valeurs. L’opérateur `If` peut être appelé avec trois arguments ou avec deux arguments.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
If( [argument1,] argument2, argument3 )  
```  
  
## <a name="if-operator-called-with-three-arguments"></a>Opérateur If appelé avec trois arguments  
 Lorsque `If` est appelé à l’aide de trois arguments, le premier argument doit correspondre à une valeur qui peut être convertie en `Boolean`. Cette valeur `Boolean` déterminera les deux autres arguments qui seront évalués et retournés. La liste suivante s’applique uniquement lorsque l’opérateur `If` est appelé à l’aide de trois arguments.  
  
## <a name="parts"></a>Composants  
  
|Terme|Définition|  
|---|---|  
|`argument1`|Obligatoire. `Boolean` . Détermine les arguments à évaluer et à retourner.|  
|`argument2`|Obligatoire. `Object` . Évaluée et retournée si `argument1` a pour valeur `True`.|  
|`argument3`|Obligatoire. `Object` . Évaluée et retournée si `argument1` a la valeur `False` ou si `argument1` est une variable `Boolean` [Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)qui prend la valeur [Nothing](../../../visual-basic/language-reference/nothing.md).|  
  
 Un opérateur `If` qui est appelé avec trois arguments fonctionne comme une fonction `IIf`, sauf qu’il utilise l’évaluation de court-circuit. Une fonction `IIf` évalue toujours les trois arguments, tandis qu’un opérateur `If` ayant trois arguments évalue uniquement deux d’entre eux. Le premier argument `If` est évalué et le résultat est casté en une valeur `Boolean`, `True` ou `False`. Si la valeur est `True`, `argument2` est évaluée et sa valeur est retournée, mais `argument3` n’est pas évaluée. Si la valeur de l’expression `Boolean` est `False`, `argument3` est évaluée et sa valeur est retournée, mais `argument2` n’est pas évaluée. Les exemples suivants illustrent l’utilisation de `If` lorsque trois arguments sont utilisés :  
  
 [!code-vb[VbVbalrOperators#100](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#100)]  
  
 L’exemple suivant illustre la valeur de l’évaluation de court-circuit. L’exemple montre deux tentatives de division de la variable `number` par la variable `divisor`, sauf si `divisor` est égal à zéro. Dans ce cas, un 0 doit être retourné et aucune tentative n’est nécessaire pour exécuter la Division, car une erreur d’exécution se produit. Étant donné que l’expression `If` utilise une évaluation de court-circuit, elle évalue le deuxième ou le troisième argument, en fonction de la valeur du premier argument. Si le premier argument est true, le diviseur n’est pas égal à zéro et il est possible d’évaluer en toute sécurité le deuxième argument et d’exécuter la Division. Si le premier argument a la valeur false, seul le troisième argument est évalué et une valeur 0 est retournée. Par conséquent, lorsque le diviseur est égal à 0, aucune tentative n’est faite pour exécuter la Division et aucun résultat d’erreur. Toutefois, étant donné que `IIf` n’utilise pas l’évaluation de court-circuit, le deuxième argument est évalué même lorsque le premier argument est false. Cela provoque une erreur de division par zéro au moment de l’exécution.  
  
 [!code-vb[VbVbalrOperators#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#101)]  
  
## <a name="if-operator-called-with-two-arguments"></a>Opérateur If appelé avec deux arguments  
 Le premier argument de `If` peut être omis. Cela permet à l’opérateur d’être appelé en utilisant uniquement deux arguments. La liste suivante s’applique uniquement lorsque l’opérateur `If` est appelé avec deux arguments.  
  
## <a name="parts"></a>Composants  
  
|Terme|Définition|  
|---|---|  
|`argument2`|Obligatoire. `Object` . Doit être une référence ou un type Nullable. Évaluée et retournée lorsqu’elle a une valeur autre que `Nothing`.|  
|`argument3`|Obligatoire. `Object` . Évaluée et retournée si `argument2` a pour valeur `Nothing`.|  
  
 Lorsque l’argument `Boolean` est omis, le premier argument doit être une référence ou un type Nullable. Si le premier argument prend la valeur `Nothing`, la valeur du deuxième argument est retournée. Dans tous les autres cas, la valeur du premier argument est retournée. L’exemple suivant illustre le fonctionnement de cette évaluation.  
  
 [!code-vb[VbVbalrOperators#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#102)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.Interaction.IIf%2A>
- [Types valeur Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [Nothing](../../../visual-basic/language-reference/nothing.md)

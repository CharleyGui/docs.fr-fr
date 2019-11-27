---
title: Comparaisons de valeurs
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], comparing values
- Visual Basic code, operators
- Visual Basic code, expressions
- comparison operators [Visual Basic], comparing expressions
- numeric expressions
- operators [Visual Basic], comparison
- expressions [Visual Basic], comparing
ms.assetid: 60da0c76-9458-4afc-97e9-44a7939c064c
ms.openlocfilehash: f766eaaada486a0f70838bafb754d25070ff4174
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346285"
---
# <a name="value-comparisons-visual-basic"></a>Comparaisons de valeurs (Visual Basic)
Les opérateurs de comparaison peuvent être utilisés pour construire des expressions qui comparent les valeurs de variables numériques. Ces expressions retournent une valeur `Boolean` selon que la comparaison est true ou false. Voici quelques exemples d’une telle expression :  
  
 `45 > 26`  
  
 `26 > 45`  
  
 La première expression prend la valeur `True`, car 45 est supérieur à 26. Le deuxième exemple prend la valeur `False`, car 26 n’est pas supérieur à 45.  
  
 Vous pouvez également comparer des expressions numériques de cette manière. Les expressions que vous comparez peuvent elles-mêmes être des expressions complexes, comme dans l’exemple suivant.  
  
 `x / 45 * (y +17) >= System.Math.Sqrt(z) / (p - (x * 16))`  
  
 L’expression complexe précédente comprend des littéraux, des variables et des appels de fonction. Les expressions des deux côtés de l’opérateur de comparaison sont évaluées, et les valeurs résultantes sont ensuite comparées à l’aide de l’opérateur de comparaison `>=`. Si la valeur de l’expression située à gauche est supérieure ou égale à la valeur de l’expression située à droite, l’expression entière prend la valeur `True`; dans le cas contraire, il prend la valeur `False`.  
  
 Les expressions qui comparent des valeurs sont le plus souvent utilisées dans les constructions de `If...Then`, comme dans l’exemple suivant.  
  
 [!code-vb[VbVbalrOperators#84](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#84)]  
  
 Le signe `=` est un opérateur de comparaison, ainsi qu’un opérateur d’assignation. Lorsqu’il est utilisé comme opérateur de comparaison, il évalue si la valeur à gauche est égale à la valeur à droite, comme illustré dans l’exemple suivant.  
  
 [!code-vb[VbVbalrOperators#85](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#85)]  
  
 Vous pouvez également utiliser une expression de comparaison partout où une valeur de `Boolean` est nécessaire, par exemple dans une instruction `If`, `While`, `Loop`ou `ElseIf`, ou lors de l’assignation à ou de la transmission d’une valeur à une variable `Boolean`. Dans l’exemple suivant, la valeur retournée par l’expression de comparaison est assignée à une variable `Boolean`.  
  
 [!code-vb[VbVbalrOperators#86](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#86)]  
  
## <a name="see-also"></a>Voir aussi

- [Expressions booléennes](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [Opérateurs et expressions](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [Opérateurs de comparaison dans Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Guide pratique : calculer des valeurs numériques](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-calculate-numeric-values.md)
- [Priorité des opérateurs en Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md)

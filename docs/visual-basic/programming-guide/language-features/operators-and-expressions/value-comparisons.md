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
ms.openlocfilehash: e424dd58cada8cda250554a4a8870e1900d0fa7d
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91085969"
---
# <a name="value-comparisons-visual-basic"></a>Comparaisons de valeurs (Visual Basic)

Les opérateurs de comparaison peuvent être utilisés pour construire des expressions qui comparent les valeurs de variables numériques. Ces expressions retournent une `Boolean` valeur selon que la comparaison est true ou false. Voici quelques exemples d’une telle expression :  
  
 `45 > 26`  
  
 `26 > 45`  
  
 La première expression prend la valeur `True` , car 45 est supérieur à 26. Le deuxième exemple prend la valeur `False` , car 26 n’est pas supérieur à 45.  
  
 Vous pouvez également comparer des expressions numériques de cette manière. Les expressions que vous comparez peuvent elles-mêmes être des expressions complexes, comme dans l’exemple suivant.  
  
 `x / 45 * (y +17) >= System.Math.Sqrt(z) / (p - (x * 16))`  
  
 L’expression complexe précédente comprend des littéraux, des variables et des appels de fonction. Les expressions des deux côtés de l’opérateur de comparaison sont évaluées, et les valeurs résultantes sont ensuite comparées à l’aide de l' `>=` opérateur de comparaison. Si la valeur de l’expression située à gauche est supérieure ou égale à la valeur de l’expression à droite, l’expression entière prend la valeur `True` ; sinon, elle prend la valeur `False` .  
  
 Les expressions qui comparent des valeurs sont le plus souvent utilisées dans `If...Then` les constructions, comme dans l’exemple suivant.  
  
 [!code-vb[VbVbalrOperators#84](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#84)]  
  
 Le `=` signe est un opérateur de comparaison, ainsi qu’un opérateur d’assignation. Lorsqu’il est utilisé comme opérateur de comparaison, il évalue si la valeur à gauche est égale à la valeur à droite, comme illustré dans l’exemple suivant.  
  
 [!code-vb[VbVbalrOperators#85](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#85)]  
  
 Vous pouvez également utiliser une expression de comparaison partout où une `Boolean` valeur est requise, par exemple dans une `If` `While` instruction,, `Loop` ou `ElseIf` , ou lorsque vous assignez ou passez une valeur à une `Boolean` variable. Dans l’exemple suivant, la valeur retournée par l’expression de comparaison est assignée à une `Boolean` variable.  
  
 [!code-vb[VbVbalrOperators#86](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#86)]  
  
## <a name="see-also"></a>Voir aussi

- [Expressions booléennes](boolean-expressions.md)
- [Opérateurs et expressions](index.md)
- [Comparison Operators in Visual Basic](comparison-operators.md)
- [Comment : calculer des valeurs numériques](how-to-calculate-numeric-values.md)
- [Priorité des opérateurs en Visual Basic](../../../language-reference/operators/operator-precedence.md)

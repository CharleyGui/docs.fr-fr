---
title: Expressions booléennes
ms.date: 07/20/2015
helpviewer_keywords:
- short-circuiting
- Boolean expressions
- logical operators [Visual Basic], Boolean expressions
- expressions [Visual Basic], Boolean
- expression evaluation [Visual Basic], Boolean expressions
- operators [Visual Basic], short-circuiting
- Visual Basic code, operators
- short-circuit evaluation
- logical operators [Visual Basic], short-circuiting
- operators [Visual Basic], Boolean
- Visual Basic code, expressions
ms.assetid: d3d90406-55c8-4404-8143-50fd7f0d0d1a
ms.openlocfilehash: 1000ec6e4b35d0cb2c6232b50f9a9551cb0dfdcd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350813"
---
# <a name="boolean-expressions-visual-basic"></a>Expressions booléennes (Visual Basic)
Une *expression booléenne* est une expression qui prend la valeur du [type de données booléen](../../../../visual-basic/language-reference/data-types/boolean-data-type.md): `True` ou `False`. les expressions `Boolean` peuvent prendre plusieurs formes. La plus simple est la comparaison directe de la valeur d’une variable de `Boolean` à un littéral de `Boolean`, comme illustré dans l’exemple suivant.  
  
 [!code-vb[VbVbalrOperators#87](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#87)]  
  
## <a name="two-meanings-of-the--operator"></a>Deux significations de l’opérateur =  
 Notez que l’instruction d’assignation `newCustomer = True` a la même apparence que l’expression dans l’exemple précédent, mais elle exécute une fonction différente et est utilisée différemment. Dans l’exemple précédent, l’expression `newCustomer = True` représente une valeur booléenne et le signe `=` est interprété comme un opérateur de comparaison. Dans une instruction autonome, le signe `=` est interprété comme un opérateur d’assignation et affecte la valeur à droite à la variable sur la gauche. L’exemple suivant illustre ces actions.  
  
 [!code-vb[VbVbalrOperators#88](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#88)]  
  
 Pour plus d’informations, consultez [comparaisons](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md) et [instructions](../../../../visual-basic/language-reference/statements/index.md)de valeur.  
  
## <a name="comparison-operators"></a>Opérateurs de comparaison  
 Les opérateurs de comparaison tels que `=`, `<`, `>`, `<>`, `<=`et `>=` produisent des expressions booléennes en comparant l’expression située à gauche de l’opérateur à l’expression située à droite de l’opérateur et en évaluant le résultat comme `True` ou `False`. L’exemple suivant illustre ces actions.  
  
 `42 < 81`  
  
 Étant donné que 42 est inférieur à 81, l’expression booléenne dans l’exemple précédent prend la valeur `True`. Pour plus d’informations sur ce type d’expression, consultez [comparaisons de valeurs](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md).  
  
### <a name="comparison-operators-combined-with-logical-operators"></a>Opérateurs de comparaison combinés aux opérateurs logiques  
 Les expressions de comparaison peuvent être combinées à l’aide d’opérateurs logiques pour produire des expressions booléennes plus complexes. L’exemple suivant illustre l’utilisation d’opérateurs de comparaison conjointement à un opérateur logique.  
  
 `x > y And x < 1000`  
  
 Dans l’exemple précédent, la valeur de l’expression globale dépend des valeurs des expressions de chaque côté de l’opérateur `And`. Si les deux expressions sont `True`, l’expression globale prend la valeur `True`. Si l’une des expressions est `False`, l’expression entière prend la valeur `False`.  
  
## <a name="short-circuiting-operators"></a>Opérateurs de court-circuit  
 Les opérateurs logiques `AndAlso` et `OrElse` comportement d’exposition connu sous le nom de *court-circuit*. Un opérateur de court-circuit évalue d’abord l’opérande de gauche. Si l’opérande de gauche détermine la valeur de l’expression entière, l’exécution du programme se poursuit sans évaluer l’expression de droite. L’exemple suivant illustre ces actions.  
  
 [!code-vb[VbVbalrOperators#89](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#89)]  
  
 Dans l’exemple précédent, l’opérateur évalue l’expression de gauche, `45 < 12`. Étant donné que l’expression de gauche correspond à `False`, la totalité de l’expression logique doit s’évaluer à `False`. L’exécution du programme ignore donc l’exécution du code dans le bloc `If` sans évaluer l’expression de droite, `testFunction(3)`. Cet exemple n’appelle pas `testFunction()`, car l’expression de gauche falsifie l’expression entière.  
  
 De même, si l’expression de gauche dans une expression logique utilisant `OrElse` a la valeur `True`, l’exécution passe à la ligne de code suivante sans évaluer l’expression de droite, car l’expression de gauche a déjà validé l’expression entière.  
  
### <a name="comparison-with-non-short-circuiting-operators"></a>Comparaison avec les opérateurs qui ne sont pas de type court-circuit  
 En revanche, les deux côtés de l’opérateur logique sont évalués lorsque les opérateurs logiques `And` et `Or` sont utilisés. L’exemple suivant illustre ces actions.  
  
 [!code-vb[VbVbalrOperators#90](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#90)]  
  
 L’exemple précédent appelle `testFunction()` même si l’expression de gauche correspond à `False`.  
  
## <a name="parenthetical-expressions"></a>Expressions entre parenthèses  
 Vous pouvez utiliser des parenthèses pour contrôler l’ordre d’évaluation des expressions booléennes. Les expressions entre parenthèses sont évaluées en premier. Pour plusieurs niveaux d’imbrication, la priorité est accordée aux expressions les plus profondément imbriquées. Entre parenthèses, l’évaluation se poursuit en fonction des règles de priorité des opérateurs. Pour plus d’informations, consultez [priorité des opérateurs dans Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).  
  
## <a name="see-also"></a>Voir aussi

- [Opérateurs logiques et au niveau du bit dans Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
- [Comparaisons de valeurs](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [Instructions](../../../../visual-basic/programming-guide/language-features/statements.md)
- [Opérateurs de comparaison](../../../../visual-basic/language-reference/operators/comparison-operators.md)
- [Association efficace d’opérateurs](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
- [Priorité des opérateurs en Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Booléen (type de données)](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)

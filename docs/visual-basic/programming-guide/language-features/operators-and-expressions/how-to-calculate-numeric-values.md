---
title: 'Comment : calculer des valeurs numériques'
ms.date: 07/20/2015
helpviewer_keywords:
- operator precedence
- operators [Visual Basic]
- expressions [Visual Basic], numeric
- calculations [Visual Basic], numeric expressions
- precedence [Visual Basic], of operators
- Visual Basic code, operators
- Visual Basic code, expressions
- numeric expressions
ms.assetid: ba6bf43d-bd96-49b8-b1de-4a7797551372
ms.openlocfilehash: d213f6b5a4abf8c52d8872ae36e89796183ff27c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348968"
---
# <a name="how-to-calculate-numeric-values-visual-basic"></a>Comment : calculer des valeurs numériques (Visual Basic)
Vous pouvez calculer des valeurs numériques à l’aide d’expressions numériques. Une *expression numérique* est une expression qui contient des littéraux, des constantes et des variables représentant des valeurs numériques, ainsi que des opérateurs qui agissent sur ces valeurs.  
  
## <a name="calculating-numeric-values"></a>Calcul de valeurs numériques  
  
#### <a name="to-calculate-a-numeric-value"></a>Pour calculer une valeur numérique  
  
- Combiner un ou plusieurs littéraux numériques, constantes et variables dans une expression numérique. L’exemple suivant montre des expressions numériques valides.  
  
     `93.217`  
  
     `System.Math.PI`  
  
     `counter`  
  
     `4 * (67 + i)`  
  
     Les trois premières lignes affichent un littéral, une constante et une variable. Chacun d’eux forme une expression numérique valide par lui-même. La dernière ligne affiche une combinaison d’une variable avec deux littéraux.  
  
     Notez qu’une expression numérique ne constitue pas une instruction Visual Basic complète par elle-même. Vous devez utiliser l’expression dans le cadre d’une instruction complète.  
  
#### <a name="to-store-a-numeric-value"></a>Pour stocker une valeur numérique  
  
- Vous pouvez utiliser une instruction d’assignation pour assigner la valeur représentée par une expression numérique à une variable, comme le montre l’exemple suivant.  
  
     [!code-vb[VbVbalrOperators#82](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#82)]  
  
     Dans l’exemple précédent, la valeur de l’expression située à droite de l’opérateur égal (`=`) est assignée à la variable `j` sur le côté gauche de l’opérateur, donc `j` prend la valeur 276.  
  
     Pour plus d’informations, consultez [Instructions](../../../../visual-basic/language-reference/statements/index.md).  
  
## <a name="multiple-operators"></a>Opérateurs multiples  
 Si l’expression numérique contient plusieurs opérateurs, l’ordre dans lequel ils sont évalués est déterminé par les règles de priorité des opérateurs. Pour remplacer les règles de priorité des opérateurs, vous devez placer les expressions entre parenthèses, comme dans l’exemple ci-dessus. les expressions entre parenthèses sont évaluées en premier.  
  
#### <a name="to-override-normal-operator-precedence"></a>Pour remplacer la priorité d’un opérateur normal  
  
- Utilisez des parenthèses pour encadrer les opérations que vous souhaitez effectuer en premier. L’exemple suivant montre deux résultats différents avec les mêmes opérandes et opérateurs.  
  
     [!code-vb[VbVbalrOperators#83](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#83)]  
  
     Dans l’exemple précédent, le calcul pour `j` exécute d’abord l’opérateur d’addition (`+`), car les parenthèses autour de `(67 + i)` substituent la priorité normale et la valeur assignée à `j` est 276 (4 fois 69). Le calcul pour `k` exécute les opérateurs dans leur priorité normale (`*` avant `+`), et la valeur assignée à `k` est 270 (268 plus 2).  
  
     Pour plus d’informations, consultez [priorité des opérateurs dans Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).  
  
## <a name="see-also"></a>Voir aussi

- [Opérateurs et expressions](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [Comparaisons de valeurs](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [Instructions](../../../../visual-basic/language-reference/statements/index.md)
- [Priorité des opérateurs en Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Opérateurs arithmétiques](../../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Association efficace d’opérateurs](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)

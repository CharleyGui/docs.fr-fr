---
title: Association efficace d'opérateurs
ms.date: 07/20/2015
helpviewer_keywords:
- expressions [Visual Basic], parentheses
- operators [Visual Basic], associativity
- expressions [Visual Basic], operators
- operators [Visual Basic], precedence
- Visual Basic code, operators
- Visual Basic code, expressions
- operators [Visual Basic], complex expressions
- expressions [Visual Basic], complex
- parentheses [Visual Basic], complex expressions
- numeric expressions
ms.assetid: bd22340e-b5be-458b-8772-3916c02309a4
ms.openlocfilehash: 83ad53e4c75490a75eba0f80a6bf0f078aa4d426
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348995"
---
# <a name="efficient-combination-of-operators-visual-basic"></a>Association efficace d'opérateurs (Visual Basic)
Les expressions complexes peuvent contenir de nombreux opérateurs différents. L’exemple suivant illustre ces actions.  
  
 `x = (45 * (y + z)) ^ (2 / 85) * 5 + z`  
  
 La création d’expressions complexes, telles que celle de l’exemple précédent, requiert une compréhension approfondie des règles de priorité des opérateurs. Pour plus d’informations, consultez [priorité des opérateurs dans Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).  
  
## <a name="parenthetical-expressions"></a>Expressions entre parenthèses  
 Souvent, vous souhaitez que les opérations se déroulent dans un ordre différent de celui déterminé par la priorité des opérateurs. Prenons l'exemple suivant.  
  
 `x = z * y + 4`  
  
 L’exemple précédent multiplie `z` par `y`, puis ajoute le résultat à `4`. Toutefois, si vous souhaitez ajouter `y` et `4` avant de multiplier le résultat par `z`, vous pouvez substituer la priorité d’opérateur normale en utilisant des parenthèses. En plaçant une expression entre parenthèses, vous forcez l’évaluation de cette expression en premier, quelle que soit la priorité des opérateurs. Pour forcer l’exemple précédent à effectuer l’addition en premier, vous pouvez le réécrire comme dans l’exemple suivant.  
  
 `x = z * (y + 4)`  
  
 L’exemple précédent ajoute `y` et `4`, puis multiplie cette somme par `z`.  
  
### <a name="nested-parenthetical-expressions"></a>Expressions entre parenthèses imbriquées  
 Vous pouvez imbriquer des expressions à plusieurs niveaux de parenthèses pour remplacer la précédence encore plus loin. Les expressions les plus profondément imbriquées entre parenthèses sont évaluées en premier, suivies du plus profondément imbriqué, et ainsi de suite jusqu’au moins profondément imbriqué, et enfin des expressions en dehors des parenthèses. L’exemple suivant illustre ces actions.  
  
 `x = (z * 4) ^ (y * (z + 2))`  
  
 Dans l’exemple précédent, `z + 2` est évalué en premier, puis les autres expressions entre parenthèses. L’élévation à une puissance, qui a généralement une priorité plus élevée que l’addition ou la multiplication, est évaluée en dernier dans cet exemple car les autres expressions sont placées entre parenthèses.  
  
## <a name="see-also"></a>Voir aussi

- [Opérateurs arithmétiques dans Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [Opérateurs de comparaison dans Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Opérateurs logiques et au niveau du bit dans Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
- [Opérateurs logiques/de bits (Visual Basic)](../../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Expressions booléennes](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [Comparaisons de valeurs](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [Guide pratique : calculer des valeurs numériques](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-calculate-numeric-values.md)
- [Priorité des opérateurs en Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md)

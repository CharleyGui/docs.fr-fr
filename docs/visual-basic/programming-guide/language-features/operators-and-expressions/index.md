---
title: Opérateurs et expressions
ms.date: 07/20/2015
helpviewer_keywords:
- operators [Visual Basic], operands
- operators [Visual Basic]
- operands [Visual Basic], definition
- Visual Basic code, operators
- Visual Basic code, expressions
- operands
- expressions [Visual Basic]
ms.assetid: b86f3131-94ee-448f-96cd-79611e028b26
ms.openlocfilehash: 01e3a53e998774caee8863675b9151a140606852
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071675"
---
# <a name="operators-and-expressions-in-visual-basic"></a>Opérateurs et expressions en Visual Basic

Un *opérateur* est un élément de code qui exécute une opération sur un ou plusieurs éléments de code qui contiennent des valeurs. Les éléments de valeur comprennent des variables, des constantes, des littéraux, des propriétés, des expressions et des retours provenant des procédures `Function` et `Operator`.  
  
 Une *expression* est une série d’éléments de valeur combinés à des opérateurs, ce qui retourne une nouvelle valeur. Les opérateurs agissent sur les éléments de valeur en effectuant des calculs, des comparaisons et d’autres opérations.  
  
## <a name="types-of-operators"></a>Types d’opérateurs  

 Visual Basic fournit les types d’opérateurs suivants :  
  
- Les [opérateurs arithmétiques](arithmetic-operators.md) exécutent des calculs familiers sur les valeurs numériques, dont le décalage de leurs modèles binaires.  
  
- Les [opérateurs de comparaison](comparison-operators.md) comparent deux expressions et retournent une valeur `Boolean` représentant le résultat de la comparaison.  
  
- Les [opérateurs de concaténation](concatenation-operators.md) joignent plusieurs chaînes en une seule chaîne.  
  
- Les [opérateurs logiques et au niveau du bit en Visual Basic](logical-and-bitwise-operators.md) combinent des valeurs `Boolean` ou numériques, et retournent un résultat du même type de données que les valeurs.  
  
 Les éléments de valeur associés à un opérateur sont appelés *opérandes* de cet opérateur. Les opérateurs associés aux éléments de valeur forment des expressions, à l’exception de l’opérateur d’assignation qui forme une *instruction*. Pour plus d’informations, consultez [Instructions](../statements.md).  
  
## <a name="evaluation-of-expressions"></a>Évaluation d’expressions  

 Le résultat final d’une expression représente une valeur qui correspond généralement à un type de données familier tel que `Boolean`, `String` ou à un type numérique.  
  
 Voici des exemples d’expressions.  
  
 `5 + 4`  
  
 `' The preceding expression evaluates to 9.`  
  
 `15 * System.Math.Sqrt(9) + x`  
  
 `' The preceding expression evaluates to 45 plus the value of x.`  
  
 `"Concat" & "ena" & "tion"`  
  
 `' The preceding expression evaluates to "Concatenation".`  
  
 `763 < 23`  
  
 `' The preceding expression evaluates to False.`  
  
 Plusieurs opérateurs peuvent effectuer des actions dans une expression ou instruction unique, comme le montre l’exemple suivant.  
  
 [!code-vb[VbVbalrOperators#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#56)]  
  
 Dans l’exemple précédent, Visual Basic effectue les opérations dans l’expression située à droite de l’opérateur d’assignation ( `=` ), puis assigne la valeur résultante à la variable `x` située à gauche. Dans la pratique, le nombre d’opérateurs pouvant être combinés dans une expression est illimité, mais il est nécessaire de comprendre la [Priorité des opérateurs en Visual Basic](../../../language-reference/operators/operator-precedence.md) pour garantir l’obtention des résultats attendus.  

## <a name="see-also"></a>Voir aussi

- [Opérateurs](../../../language-reference/operators/index.md)
- [Association efficace d’opérateurs](efficient-combination-of-operators.md)
- [Publication](../../../language-reference/statements/index.md)

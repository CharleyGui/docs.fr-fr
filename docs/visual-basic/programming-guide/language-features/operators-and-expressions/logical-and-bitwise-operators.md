---
title: Opérateurs de bits et opérateurs logiques en Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- short-circuiting
- Boolean expressions
- logical operators [Visual Basic], Boolean expressions
- operators [Visual Basic], logical
- AndAlso operator [Visual Basic]
- Not operator [Visual Basic], Boolean expressions
- Xor operator [Visual Basic], Boolean expressions
- And operator [Visual Basic], logical operators
- logical operators [Visual Basic]
- expressions [Visual Basic], Boolean
- Or operator [Visual Basic], logical operators
- Visual Basic code, operators
- short-circuiting [Visual Basic], logical operators
- logical operators [Visual Basic], short-circuiting
- Visual Basic code, expressions
- logical operators [Visual Basic], binary
- OrElse operator [Visual Basic]
- logical operators [Visual Basic], unary
ms.assetid: ca474e13-567d-4b1d-a18b-301433705e57
ms.openlocfilehash: 40076b2ad6606b4c565bcd39dbeea9e55da47211
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963318"
---
# <a name="logical-and-bitwise-operators-in-visual-basic"></a>Opérateurs de bits et opérateurs logiques en Visual Basic
Les opérateurs logiques comparent `Boolean` les expressions et retournent un `Boolean` résultat. Les `And`opérateurs `Or`, ,`AndAlso`,et `Not` sont binaires, car ils prennent deux opérandes, tandis que l’opérateur est unaire, car il accepte un seul opérande. `OrElse` `Xor` Certains de ces opérateurs peuvent également effectuer des opérations logiques au niveau du bit sur des valeurs intégrales.  
  
## <a name="unary-logical-operator"></a>Opérateur logique unaire  
 L' [opérateur NOT](../../../../visual-basic/language-reference/operators/not-operator.md) effectue une *négation* logique sur une `Boolean` expression. Il produit l’opposé logique de son opérande. `True`Si l’expression prend la valeur `Not` , retourne `False`; `Not` si l’expression prend `False`la valeur, retourne `True`. L'exemple suivant illustre ce comportement.  
  
 [!code-vb[VbVbalrOperators#77](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#77)]  
  
## <a name="binary-logical-operators"></a>Opérateurs logiques binaires  
 L' [opérateur and](../../../../visual-basic/language-reference/operators/and-operator.md) effectue une *conjonction* logique `Boolean` sur deux expressions. Si les deux expressions ont `True`la valeur `And` , `True`retourne. Si au moins une des expressions prend la valeur `False` `And` , retourne `False`.  
  
 L' [opérateur or](../../../../visual-basic/language-reference/operators/or-operator.md) effectue une *disjonction* ou une *inclusion* logique `Boolean` sur deux expressions. Si l’une des `True`expressions a la valeur, ou si la `True`valeur est `True`égale à, alors `Or` retourne. Si aucune `True`des expressions n’a la valeur `False`, `Or` retourne.  
  
 L' [opérateur XOR](../../../../visual-basic/language-reference/operators/xor-operator.md) effectue une *exclusion* logique sur `Boolean` deux expressions. Si une seule expression prend la valeur `True`, mais pas les deux `Xor` , `True`retourne. Si les deux expressions ont `True` la valeur ou si `False`la `Xor` valeur `False`est, retourne.  
  
 L’exemple suivant illustre les `And`opérateurs, `Or`et. `Xor`  
  
 [!code-vb[VbVbalrOperators#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#78)]  
  
## <a name="short-circuiting-logical-operations"></a>Opérations logiques de court-circuit  
 L' [opérateur AndAlso](../../../../visual-basic/language-reference/operators/andalso-operator.md) est très similaire à l' `And` opérateur, en ce qu’il effectue également une conjonction `Boolean` logique sur deux expressions. La principale différence entre les deux est que `AndAlso` présente *un comportement de court-circuit* . Si la première expression d’une `AndAlso` expression prend la valeur `False`, la deuxième expression n’est pas évaluée, car elle ne peut pas modifier le `AndAlso` résultat `False`final et retourne.  
  
 De même, l' [opérateur OrElse](../../../../visual-basic/language-reference/operators/orelse-operator.md) effectue une disjonction logique de court-circuit sur `Boolean` deux expressions. Si la première expression d’une `OrElse` expression prend la valeur `True`, la deuxième expression n’est pas évaluée, car elle ne peut pas modifier le `OrElse` résultat `True`final et retourne.  
  
### <a name="short-circuiting-trade-offs"></a>Compromis de court-circuit  
 Le court-circuit peut améliorer les performances en n’évaluant pas une expression qui ne peut pas modifier le résultat de l’opération logique. Toutefois, si cette expression effectue des actions supplémentaires, le court-circuit ignore ces actions. Par exemple, si l’expression comprend un appel à une `Function` procédure, cette procédure n’est pas appelée si l’expression est court-circuitée et que tout code supplémentaire contenu dans `Function` le ne s’exécute pas. Par conséquent, la fonction peut s’exécuter uniquement occasionnellement et ne pas être testée correctement. Ou la logique du programme peut dépendre du code dans `Function`.  
  
 L’exemple suivant illustre la différence entre `And`, `Or`et leurs équivalents de court-circuit.  
  
 [!code-vb[VbVbalrOperators#81](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#81)]  
  
 [!code-vb[VbVbalrOperators#80](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#80)]  
  
 [!code-vb[VbVbalrOperators#79](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#79)]  
  
 Dans l’exemple précédent, Notez que certains codes importants à `checkIfValid()` l’intérieur de ne s’exécutent pas lorsque l’appel est court-circuité. La première `If` instruction appelle `checkIfValid()` même si `12 > 45` retourne `False`, car `And` n’est pas un court-circuit. La deuxième `If` instruction n’appelle `checkIfValid()`pas, car lorsque `12 > 45` retourne `False`, `AndAlso` les courts-circuits la seconde expression. La troisième `If` instruction appelle `checkIfValid()` même si `12 < 45` retourne `True`, car `Or` n’est pas un court-circuit. La quatrième `If` instruction n’appelle `checkIfValid()`pas, car lorsque `12 < 45` retourne `True`, `OrElse` les courts-circuits la seconde expression.  
  
## <a name="bitwise-operations"></a>Opérations au niveau du bit  
 Les opérations au niveau du bit évaluent deux valeurs intégrales sous forme binaire (base 2). Ils comparent les bits aux positions correspondantes, puis attribuent des valeurs en fonction de la comparaison. L’exemple suivant illustre l' `And` opérateur.  
  
 [!code-vb[VbVbalrConcepts#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConcepts/VB/Class1.vb#2)]  
  
 L’exemple précédent définit la valeur de `x` sur 1. Cela se produit pour les raisons suivantes:  
  
- Les valeurs sont traitées comme binaires:  
  
     3 sous forme binaire = 011  
  
     5 sous forme binaire = 101  
  
- L' `And` opérateur compare les représentations binaires, une position binaire (bit) à la fois. Si les deux bits à une position donnée sont 1, un 1 est placé à cette position dans le résultat. Si un bit est égal à 0, la valeur 0 est placée à cette position dans le résultat. Dans l’exemple précédent, cela fonctionne comme suit:  
  
     011 (3 sous forme binaire)  
  
     101 (5 sous forme binaire)  
  
     001 (résultat, au format binaire)  
  
- Le résultat est traité comme un nombre décimal. La valeur 001 est la représentation binaire de 1, donc `x` = 1.  
  
 L’opération `Or` au niveau du bit est similaire, à ceci près qu’une valeur 1 est assignée au bit de résultat si l’un des deux bits comparés est 1. `Xor`assigne un 1 au bit de résultat si exactement l’un des bits comparés (pas les deux) est 1. `Not`prend un opérande unique et inverse tous les bits, y compris le bit de signe, et assigne cette valeur au résultat. Cela signifie que pour les nombres positifs signés, `Not` retourne toujours une valeur négative et, pour les nombres négatifs, `Not` retourne toujours une valeur positive ou nulle.  
  
 Les `AndAlso` opérateurs `OrElse` et ne prennent pas en charge les opérations au niveau du bit.  
  
> [!NOTE]
> Les opérations au niveau du bit ne peuvent être exécutées que sur des types intégraux. Les valeurs à virgule flottante doivent être converties en types intégraux avant que l’opération au niveau du bit puisse se poursuivre.  
  
## <a name="see-also"></a>Voir aussi

- [Opérateurs logiques/de bits (Visual Basic)](../../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Expressions booléennes](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [Opérateurs arithmétiques dans Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [Opérateurs de comparaison dans Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Opérateurs de concaténation dans Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
- [Association efficace d’opérateurs](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)

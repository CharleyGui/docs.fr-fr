---
title: Opérateurs arithmétiques
ms.date: 07/20/2015
helpviewer_keywords:
- type safety
- operators [Visual Basic], bitwise
- operators [Visual Basic], bit-shift
- bitwise operators [Visual Basic]
- bit-shift operators [Visual Basic]
- zero, division by zero
- operators [Visual Basic], arithmetic
- division [Visual Basic], by zero
- Visual Basic code, operators
- arithmetic operators [Visual Basic], about arithmetic operators
ms.assetid: 325dac7a-ea4f-41d5-8b48-f6e904211569
ms.openlocfilehash: d5f79f3e45fc887dcb32c959f04703253ade198c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84389034"
---
# <a name="arithmetic-operators-in-visual-basic"></a>Opérateurs arithmétiques en Visual Basic
Les opérateurs arithmétiques sont utilisés pour effectuer de nombreuses opérations arithmétiques familières qui impliquent le calcul de valeurs numériques représentées par des littéraux, des variables, d’autres expressions, des appels de fonction et de propriété et des constantes. Les opérateurs de décalage de bits sont également classés avec les opérateurs arithmétiques, qui agissent au niveau des bits individuels des opérandes et décalent leurs modèles binaires vers la gauche ou vers la droite.  
  
## <a name="arithmetic-operations"></a>Opérations arithmétiques  
 Vous pouvez ajouter deux valeurs dans une expression avec l' [opérateur +](../../../language-reference/operators/addition-operator.md), ou en soustraire une d’une autre à l' [opérateur-(Visual Basic)](../../../language-reference/operators/subtraction-operator.md), comme le montre l’exemple suivant.  
  
 [!code-vb[VbVbalrOperators#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#57)]  
  
 La négation utilise également l' [opérateur-(Visual Basic)](../../../language-reference/operators/subtraction-operator.md), mais avec un seul opérande, comme le montre l’exemple suivant.  
  
 [!code-vb[VbVbalrOperators#58](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#58)]  
  
 La multiplication et la division utilisent respectivement l' [opérateur *](../../../language-reference/operators/multiplication-operator.md) et [/(Visual Basic)](../../../language-reference/operators/floating-point-division-operator.md), comme le montre l’exemple suivant.  
  
 [!code-vb[VbVbalrOperators#59](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#59)]  
  
 L’élévation à la puissance utilise l' [opérateur ^](../../../language-reference/operators/exponentiation-operator.md), comme le montre l’exemple suivant.  
  
 [!code-vb[VbVbalrOperators#60](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#60)]  
  
 La Division d’entiers est effectuée à l’aide de l' [opérateur \ (Visual Basic)](../../../language-reference/operators/integer-division-operator.md). La Division d’entier retourne le quotient, autrement dit, l’entier qui représente le nombre de fois que le diviseur peut être divisé en dividende sans tenir compte du reste. Le diviseur et le dividende doivent tous deux être des types intégraux ( `SByte` , `Byte` ,, `Short` `UShort` , `Integer` , `UInteger` , `Long` et `ULong` ) pour cet opérateur. Tous les autres types doivent d’abord être convertis en un type intégral. L’exemple suivant illustre la Division d’entiers.  
  
 [!code-vb[VbVbalrOperators#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#61)]  
  
 L’arithmétique modulo est effectuée à l’aide de l' [opérateur mod](../../../language-reference/operators/mod-operator.md). Cet opérateur retourne le reste après avoir divisé le diviseur en dividende un nombre entier de fois. Si diviseur et Dividend sont des types intégraux, la valeur retournée est intégrale. Si Divisor et dividendes sont des types à virgule flottante, la valeur retournée est également à virgule flottante. L'exemple ci-dessous illustre ce comportement.  
  
 [!code-vb[VbVbalrOperators#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#62)]  
  
 [!code-vb[VbVbalrOperators#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#63)]  
  
### <a name="attempted-division-by-zero"></a>Division par zéro  
 La division par zéro a des résultats différents selon les types de données impliqués. Dans les divisions intégrales ( `SByte` , `Byte` , `Short` , `UShort` , `Integer` , `UInteger` , `Long` , `ULong` ), le .NET Framework lève une <xref:System.DivideByZeroException> exception. Dans les opérations de division sur le `Decimal` `Single` type de données ou, le .NET Framework lève également une <xref:System.DivideByZeroException> exception.  
  
 Dans les divisions à virgule flottante impliquant le `Double` type de données, aucune exception n’est levée et le résultat est le membre de classe représentant <xref:System.Double.NaN> , <xref:System.Double.PositiveInfinity> ou <xref:System.Double.NegativeInfinity> , selon le dividende. Le tableau suivant résume les différents résultats de la tentative de division d’une `Double` valeur par zéro.  
  
|Type de données dividende|Type de données diviseur|Valeur de dividende|Résultats|  
|---|---|---|---|  
|`Double`|`Double`|0|<xref:System.Double.NaN>(pas un nombre défini de façon mathématique)|  
|`Double`|`Double`|> 0|<xref:System.Double.PositiveInfinity>|  
|`Double`|`Double`|\< 0|<xref:System.Double.NegativeInfinity>|  
  
 Quand vous interceptez une <xref:System.DivideByZeroException> exception, vous pouvez utiliser ses membres pour vous aider à la gérer. Par exemple, la <xref:System.Exception.Message%2A> propriété contient le texte du message pour l’exception. Pour plus d’informations, consultez [Try...Catch...Finally, instruction](../../../language-reference/statements/try-catch-finally-statement.md).  
  
## <a name="bit-shift-operations"></a>Opérations de décalage de bits  
 Une opération de décalage binaire effectue un décalage arithmétique sur un modèle binaire. Le modèle est contenu dans l’opérande de gauche, tandis que l’opérande à droite spécifie le nombre de positions pour déplacer le modèle. Vous pouvez déplacer le modèle vers la droite avec l' [opérateur>> ](../../../language-reference/operators/right-shift-operator.md) ou vers la gauche à l’aide de l' [opérateur<< ](../../../language-reference/operators/left-shift-operator.md).  
  
 Le type de données de l’opérande de modèle doit être `SByte` , `Byte` , `Short` , `UShort` , `Integer` , `UInteger` , `Long` ou `ULong` . Le type de données de l’opérande de la valeur de décalage doit être `Integer` ou doit s’étendre à `Integer` .  
  
 Les décalages arithmétiques ne sont pas circulaires, ce qui signifie que les bits décalés d’une extrémité du résultat ne sont pas réintroduits à l’autre extrémité. Les positions de bits libérées par une équipe sont définies comme suit :  
  
- 0 pour un décalage arithmétique vers la gauche  
  
- 0 pour un décalage arithmétique vers la droite d’un nombre positif  
  
- 0 pour un décalage arithmétique vers la droite d’un type de données non signé ( `Byte` , `UShort` , `UInteger` , `ULong` )  
  
- 1 pour un décalage arithmétique vers la droite d’un nombre négatif ( `SByte` , `Short` , `Integer` ou `Long` )  
  
 L’exemple suivant décale une `Integer` valeur vers la gauche et vers la droite.  
  
 [!code-vb[VbVbalrOperators#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#64)]  
  
 Les décalages arithmétiques ne génèrent jamais d’exceptions de dépassement de capacité.  
  
## <a name="bitwise-operations"></a>Opérations au niveau du bit  
 En plus des opérateurs logiques,,, `Not` `Or` `And` et `Xor` effectuent également une opération arithmétique au niveau du bit lorsqu’ils sont utilisés sur des valeurs numériques. Pour plus d’informations, consultez « opérations au niveau du bit » dans [opérateurs logiques et au niveau du bit dans Visual Basic](logical-and-bitwise-operators.md).  
  
## <a name="type-safety"></a>Sécurité de type  
 Les opérandes doivent normalement être du même type. Par exemple, si vous `Integer` Ajoutez une variable, vous devez l’ajouter à une autre `Integer` variable, et vous devez assigner le résultat à une variable de type `Integer` également.  
  
 Pour garantir une bonne pratique de codage de type sécurisé, vous pouvez utiliser l' [instruction Option Strict](../../../language-reference/statements/option-strict-statement.md). Si vous définissez `Option Strict On` , Visual Basic effectue automatiquement des conversions *de type sécurisé* . Par exemple, si vous essayez d’ajouter une `Integer` variable à une variable `Double` et d’affecter la valeur à une `Double` variable, l’opération se poursuit normalement, car une `Integer` valeur peut être convertie en `Double` sans perte de données. Les conversions de type non sécurisées, en revanche, provoquent une erreur du compilateur avec `Option Strict On` . Par exemple, si vous essayez d’ajouter une `Integer` variable à une variable `Double` et d’assigner la valeur à une `Integer` variable, une erreur de compilation se produit, car une `Double` variable ne peut pas être convertie implicitement en type `Integer` .  
  
 Toutefois, si vous définissez `Option Strict Off` , Visual Basic permet d’effectuer des conversions restrictives implicites, même si elles peuvent entraîner une perte de données ou de précision inattendue. Pour cette raison, nous vous recommandons d’utiliser `Option Strict On` lors de l’écriture de code de production. Pour plus d’informations, consultez [Widening and Narrowing Conversions](../data-types/widening-and-narrowing-conversions.md).  
  
## <a name="see-also"></a>Voir aussi

- [Opérateurs arithmétiques](../../../language-reference/operators/arithmetic-operators.md)
- [Opérateurs de décalage de bits](../../../language-reference/operators/bit-shift-operators.md)
- [Comparison Operators in Visual Basic](comparison-operators.md)
- [Opérateurs de concaténation (Visual Basic)](concatenation-operators.md)
- [Opérateurs de bits et opérateurs logiques en Visual Basic](logical-and-bitwise-operators.md)
- [Association efficace d’opérateurs](efficient-combination-of-operators.md)

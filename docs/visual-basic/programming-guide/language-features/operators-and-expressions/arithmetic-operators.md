---
title: Opérateurs arithmétiques en Visual Basic
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
ms.openlocfilehash: 9f1d77ac27def556d94fac12dbde2f36d5b139de
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64649756"
---
# <a name="arithmetic-operators-in-visual-basic"></a>Opérateurs arithmétiques en Visual Basic
Opérateurs arithmétiques sont utilisés pour effectuer la plupart des opérations arithmétiques familières qui impliquent le calcul de valeurs numériques représentées par des littéraux, des variables, autres expressions, fonction et les appels de propriété et constantes. Également classés avec des opérateurs arithmétiques sont les opérateurs de décalage de bits, qui agissent au niveau des bits individuels des opérandes- and -shift de leurs modèles binaires vers la gauche ou droite.  
  
## <a name="arithmetic-operations"></a>Opérations arithmétiques  
 Vous pouvez ajouter deux valeurs dans une expression avec le [opérateur +](../../../../visual-basic/language-reference/operators/addition-operator.md), ou soustraire une valeur d’une autre avec la [-, opérateur (Visual Basic)](../../../../visual-basic/language-reference/operators/subtraction-operator.md), comme le montre l’exemple suivant.  
  
 [!code-vb[VbVbalrOperators#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#57)]  
  
 Négation utilise également le [-, opérateur (Visual Basic)](../../../../visual-basic/language-reference/operators/subtraction-operator.md), mais avec un seul opérande, comme dans l’exemple suivant montre.  
  
 [!code-vb[VbVbalrOperators#58](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#58)]  
  
 Multiplication et division utilisent le [* opérateur](../../../../visual-basic/language-reference/operators/multiplication-operator.md) et [/, opérateur (Visual Basic)](../../../../visual-basic/language-reference/operators/floating-point-division-operator.md), respectivement, comme le montre l’exemple suivant.  
  
 [!code-vb[VbVbalrOperators#59](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#59)]  
  
 Exponentiation utilise le [^ opérateur](../../../../visual-basic/language-reference/operators/exponentiation-operator.md), comme le montre l’exemple suivant.  
  
 [!code-vb[VbVbalrOperators#60](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#60)]  
  
 Division d’entier est effectuée à l’aide de la [\, opérateur (Visual Basic)](../../../../visual-basic/language-reference/operators/integer-division-operator.md). Division d’entier retourne le quotient, autrement dit, l’entier qui représente le nombre de fois où le diviseur peut diviser le dividende sans tenir compte de tout élément restant. Le diviseur et le dividende doivent être de types intégraux (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, et `ULong`) pour cet opérateur. Tous les autres types doivent tout d’abord être convertis en un type intégral. L’exemple suivant montre la division d’entier.  
  
 [!code-vb[VbVbalrOperators#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#61)]  
  
 Modulo arithmétique est effectué à l’aide de la [opérateur Mod](../../../../visual-basic/language-reference/operators/mod-operator.md). Cet opérateur retourne le reste après que le diviseur par le dividende un nombre entier d’heures. Si le diviseur et le dividende sont des types intégraux, la valeur retournée est intégral. Si le diviseur et le dividende sont des types à virgule flottante, la valeur retournée est également à virgule flottante. L’exemple suivant illustre ce comportement.  
  
 [!code-vb[VbVbalrOperators#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#62)]  
  
 [!code-vb[VbVbalrOperators#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#63)]  
  
### <a name="attempted-division-by-zero"></a>Tentative de Division par zéro  
 Division par zéro a des résultats différents selon les types de données impliqués. Dans les divisions intégrales (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`), la [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] lève un <xref:System.DivideByZeroException> exception. Dans les opérations de division sur la `Decimal` ou `Single` type de données, le [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] lève également une <xref:System.DivideByZeroException> exception.  
  
 Unités de division à virgule flottante qui impliquent le `Double` type de données, aucune exception n’est levée et le résultat est le membre de classe représentant <xref:System.Double.NaN>, <xref:System.Double.PositiveInfinity>, ou <xref:System.Double.NegativeInfinity>, selon le dividende. Le tableau suivant récapitule les différents résultats de la tentative de diviser un `Double` valeur par zéro.  
  
|Type de données de dividende|Type de données de diviseur|Valeur de dividende|Résultat|  
|---|---|---|---|  
|`Double`|`Double`|0|<xref:System.Double.NaN> (pas un nombre défini mathématiquement)|  
|`Double`|`Double`|> 0|<xref:System.Double.PositiveInfinity>|  
|`Double`|`Double`|\< 0|<xref:System.Double.NegativeInfinity>|  
  
 Lorsque vous interceptez une <xref:System.DivideByZeroException> exception, vous pouvez utiliser ses membres pour vous aider à gérer. Par exemple, le <xref:System.Exception.Message%2A> propriété contient le texte du message pour l’exception. Pour plus d’informations, consultez [Try...Catch...Finally, instruction](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
## <a name="bit-shift-operations"></a>Opérations de décalage de bits  
 Une opération de décalage de bits effectue un décalage arithmétique sur un modèle binaire. Le modèle est contenu dans l’opérande de gauche, tandis que l’opérande de droite indique le nombre de positions de décalage du modèle. Vous pouvez décaler le modèle vers la droite avec la [>> opérateur](../../../../visual-basic/language-reference/operators/right-shift-operator.md) ou à gauche avec la [<< opérateur](../../../../visual-basic/language-reference/operators/left-shift-operator.md).  
  
 Le type de données de l’opérande de modèle doit être `SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, ou `ULong`. Le type de données de l’opérande de décalage doit être `Integer` ou doit s’étendre à `Integer`.  
  
 Les décalages arithmétiques ne sont pas circulaires, ce qui signifie que les bits décalés à une extrémité du résultat ne sont pas réintroduits à l’autre extrémité. Les positions binaires libérées par un décalage sont définies comme suit :  
  
- 0 pour un décalage arithmétique vers la gauche  
  
- 0 pour un décalage arithmétique vers la droite d’un nombre positif  
  
- 0 pour un décalage arithmétique vers la droite d’un type de données non signé (`Byte`, `UShort`, `UInteger`, `ULong`)  
  
- 1 pour un décalage arithmétique vers la droite d’un nombre négatif (`SByte`, `Short`, `Integer`, ou `Long`)  
  
 L’exemple suivant Décale une `Integer` valeur gauche et droite.  
  
 [!code-vb[VbVbalrOperators#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#64)]  
  
 Les décalages arithmétiques ne génèrent jamais des exceptions de dépassement de capacité.  
  
## <a name="bitwise-operations"></a>Opérations au niveau du bit  
 Opérateurs logiques, `Not`, `Or`, `And`, et `Xor` également effectuer des opérations de bits arithmétiques lorsqu’il est utilisé sur des valeurs numériques. Pour plus d’informations, consultez « Opérations de bits » dans [opérateurs logiques et au niveau du bit en Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md).  
  
## <a name="type-safety"></a>Sécurité de type  
 Opérandes doivent normalement être du même type. Par exemple, si vous effectuez un ajout avec un `Integer` variable, vous devez l’ajouter à un autre `Integer` variable et vous devez assigner le résultat à une variable de type `Integer` également.  
  
 Pour vous assurer du bon type sécurisé pratique de programmation consiste à utiliser le [Option Strict, instruction](../../../../visual-basic/language-reference/statements/option-strict-statement.md). Si vous définissez `Option Strict On`, Visual Basic effectue automatiquement *type-safe* conversions. Par exemple, si vous essayez d’ajouter un `Integer` variable à un `Double` variable et affectez la valeur à un `Double` variable, l’opération se poursuit normalement, car un `Integer` valeur peut être convertie en `Double` sans perte de données. Conversions de type sécurisé en revanche, le compilateur génère une erreur avec `Option Strict On`. Par exemple, si vous essayez d’ajouter un `Integer` variable à un `Double` variable et affectez la valeur à une `Integer` variable, une erreur du compilateur se produit, car un `Double` variable ne peut pas être convertie implicitement en type `Integer`.  
  
 Si vous définissez `Option Strict Off`, toutefois, Visual Basic permet les conversions restrictives implicites, même si elles peuvent entraîner une perte inattendue de données ou de précision. Pour cette raison, nous vous recommandons d’utiliser `Option Strict On` lors de l’écriture de code de production. Pour plus d’informations, consultez [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
## <a name="see-also"></a>Voir aussi

- [Opérateurs arithmétiques](../../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Opérateurs de décalage de bits](../../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [Opérateurs de comparaison en Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Opérateurs de concaténation dans Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
- [Opérateurs logiques et au niveau du bit en Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
- [Association efficace d’opérateurs](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)

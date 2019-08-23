---
title: Types de données des résultats d'opérateur (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- data types [Visual Basic], operator result data types
- result data types [Visual Basic]
- operator result data types [Visual Basic]
- operators [Visual Basic], data types
- data types [Visual Basic], ranges
- operators [Visual Basic], result data types
ms.assetid: 9d524533-e1a1-4aa8-b1b8-622068173d06
ms.openlocfilehash: b0ebdb723df6bdb4f74e1558537c307ddb917f64
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923272"
---
# <a name="data-types-of-operator-results-visual-basic"></a>Types de données des résultats d'opérateur (Visual Basic)
Visual Basic détermine le type de données de résultat d’une opération en fonction des types de données des opérandes. Dans certains cas, il peut s’agir d’un type de données avec une plage supérieure à celle de l’un des opérandes.  
  
## <a name="data-type-ranges"></a>plages de types de données  
 Les plages des types de données pertinents, dans l’ordre du plus petit au plus grand, sont les suivantes:  
  
- [Booléen](../../../visual-basic/language-reference/data-types/boolean-data-type.md) : deux valeurs possibles  
  
- [SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md) : 256 valeurs intégrales possibles  
  
- [Short](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md) : 65 536 (6.5... E + 4) valeurs intégrales possibles  
  
- [Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md), [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md) — 4 294 967 296 (4.2... E + 9) valeurs intégrales possibles  
  
- [Long](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md) — 18446744073709551615 (1.8... E + 19) valeurs intégrales possibles  
  
- [Décimale](../../../visual-basic/language-reference/data-types/decimal-data-type.md) : 1.5... e + 29 valeurs intégrales possibles, plage maximale 7.9... e + 28 (valeur absolue)  
  
- [Unique](../../../visual-basic/language-reference/data-types/single-data-type.md) : plage maximale 3.4... E + 38 (valeur absolue)  
  
- [Double](../../../visual-basic/language-reference/data-types/double-data-type.md) : plage maximale 1.7... E + 308 (valeur absolue)  
  
 Pour plus d’informations sur les types de données Visual Basic, consultez [types de données](../../../visual-basic/language-reference/data-types/index.md).  
  
 Si un opérande a la valeur [Nothing](../../../visual-basic/language-reference/nothing.md), les opérateurs arithmétiques Visual Basic le considèrent comme zéro.  
  
## <a name="decimal-arithmetic"></a>Arithmétique décimale  
 Notez que le type de données [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md) n’est ni un nombre à virgule flottante, ni un entier.  
  
 Si l’un `+`des opérandes d’une `/`opération, `Mod` `–`, `*`, `Decimal` ou est et que l' `Single` autre `Double`n’est pas ou, Visual Basic étend l’autre opérande à `Decimal`. Il effectue l’opération dans `Decimal`, et le type de données de `Decimal`résultat est.  
  
## <a name="floating-point-arithmetic"></a>Arithmétique à virgule flottante  
 Visual Basic effectue la plupart des opérations arithmétiques à virgule flottante en [double](../../../visual-basic/language-reference/data-types/double-data-type.md), ce qui est le type de données le plus efficace pour ces opérations. Toutefois, si un opérande est [unique](../../../visual-basic/language-reference/data-types/single-data-type.md) et que l’autre ne `Double`l’est pas, Visual Basic effectue `Single`l’opération dans. Il élargit chaque opérande si nécessaire au type de données approprié avant l’opération, et le résultat a ce type de données.  
  
### <a name="-and--operators"></a>Opérateurs/et ^  
 L' `/` opérateur est défini uniquement pour les types de données [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md), [Single](../../../visual-basic/language-reference/data-types/single-data-type.md)et [double](../../../visual-basic/language-reference/data-types/double-data-type.md) . Visual Basic élargit chaque opérande si nécessaire au type de données approprié avant l’opération, et le résultat a ce type de données.  
  
 Le tableau suivant présente les types de données de résultat `/` pour l’opérateur. Notez que ce tableau est symétrique; pour une combinaison donnée de types de données d’opérandes, le type de données de résultat est le même, quel que soit l’ordre des opérandes.  
  
||||||  
|---|---|---|---|---|  
||`Decimal`|`Single`|`Double`|Tout type entier|  
|`Decimal`|Decimal|Single|Double|Decimal|  
|`Single`|Single|Single|Double|Single|  
|`Double`|Double|Double|Double|Double|  
|Tout type entier|Decimal|Single|Double|Double|  
  
 L' `^` opérateur est défini uniquement pour le `Double` type de données. Visual Basic élargit chaque opérande en fonction des `Double` besoins avant l’opération, et le type de données de `Double`résultat est toujours.  
  
## <a name="integer-arithmetic"></a>Arithmétiques sur les entiers  
 Le type de données de résultat d’une opération entière dépend des types de données des opérandes. En général, Visual Basic utilise les stratégies suivantes pour déterminer le type de données de résultat:  
  
- Si les deux opérandes d’un opérateur binaire ont le même type de données, le résultat a ce type de données. Une exception est `Boolean`, qui est forcée `Short`à.  
  
- Si un opérande non signé participe à un opérande signé, le résultat a un type signé avec au moins une plage comme opérande.  
  
- Dans le cas contraire, le résultat est généralement le plus grand des deux types de données des opérandes.  
  
 Notez que le type de données de résultat peut ne pas être le même que le type de données de l’opérande.  
  
> [!NOTE]
> Le type de données de résultat n’est pas toujours assez grand pour contenir toutes les valeurs possibles résultant de l’opération. Une <xref:System.OverflowException> exception peut se produire si la valeur est trop grande pour le type de données de résultat.  
  
### <a name="unary--and--operators"></a>Opérateurs unaires + et –  
 Le tableau suivant présente les types de données de résultat pour les deux opérateurs `+` unaires, et `–`.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|Unaire`+`|Courte|SByte|Byte|Courte|UShort|Entier|UInteger|Longue|ULong|  
|Unaire`–`|Courte|SByte|Courte|Courte|Entier|Entier|long|long|Decimal|  
  
### <a name="-and--operators"></a><\<et > opérateurs >  
 Le tableau suivant présente les types de données de résultat pour les opérateurs de décalage de `<<` bits `>>`, et. Visual Basic traite chaque opérateur de décalage de bits comme un opérateur unaire sur son opérande gauche (le modèle binaire à décaler).  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`<<`, `>>`|Courte|SByte|Byte|Courte|UShort|Entier|UInteger|Longue|ULong|  
  
 Si l’opérande de gauche `Decimal`est `Single`, `Double`, ou `String`, Visual Basic tente de le convertir en `Long` avant l’opération, et le type de données de `Long`résultat est. L’opérande de droite (le nombre de positions de bits à déplacer) `Integer` doit être ou un type qui s' `Integer`étend à.  
  
### <a name="binary----and-mod-operators"></a>Opérateurs Binary +, –, * et mod  
 Le tableau suivant présente les types de données de résultat pour `+` les `–` opérateurs binaires `*` et `Mod` et. Notez que ce tableau est symétrique; pour une combinaison donnée de types de données d’opérandes, le type de données de résultat est le même, quel que soit l’ordre des opérandes.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|Courte|SByte|Courte|Courte|Entier|Entier|long|long|Decimal|  
|`SByte`|SByte|SByte|Courte|Courte|Entier|Entier|long|long|Decimal|  
|`Byte`|Courte|Courte|Byte|Courte|UShort|Entier|UInteger|Longue|ULong|  
|`Short`|Courte|Courte|Courte|Courte|Entier|Entier|long|long|Decimal|  
|`UShort`|Entier|Entier|UShort|Entier|UShort|Entier|UInteger|Longue|ULong|  
|`Integer`|Entier|Entier|Entier|Entier|Entier|Entier|long|long|Decimal|  
|`UInteger`|long|long|UInteger|long|UInteger|long|UInteger|Longue|ULong|  
|`Long`|long|long|long|long|long|long|long|long|Decimal|  
|`ULong`|Decimal|Decimal|ULong|Decimal|ULong|Decimal|ULong|Decimal|ULong|  
  
### <a name="-operator"></a>\, opérateur  
 Le tableau suivant présente les types de données de résultat `\` pour l’opérateur. Notez que ce tableau est symétrique; pour une combinaison donnée de types de données d’opérandes, le type de données de résultat est le même, quel que soit l’ordre des opérandes.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|Courte|SByte|Courte|Courte|Entier|Entier|long|long|long|  
|`SByte`|SByte|SByte|Courte|Courte|Entier|Entier|long|long|long|  
|`Byte`|Courte|Courte|Byte|Courte|UShort|Entier|UInteger|Longue|ULong|  
|`Short`|Courte|Courte|Courte|Courte|Entier|Entier|long|long|long|  
|`UShort`|Entier|Entier|UShort|Entier|UShort|Entier|UInteger|Longue|ULong|  
|`Integer`|Entier|Entier|Entier|Entier|Entier|Entier|long|long|long|  
|`UInteger`|long|long|UInteger|long|UInteger|long|UInteger|Longue|ULong|  
|`Long`|long|long|long|long|long|long|long|long|long|  
|`ULong`|long|long|ULong|long|ULong|long|ULong|long|ULong|  
  
 Si l’un des opérandes de l' `\` opérateur est [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md), [Single](../../../visual-basic/language-reference/data-types/single-data-type.md)ou [double](../../../visual-basic/language-reference/data-types/double-data-type.md), Visual Basic tente de le convertir en [long](../../../visual-basic/language-reference/data-types/long-data-type.md) avant l’opération, et le type de `Long`données de résultat est.  
  
## <a name="relational-and-bitwise-comparisons"></a>Comparaisons relationnelles et au niveau du bit  
 Le type de données de résultat d’une opération relationnelle `<>`( `<``=`, `>`, `<=`, `>=`,,) `Boolean`est toujours un [type de données booléen](../../../visual-basic/language-reference/data-types/boolean-data-type.md). Il en va de même pour les opérations`And`logiques `Not`( `Or`, `OrElse` `AndAlso`, `Xor`,, `Boolean` ,) sur les opérandes.  
  
 Le type de données de résultat d’une opération logique au niveau du bit dépend des types de données des opérandes. Notez que `AndAlso` et `OrElse` sont définis uniquement pour `Boolean`, et Visual Basic convertit chaque opérande si nécessaire `Boolean` en avant d’effectuer l’opération.  
  
### <a name="-----and--operators"></a>=, < >, \<, >, \<= et > = opérateurs  
 Si les deux opérandes `Boolean`sont, Visual Basic `True` considère qu’ils sont `False`inférieurs à. Si un type numérique est comparé à un `String`, Visual Basic tente de convertir le `String` en `Double` avant l’opération. Un `Char` opérande `Date` ou ne peut être comparé qu’avec un autre opérande du même type de données. Le type de données de résultat `Boolean`est Always.  
  
### <a name="bitwise-not-operator"></a>Opérateur de bits NOT  
 Le tableau suivant présente les types de données de résultat pour `Not` l’opérateur au niveau du bit.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Not`|Boolean|SByte|Byte|Courte|UShort|Entier|UInteger|Longue|ULong|  
  
 Si l’opérande est `Decimal`, `Single`, `Double`ou `String`, Visual Basic tente de le convertir en `Long` avant l’opération, et le type de données de résultat `Long`est.  
  
### <a name="bitwise-and-or-and-xor-operators"></a>Opérateurs de bits and, or et XOR  
 Le tableau suivant présente les types de données de résultat pour `And`les `Or`opérateurs de `Xor` bits, et. Notez que ce tableau est symétrique; pour une combinaison donnée de types de données d’opérandes, le type de données de résultat est le même, quel que soit l’ordre des opérandes.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|Boolean|SByte|Courte|Courte|Entier|Entier|long|long|long|  
|`SByte`|SByte|SByte|Courte|Courte|Entier|Entier|long|long|long|  
|`Byte`|Courte|Courte|Byte|Courte|UShort|Entier|UInteger|Longue|ULong|  
|`Short`|Courte|Courte|Courte|Courte|Entier|Entier|long|long|long|  
|`UShort`|Entier|Entier|UShort|Entier|UShort|Entier|UInteger|Longue|ULong|  
|`Integer`|Entier|Entier|Entier|Entier|Entier|Entier|long|long|long|  
|`UInteger`|long|long|UInteger|long|UInteger|long|UInteger|Longue|ULong|  
|`Long`|long|long|long|long|long|long|long|long|long|  
|`ULong`|long|long|ULong|long|ULong|long|ULong|long|ULong|  
  
 Si un opérande est `Decimal`, `Single`, `Double`ou `String`, Visual Basic tente de le convertir vers `Long` avant l’opération, et le type de données de résultat est le même que si cet opérande avait déjà `Long`été.  
  
## <a name="miscellaneous-operators"></a>Opérateurs divers  
 L' `&` opérateur est défini uniquement pour la concaténation `String` des opérandes. Visual Basic convertit chaque opérande si nécessaire `String` vers avant l’opération, et le type de données de `String`résultat est toujours. Dans le cadre de l' `&` opérateur, toutes les conversions `String` en sont considérées comme des élargissements, `Option Strict` même `On`si est.  
  
 Les `Is` opérateurs `IsNot` et requièrent que les deux opérandes soient de type référence. `TypeOf`... `Is` l’expression requiert que le premier opérande soit d’un type référence et le second opérande soit le nom d’un type de données. Dans tous ces cas, le type de données `Boolean`de résultat est.  
  
 L' `Like` opérateur est défini uniquement pour les critères spéciaux `String` des opérandes. Visual Basic tente de convertir chaque opérande si nécessaire vers `String` avant l’opération. Le type de données de résultat `Boolean`est Always.  
  
## <a name="see-also"></a>Voir aussi

- [Types de données](../../../visual-basic/language-reference/data-types/index.md)
- [Opérateurs et expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [Opérateurs arithmétiques dans Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [Opérateurs de comparaison dans Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Opérateurs](../../../visual-basic/language-reference/operators/index.md)
- [Priorité des opérateurs en Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Opérateurs répertoriés par fonctionnalité](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Opérateurs arithmétiques](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Opérateurs de comparaison](../../../visual-basic/language-reference/operators/comparison-operators.md)
- [Option Strict (instruction)](../../../visual-basic/language-reference/statements/option-strict-statement.md)

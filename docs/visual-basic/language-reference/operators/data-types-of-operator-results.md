---
title: Types de données des résultats d’opérateur
ms.date: 07/20/2015
helpviewer_keywords:
- data types [Visual Basic], operator result data types
- result data types [Visual Basic]
- operator result data types [Visual Basic]
- operators [Visual Basic], data types
- data types [Visual Basic], ranges
- operators [Visual Basic], result data types
ms.assetid: 9d524533-e1a1-4aa8-b1b8-622068173d06
ms.openlocfilehash: f7a1249cec159f98ede48b960fadc5e2ff4a75f3
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867100"
---
# <a name="data-types-of-operator-results-visual-basic"></a>Types de données des résultats d'opérateur (Visual Basic)

Visual Basic détermine le type de données de résultat d’une opération en fonction des types de données des opérandes. Dans certains cas, il peut s’agir d’un type de données avec une plage supérieure à celle de l’un des opérandes.  
  
## <a name="data-type-ranges"></a>plages de types de données  

 Les plages des types de données pertinents, dans l’ordre du plus petit au plus grand, sont les suivantes :  
  
- [Booléen](../data-types/boolean-data-type.md) : deux valeurs possibles  
  
- [SByte](../data-types/sbyte-data-type.md), [Byte](../data-types/byte-data-type.md) : 256 valeurs intégrales possibles  
  
- [Short](../data-types/short-data-type.md), [UShort](../data-types/ushort-data-type.md) : 65 536 (6.5... E + 4) valeurs intégrales possibles  
  
- [Integer](../data-types/integer-data-type.md), [UInteger](../data-types/uinteger-data-type.md) — 4 294 967 296 (4.2... E + 9) valeurs intégrales possibles  
  
- [Long](../data-types/long-data-type.md), [ULong](../data-types/ulong-data-type.md) — 18446744073709551615 (1.8... E + 19) valeurs intégrales possibles  
  
- [Décimale](../data-types/decimal-data-type.md) : 1.5... e + 29 valeurs intégrales possibles, plage maximale 7.9... e + 28 (valeur absolue)  
  
- [Unique](../data-types/single-data-type.md) : plage maximale 3.4... E + 38 (valeur absolue)  
  
- [Double](../data-types/double-data-type.md) : plage maximale 1.7... E + 308 (valeur absolue)  
  
 Pour plus d’informations sur les types de données Visual Basic, consultez [types de données](../data-types/index.md).  
  
 Si un opérande a la valeur [Nothing](../nothing.md), les opérateurs arithmétiques Visual Basic le considèrent comme zéro.  
  
## <a name="decimal-arithmetic"></a>Arithmétique décimale  

 Notez que le type de données [Decimal](../data-types/decimal-data-type.md) n’est ni un nombre à virgule flottante, ni un entier.  
  
 Si l’un des opérandes d’une `+` `–` opération,,, `*` `/` ou `Mod` est `Decimal` et que l’autre n’est pas `Single` ou `Double` , Visual Basic étend l’autre opérande à `Decimal` . Il effectue l’opération dans `Decimal` , et le type de données de résultat est `Decimal` .  
  
## <a name="floating-point-arithmetic"></a>Arithmétique à virgule flottante  

 Visual Basic effectue la plupart des opérations arithmétiques à virgule flottante en [double](../data-types/double-data-type.md), ce qui est le type de données le plus efficace pour ces opérations. Toutefois, si un opérande est [unique](../data-types/single-data-type.md) et que l’autre ne l’est pas `Double` , Visual Basic effectue l’opération dans `Single` . Il élargit chaque opérande si nécessaire au type de données approprié avant l’opération, et le résultat a ce type de données.  
  
### <a name="-and--operators"></a>Opérateurs/et ^  

 L' `/` opérateur est défini uniquement pour les types de données [Decimal](../data-types/decimal-data-type.md), [Single](../data-types/single-data-type.md)et [double](../data-types/double-data-type.md) . Visual Basic élargit chaque opérande si nécessaire au type de données approprié avant l’opération, et le résultat a ce type de données.  
  
 Le tableau suivant présente les types de données de résultat pour l' `/` opérateur. Notez que ce tableau est symétrique ; pour une combinaison donnée de types de données d’opérandes, le type de données de résultat est le même, quel que soit l’ordre des opérandes.  
  
||||||  
|---|---|---|---|---|  
||`Decimal`|`Single`|`Double`|Tout type entier|  
|`Decimal`|Decimal|Unique|Double|Decimal|  
|`Single`|Unique|Unique|Double|Unique|  
|`Double`|Double|Double|Double|Double|  
|Tout type entier|Decimal|Unique|Double|Double|  
  
 L' `^` opérateur est défini uniquement pour le `Double` type de données. Visual Basic élargit chaque opérande en fonction des besoins `Double` avant l’opération, et le type de données de résultat est toujours `Double` .  
  
## <a name="integer-arithmetic"></a>Arithmétiques sur les entiers  

 Le type de données de résultat d’une opération entière dépend des types de données des opérandes. En général, Visual Basic utilise les stratégies suivantes pour déterminer le type de données de résultat :  
  
- Si les deux opérandes d’un opérateur binaire ont le même type de données, le résultat a ce type de données. Une exception est `Boolean` , qui est forcée à `Short` .  
  
- Si un opérande non signé participe à un opérande signé, le résultat a un type signé avec au moins une plage comme opérande.  
  
- Dans le cas contraire, le résultat est généralement le plus grand des deux types de données des opérandes.  
  
 Notez que le type de données de résultat peut ne pas être le même que le type de données de l’opérande.  
  
> [!NOTE]
> Le type de données de résultat n’est pas toujours assez grand pour contenir toutes les valeurs possibles résultant de l’opération. Une <xref:System.OverflowException> exception peut se produire si la valeur est trop grande pour le type de données de résultat.  
  
### <a name="unary--and--operators"></a>Opérateurs unaires + et –  

 Le tableau suivant présente les types de données de résultat pour les deux opérateurs unaires, `+` et `–` .  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|Unaire `+`|Court|SByte|Byte|Court|UShort|Integer|UInteger|Long|ULong|  
|Unaire `–`|Court|SByte|Court|Court|Integer|Integer|Long|Long|Decimal|  
  
### <a name="-and--operators"></a><\< and > Opérateurs>  

 Le tableau suivant présente les types de données de résultat pour les opérateurs de décalage de bits, `<<` et `>>` . Visual Basic traite chaque opérateur de décalage de bits comme un opérateur unaire sur son opérande gauche (le modèle binaire à décaler).  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`<<`, `>>`|Court|SByte|Byte|Court|UShort|Integer|UInteger|Long|ULong|  
  
 Si l’opérande de gauche est `Decimal` , `Single` , `Double` ou `String` , Visual Basic tente de le convertir en `Long` avant l’opération, et le type de données de résultat est `Long` . L’opérande de droite (le nombre de positions de bits à déplacer) doit être `Integer` ou un type qui s’étend à `Integer` .  
  
### <a name="binary----and-mod-operators"></a>Opérateurs Binary +, –, \* et mod  

 Le tableau suivant présente les types de données de résultat pour les opérateurs binaires `+` et et `–` `*` `Mod` . Notez que ce tableau est symétrique ; pour une combinaison donnée de types de données d’opérandes, le type de données de résultat est le même, quel que soit l’ordre des opérandes.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|Court|SByte|Court|Court|Integer|Integer|Long|Long|Decimal|  
|`SByte`|SByte|SByte|Court|Court|Integer|Integer|Long|Long|Decimal|  
|`Byte`|Court|Court|Byte|Court|UShort|Integer|UInteger|Long|ULong|  
|`Short`|Court|Court|Court|Court|Integer|Integer|Long|Long|Decimal|  
|`UShort`|Integer|Integer|UShort|Integer|UShort|Integer|UInteger|Long|ULong|  
|`Integer`|Integer|Integer|Integer|Integer|Integer|Integer|Long|Long|Decimal|  
|`UInteger`|Long|Long|UInteger|Long|UInteger|Long|UInteger|Long|ULong|  
|`Long`|Long|Long|Long|Long|Long|Long|Long|Long|Decimal|  
|`ULong`|Decimal|Decimal|ULong|Decimal|ULong|Decimal|ULong|Decimal|ULong|  
  
### <a name="-operator"></a>\\, opérateur  

 Le tableau suivant présente les types de données de résultat pour l' `\` opérateur. Notez que ce tableau est symétrique ; pour une combinaison donnée de types de données d’opérandes, le type de données de résultat est le même, quel que soit l’ordre des opérandes.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|Court|SByte|Court|Court|Integer|Integer|Long|Long|Long|  
|`SByte`|SByte|SByte|Court|Court|Integer|Integer|Long|Long|Long|  
|`Byte`|Court|Court|Byte|Court|UShort|Integer|UInteger|Long|ULong|  
|`Short`|Court|Court|Court|Court|Integer|Integer|Long|Long|Long|  
|`UShort`|Integer|Integer|UShort|Integer|UShort|Integer|UInteger|Long|ULong|  
|`Integer`|Integer|Integer|Integer|Integer|Integer|Integer|Long|Long|Long|  
|`UInteger`|Long|Long|UInteger|Long|UInteger|Long|UInteger|Long|ULong|  
|`Long`|Long|Long|Long|Long|Long|Long|Long|Long|Long|  
|`ULong`|Long|Long|ULong|Long|ULong|Long|ULong|Long|ULong|  
  
 Si l’un des opérandes de l' `\` opérateur est [Decimal](../data-types/decimal-data-type.md), [Single](../data-types/single-data-type.md)ou [double](../data-types/double-data-type.md), Visual Basic tente de le convertir en [long](../data-types/long-data-type.md) avant l’opération, et le type de données de résultat est `Long` .  
  
## <a name="relational-and-bitwise-comparisons"></a>Comparaisons relationnelles et au niveau du bit  

 Le type de données de résultat d’une opération relationnelle ( `=` , `<>` , `<` ,, `>` `<=` , `>=` ) est toujours un `Boolean` [type de données booléen](../data-types/boolean-data-type.md). Il en va de même pour les opérations logiques ( `And` , `AndAlso` , `Not` , `Or` , `OrElse` , `Xor` ) sur les `Boolean` opérandes.  
  
 Le type de données de résultat d’une opération logique au niveau du bit dépend des types de données des opérandes. Notez que `AndAlso` et `OrElse` sont définis uniquement pour `Boolean` , et Visual Basic convertit chaque opérande si nécessaire en `Boolean` avant d’effectuer l’opération.  
  
### <a name="-----and--operators"></a>=,  <>, \<, > , \<=, and > = opérateurs  

 Si les deux opérandes sont `Boolean` , Visual Basic considère qu’ils sont `True` inférieurs à `False` . Si un type numérique est comparé à un `String` , Visual Basic tente de convertir le `String` en `Double` avant l’opération. Un `Char` `Date` opérande ou ne peut être comparé qu’avec un autre opérande du même type de données. Le type de données de résultat est Always `Boolean` .  
  
### <a name="bitwise-not-operator"></a>Opérateur de bits NOT  

 Le tableau suivant présente les types de données de résultat pour l’opérateur au niveau du bit `Not` .  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Not`|Boolean|SByte|Byte|Court|UShort|Integer|UInteger|Long|ULong|  
  
 Si l’opérande est `Decimal` , `Single` , `Double` ou `String` , Visual Basic tente de le convertir en `Long` avant l’opération, et le type de données de résultat est `Long` .  
  
### <a name="bitwise-and-or-and-xor-operators"></a>Opérateurs de bits and, or et XOR  

 Le tableau suivant présente les types de données de résultat pour les opérateurs de bits `And` , `Or` et `Xor` . Notez que ce tableau est symétrique ; pour une combinaison donnée de types de données d’opérandes, le type de données de résultat est le même, quel que soit l’ordre des opérandes.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|Boolean|SByte|Court|Court|Integer|Integer|Long|Long|Long|  
|`SByte`|SByte|SByte|Court|Court|Integer|Integer|Long|Long|Long|  
|`Byte`|Court|Court|Byte|Court|UShort|Integer|UInteger|Long|ULong|  
|`Short`|Court|Court|Court|Court|Integer|Integer|Long|Long|Long|  
|`UShort`|Integer|Integer|UShort|Integer|UShort|Integer|UInteger|Long|ULong|  
|`Integer`|Integer|Integer|Integer|Integer|Integer|Integer|Long|Long|Long|  
|`UInteger`|Long|Long|UInteger|Long|UInteger|Long|UInteger|Long|ULong|  
|`Long`|Long|Long|Long|Long|Long|Long|Long|Long|Long|  
|`ULong`|Long|Long|ULong|Long|ULong|Long|ULong|Long|ULong|  
  
 Si un opérande est `Decimal` , `Single` , `Double` ou `String` , Visual Basic tente de le convertir vers `Long` avant l’opération, et le type de données de résultat est le même que si cet opérande avait déjà été `Long` .  
  
## <a name="miscellaneous-operators"></a>Opérateurs divers  

 L' `&` opérateur est défini uniquement pour la concaténation des `String` opérandes. Visual Basic convertit chaque opérande si nécessaire vers `String` avant l’opération, et le type de données de résultat est toujours `String` . Dans le cadre de l' `&` opérateur, toutes les conversions en `String` sont considérées comme des élargissements, même si `Option Strict` est `On` .  
  
 Les `Is` `IsNot` opérateurs et requièrent que les deux opérandes soient de type référence. L' `TypeOf` expression... `Is` requiert que le premier opérande soit d’un type référence et le second opérande soit le nom d’un type de données. Dans tous ces cas, le type de données de résultat est `Boolean` .  
  
 L' `Like` opérateur est défini uniquement pour les critères spéciaux des `String` opérandes. Visual Basic tente de convertir chaque opérande si nécessaire vers `String` avant l’opération. Le type de données de résultat est Always `Boolean` .  
  
## <a name="see-also"></a>Voir aussi

- [Data types](../data-types/index.md)
- [Opérateurs et expressions](../../programming-guide/language-features/operators-and-expressions/index.md)
- [Opérateurs arithmétiques en Visual Basic](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [Comparison Operators in Visual Basic](../../programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Opérateurs](index.md)
- [Priorité des opérateurs en Visual Basic](operator-precedence.md)
- [Opérateurs listés par fonctionnalité](operators-listed-by-functionality.md)
- [Opérateurs arithmétiques](arithmetic-operators.md)
- [Opérateurs de comparaison](comparison-operators.md)
- [Option Strict Statement](../statements/option-strict-statement.md)

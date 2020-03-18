---
title: Surcharges d'opérateurs
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- operators [.NET Framework], overloads
- names [.NET Framework], overloaded operators
- member design guidelines, operators
- overloaded operators
ms.assetid: 37585bf2-4c27-4dee-849a-af70e3338cc1
ms.openlocfilehash: 0999e94c8d77396b237522e89c51206ce1226718
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400567"
---
# <a name="operator-overloads"></a>Surcharges d'opérateurs
Les surcharges de l’opérateur permettent aux types de cadres d’apparaître comme s’ils étaient des primitifs en langue intégrée.

 Bien qu’elles soient autorisées et utiles dans certaines situations, les surcharges de l’opérateur doivent être utilisées avec prudence. Il y a beaucoup de cas dans lesquels la surcharge d’opérateur a été abusée, telle que quand les concepteurs de cadre ont commencé à employer des opérateurs pour des opérations qui devraient être des méthodes simples. Les lignes directrices suivantes devraient vous aider à décider quand et comment utiliser la surcharge de l’opérateur.

 ❌AVOID définissant les surcharges de l’opérateur, sauf dans les types qui devraient se sentir comme des types primitifs (intégrés).

 ✔️ CONSIDER définissant les surcharges de l’opérateur dans un type qui devrait se sentir comme un type primitif.

 Par <xref:System.String?displayProperty=nameWithType> exemple, `operator==` `operator!=` a et défini.

 ✔️ NE définissez les surcharges d’opérateur dans les <xref:System.Decimal?displayProperty=nameWithType>structs qui représentent des nombres (tels que ).

 ❌NE pas être mignon lors de la définition des surcharges de l’opérateur.

 La surcharge de l’opérateur est utile dans les cas où il est immédiatement évident quel sera le résultat de l’opération. Par exemple, il est logique d’être `DateTime` en mesure <xref:System.TimeSpan>de soustraire l’un de l’autre <xref:System.DateTime> et d’obtenir un . Toutefois, il n’est pas approprié d’utiliser l’exploitant syndical logique pour syndiquer deux requêtes de base de données ou d’utiliser l’opérateur de quart pour écrire à un flux.

 ❌NE PAS fournir des surcharges d’opérateur à moins qu’au moins un des opérandes soit du type définissant la surcharge.

 ✔️ les opérateurs de surcharge DO d’une manière symétrique.

 Par exemple, si vous `operator==`surchargez le , `operator!=`vous devriez également surcharger le . De même, si `operator<`vous surchargez le `operator>`, vous devriez également surcharger le , et ainsi de suite.

 ✔️ CONSIDER fournissant des méthodes avec des noms amicaux qui correspondent à chaque opérateur surchargé.

 De nombreuses langues ne prennent pas en charge la surcharge des opérateurs. Pour cette raison, il est recommandé que les types qui surchargent les opérateurs comprennent une méthode secondaire avec un nom spécifique au domaine approprié qui fournit des fonctionnalités équivalentes.

 Le tableau suivant contient une liste d’opérateurs et les noms de méthode amicale correspondants.

|Symbole de l’opérateur CMD|Nom des métadonnées|Nom convivial|
|-------------------------|-------------------|-------------------|
|`N/A`|`op_Implicit`|`To<TypeName>/From<TypeName>`|
|`N/A`|`op_Explicit`|`To<TypeName>/From<TypeName>`|
|`+ (binary)`|`op_Addition`|`Add`|
|`- (binary)`|`op_Subtraction`|`Subtract`|
|`* (binary)`|`op_Multiply`|`Multiply`|
|`/`|`op_Division`|`Divide`|
|`%`|`op_Modulus`|`Mod or Remainder`|
|`^`|`op_ExclusiveOr`|`Xor`|
|`& (binary)`|`op_BitwiseAnd`|`BitwiseAnd`|
|<code>&#124;</code>|`op_BitwiseOr`|`BitwiseOr`|
|`&&`|`op_LogicalAnd`|`And`|
|<code>&#124;&#124;</code>|`op_LogicalOr`|`Or`|
|`=`|`op_Assign`|`Assign`|
|`<<`|`op_LeftShift`|`LeftShift`|
|`>>`|`op_RightShift`|`RightShift`|
|`N/A`|`op_SignedRightShift`|`SignedRightShift`|
|`N/A`|`op_UnsignedRightShift`|`UnsignedRightShift`|
|`==`|`op_Equality`|`Equals`|
|`!=`|`op_Inequality`|`Equals`|
|`>`|`op_GreaterThan`|`CompareTo`|
|`<`|`op_LessThan`|`CompareTo`|
|`>=`|`op_GreaterThanOrEqual`|`CompareTo`|
|`<=`|`op_LessThanOrEqual`|`CompareTo`|
|`*=`|`op_MultiplicationAssignment`|`Multiply`|
|`-=`|`op_SubtractionAssignment`|`Subtract`|
|`^=`|`op_ExclusiveOrAssignment`|`Xor`|
|`<<=`|`op_LeftShiftAssignment`|`LeftShift`|
|`%=`|`op_ModulusAssignment`|`Mod`|
|`+=`|`op_AdditionAssignment`|`Add`|
|`&=`|`op_BitwiseAndAssignment`|`BitwiseAnd`|
|<code>&#124;=</code>|`op_BitwiseOrAssignment`|`BitwiseOr`|
|`,`|`op_Comma`|`Comma`|
|`/=`|`op_DivisionAssignment`|`Divide`|
|`--`|`op_Decrement`|`Decrement`|
|`++`|`op_Increment`|`Increment`|
|`- (unary)`|`op_UnaryNegation`|`Negate`|
|`+ (unary)`|`op_UnaryPlus`|`Plus`|
|`~`|`op_OnesComplement`|`OnesComplement`|

### <a name="overloading-operator-"></a>Opérateur de surcharge
 La surcharge `operator ==` est assez compliquée. La sémantique de l’opérateur doit être compatible <xref:System.Object.Equals%2A?displayProperty=nameWithType>avec plusieurs autres membres, tels que .

### <a name="conversion-operators"></a>Opérateurs de conversion
 Les opérateurs de conversion sont des opérateurs non intentionnaires qui permettent la conversion d’un type à l’autre. Les opérateurs doivent être définis comme des membres statiques sur l’opéra ou le type de retour. Il existe deux types d’opérateurs de conversion : implicite et explicite.

 ❌NE PAS fournir un opérateur de conversion si cette conversion n’est pas clairement attendue par les utilisateurs finaux.

 ❌NE DÉFINIssez PAS les opérateurs de conversion en dehors du domaine d’un type.

 Par <xref:System.Int32>exemple, <xref:System.Double>, <xref:System.Decimal> , et sont <xref:System.DateTime> tous les types numériques, alors que n’est pas. Par conséquent, il ne devrait `Double(long)` pas `DateTime`y avoir d’opérateur de conversion pour convertir un . Un constructeur est préféré dans un tel cas.

 ❌NE PAS fournir un opérateur de conversion implicite si la conversion est potentiellement déficiteuse.

 Par exemple, il ne devrait `Double` pas `Int32` `Double` y avoir une `Int32`conversion implicite de parce que a une gamme plus large que . Un opérateur de conversion explicite peut être fourni même si la conversion est potentiellement déficiteuse.

 ❌NE PAS jeter des exceptions des moulages implicites.

 Il est très difficile pour les utilisateurs finaux de comprendre ce qui se passe, car ils pourraient ne pas être conscients qu’une conversion a lieu.

 ✔️ NE jeter <xref:System.InvalidCastException?displayProperty=nameWithType> si un appel à un opérateur de casting entraîne une conversion déficit et le contrat de l’opérateur ne permet pas des conversions déficitaires.

 *Parts © 2005, 2009 Microsoft Corporation. Tous droits réservés.*

 *Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*

## <a name="see-also"></a>Voir aussi

- [Instructions de conception des membres](../../../docs/standard/design-guidelines/member.md)
- [Règles de conception de .NET Framework](../../../docs/standard/design-guidelines/index.md)

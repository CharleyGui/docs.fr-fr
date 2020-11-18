---
title: Surcharges d'opérateurs
ms.date: 10/22/2008
helpviewer_keywords:
- operators [.NET Framework], overloads
- names [.NET Framework], overloaded operators
- member design guidelines, operators
- overloaded operators
ms.assetid: 37585bf2-4c27-4dee-849a-af70e3338cc1
ms.openlocfilehash: 40e1c6a4a65bfc20c94223e4012e34928b25a2ab
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830036"
---
# <a name="operator-overloads"></a>Surcharges d'opérateurs
Les surcharges d’opérateur permettent d’afficher les types de Framework comme s’ils étaient des primitives de langage intégrées.

 Bien qu’elles soient autorisées et utiles dans certains cas, les surcharges d’opérateur doivent être utilisées avec prudence. Il existe de nombreux cas dans lesquels la surcharge d’opérateur a été abusée, par exemple quand les concepteurs de Framework ont commencé à utiliser des opérateurs pour les opérations qui doivent être des méthodes simples. Les instructions suivantes doivent vous aider à déterminer quand et comment utiliser la surcharge d’opérateur.

 ❌ Évitez de définir des surcharges d’opérateur, sauf dans les types qui doivent ressembler à des types primitifs (intégrés).

 ✔️ envisagez de définir des surcharges d’opérateur dans un type qui doit ressembler à un type primitif.

 Par exemple, <xref:System.String?displayProperty=nameWithType> a `operator==` et `operator!=` défini.

 ✔️ définir des surcharges d’opérateur dans des structs qui représentent des nombres (tels que <xref:System.Decimal?displayProperty=nameWithType> ).

 ❌ NE soyez pas au fait de définir des surcharges d’opérateur.

 La surcharge d’opérateur est utile dans les cas où il est immédiatement évident de savoir ce que sera le résultat de l’opération. Par exemple, il est logique de pouvoir soustraire l’un <xref:System.DateTime> d’un autre `DateTime` et d’obtenir un <xref:System.TimeSpan> . Toutefois, il n’est pas approprié d’utiliser l’opérateur d’Union logique pour unir deux requêtes de base de données, ou pour utiliser l’opérateur Shift pour écrire dans un flux.

 ❌ NE fournissez pas de surcharges d’opérateur sauf si au moins l’un des opérandes est du type définissant la surcharge.

 ✔️ surchargent les opérateurs de manière symétrique.

 Par exemple, si vous surchargez le `operator==` , vous devez également surcharger `operator!=` . De même, si vous surchargez le `operator<` , vous devez également surcharger `operator>` , et ainsi de suite.

 ✔️ envisagez de fournir des méthodes avec des noms conviviaux qui correspondent à chaque opérateur surchargé.

 De nombreux langages ne prennent pas en charge la surcharge d’opérateur. Pour cette raison, il est recommandé que les types qui surchargent les opérateurs incluent une méthode secondaire avec un nom spécifique au domaine approprié qui fournit des fonctionnalités équivalentes.

 Le tableau suivant contient une liste d’opérateurs et les noms de méthode conviviaux correspondants.

|Symbole d’opérateur C#|Nom des métadonnées|Nom convivial|
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

### <a name="overloading-operator-"></a>Surcharge de l’opérateur = =
 La surcharge `operator ==` est assez complexe. La sémantique de l’opérateur doit être compatible avec plusieurs autres membres, tels que <xref:System.Object.Equals%2A?displayProperty=nameWithType> .

### <a name="conversion-operators"></a>Opérateurs de conversion
 Les opérateurs de conversion sont des opérateurs unaires qui autorisent la conversion d’un type en un autre. Les opérateurs doivent être définis en tant que membres statiques sur l’opérande ou le type de retour. Il existe deux types d’opérateurs de conversion : implicites et explicites.

 ❌ NE fournissez pas d’opérateur de conversion si une telle conversion n’est pas clairement attendue par les utilisateurs finaux.

 ❌ NE définissez pas d’opérateurs de conversion en dehors du domaine d’un type.

 Par exemple, <xref:System.Int32> , <xref:System.Double> et <xref:System.Decimal> sont tous des types numériques, alors que <xref:System.DateTime> n’est pas. Par conséquent, il ne doit y avoir aucun opérateur de conversion pour convertir un `Double(long)` en `DateTime` . Un constructeur est préféré dans ce cas.

 ❌ NE fournissez pas d’opérateur de conversion implicite si la conversion est potentiellement perdue.

 Par exemple, il ne doit pas y avoir de conversion implicite de `Double` en `Int32` , car `Double` a une plage plus large que `Int32` . Un opérateur de conversion explicite peut être fourni même si la conversion est potentiellement perdue.

 ❌ NE levez pas d’exceptions à partir de casts implicites.

 Il est très difficile pour les utilisateurs finaux de comprendre ce qui se passe, car ils n’ont peut-être pas conscience qu’une conversion a lieu.

 ✔️ Levez une exception <xref:System.InvalidCastException?displayProperty=nameWithType> si un appel à un opérateur de cast entraîne une conversion avec perte et que le contrat de l’opérateur n’autorise pas les conversions avec perte de résultats.

 *Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*

 *Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*

## <a name="see-also"></a>Voir aussi

- [Recommandations en matière de conception de membres](member.md)
- [Directives de conception d’infrastructure](index.md)

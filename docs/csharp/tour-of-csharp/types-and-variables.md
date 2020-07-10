---
title: Variables et types C# - Visite guidée du langage C#
description: En savoir plus sur la définition des types et la déclaration de variables en C#
ms.date: 04/24/2020
ms.assetid: f8a8051e-0049-43f1-b594-9c84cc7b1224
ms.openlocfilehash: a14291d1eec4d090b0275875326c5a580e5abe9d
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174125"
---
# <a name="types-and-variables"></a>Types et variables

Il existe deux genres de types en C# : les *types référence* et les *types valeur*. Les variables des types valeur contiennent directement leurs données alors que les variables des types référence contiennent des références à leurs données, connues sous le nom d’objets. Avec les types référence, deux variables peuvent faire référence au même objet et, par conséquent, les opérations sur une variable peuvent affecter l’objet référencé par l’autre variable. Avec les types valeur, les variables ont chacune leur propre copie des données, et il n’est pas possible pour les opérations sur l’une d’affecter l’autre (à l’exception des `ref` `out` variables de paramètre et).

Les types de valeur C# sont divisés en *types simples*, *types ENUM*, *types struct*et *types valeur Nullable*. Les types référence de C# sont encore divisés en *types classe*, *types interface*, *types tableau*et *types délégués*.

Le schéma suivant fournit une vue d’ensemble du système de type de C#.

- [Types valeur][ValueTypes]
  - [Types simples][SimpleTypes]
    - Entier signé : `sbyte`, `short`, `int`, `long`
    - Entier non signé : `byte`, `ushort`, `uint`, `ulong`
    - Caractères Unicode : `char`
    - Virgule flottante pour valeur binaire IEEE : `float`, `double`
    - Virgule flottante pour valeur décimale haute précision : `decimal`
    - Booléen : `bool`
  - [Types ENUM][EnumTypes]
    - Types définis par l'utilisateur de la forme `enum E {...}`
  - [Types struct][StructTypes]
    - Types définis par l'utilisateur de la forme `struct S {...}`
  - [Types valeur Nullable][NullableTypes]
    - Extensions de tous les autres types de valeurs avec une valeur `null`
  - [Types de valeur de Tuple][TupleTypes]
    - Types définis par l'utilisateur de la forme `(T1, T2, ...)`
- [Types référence][ReferenceTypes]
  - [Types de classe][ClassTypes]
    - Classe de base fondamentale de tous les autres types : `object`
    - Chaînes Unicode : `string`
    - Types définis par l'utilisateur de la forme `class C {...}`
  - [Types d'interface][InterfaceTypes]
    - Types définis par l'utilisateur de la forme `interface I {...}`
  - [Types tableau][ArrayTypes]
    - Uni et multidimensionnels, par exemple `int[]` et `int[,]`
  - [Types délégués][DelegateTypes]
    - Types définis par l'utilisateur de la forme `delegate int D(...)`

[ValueTypes]: ../language-reference/builtin-types/value-types.md
[SimpleTypes]: ../language-reference/builtin-types/value-types.md#built-in-value-types
[EnumTypes]: ../language-reference/builtin-types/enum.md
[StructTypes]: ../language-reference/builtin-types/struct.md
[NullableTypes]: ../language-reference/builtin-types/nullable-value-types.md
[TupleTypes]: ../language-reference/builtin-types/value-tuples.md
[ReferenceTypes]: ../language-reference/keywords/reference-types.md
[ClassTypes]: ../language-reference/keywords/class.md
[InterfaceTypes]: ../language-reference/keywords/interface.md
[DelegateTypes]: ../language-reference/keywords/delegate.md
[ArrayTypes]: ../programming-guide/arrays/index.md

Pour plus d’informations sur les types numériques, consultez [Types intégraux](../language-reference/builtin-types/integral-numeric-types.md) et [Tableau des types à virgule flottante](../language-reference/builtin-types/floating-point-numeric-types.md).

Le type de C# `bool` est utilisé pour représenter des valeurs booléennes, qui sont des valeurs `true` ou `false` .

Le traitement des caractères et chaînes dans le langage C# utilise l’encodage Unicode. Le type `char` représente une unité de code UTF-16, et le type `string` représente une séquence d’unités de code UTF-16.

Les programmes C# utilisent les *déclarations de type* pour créer de nouveaux types. Une déclaration de type spécifie le nom et les membres du nouveau type. Cinq des catégories de types C# sont définissables par l’utilisateur : types classe, types struct, types interface, types ENUM et types délégués.

Un type `class` définit une structure de données qui contient des données membres (champs) et des fonctions membres (méthodes, propriétés, etc.). Les types de classes prennent en charge l’héritage unique et le polymorphisme, des mécanismes par lesquels les classes dérivées peuvent étendre et spécialiser les classes de base.

Un type `struct` est similaire à un type de classe dans la mesure où il représente une structure avec des membres de données et des membres de fonctions. Toutefois, contrairement aux classes, les structs sont des types valeur et ne nécessitent généralement pas d’allocation de tas. Les types struct ne prennent pas en charge l’héritage spécifié par l’utilisateur, et tous les types struct héritent implicitement du type `object` .

Un type `interface` définit un contrat en tant que jeu nommé de membres de la fonction publique. Un `class` ou `struct` qui implémente un `interface` doit fournir des implémentations des membres de la fonction de l’interface. Une `interface` peut hériter de plusieurs interfaces de base, et une `class` ou `struct` peut implémenter plusieurs interfaces.

Un type `delegate` représente des références aux méthodes avec une liste de paramètres et un type de retour particuliers. Les délégués permettent de traiter les méthodes en tant qu’entités qui peuvent être affectées à des variables et passées comme paramètres. Les délégués sont semblables aux types de fonction fournis par les langages fonctionnels. Elles sont également similaires au concept de pointeurs de fonction qui se trouvent dans d’autres langages. Contrairement aux pointeurs de fonction, les délégués sont orientés objet et de type sécurisé.

Les `class` types,, `struct` `interface` et `delegate` prennent tous en charge les génériques, dans lesquels ils peuvent être paramétrés avec d’autres types.

Un type `enum` est un type distinct avec des constantes nommées. Chaque type `enum` a un type sous-jacent qui doit être un des huit types intégraux. L’ensemble de valeurs d’un type `enum` est le même que l’ensemble de valeurs du type sous-jacent.

C# prend en charge les tableaux uni et multidimensionnels de tout type. Contrairement aux types indiqués ci-dessus, les types de tableau ne doivent pas nécessairement être déclarés avant de pouvoir être utilisés. Au lieu de cela, les types de tableaux sont construits en ajoutant des crochets à un nom de type. Par exemple, `int[]` est un tableau unidimensionnel de `int`, `int[,]` est un tableau bidimensionnel de `int`, et `int[][]` est un tableau unidimensionnel d’un tableau unidimensionnel de `int`.

Les types valeur Nullable n’ont pas non plus besoin d’être déclarés avant de pouvoir être utilisés. Pour chaque type valeur qui n’autorise pas les valeurs null `T` , il existe un type valeur Nullable correspondant `T?` qui peut contenir une valeur supplémentaire, `null` . Par exemple, `int?` est un type qui peut contenir un entier 32 bits ou la valeur `null`.

Le système de type C# est unifié de telle façon qu’une valeur de n’importe quel type peut être traitée comme un `object` . Chaque type dans C# dérive directement ou indirectement du type `object`, et `object` est la classe de base fondamentale de tous les types. Les valeurs des types référence sont considérées comme des objets simplement en affichant les valeurs en tant que type `object`. Les valeurs des types valeur sont considérées comme des objets en effectuant des opérations de *boxing* et *d’unboxing*. Dans l’exemple suivant, une valeur `int` est convertie en `object` et à nouveau en `int`.

[!code-csharp[Boxing](../../../samples/snippets/csharp/tour/types-and-variables/Program.cs#L1-L10)]

Quand une valeur d’un type de valeur est assignée à une `object` référence, un « Box » est alloué pour contenir la valeur. Cette zone est une instance d’un type référence, et la valeur est copiée dans cette zone. À l’inverse, lorsqu’une `object` référence est castée en un type valeur, une vérification est effectuée que le référencé `object` est une zone du type valeur correct. Si la vérification est réussie, la valeur dans la zone est copiée dans le type valeur.

Le système de type unifié de C# signifie que les types valeur sont traités comme `object` des références « à la demande ». En raison de l’unification, les bibliothèques à usage général qui utilisent le type `object` peuvent être utilisées avec tous les types qui dérivent de `object` , y compris les types référence et les types valeur.

Il existe plusieurs types de *variables* en C#, y compris les champs, les éléments de tableau, les variables locales et les paramètres. Les variables représentent des emplacements de stockage, et chaque variable possède un type qui détermine les valeurs pouvant être stockées dans la variable, comme indiqué ci-dessous.

- Type de valeur n’acceptant pas Null
  - Une valeur de ce type exact
- Types valeur Nullable
  - Une valeur `null` ou une valeur de ce type exact
- object
  - Une référence `null`, une référence à un objet de tout type référence ou une référence à une valeur boxed de n’importe quel type valeur
- Type de classe
  - Une référence `null`, une référence à une instance de ce type de classe ou une référence à une instance d’une classe dérivée de ce type de classe
- Type d'interface
  - Une référence `null`, une référence à une instance d’un type de classe qui implémente ce type d’interface ou une référence à une valeur boxed d’un type valeur qui implémente ce type d’interface
- Type tableau
  - Une référence `null`, une référence à une instance de ce type de tableau ou une instance d’un type de tableau compatible
- Type délégué
  - Une référence `null` ou une référence à une instance d’un type délégué compatible

> [!div class="step-by-step"]
> [Précédent](program-structure.md) 
>  [Suivant](expressions.md)

---
title: Variables et types C# - Visite guidée du langage C#
description: En savoir plus sur la définition des types et la déclaration de variables en C#
ms.date: 02/25/2020
ms.assetid: f8a8051e-0049-43f1-b594-9c84cc7b1224
ms.openlocfilehash: b2a5255a243c12543a1cd59b5724b6c826306e04
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78159089"
---
# <a name="types-and-variables"></a>Types et variables

Il existe deux genres de types en C# : les *types référence* et les *types valeur*. Les variables des types valeur contiennent directement leurs données alors que les variables des types référence contiennent des références à leurs données, connues sous le nom d’objets. Avec les types de référence, il est possible pour deux variables de référencer le même objet et donc possible pour les opérations sur une variable d’affecter l’objet référencé par l’autre variable. Avec les types de valeur, les variables ont chacune leur propre copie des données, et `ref` `out` il n’est pas possible pour les opérations sur l’un d’affecter l’autre (sauf pour et les variables de paramètres).

Les types de valeur de C# sont divisés entre *types simples*, *types enum*, *types struct* et *types valeur nullable*. Les types de référence de C# sont encore divisés en *types de classes*, *types d’interfaces*, *types de tableaux* et *types délégués*.

Le contour suivant donne un aperçu du système de type de C.

- [Types de valeur][ValueTypes]
  - [Types simples][SimpleTypes]
    - Entier signé : `sbyte`, `short`, `int`, `long`
    - Entier non signé : `byte`, `ushort`, `uint`, `ulong`
    - Caractères Unicode : `char`
    - Virgule flottante pour valeur binaire IEEE : `float`, `double`
    - Virgule flottante pour valeur décimale haute précision : `decimal`
    - Booléen : `bool`
  - [Types Enum][EnumTypes]
    - Types définis par l'utilisateur de la forme `enum E {...}`
  - [Types struct][StructTypes]
    - Types définis par l'utilisateur de la forme `struct S {...}`
  - [types valeur Nullable][NullableTypes]
    - Extensions de tous les autres types de valeurs avec une valeur `null`
- [Types référence][ReferenceTypes]
  - [Types de classe][ClassTypes]
    - Classe de base fondamentale de tous les autres types : `object`
    - Chaînes Unicode : `string`
    - Types définis par l'utilisateur de la forme `class C {...}`
  - [Types interface][InterfaceTypes]
    - Types définis par l'utilisateur de la forme `interface I {...}`
  - [Types de tableaux][ArrayTypes]
    - Uni et multidimensionnels, par exemple `int[]` et `int[,]`
  - [Types délégués][DelegateTypes]
    - Types définis par l'utilisateur de la forme `delegate int D(...)`

[ValueTypes]: ../language-reference/builtin-types/value-types.md
[SimpleTypes]: ../language-reference/builtin-types/value-types.md#built-in-value-types
[EnumTypes]: ../language-reference/builtin-types/enum.md
[StructTypes]: ../language-reference/builtin-types/struct.md
[NullableTypes]: ../language-reference/builtin-types/nullable-value-types.md
[ReferenceTypes]: ../language-reference/keywords/reference-types.md
[ClassTypes]: ../language-reference/keywords/class.md
[InterfaceTypes]: ../language-reference/keywords/interface.md
[DelegateTypes]: ../language-reference/keywords/delegate.md
[ArrayTypes]: ../programming-guide/arrays/index.md

Pour plus d’informations sur les types numériques, consultez [Types intégraux](../language-reference/builtin-types/integral-numeric-types.md) et [Tableau des types à virgule flottante](../language-reference/builtin-types/floating-point-numeric-types.md).

Le type `bool` de C# est utilisé pour représenter des valeurs booléennes, qui peuvent être `true` ou `false`.

Le traitement des caractères et chaînes dans le langage C# utilise l’encodage Unicode. Le type `char` représente une unité de code UTF-16, et le type `string` représente une séquence d’unités de code UTF-16.

Les programmes C# utilisent les *déclarations de type* pour créer de nouveaux types. Une déclaration de type spécifie le nom et les membres du nouveau type. Cinq catégories de types C# sont définies par l’utilisateur : les types de classes, les types struct, les types d’interfaces, les types enum et les types délégués.

Un type `class` définit une structure de données qui contient des données membres (champs) et des fonctions membres (méthodes, propriétés, etc.). Les types de classes prennent en charge l’héritage unique et le polymorphisme, des mécanismes par lesquels les classes dérivées peuvent étendre et spécialiser les classes de base.

Un type `struct` est similaire à un type de classe dans la mesure où il représente une structure avec des membres de données et des membres de fonctions. Cependant, contrairement aux classes, les structs sont des types de valeur et ne nécessitent généralement pas d’allocation de tas. Les types de struct ne prennent pas en charge l’héritage `object`spécifié par l’utilisateur, et tous les types de struct héritent implicitement du type .

Un type `interface` définit un contrat en tant que jeu nommé de membres de la fonction publique. Une `class` ou `struct` qui implémente une `interface` doit fournir des implémentations de fonctions membres de l’interface. Une `interface` peut hériter de plusieurs interfaces de base, et une `class` ou `struct` peut implémenter plusieurs interfaces.

Un type `delegate` représente des références aux méthodes avec une liste de paramètres et un type de retour particuliers. Les délégués permettent de traiter les méthodes en tant qu’entités qui peuvent être affectées à des variables et passées comme paramètres. Les délégués sont semblables aux types de fonction fournis par les langages fonctionnels. Ils sont également similaires au concept de pointeurs de fonction trouvés dans certaines autres langues. Contrairement aux pointeurs de fonction, les délégués sont orientés vers les objets et de type-sûr.

Le `class` `struct`, `interface`, `delegate` , et les types tous les génériques de prise en charge, par lequel ils peuvent être paramétrés avec d’autres types.

Un type `enum` est un type distinct avec des constantes nommées. Chaque type `enum` a un type sous-jacent qui doit être un des huit types intégraux. L’ensemble de valeurs d’un type `enum` est le même que l’ensemble de valeurs du type sous-jacent.

C# prend en charge les tableaux uni et multidimensionnels de tout type. Contrairement aux types énumérés ci-dessus, les types de tableaux n’ont pas besoin d’être déclarés avant qu’ils puissent être utilisés. Au lieu de cela, les types de tableaux sont construits en ajoutant des crochets à un nom de type. Par exemple, `int[]` est un tableau unidimensionnel de `int`, `int[,]` est un tableau bidimensionnel de `int`, et `int[][]` est un tableau unidimensionnel d’un tableau unidimensionnel de `int`.

Les types de valeur nuls n’ont pas non plus à être déclarés avant qu’ils puissent être utilisés. Pour chaque type `T`de valeur non annulable, il `T?`existe un type de `null`valeur nulle correspondant , qui peut contenir une valeur supplémentaire, . Par exemple, `int?` est un type qui peut contenir un entier 32 bits ou la valeur `null`.

Le système de types de C# est unifié afin qu’une valeur de n’importe quel type puisse être traitée en tant que type `object`. Chaque type dans C# dérive directement ou indirectement du type `object`, et `object` est la classe de base fondamentale de tous les types. Les valeurs des types référence sont considérées comme des objets simplement en affichant les valeurs en tant que type `object`. Les valeurs des types valeur sont considérées comme des objets en effectuant des opérations de *boxing* et *d’unboxing*. Dans l’exemple suivant, une valeur `int` est convertie en `object` et à nouveau en `int`.

[!code-csharp[Boxing](../../../samples/snippets/csharp/tour/types-and-variables/Program.cs#L1-L10)]

Quand une valeur d’un type valeur est convertie en type `object`, une instance `object`, également appelée « boîte », est allouée pour contenir la valeur, et la valeur est copiée dans cette boîte. À l’inverse, lorsqu’une référence `object` est castée en un type valeur, une vérification est effectuée pour s’assurer que l’instance `object` est une boîte du bon type valeur, et, si la vérification réussit, la valeur de la zone est copiée.

Le système des types unifié de C# signifie que les types valeur peuvent devenir des objets « à la demande ». En raison de l’unification, les bibliothèques à usage général qui utilisent le type `object` peuvent être utilisées avec les types référence et les types valeur.

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
> [Suivant précédent](program-structure.md)
> [Next](expressions.md)

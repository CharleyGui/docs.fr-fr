---
title: Types de structure - Référence C
ms.date: 02/24/2020
f1_keywords:
- struct_CSharpKeyword
helpviewer_keywords:
- struct keyword [C#]
- struct type [C#]
- structure type [C#]
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
ms.openlocfilehash: b126706ff9c881e5c2d5cc7ee4833ac8896e3fcc
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507241"
---
# <a name="structure-types-c-reference"></a>Types de structure (référence C)

Un *type de structure* (ou type *struct*) est un [type de valeur](value-types.md) qui peut encapsuler les données et les fonctionnalités connexes. Vous utilisez `struct` le mot clé pour définir un type de structure :

[!code-csharp[struct example](snippets/StructType.cs#StructExample)]

Les types de structure ont *la sémantique de valeur.* Autrement dit, une variable d’un type de structure contient une instance du type. Par défaut, les valeurs variables sont copiées sur l’affectation, en transmettant un argument à une méthode et en retournant un résultat de méthode. Dans le cas d’une variable de type structure, un cas du type est copié. Pour plus d’informations, voir [types de valeur](value-types.md).

En règle générale, vous utilisez des types de structure pour concevoir de petits types axés sur les données qui fournissent peu ou pas de comportement. Par exemple, .NET utilise des types de structure pour représenter un nombre (à la fois [integer](integral-numeric-types.md) et [réel](floating-point-numeric-types.md)), une [valeur Boolean](bool.md), un [personnage Unicode](char.md), une [instance temporelle](xref:System.DateTime). Si vous êtes concentré sur le comportement d’un type, envisagez de définir une [classe](../keywords/class.md). Les types de classes ont *la sémantique de référence.* Autrement dit, une variable d’un type de classe contient une référence à une instance du type, et non à l’instance elle-même.

## <a name="limitations-with-the-design-of-a-structure-type"></a>Limitations avec la conception d’un type de structure

Lorsque vous concevez un type de structure, vous avez les mêmes capacités qu’avec un type [de classe,](../keywords/class.md) à quelques exceptions près :

- Vous ne pouvez pas déclarer un constructeur sans paramètres. Chaque type de structure fournit déjà un constructeur implicite sans paramètres qui produit la [valeur par défaut](default-values.md) du type.

- Vous ne pouvez pas initialiser un champ d’instance ou une propriété à sa déclaration. Cependant, vous pouvez initialiser un champ [statique](../keywords/static.md) ou [const](../keywords/const.md) ou une propriété statique à sa déclaration.

- Un constructeur d’un type de structure doit initialiser tous les champs d’instance du type.

- Un type de structure ne peut pas hériter d’un autre type de classe ou de structure et il ne peut pas être la base d’une classe. Cependant, un type de structure peut implémenter [des interfaces](../keywords/interface.md).

- Vous ne pouvez pas déclarer un [finalisateur](../../programming-guide/classes-and-structs/destructors.md) dans un type de structure.

## <a name="instantiation-of-a-structure-type"></a>Instantanéisation d’un type de structure

Dans le C, vous devez initialiser une variable déclarée avant qu’elle puisse être utilisée. Étant donné qu’une `null` variable de type structure ne peut pas être (sauf s’il s’agit d’une variable d’un type de [valeur nul),](nullable-value-types.md)vous devez instantanéiser une instance du type correspondant. Il y a plusieurs façons de le faire.

En règle générale, vous instantanéez un type de [`new`](../operators/new-operator.md) structure en appelant un constructeur approprié avec l’opérateur. Chaque type de structure a au moins un constructeur. C’est un constructeur implicite sans paramètres, qui produit la [valeur par défaut](default-values.md) du type. Vous pouvez également utiliser une [expression de valeur par défaut](../operators/default.md) pour produire la valeur par défaut d’un type.

Si tous les champs d’instance d’un type de `new` structure sont accessibles, vous pouvez également l’instantanér sans l’opérateur. Dans ce cas, vous devez initialiser tous les champs d’instance avant la première utilisation de l’instance. L’exemple suivant montre comment effectuer cette opération :

[!code-csharp[without new](snippets/StructType.cs#WithoutNew)]

Dans le cas des types de [valeur intégrée,](value-types.md#built-in-value-types)utilisez les littérals correspondants pour spécifier une valeur du type.

## <a name="passing-structure-type-variables-by-reference"></a>Passer des variables de type structure par référence

Lorsque vous passez une variable de type structure à une méthode comme argument ou retournez une valeur de type structure à partir d’une méthode, toute l’instance d’un type de structure est copiée. Cela peut affecter les performances de votre code dans des scénarios haute performance qui impliquent de grands types de structure. Vous pouvez éviter la copie de valeur en passant une variable de type structure par référence. Utilisez [`ref`](../keywords/ref.md#passing-an-argument-by-reference)les [`out`](../keywords/out-parameter-modifier.md)modificateurs de paramètres, ou [`in`](../keywords/in-parameter-modifier.md) de méthode pour indiquer qu’un argument doit être adopté par référence. Utilisez [les retours d’arbitre](../../programming-guide/classes-and-structs/ref-returns.md) pour retourner un résultat de méthode par référence. Pour plus d’informations, voir [Écrire un code Cmd sûr et efficace](../../write-safe-efficient-code.md).

## <a name="conversions"></a>Conversions

Pour n’importe quel type de structure, il existe <xref:System.ValueType?displayProperty=nameWithType> <xref:System.Object?displayProperty=nameWithType> des conversions de boxe et [de déballage](../../programming-guide/types/boxing-and-unboxing.md) à et à partir de la et les types. Il existe également des conversions de boxe et de déballage entre un type de structure et toute interface qu’il implémente.

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez la section [Structs](~/_csharplang/spec/structs.md) de la [spécification linguistique C .](~/_csharplang/spec/introduction.md)

## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Lignes directrices de conception - Choisir entre la classe et la struct](../../../standard/design-guidelines/choosing-between-class-and-struct.md)
- [Lignes directrices de conception - Conception de Struct](../../../standard/design-guidelines/struct.md)
- [Classes et structs](../../programming-guide/classes-and-structs/index.md)

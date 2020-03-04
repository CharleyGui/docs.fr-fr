---
title: Types de structures C# -référence
ms.date: 02/24/2020
f1_keywords:
- struct_CSharpKeyword
helpviewer_keywords:
- struct keyword [C#]
- struct type [C#]
- structure type [C#]
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
ms.openlocfilehash: 523269ffc9de9b750330fcefd15a9026d6dc59b8
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239779"
---
# <a name="structure-types-c-reference"></a>Types de structuresC# (référence)

Un type de *structure* (ou *type struct*) est un [type valeur](value-types.md) qui peut encapsuler des données et des fonctionnalités associées. Vous utilisez le mot clé `struct` pour définir un type de structure :

[!code-csharp[struct example](~/samples/snippets/csharp/language-reference/builtin-types/StructType.cs#StructExample)]

Les types de structure ont une *sémantique de valeur*. Autrement dit, une variable d’un type structure contient une instance du type. Par défaut, les valeurs des variables sont copiées lors de l’assignation, en passant un argument à une méthode et en retournant un résultat de méthode. Dans le cas d’une variable de type structure, une instance du type est copiée. Pour plus d’informations, consultez [types valeur](value-types.md).

En général, vous utilisez des types de structure pour concevoir de petits types centrés sur les données qui fournissent peu ou pas de comportement. Par exemple, .NET utilise des types structure pour représenter un nombre ( [entier](integral-numeric-types.md) et [réel](floating-point-numeric-types.md)), une [valeur booléenne](bool.md), un [caractère Unicode](char.md), une [instance d’heure](xref:System.DateTime). Si vous avez le focus sur le comportement d’un type, vous pouvez définir une [classe](../keywords/class.md). Les types de classe ont une *sémantique de référence*. Autrement dit, une variable d’un type de classe contient une référence à une instance du type, et non à l’instance elle-même.

## <a name="limitations-with-the-design-of-a-structure-type"></a>Limitations liées à la conception d’un type structure

Lorsque vous concevez un type structure, vous avez les mêmes fonctionnalités qu’avec un type de [classe](../keywords/class.md) , avec les exceptions suivantes :

- Vous ne pouvez pas déclarer un constructeur sans paramètre. Chaque type de structure fournit déjà un constructeur sans paramètre implicite qui produit la [valeur par défaut](default-values.md) du type.

- Vous ne pouvez pas initialiser un champ ou une propriété d’instance dans sa déclaration. Toutefois, vous pouvez initialiser un champ [statique](../keywords/static.md) ou [const](../keywords/const.md) ou une propriété statique dans sa déclaration.

- Un constructeur d’un type structure doit initialiser tous les champs d’instance du type.

- Un type structure ne peut pas hériter d’un autre type de classe ou de structure et il ne peut pas être la base d’une classe. Toutefois, un type structure peut implémenter des [interfaces](../keywords/interface.md).

- Vous ne pouvez pas déclarer un [finaliseur](../../programming-guide/classes-and-structs/destructors.md) dans un type structure.

## <a name="instantiation-of-a-structure-type"></a>Instanciation d’un type structure

Dans C#, vous devez initialiser une variable déclarée avant de pouvoir l’utiliser. Comme une variable de type structure ne peut pas être `null` (à moins qu’il ne s’agisse d’une variable d’un [type valeur Nullable](nullable-value-types.md)), vous devez instancier une instance du type correspondant. Il existe plusieurs façons de procéder.

En général, vous instanciez un type structure en appelant un constructeur approprié avec l’opérateur [`new`](../operators/new-operator.md) . Chaque type de structure a au moins un constructeur. Il s’agit d’un constructeur sans paramètre implicite, qui produit la [valeur par défaut](default-values.md) du type. Vous pouvez également utiliser l’opérateur ou le littéral [par défaut](../operators/default.md) pour produire la valeur par défaut d’un type.

Si tous les champs d’instance d’un type structure sont accessibles, vous pouvez également l’instancier sans l’opérateur `new`. Dans ce cas, vous devez initialiser tous les champs d’instance avant la première utilisation de l’instance. L’exemple suivant montre comment effectuer cette opération :

[!code-csharp[without new](~/samples/snippets/csharp/language-reference/builtin-types/StructType.cs#WithoutNew)]

Dans le cas des [types valeur intégrés](value-types.md#built-in-value-types), utilisez les littéraux correspondants pour spécifier une valeur du type.

## <a name="passing-structure-type-variables-by-reference"></a>Passage de variables de type structure par référence

Lorsque vous transmettez une variable de type structure à une méthode en tant qu’argument ou que vous retournez une valeur structure-type à partir d’une méthode, l’ensemble de l’instance d’un type structure est copié. Cela peut affecter les performances de votre code dans les scénarios de haute performance qui impliquent des types de structure volumineux. Vous pouvez éviter la copie de valeurs en passant une variable de type structure par référence. Utilisez les modificateurs de paramètre de méthode [`ref`](../keywords/ref.md#passing-an-argument-by-reference), [`out`](../keywords/out-parameter-modifier.md)ou [`in`](../keywords/in-parameter-modifier.md) pour indiquer qu’un argument doit être passé par référence. Utilisez les [retours Ref](../../programming-guide/classes-and-structs/ref-returns.md) pour retourner un résultat de méthode par référence. Pour plus d’informations, consultez [écrire du code C# sécurisé et efficace](../../write-safe-efficient-code.md).

## <a name="conversions"></a>Conversions

Pour tout type de structure, il existe des conversions [boxing et unboxing](../../programming-guide/types/boxing-and-unboxing.md) vers et à partir des types <xref:System.ValueType?displayProperty=nameWithType> et <xref:System.Object?displayProperty=nameWithType>. Il existe également des conversions boxing et unboxing entre un type structure et toute interface qu’il implémente.

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez la section [structs](~/_csharplang/spec/structs.md) de la [ C# spécification du langage](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur C#](../index.md)
- [Instructions de conception-choix entre une classe et une structure](../../../standard/design-guidelines/choosing-between-class-and-struct.md)
- [Directives de conception-conception de struct](../../../standard/design-guidelines/struct.md)
- [Classes et structs](../../programming-guide/classes-and-structs/index.md)

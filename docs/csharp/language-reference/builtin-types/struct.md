---
title: Types de structures-référence C#
description: 'En savoir plus sur le type struct en C #'
ms.date: 10/23/2020
f1_keywords:
- struct_CSharpKeyword
helpviewer_keywords:
- struct keyword [C#]
- struct type [C#]
- structure type [C#]
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
ms.openlocfilehash: daf332dae483d75ef27e78dad5ee912734ccdb5f
ms.sourcegitcommit: 532b03d5bbab764d63356193b04cd2281bc01239
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/26/2020
ms.locfileid: "92526597"
---
# <a name="structure-types-c-reference"></a>Types de structures (référence C#)

Un type de *structure* (ou *type struct*) est un [type valeur](value-types.md) qui peut encapsuler des données et des fonctionnalités associées. Le `struct` mot clé vous permet de définir un type de structure :

[!code-csharp[struct example](snippets/shared/StructType.cs#StructExample)]

Les types de structure ont une *sémantique de valeur*. Autrement dit, une variable d’un type structure contient une instance du type. Par défaut, les valeurs des variables sont copiées lors de l’assignation, en passant un argument à une méthode et en retournant un résultat de méthode. Dans le cas d’une variable de type structure, une instance du type est copiée. Pour plus d’informations, consultez [types valeur](value-types.md).

En général, vous utilisez des types de structure pour concevoir de petits types centrés sur les données qui fournissent peu ou pas de comportement. Par exemple, .NET utilise des types structure pour représenter un nombre ( [entier](integral-numeric-types.md) et [réel](floating-point-numeric-types.md)), une [valeur booléenne](bool.md), un [caractère Unicode](char.md), une [instance d’heure](xref:System.DateTime). Si vous avez le focus sur le comportement d’un type, vous pouvez définir une [classe](../keywords/class.md). Les types de classe ont une *sémantique de référence*. Autrement dit, une variable d’un type de classe contient une référence à une instance du type, et non à l’instance elle-même.

Étant donné que les types de structure ont une sémantique de valeur, nous vous recommandons de définir des types de structures *immuables* .

## <a name="readonly-struct"></a>`readonly` modélis

À compter de C# 7,2, vous utilisez le `readonly` modificateur pour déclarer qu’un type structure est immuable :

[!code-csharp[readonly struct](snippets/shared/StructType.cs#ReadonlyStruct)]

Tous les membres de données d’un `readonly` struct doivent être en lecture seule, comme suit :

- Toute déclaration de champ doit avoir le [ `readonly` modificateur](../keywords/readonly.md)
- Toute propriété, y compris celles implémentées automatiquement, doit être en lecture seule. Dans C# 9,0 et versions ultérieures, une propriété peut avoir un [ `init` accesseur](../../whats-new/csharp-9.md#init-only-setters).

Cela garantit qu’aucun membre d’un `readonly` struct ne modifie l’état de la structure. En C# 8,0 et versions ultérieures, cela signifie que d’autres membres d’instance, à l’exception des constructeurs, sont implicitement [`readonly`](#readonly-instance-members) .

> [!NOTE]
> Dans un `readonly` struct, un membre de données d’un type référence mutable peut toujours muter son propre État. Par exemple, vous ne pouvez pas remplacer une <xref:System.Collections.Generic.List%601> instance, mais vous pouvez lui ajouter de nouveaux éléments.

## <a name="readonly-instance-members"></a>`readonly` membres d’instance

À compter de C# 8,0, vous pouvez également utiliser le `readonly` modificateur pour déclarer qu’un membre d’instance ne modifie pas l’état d’un struct. Si vous ne pouvez pas déclarer le type de structure entier comme `readonly` , utilisez le `readonly` modificateur pour marquer les membres d’instance qui ne modifient pas l’état de la structure.

Dans un `readonly` membre d’instance, vous ne pouvez pas assigner aux champs d’instance de la structure. Toutefois, un `readonly` membre peut appeler un non- `readonly` membre. Dans ce cas, le compilateur crée une copie de l’instance de structure et appelle le non `readonly` membre sur cette copie. Par conséquent, l’instance de la structure d’origine n’est pas modifiée.

En règle générale, vous appliquez le `readonly` modificateur aux genres suivants de membres d’instance :

- leurs

  [!code-csharp[readonly method](snippets/shared/StructType.cs#ReadonlyMethod)]

  Vous pouvez également appliquer le `readonly` modificateur aux méthodes qui remplacent les méthodes déclarées dans <xref:System.Object?displayProperty=nameWithType> :

  [!code-csharp[readonly override](snippets/shared/StructType.cs#ReadonlyOverride)]

- Propriétés et indexeurs :

  [!code-csharp[readonly property get](snippets/shared/StructType.cs#ReadonlyProperty)]

  Si vous devez appliquer le `readonly` modificateur aux deux accesseurs d’une propriété ou d’un indexeur, appliquez-le dans la déclaration de la propriété ou de l’indexeur.

  > [!NOTE]
  > Le compilateur déclare un `get` accesseur d’une [propriété implémentée automatiquement](../../programming-guide/classes-and-structs/auto-implemented-properties.md) en tant que `readonly` , quelle que soit la présence du `readonly` modificateur dans une déclaration de propriété.

  Dans C# 9,0 et versions ultérieures, vous pouvez appliquer le `readonly` modificateur à une propriété ou à un indexeur avec un `init` accesseur :

  :::code language="csharp" source="snippets/shared/StructType.cs" id="ReadonlyWithInit":::

Vous ne pouvez pas appliquer le `readonly` modificateur aux membres statiques d’un type structure.

Le compilateur peut utiliser le `readonly` modificateur pour les optimisations de performances. Pour plus d’informations, consultez [écrire du code C# sécurisé et efficace](../../write-safe-efficient-code.md).

## <a name="limitations-with-the-design-of-a-structure-type"></a>Limitations liées à la conception d’un type structure

Lorsque vous concevez un type structure, vous avez les mêmes fonctionnalités qu’avec un type de [classe](../keywords/class.md) , avec les exceptions suivantes :

- Vous ne pouvez pas déclarer un constructeur sans paramètre. Chaque type de structure fournit déjà un constructeur sans paramètre implicite qui produit la [valeur par défaut](default-values.md) du type.

- Vous ne pouvez pas initialiser un champ ou une propriété d’instance dans sa déclaration. Toutefois, vous pouvez initialiser un champ [statique](../keywords/static.md) ou [const](../keywords/const.md) ou une propriété statique dans sa déclaration.

- Un constructeur d’un type structure doit initialiser tous les champs d’instance du type.

- Un type structure ne peut pas hériter d’un autre type de classe ou de structure et il ne peut pas être la base d’une classe. Toutefois, un type structure peut implémenter des [interfaces](../keywords/interface.md).

- Vous ne pouvez pas déclarer un [finaliseur](../../programming-guide/classes-and-structs/destructors.md) dans un type structure.

## <a name="instantiation-of-a-structure-type"></a>Instanciation d’un type structure

En C#, vous devez initialiser une variable déclarée avant de pouvoir l’utiliser. Comme une variable de type structure ne peut pas être `null` (à moins qu’il ne s’agisse d’une variable d’un [type valeur Nullable](nullable-value-types.md)), vous devez instancier une instance du type correspondant. Il existe plusieurs façons de procéder.

En général, vous instanciez un type structure en appelant un constructeur approprié avec l' [`new`](../operators/new-operator.md) opérateur. Chaque type de structure a au moins un constructeur. Il s’agit d’un constructeur sans paramètre implicite, qui produit la [valeur par défaut](default-values.md) du type. Vous pouvez également utiliser une [expression de valeur par défaut](../operators/default.md) pour produire la valeur par défaut d’un type.

Si tous les champs d’instance d’un type structure sont accessibles, vous pouvez également l’instancier sans l' `new` opérateur. Dans ce cas, vous devez initialiser tous les champs d’instance avant la première utilisation de l’instance. L’exemple suivant montre comment effectuer cette opération :

[!code-csharp[without new](snippets/shared/StructType.cs#WithoutNew)]

Dans le cas des [types valeur intégrés](value-types.md#built-in-value-types), utilisez les littéraux correspondants pour spécifier une valeur du type.

## <a name="passing-structure-type-variables-by-reference"></a>Passage de variables de type structure par référence

Lorsque vous transmettez une variable de type structure à une méthode en tant qu’argument ou que vous retournez une valeur structure-type à partir d’une méthode, l’ensemble de l’instance d’un type structure est copié. Cela peut affecter les performances de votre code dans les scénarios de haute performance qui impliquent des types de structure volumineux. Vous pouvez éviter la copie de valeurs en passant une variable de type structure par référence. Utilisez les [`ref`](../keywords/ref.md#passing-an-argument-by-reference) [`out`](../keywords/out-parameter-modifier.md) [`in`](../keywords/in-parameter-modifier.md) modificateurs de paramètre de méthode, ou pour indiquer qu’un argument doit être passé par référence. Utilisez les [retours Ref](../../programming-guide/classes-and-structs/ref-returns.md) pour retourner un résultat de méthode par référence. Pour plus d’informations, consultez [écrire du code C# sécurisé et efficace](../../write-safe-efficient-code.md).

## <a name="ref-struct"></a>`ref` modélis

À compter de C# 7,2, vous pouvez utiliser le `ref` modificateur dans la déclaration d’un type structure. Les instances d’un `ref` type struct sont allouées sur la pile et ne peuvent pas échapper au tas managé. Pour garantir que, le compilateur limite l’utilisation des `ref` types struct comme suit :

- Un `ref` struct ne peut pas être le type d’élément d’un tableau.
- Un `ref` struct ne peut pas être un type déclaré d’un champ d’une classe ou d’un non- `ref` struct.
- Un `ref` struct ne peut pas implémenter des interfaces.
- Un `ref` struct ne peut pas être converti en <xref:System.ValueType?displayProperty=nameWithType> ou <xref:System.Object?displayProperty=nameWithType> .
- Un `ref` struct ne peut pas être un argument de type.
- Une `ref` variable de struct ne peut pas être capturée par une [expression lambda](../operators/lambda-expressions.md) ou une [fonction locale](../../programming-guide/classes-and-structs/local-functions.md).
- Une `ref` variable de struct ne peut pas être utilisée dans une [`async`](../keywords/async.md) méthode. Toutefois, vous pouvez utiliser des `ref` variables de struct dans des méthodes synchrones, par exemple, dans celles qui retournent <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601> .
- Une `ref` variable de struct ne peut pas être utilisée dans les [itérateurs](../../iterators.md).

En général, vous définissez un `ref` type struct lorsque vous avez besoin d’un type qui comprend également des membres de données de `ref` types struct :

[!code-csharp[ref struct](snippets/shared/StructType.cs#RefStruct)]

Pour déclarer un `ref` struct en tant que [`readonly`](#readonly-struct) , combinez les `readonly` `ref` modificateurs et dans la déclaration de type (le `readonly` modificateur doit précéder le `ref` modificateur) :

[!code-csharp[readonly ref struct](snippets/shared/StructType.cs#ReadonlyRef)]

Dans .NET, les exemples d’un `ref` struct sont <xref:System.Span%601?displayProperty=nameWithType> et <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> .

## <a name="conversions"></a>Conversions

Pour tout type de structure (à l’exception des types [ `ref` struct](#ref-struct) ), il existe des conversions [boxing et unboxing](../../programming-guide/types/boxing-and-unboxing.md) vers et à partir des <xref:System.ValueType?displayProperty=nameWithType> <xref:System.Object?displayProperty=nameWithType> types et. Il existe également des conversions boxing et unboxing entre un type structure et toute interface qu’il implémente.

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez la section [structs](~/_csharplang/spec/structs.md) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).

Pour plus d’informations sur les fonctionnalités introduites dans C# 7,2 et versions ultérieures, consultez les notes de proposition de fonctionnalités suivantes :

- [Structs en lecture seule](~/_csharplang/proposals/csharp-7.2/readonly-ref.md#readonly-structs)
- [Membres d'instance en lecture seule](~/_csharplang/proposals/csharp-8.0/readonly-instance-members.md)
- [Sécurité au moment de la compilation pour les types référence](~/_csharplang/proposals/csharp-7.2/span-safety.md)

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur C#](../index.md)
- [Instructions de conception-choix entre une classe et une structure](../../../standard/design-guidelines/choosing-between-class-and-struct.md)
- [Directives de conception-conception de struct](../../../standard/design-guidelines/struct.md)
- [Classes et structs](../../programming-guide/classes-and-structs/index.md)

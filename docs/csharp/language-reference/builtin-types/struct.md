---
title: Types de structure - Référence C
ms.date: 04/21/2020
f1_keywords:
- struct_CSharpKeyword
helpviewer_keywords:
- struct keyword [C#]
- struct type [C#]
- structure type [C#]
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
ms.openlocfilehash: dbe9b47625589de834b7a8021640885ca0920b96
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "82021270"
---
# <a name="structure-types-c-reference"></a>Types de structure (référence C)

Un *type de structure* (ou type *struct*) est un [type de valeur](value-types.md) qui peut encapsuler les données et les fonctionnalités connexes. Vous utilisez `struct` le mot clé pour définir un type de structure :

[!code-csharp[struct example](snippets/StructType.cs#StructExample)]

Les types de structure ont *la sémantique de valeur.* Autrement dit, une variable d’un type de structure contient une instance du type. Par défaut, les valeurs variables sont copiées sur l’affectation, en transmettant un argument à une méthode et en retournant un résultat de méthode. Dans le cas d’une variable de type structure, un cas du type est copié. Pour plus d’informations, voir [types de valeur](value-types.md).

En règle générale, vous utilisez des types de structure pour concevoir de petits types axés sur les données qui fournissent peu ou pas de comportement. Par exemple, .NET utilise des types de structure pour représenter un nombre (à la fois [integer](integral-numeric-types.md) et [réel](floating-point-numeric-types.md)), une [valeur Boolean](bool.md), un [personnage Unicode](char.md), une [instance temporelle](xref:System.DateTime). Si vous êtes concentré sur le comportement d’un type, envisagez de définir une [classe](../keywords/class.md). Les types de classes ont *la sémantique de référence.* Autrement dit, une variable d’un type de classe contient une référence à une instance du type, et non à l’instance elle-même.

Étant donné que les types de structure ont de la sémantique de valeur, nous vous recommandons de définir les types de structure *immuable.*

## <a name="readonly-struct"></a>`readonly`Struct

En commençant par le C 7.2, vous utilisez le `readonly` modificateur pour déclarer qu’un type de structure est immuable :

[!code-csharp[readonly struct](snippets/StructType.cs#ReadonlyStruct)]

Tous les membres `readonly` de données d’une struct doivent être lus uniquement comme suit :

- Toute déclaration de terrain doit avoir le [ `readonly` modificateur](../keywords/readonly.md)
- Toute propriété, y compris les propriétés auto-mises en œuvre, doit être lue-seulement

Cela garantit qu’aucun `readonly` membre d’une structure ne modifie l’état de la struction.

> [!NOTE]
> Dans `readonly` une struct, un membre des données d’un type de référence mutable peut encore muter son propre état. Par exemple, vous ne <xref:System.Collections.Generic.List%601> pouvez pas remplacer une instance, mais vous pouvez y ajouter de nouveaux éléments.

## <a name="readonly-instance-members"></a>`readonly`membres d’instance

En commençant par le C 8.0, vous pouvez également utiliser le `readonly` modificateur pour déclarer qu’un membre de l’instance ne modifie pas l’état d’une struct. Si vous ne pouvez pas déclarer `readonly`l’ensemble du type de structure comme , utilisez le `readonly` modificateur pour marquer les membres d’instance qui ne modifient pas l’état de la structure. Dans `readonly` une struct, chaque membre `readonly`d’instance est implicitement .

Dans `readonly` un membre d’instance, vous ne pouvez pas attribuer aux champs d’instance de la structure. Cependant, `readonly` un membre peut`readonly` appeler un non-membre. Dans ce cas, le compilateur crée une copie`readonly` de l’instance de la structure et appelle le non-membre sur cette copie. Par conséquent, l’instance de structure d’origine n’est pas modifiée.

En règle générale, vous appliquez le `readonly` modificateur aux types suivants de membres d’instance :

- Méthodes:

  [!code-csharp[readonly method](snippets/StructType.cs#ReadonlyMethod)]

  Vous pouvez également `readonly` appliquer le modificateur aux <xref:System.Object?displayProperty=nameWithType>méthodes qui remplacent les méthodes déclarées dans :

  [!code-csharp[readonly override](snippets/StructType.cs#ReadonlyOverride)]

- propriétés et indexateurs :

  [!code-csharp[readonly property get](snippets/StructType.cs#ReadonlyProperty)]

  Si vous devez `readonly` appliquer le modificateur aux deux accesseurs d’une propriété ou d’un indexeur, appliquez-le dans la déclaration de la propriété ou de l’indexeur.

  > [!NOTE]
  > Le compilateur déclare `get` un accessoiriste d’une [propriété auto-mise en œuvre](../../programming-guide/classes-and-structs/auto-implemented-properties.md) comme, `readonly`indépendamment de la `readonly` présence du modificateur dans une déclaration de propriété.

Vous ne pouvez `readonly` pas appliquer le modificateur aux membres statiques d’un type de structure.

Le compilateur peut utiliser `readonly` le modificateur pour les optimisations de performance. Pour plus d’informations, voir [Écrire un code Cmd sûr et efficace](../../write-safe-efficient-code.md).

## <a name="limitations-with-the-design-of-a-structure-type"></a>Limitations avec la conception d’un type de structure

Lorsque vous concevez un type de structure, vous avez les mêmes capacités qu’avec un type [de classe,](../keywords/class.md) à quelques exceptions près :

- Vous ne pouvez pas déclarer un constructeur sans paramètres. Chaque type de structure fournit déjà un constructeur implicite sans paramètres qui produit la [valeur par défaut](default-values.md) du type.

- Vous ne pouvez pas initialiser un champ d’instance ou une propriété à sa déclaration. Cependant, vous pouvez initialiser un champ [statique](../keywords/static.md) ou [const](../keywords/const.md) ou une propriété statique à sa déclaration.

- Un constructeur d’un type de structure doit initialiser tous les champs d’instance du type.

- Un type de structure ne peut pas hériter d’un autre type de classe ou de structure et il ne peut pas être la base d’une classe. Cependant, un type de structure peut implémenter [des interfaces](../keywords/interface.md).

- Vous ne pouvez pas déclarer un [finalisateur](../../programming-guide/classes-and-structs/destructors.md) dans un type de structure.

## <a name="instantiation-of-a-structure-type"></a>Instantanéisation d’un type de structure

Dans le C, vous devez initialiser une variable déclarée avant qu’elle puisse être utilisée. Étant donné qu’une variable `null` de type structure ne peut pas être (sauf si c’est une variable d’un type de [valeur nul),](nullable-value-types.md)vous devez instantanéiser une instance du type correspondant. Il y a plusieurs façons de le faire.

En règle générale, vous instantanéez un type de [`new`](../operators/new-operator.md) structure en appelant un constructeur approprié avec l’opérateur. Chaque type de structure a au moins un constructeur. C’est un constructeur implicite sans paramètres, qui produit la [valeur par défaut](default-values.md) du type. Vous pouvez également utiliser une [expression de valeur par défaut](../operators/default.md) pour produire la valeur par défaut d’un type.

Si tous les champs d’instance d’un type de `new` structure sont accessibles, vous pouvez également l’instantanér sans l’opérateur. Dans ce cas, vous devez initialiser tous les champs d’instance avant la première utilisation de l’instance. L’exemple suivant montre comment effectuer cette opération :

[!code-csharp[without new](snippets/StructType.cs#WithoutNew)]

Dans le cas des types de [valeur intégrée,](value-types.md#built-in-value-types)utilisez les littérals correspondants pour spécifier une valeur du type.

## <a name="passing-structure-type-variables-by-reference"></a>Passer des variables de type structure par référence

Lorsque vous passez une variable de type structure à une méthode comme argument ou retournez une valeur de type structure à partir d’une méthode, toute l’instance d’un type de structure est copiée. Cela peut affecter les performances de votre code dans des scénarios haute performance qui impliquent de grands types de structure. Vous pouvez éviter la copie de valeur en passant une variable de type structure par référence. Utilisez [`ref`](../keywords/ref.md#passing-an-argument-by-reference)les [`out`](../keywords/out-parameter-modifier.md)modificateurs de paramètres, ou [`in`](../keywords/in-parameter-modifier.md) de méthode pour indiquer qu’un argument doit être adopté par référence. Utilisez [les retours d’arbitre](../../programming-guide/classes-and-structs/ref-returns.md) pour retourner un résultat de méthode par référence. Pour plus d’informations, voir [Écrire un code Cmd sûr et efficace](../../write-safe-efficient-code.md).

## <a name="ref-struct"></a>`ref`Struct

En commençant par le C 7.2, vous pouvez utiliser le `ref` modificateur dans la déclaration d’un type de structure. Les cas `ref` d’un type de struct sont attribués sur la pile et ne peuvent pas s’échapper au tas géré. Pour s’assurer que, le compilateur limite l’utilisation des `ref` types de struct comme suit :

- Une `ref` struct ne peut pas être le type d’élément d’un tableau.
- Une `ref` struct ne peut pas être un type déclaré d’un champ d’une classe ou d’une non-struct.`ref`
- Une `ref` struct ne peut pas implémenter des interfaces.
- Une `ref` struct ne peut pas <xref:System.ValueType?displayProperty=nameWithType> <xref:System.Object?displayProperty=nameWithType>être en boîte ou .
- Une `ref` struct ne peut pas être un argument de type.
- Une `ref` variable structurant ne peut pas être capturée par une [expression lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) ou une [fonction locale.](../../programming-guide/classes-and-structs/local-functions.md)
- Une `ref` variable de struct ne [`async`](../keywords/async.md) peut pas être utilisée dans une méthode. Cependant, vous `ref` pouvez utiliser des variables struct dans les méthodes <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601>synchrones, par exemple, dans ceux qui reviennent ou .
- Une `ref` variable struct ne peut pas être utilisée dans [les itérateurs](../../iterators.md).

En règle générale, vous définissez un `ref` type de struct lorsque vous avez besoin d’un type qui inclut également les données des membres des `ref` types de struct :

[!code-csharp[ref struct](snippets/StructType.cs#RefStruct)]

Pour déclarer `ref` une [`readonly`](#readonly-struct)struct `readonly` comme `ref` , combiner les et `readonly` les modificateurs dans la déclaration de type (le modificateur doit venir avant le `ref` modificateur):

[!code-csharp[readonly ref struct](snippets/StructType.cs#ReadonlyRef)]

Dans .NET, les `ref` exemples <xref:System.Span%601?displayProperty=nameWithType> <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>d’une struct sont et .

## <a name="conversions"></a>Conversions

Pour n’importe quel type de structure <xref:System.ValueType?displayProperty=nameWithType> (sauf <xref:System.Object?displayProperty=nameWithType> [ `ref` ](#ref-struct) les types de struct), il existe des conversions [de boxe et de déballage](../../programming-guide/types/boxing-and-unboxing.md) à et à partir de la et les types. Il existe également des conversions de boxe et de déballage entre un type de structure et toute interface qu’il implémente.

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez la section [Structs](~/_csharplang/spec/structs.md) de la [spécification linguistique C .](~/_csharplang/spec/introduction.md)

Pour plus d’informations sur les fonctionnalités introduites dans C 7.2 et plus tard, voir les notes de proposition de fonctionnalités suivantes :

- [Restructurations de Readonly](~/_csharplang/proposals/csharp-7.2/readonly-ref.md#readonly-structs)
- [Membres d'instance en lecture seule](~/_csharplang/proposals/csharp-8.0/readonly-instance-members.md)
- [Sécurité au moment de la compilation pour les types référence](~/_csharplang/proposals/csharp-7.2/span-safety.md)

## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Lignes directrices de conception - Choisir entre la classe et la struct](../../../standard/design-guidelines/choosing-between-class-and-struct.md)
- [Lignes directrices de conception - Conception de Struct](../../../standard/design-guidelines/struct.md)
- [Classes et structs](../../programming-guide/classes-and-structs/index.md)

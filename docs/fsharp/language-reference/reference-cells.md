---
title: Cellules de référence
description: Découvrez comment F# les cellules de référence sont des emplacements de stockage qui vous permettent de créer des valeurs mutables avec la sémantique de référence.
ms.date: 05/16/2016
ms.openlocfilehash: 2bca7797b272c0e7d5bf54df07041dc08e33709a
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216770"
---
# <a name="reference-cells"></a>Cellules de référence

Les *cellules de référence* sont des emplacements de stockage qui vous permettent de créer des valeurs mutables avec la sémantique de référence.

## <a name="syntax"></a>Syntaxe

```fsharp
ref expression
```

## <a name="remarks"></a>Notes

Pour créer une cellule de référence qui encapsule la valeur, utilisez l'opérateur `ref`. Vous pouvez ensuite modifier la valeur sous-jacente, car elle est mutable.

Une cellule de référence contient une valeur réelle, et pas uniquement une adresse. Lorsque vous créez une cellule de référence à l'aide de l'opérateur `ref`, vous créez une copie de la valeur sous-jacente en tant que valeur mutable encapsulée.

Vous pouvez déréférencer une cellule de référence à l'aide de l'opérateur `!` (bang).

L'exemple de code suivant illustre la déclaration et l'utilisation de cellules de référence.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2201.fs)]

Le résultat est `50`.

Les cellules de référence sont des instances du type d'enregistrement générique `Ref` qui est déclaré comme suit.

```fsharp
type Ref<'a> =
{ mutable contents: 'a }
```

Le type `'a ref` (affiché par le compilateur et IntelliSense dans l'IDE) est un synonyme de `Ref<'a>` (définition sous-jacente).

L'opérateur `ref` crée une cellule de référence. Le code suivant est la déclaration de l'opérateur `ref`.

```fsharp
let ref x = { contents = x }
```

Le tableau suivant répertorie les fonctionnalités disponibles sur la cellule de référence.

|Opérateur, membre ou champ|Description|Type|Définition|
|--------------------------|-----------|----|----------|
|`!` (opérateur de déréférence)|Retourne la valeur sous-jacente.|`'a ref -> 'a`|`let (!) r = r.contents`|
|`:=` (opérateur d'assignation)|Modifie la valeur sous-jacente.|`'a ref -> 'a -> unit`|`let (:=) r x = r.contents <- x`|
|`ref` (opérateur)|Encapsule une valeur dans une nouvelle cellule de référence.|`'a -> 'a ref`|`let ref x = { contents = x }`|
|`Value` (propriété)|Obtient ou définit la valeur sous-jacente.|`unit -> 'a`|`member x.Value = x.contents`|
|`contents` (champ d'enregistrement)|Obtient ou définit la valeur sous-jacente.|`'a`|`let ref x = { contents = x }`|

Vous pouvez accéder à la valeur sous-jacente de plusieurs façons. La valeur retournée par l'opérateur de déréférence (`!`) n'est pas une valeur assignable. Par conséquent, si vous modifiez la valeur sous-jacente, vous devez utiliser à la place l'opérateur d'assignation (`:=`).

La propriété `Value` et le champ `contents` sont des valeurs assignables. Par conséquent, vous pouvez les utiliser pour accéder ou modifier la valeur sous-jacente, comme indiqué dans le code suivant.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2203.fs)]

La sortie est la suivante.

```console
10
10
11
12
```

Le champ `contents` est fourni à des fins de compatibilité avec d'autres versions de ML et produit un avertissement au cours de la compilation. Pour désactiver l'avertissement, utilisez l'option de compilateur `--mlcompatibility`. Pour plus d’informations, consultez l’article [Options du compilateur](compiler-options.md).

C#les programmeurs doivent savoir `ref` que C# dans n’est pas la même `ref` chose F#que dans. Les constructions équivalentes dans F# sont des [types ByRef](byrefs.md), qui sont un concept différent des cellules de référence.

Les valeurs marquées comme pouvant être `mutable` `'a ref` promues automatiquement en s’ils sont capturés par une fermeture ; consultez [valeurs](./values/index.md).

## <a name="see-also"></a>Voir aussi

- [Informations de référence du langage F#](index.md)
- [Paramètres et arguments](parameters-and-arguments.md)
- [Informations de référence des symboles et opérateurs](./symbol-and-operator-reference/index.md)
- [Valeurs](./values/index.md)

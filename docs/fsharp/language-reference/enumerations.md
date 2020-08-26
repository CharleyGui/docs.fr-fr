---
title: Énumérations
description: 'Découvrez comment utiliser des énumérations F # à la place de littéraux pour rendre votre code plus lisible et plus facile à gérer.'
ms.date: 08/15/2020
ms.openlocfilehash: 5f298691ce48a06c203930c7742cf007c819dc33
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812105"
---
# <a name="enumerations"></a>Énumérations

Les *énumérations*, également appelées « *enums*», sont des types intégraux où les étiquettes sont assignées à un sous-ensemble des valeurs. Vous pouvez les utiliser à la place de littéraux pour rendre le code plus lisible et plus facile à gérer.

## <a name="syntax"></a>Syntaxe

```fsharp
type enum-name =
| value1 = integer-literal1
| value2 = integer-literal2
...
```

## <a name="remarks"></a>Notes

Une énumération ressemble à une union discriminée qui a des valeurs simples, sauf que les valeurs peuvent être spécifiées. Les valeurs sont généralement des entiers qui commencent à 0 ou 1, ou des entiers qui représentent des positions de bits. Si une énumération est destinée à représenter des positions de bits, vous devez également utiliser l’attribut [Flags](xref:System.FlagsAttribute) .

Le type sous-jacent de l’énumération est déterminé à partir du littéral utilisé. ainsi, par exemple, vous pouvez utiliser des littéraux avec un suffixe, tel que `1u` , `2u` , et ainsi de suite, pour un type entier non signé ( `uint32` ).

Quand vous faites référence aux valeurs nommées, vous devez utiliser le nom du type d’énumération lui-même en tant que qualificateur, autrement dit, `enum-name.value1` et pas seulement `value1` . Ce comportement diffère de celui des unions discriminées. Cela est dû au fait que les énumérations ont toujours l’attribut [RequireQualifiedAccess](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-requirequalifiedaccessattribute.html) .

Le code suivant illustre la déclaration et l’utilisation d’une énumération.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2101.fs)]

Vous pouvez facilement convertir des énumérations au type sous-jacent à l’aide de l’opérateur approprié, comme indiqué dans le code suivant.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2102.fs)]

Les types énumérés peuvent avoir l’un des types sous-jacents suivants : `sbyte` , `byte` , `int16` , `uint16` , `int32` , `uint32` , `int64` ,, `uint16` `uint64` et `char` . Les types énumération sont représentés dans le .NET Framework en tant que types hérités de qui `System.Enum` , à son tour, sont hérités de `System.ValueType` . Par conséquent, il s’agit de types de valeur situés sur la pile ou inline dans l’objet conteneur, et toute valeur du type sous-jacent est une valeur valide de l’énumération. Cela est important quand vous utilisez des critères spéciaux sur des valeurs d’énumération, car vous devez fournir un modèle qui intercepte les valeurs sans nom.

La `enum` fonction de la bibliothèque F # peut être utilisée pour générer une valeur d’énumération, même une valeur autre que l’une des valeurs nommées prédéfinies. Vous utilisez la `enum` fonction comme suit.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2103.fs)]

La fonction par défaut `enum` fonctionne avec le type `int32` . Par conséquent, il ne peut pas être utilisé avec des types d’énumération qui ont d’autres types sous-jacents. Au lieu de cela, utilisez ce qui suit.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2104.fs)]

En outre, les cas des enums sont toujours émis en tant que `public` . C’est pourquoi ils s’alignent avec C# et le reste de la plate-forme .NET.

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur le langage F #](index.md)
- [Cast et conversions](casting-and-conversions.md)

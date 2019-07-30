---
title: Abréviations de types
description: En savoir F# plus sur les abréviations de type pour donner un nom plus explicite à un type afin de faciliter la lecture du code.
ms.date: 05/16/2016
ms.openlocfilehash: 339b22a675e3f1ad8a3da207053e611942b55a22
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630215"
---
# <a name="type-abbreviations"></a>Abréviations de types

Une *abréviation de type* est un alias ou un nom de remplacement pour un type.

## <a name="syntax"></a>Syntaxe

```fsharp
type [accessibility-modifier] type-abbreviation = type-name
```

## <a name="remarks"></a>Notes

Vous pouvez utiliser des abréviations de type pour donner un nom plus explicite à un type, afin de rendre le code plus facile à lire. Vous pouvez également les utiliser pour créer un nom facile à utiliser pour un type qui est autrement lourd à écrire. En outre, vous pouvez utiliser des abréviations de type pour faciliter la modification d’un type sous-jacent sans modifier l’ensemble du code qui utilise le type. Voici une abréviation de type simple.

L’accessibilité des abréviations de type est `public`définie par défaut sur.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2301.fs)]

Les abréviations de type peuvent inclure des paramètres génériques, comme dans le code suivant.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2302.fs)]

Dans le code précédent, `Transform` est une abréviation de type qui représente une fonction qui accepte un argument unique de n’importe quel type et qui retourne une valeur unique de ce même type.

Les abréviations de type ne sont pas conservées dans le code MSIL .NET Framework. Par conséquent, lorsque vous utilisez F# un assembly d’un autre langage de .NET Framework, vous devez utiliser le nom de type sous-jacent pour une abréviation de type.

Les abréviations de type peuvent également être utilisées sur les unités de mesure. Pour plus d’informations, consultez [unités de mesure](units-of-measure.md).

## <a name="see-also"></a>Voir aussi

- [Informations de référence du langage F#](index.md)

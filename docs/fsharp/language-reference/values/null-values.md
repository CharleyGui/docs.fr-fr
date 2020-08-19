---
title: Valeurs Null
description: 'Découvrez comment la valeur null est utilisée dans le langage de programmation F #.'
ms.date: 08/15/2020
ms.openlocfilehash: 3b2c7ebe7b8eff08f7c3e76b9715ccab1bbd5d36
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88558346"
---
# <a name="null-values"></a>Valeurs Null

Cette rubrique décrit comment la valeur null est utilisée en F #.

## <a name="null-value"></a>Valeur Null

La valeur NULL n’est généralement pas utilisée dans F # pour les valeurs ou les variables. Toutefois, NULL apparaît comme une valeur anormale dans certaines situations. Si un type est défini en F #, NULL n’est pas autorisé comme valeur normale, sauf si l’attribut [AllowNullLiteral](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-allownullliteralattribute.html#Value) est appliqué au type. Si un type est défini dans un autre langage .NET, NULL est une valeur possible et, lorsque vous interagitez avec ces types, votre code F # peut rencontrer des valeurs NULL.

Pour un type défini en F # et utilisé uniquement à partir de F #, la seule façon de créer une valeur null à l’aide de la bibliothèque F # directement consiste à utiliser [unchecked. defaultof](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-operators-unchecked.html#defaultof) ou [Array. zeroCreate](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#zeroCreate). Toutefois, pour un type F # utilisé à partir d’autres langages .NET, ou si vous utilisez ce type avec une API qui n’est pas écrite en F #, comme le .NET Framework, des valeurs NULL peuvent se produire.

Vous pouvez utiliser le `option` type en F # quand vous pouvez utiliser une variable de référence avec une valeur NULL possible dans un autre langage .net. Au lieu de null, avec un type F # `option` , vous utilisez la valeur d’option `None` s’il n’y a pas d’objet. Vous utilisez la valeur `Some(obj)` d’option avec un objet `obj` en présence d’un objet. Pour plus d’informations, consultez [Options ](../options.md). Notez que vous pouvez toujours compresser une `null` valeur dans une option si, pour `Some x` , `x` se produit `null` . Pour cette raison, il est important d’utiliser `None` quand une valeur est `null` .

Le `null` mot clé est un mot clé valide en langage F #, et vous devez l’utiliser lorsque vous travaillez avec des api .NET Framework ou d’autres API écrites dans un autre langage .net. Les deux situations dans lesquelles vous pouvez avoir besoin d’une valeur NULL sont lorsque vous appelez une API .NET et transmettez une valeur null en tant qu’argument, et lorsque vous interprétez la valeur de retour ou un paramètre de sortie d’un appel de méthode .NET.

Pour passer une valeur null à une méthode .NET, utilisez simplement le `null` mot clé dans le code appelant. L'exemple de code suivant illustre ceci.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet701.fs)]

Pour interpréter une valeur null obtenue à partir d’une méthode .NET, utilisez des critères spéciaux si vous le pouvez. L’exemple de code suivant montre comment utiliser des critères spéciaux pour interpréter la valeur null retournée par `ReadLine` lorsqu’il tente de lire au-delà de la fin d’un flux d’entrée.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet702.fs)]

Les valeurs NULL pour les types F # peuvent également être générées d’autres façons, par exemple lorsque vous utilisez `Array.zeroCreate` , qui appelle `Unchecked.defaultof` . Vous devez faire attention à ce type de code pour conserver les valeurs NULL encapsulées. Dans une bibliothèque prévue uniquement pour F #, vous n’avez pas besoin de rechercher les valeurs NULL dans chaque fonction. Si vous écrivez une bibliothèque pour l’interopérabilité avec d’autres langages .NET, vous devrez peut-être ajouter des vérifications pour les paramètres d’entrée null et lever un `ArgumentNullException` , comme vous le feriez en C# ou Visual Basic code.

Vous pouvez utiliser le code suivant pour vérifier si une valeur arbitraire est null.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet703.fs)]

## <a name="see-also"></a>Voir aussi

- [Valeurs](index.md)
- [Expressions de correspondance](../match-expressions.md)

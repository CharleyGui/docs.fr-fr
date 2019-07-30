---
title: Valeurs Null
description: Découvrez comment la valeur null est utilisée dans le F# langage de programmation.
ms.date: 03/22/2019
ms.openlocfilehash: 2038c0a461fec9884c51edd50c3c9f336104e30e
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630803"
---
# <a name="null-values"></a>Valeurs Null

Cette rubrique décrit comment la valeur null est utilisée dans F#.

## <a name="null-value"></a>Valeur null

La valeur NULL n’est généralement pas utilisée F# dans pour les valeurs ou les variables. Toutefois, NULL apparaît comme une valeur anormale dans certaines situations. Si un type est défini dans F#, NULL n’est pas autorisé comme valeur normale, sauf si l’attribut [AllowNullLiteral](https://msdn.microsoft.com/library/4f315196-f444-4cca-ba07-1176ff71eb0f) est appliqué au type. Si un type est défini dans un autre langage .NET, NULL est une valeur possible et, lorsque vous interagitez avec ces types, votre F# code risque de rencontrer des valeurs NULL.

Pour un type défini dans F# et utilisé strictement à F#partir de, la seule façon de créer une valeur null F# à l’aide de la bibliothèque directement consiste à utiliser unchecked [. defaultof](https://msdn.microsoft.com/library/9ff97f2a-1bd4-4f4c-afbe-5886a74ab977) ou [Array. zeroCreate](https://msdn.microsoft.com/library/fa5b8e7a-1b5b-411c-8622-b58d7a14d3b2). Toutefois, pour un F# type utilisé à partir d’autres langages .net, ou si vous utilisez ce type avec une API qui n’est pas écrite F#dans, comme le .NET Framework, des valeurs NULL peuvent se produire.

Vous pouvez utiliser le `option` type dans F# quand vous pouvez utiliser une variable de référence avec une valeur NULL possible dans un autre langage .net. Au lieu de null, avec F# `option` un type, vous utilisez la valeur `None` d’option s’il n’y a pas d’objet. Vous utilisez la valeur `Some(obj)` d’option avec un objet `obj` en présence d’un objet. Pour plus d’informations, consultez [Options ](../options.md). Notez que vous pouvez toujours compresser `null` une valeur dans une option si, pour `Some x`, `x` se `null`produit. Pour cette raison, il est important d’utiliser `None` quand une valeur est `null`.

Le `null` mot clé est un mot clé valide F# dans le langage, et vous devez l’utiliser lorsque vous travaillez avec des API .NET Framework ou d’autres API qui sont écrites dans un autre langage .net. Les deux situations dans lesquelles vous pouvez avoir besoin d’une valeur NULL sont lorsque vous appelez une API .NET et transmettez une valeur null en tant qu’argument, et lorsque vous interprétez la valeur de retour ou un paramètre de sortie d’un appel de méthode .NET.

Pour passer une valeur null à une méthode .net, utilisez simplement le `null` mot clé dans le code appelant. L'exemple de code suivant illustre ceci.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet701.fs)]

Pour interpréter une valeur null obtenue à partir d’une méthode .NET, utilisez des critères spéciaux si vous le pouvez. L’exemple de code suivant montre comment utiliser des critères spéciaux pour interpréter la valeur null retournée par `ReadLine` lorsqu’il tente de lire au-delà de la fin d’un flux d’entrée.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet702.fs)]

Les valeurs null F# pour les types peuvent également être générées d’autres façons, par exemple `Array.zeroCreate`lorsque vous utilisez `Unchecked.defaultof`, qui appelle. Vous devez faire attention à ce type de code pour conserver les valeurs NULL encapsulées. Dans une bibliothèque prévue uniquement pour F#, il n’est pas nécessaire de rechercher les valeurs NULL dans chaque fonction. Si vous écrivez une bibliothèque pour l’interopérabilité avec d’autres langages .net, vous devrez peut-être ajouter des vérifications pour les paramètres `ArgumentNullException`d’entrée null et lever un C# , de la même façon que dans ou Visual Basic code.

Vous pouvez utiliser le code suivant pour vérifier si une valeur arbitraire est null.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet703.fs)]

## <a name="see-also"></a>Voir aussi

- [Valeurs](index.md)
- [Expressions match](../match-expressions.md)

---
title: Types d'exceptions
description: 'Découvrez comment définir et utiliser les types d’exception F #.'
ms.date: 05/16/2016
ms.openlocfilehash: 8b4ceec31a2d68abbcd025812ffeeefc0c090efb
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557227"
---
# <a name="exception-types"></a>Types d'exceptions

Il existe deux catégories d’exceptions en F # : les types d’exception .NET et les types d’exception F #. Cette rubrique explique comment définir et utiliser les types d’exception F #.

## <a name="syntax"></a>Syntaxe

```fsharp
exception exception-type of argument-type
```

## <a name="remarks"></a>Notes

Dans la syntaxe précédente, *exception-type* est le nom d’un nouveau type d’exception F #, et *argument-type* représente le type d’un argument qui peut être fourni lorsque vous levez une exception de ce type. Vous pouvez spécifier plusieurs arguments à l’aide d’un type de tuple pour l' *argument-type*.

Une définition type pour une exception F # ressemble à ce qui suit.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5501.fs)]

Vous pouvez générer une exception de ce type à l’aide de la `raise` fonction, comme suit.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5502.fs)]

Vous pouvez utiliser un type d’exception F # directement dans les filtres d’une `try...with` expression, comme indiqué dans l’exemple suivant.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5503.fs)]

Le type d’exception que vous définissez avec le `exception` mot clé en F # est un nouveau type qui hérite de `System.Exception` .

## <a name="see-also"></a>Voir aussi

- [Gestion des exceptions](index.md)
- [Exceptions : la `raise` fonction](the-raise-function.md)
- [Hiérarchie des exceptions](../../../standard/exceptions/index.md)

---
title: Types d'exceptions
description: Découvrez comment définir et utiliser F# des types d’exception.
ms.date: 05/16/2016
ms.openlocfilehash: 8545fab50ff6338d1f1621710a838a200f9ac705
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630317"
---
# <a name="exception-types"></a>Types d'exceptions

Il existe deux catégories d’exceptions dans F#: les types d’exception F# .net et les types d’exception. Cette rubrique explique comment définir et utiliser F# des types d’exception.

## <a name="syntax"></a>Syntaxe

```fsharp
exception exception-type of argument-type
```

## <a name="remarks"></a>Notes

Dans la syntaxe précédente, *exception-type* est le nom d’un nouveau F# type d’exception, et *argument-type* représente le type d’un argument qui peut être fourni lorsque vous levez une exception de ce type. Vous pouvez spécifier plusieurs arguments à l’aide d’un type de tuple pour l' *argument-type*.

Une définition classique d’une F# exception ressemble à ce qui suit.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5501.fs)]

Vous pouvez générer une exception de ce type à l’aide `raise` de la fonction, comme suit.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5502.fs)]

Vous pouvez utiliser un F# type d’exception directement dans les filtres d' `try...with` une expression, comme indiqué dans l’exemple suivant.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5503.fs)]

Le type d’exception que vous définissez avec `exception` le mot F# clé dans est un nouveau type qui hérite de `System.Exception`.

## <a name="see-also"></a>Voir aussi

- [Gestion des exceptions](index.md)
- [Exceptions : fonction `raise`](the-raise-function.md)
- [Hiérarchie des exceptions](https://msdn.microsoft.com/library/z4c5tckx.aspx)

---
title: 'Exceptions : invalidArg (fonction)'
description: Découvrez comment la F# fonction « invalidArg » génère une exception d’argument.
ms.date: 05/16/2016
ms.openlocfilehash: 6b1c5fdb5a541da336977d3a67d471302edb36b6
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2019
ms.locfileid: "71083009"
---
# <a name="exceptions-the-invalidarg-function"></a>Exceptions : invalidArg (fonction)

La `invalidArg` fonction génère une exception d’argument.

## <a name="syntax"></a>Syntaxe

```fsharp
invalidArg parameter-name error-message-string
```

## <a name="remarks"></a>Notes

Le nom du paramètre dans la syntaxe précédente est une chaîne avec le nom du paramètre dont l’argument n’était pas valide. La *chaîne de message d’erreur* est une chaîne littérale ou une valeur de `string`type. Il devient la `Message` propriété de l’objet exception.

L’exception générée par `invalidArg` est une `System.ArgumentException` exception. Le code suivant illustre l’utilisation de `invalidArg` pour lever une exception.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6101.fs)]

La sortie est la suivante, suivie d’une trace de la pile (non affichée).

```console
December
January
System.ArgumentException: Month parameter out of range.
```

## <a name="see-also"></a>Voir aussi

- [Gestion des exceptions](index.md)
- [Types d'exceptions](exception-types.md)
- [Exceptions : L' `try...with` expression](the-try-with-expression.md)
- [Exceptions : L' `try...finally` expression](the-try-finally-expression.md)
- [Exceptions : fonction `raise`](the-raise-function.md)
- [Exceptions : La `failwith` fonction](the-failwith-function.md)

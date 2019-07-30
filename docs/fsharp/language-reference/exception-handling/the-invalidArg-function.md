---
title: 'Exceptions : invalidArg (fonction)'
description: Découvrez comment la F# fonction «invalidArg» génère une exception d’argument.
ms.date: 05/16/2016
ms.openlocfilehash: 010dbfe313f539093b4ee7a19984ef54500b072d
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630306"
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

```
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

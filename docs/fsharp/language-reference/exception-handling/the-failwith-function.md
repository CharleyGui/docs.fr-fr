---
title: 'Exceptions : failwith (fonction)'
description: Découvrez comment la fonction «failwith» génère une F# exception.
ms.date: 05/16/2016
ms.openlocfilehash: f2c86362d5bdde7bab55751f019965a5f4ca6236
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630325"
---
# <a name="exceptions-the-failwith-function"></a>Exceptions : failwith (fonction)

La `failwith` fonction génère une F# exception.

## <a name="syntax"></a>Syntaxe

```fsharp
failwith error-message-string
```

## <a name="remarks"></a>Notes

La *chaîne de message d’erreur* dans la syntaxe précédente est une chaîne littérale ou une valeur de `string`type. Il devient la `Message` propriété de l’exception.

L' `failwith` exception générée par est une `System.Exception` exception, qui est une référence qui porte le nom `Failure` dans F# le code. Le code suivant illustre l’utilisation de `failwith` pour lever une exception.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6001.fs)]

## <a name="see-also"></a>Voir aussi

- [Gestion des exceptions](index.md)
- [Types d'exceptions](exception-types.md)
- [Exceptions : L' `try...with` expression](the-try-with-expression.md)
- [Exceptions : L' `try...finally` expression](the-try-finally-expression.md)
- [Exceptions : fonction `raise`](the-raise-function.md)
